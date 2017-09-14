# JaikeRaidRoster

First update: I started using a googlesheet someone created to keep track of relic types and class roster for raids since we expected relic stacking to be an issue early xpac. Anyway, I've longed since then created more tabs and functionality from that original sheet. At this time this is what it containts on the main page:

* Each tab automatically fills player's name in their rows.
* Keeping tab of many of the player's values, such as Rank, Ilvl, number of BiS legendaries (2-4th BiS worth 0.5 value)
* Category to input each tier pieces raiders have, and sums total individual pieces at the bottom.
* Autocalculate those pieces to state T20 Bonus status --> -- OR (2) Bonus! OR (4) Bonus!
* Professions
* Last updated field
* Every column has an average at the bottom to compare player to team's value.
* Attendance percentage average from the start of the tier (info gathered from Attendance tab)
* Ranking average (info gathered from Rankings_Beta)
* Totalscore that takes value from ilvl, ranks, legend, and set bonus

Totalscore = Ranks * Ilvl * Legend * T20Bonus

* RANKS:0 to 51 =0, 52=1, additional points=0.07 (which is a full concord divided by 1/13.33 since it only gives that much for each additional)
* Ilvl: value x 5
* Legend: 0=1, additional points=0.2
* T20 Bonus: 0=1, (2)=1.05, (4)=1.2

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
