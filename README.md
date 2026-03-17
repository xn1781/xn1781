```lua
--!strict

type Project = {
	name: string,
	description: string,
	languages: string,
	tools: string,
}

type Profile = {
	name: string,
	aliases: { [number]: string },
	socials: { [string]: string },
	currentGoals: string,
	currentProjects: { [number]: Project },
	pastProjects: { [number]: Project },

	showProfile: (Profile) -> (),
}

local MyProfile = {
	name = "xn1781",
	aliases = { "len" },
	socials = {
		["discord"] = "xn1781",
		["youtube"] = "@xn-1781",
		["roblox"] = "664FEB74873A00E0E6CC",
	},

	currentGoals = "Learning how to make a website and also Python",

	currentProjects = {
		{
			name = "Ore ESP",
			description = "A cheat that allows you to see any ore through blocks.",
			languages = "python",
			tools = "Visual Studio Code, Minescript",
		},

		{
			name = "Brainrot Race",
			description = "A game based on racing to grab as many brainrots as possible while avoiding obstacles before the timer runs out.",
			languages = "luau",
			tools = "Visual Studio Code, Rojo, Rokit, Wally, Git",
		},
	},

	pastProjects = {
		{
			name = "ReHydra",
			description = 'A cheat for the ROBLOX game "Combat Warriors" which has features such as godmode, invisibility, destroy maps and infinite credits.\n    (All of these vulnerabilites have been reported to the developers before they were public)',
			languages = "luau",
			tools = "Visual Studio Code",
		},

		{
			name = "Grow A Garden Modded",
			description = "A modified version of Grow A Garden which was able to gain around 30k+ CCU.",
			languages = "luau",
			tools = "Visual Studio Code, Rojo",
		},

		{
			name = "99 Nights In The Forest Modded",
			description = "A modified version of 99 Nights In The Forest which was able to gain around 100k+ CCU.",
			languages = "luau",
			tools = "Visual Studio Code, Rojo",
		},

		{
			name = "Trade RNG",
			description = "An RNG game that centers around trading with your limiteds.",
			languages = "luau",
			tools = "Visual Studio Code, Rojo",
		},
	},
} :: Profile

-- Appends a list of projects to profile
-- @param list The projects to append to profile
-- @param myProfile Current profile string
-- @return myProfile The profile which has all projects appended to
local function appendProjects(projectList: { [number]: Project }, myProfile: string)
	for index, project in projectList do
		myProfile ..= string.format(
			"\n  > %s [%s]\n    Description: %s\n    Tools: %s",
			project.name,
			project.languages,
			project.description,
			project.tools
		)
	end

	return myProfile
end

-- Displays the profile
function MyProfile:showProfile()
	local headerTemplate = [[
%s (Aka: %s)
Current Goals: %s

All my socials:]]

	local myProfile = string.format(headerTemplate, self.name, table.concat(self.aliases, ", "), self.currentGoals)
	for platform, handle in self.socials do
		local formattedPlatform = platform:sub(1, 1):upper() .. platform:sub(2)
		myProfile ..= string.format("\n  - %s: %s", formattedPlatform, handle)
	end

	myProfile ..= "\n\nCurrent Projects:"
	myProfile = appendProjects(self.currentProjects, myProfile)
	myProfile ..= "\n\nPast Projects:"
	myProfile = appendProjects(self.pastProjects, myProfile)

	print(myProfile)
end

MyProfile:showProfile()

```
