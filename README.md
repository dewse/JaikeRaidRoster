# JaikeRaidRoster

First update: I started using a googlesheet someone created to keep track of relic types and class roster for raids since we expected relic stacking to be an issue early xpac. Anyway, I've longed since then created more tabs and functionality from that original sheet. At this time this is what it containts on the main page:

* Each tab automatically fills player's name in their rows.
* Keeping tab of many of the player's values, such as Rank, Ilvl, specs
* Store info on all classes/spec: Primary stat, Top secondary stats (based on icyveins), Gear type, Role (melee, ranged, heal, tank), CCs and utility, Pawn strings.
* This information is then provided on the frontpage for each class, along with player's profession
* Metadata added to "ROSTER_FRONTPAGE* This information is gathered to show a counter for each of these previously mentioned values to assess raid needs. Additionally, it shows melee/ranged ratio, tank/heal/dps ratio. 
* Automatic timestamp when someone changes their ilvl or HoA rank.
* Every column has an average at the bottom to compare player to team's value.
* Attendance percentage average from the start of the tier (info gathered from Attendance tab)
* Ranking average (info gathered from Rankings_Beta)
* Totalscore that takes value from ilvl and ranks (used to be more, but they removed tier and legendaries)

((ILVL * 10) * ((HoA Ranks * 0.1) +40))

# Char_DB

Previously, all info was to be modified by the roster in "ROSTER_FRONTPAGE". However, given the amount of auto-calculated fields and the conditional formatting, I decided to switch all the user-inputed data to its own sheet, "Char_DB" that lacks these. Now every other sheet pulls its info from that sheet, using the ID on the left and VLOOKUP functions.

# Attendance TAB

This tab is the backend of the single value cell in Roster_Gear_Ranks. You could keep it open, but we protect the range from non-admin edits. It contains the month OCT to MAR. Input between 0-6 into the player's day. You could change the values to your own guild's fit. For our own, the number's values are as follows:

* 0 = Missing w/out notice -- 3 within a tier, OUT -- Unless extreme emergencies
* 1 = Missing with notice -- No more than 10% per tier
* 2 = Beyond 10 mins or within 10 mins but without notice
* 3 = Late within 10 mins but with notice given prior to raid start
* 4 = Attended
* 5 = 15 minutes early

Column P (and similar) will only show a green O if the player is wasn't late or missing on any of the days that month.
The column TOTAL is the totality of every day of attendance since the start of October. This value is the one that is returned on the Attendance column in Roster_Gear_Ranks

# Rankings TAB

This window is also a backend for the admins to input the rankings of a night. It is fairly identical in layout as Attendance. The value that should be input into the cells is the average of a player's ilvl bracket ranking% for each boss fight. Currently warcraftlogs does not have an API to do this, so my work around that is friendly for non-coders is to just select the entire page of all the rankings of warcraftlogs and paste it into googlesheet. Currently I'm still working on adding this to the live sheet, but it's either going to be much lower on Ranking_Beta or it will be in its own window. I have codes that gather all the information from the cells it needs and then sums all the findings to give an average ilvl ranking, which will add the end value that you can just copy paste into that raid's rankings.

# Death TAB

This sheet is meant to keep track of every 2 first deaths of every player in every encounter, regardless of a kill or a wipe. The numbers are then averaged out and shown on Roster_Frontpage.

# DRS TAB

This is where I now store the 2 scrappers.

1. 1st and 2nd death Scrapper
    To use this, you'll want to go on a warcraftlog entry and click death. At the bottom, you should see a table with %. Copy the entire thing and paste it into the scrapper and it will calculate every one of your raider's deaths in order so you can simply copy and special paste (value only) into that day's column in the "Deaths" sheet.
    
2. Average ilvl bracket ranking scrapper.
    Once needed to see the average of all the ilvl bracket ranks from warcraftlogs. Now they make it easier, so this scrapper serves to reorganize the names in order to be able to copy + special paste (value) into the corresponding column in the "Rankings" sheet.
    
# UTIL_CC

Using the data in "ADMIN", it shows every CC/utility that the core has at their disposal. This is primarily to know what you have plenty of and what you are lacking.

# CG_PROG

This is the newest sheet. The purpose of this portion is to copy + special paste (value) from "ROSTER_FRONTPAGE" every week. The purpose of this is 2-fold. The main one is to have an idea how much progress folks are doing on gearing up as the weeks go by. The 2nd one is to ensure that folks actually update their sheet every week, otherwise, their average will be lower.
