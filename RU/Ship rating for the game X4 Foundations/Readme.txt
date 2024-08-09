Introduction.
This project is dedicated to the game X4 Foundations and its purpose is to estimate all ships player can access to and compute its rank.

Used: Pandas, numpy, matplotlib, requests, beatifulsoup, regular expressions, tableau.

To show the ranks of ships I constructed dashboard on th  public Tableau server and you can see it on the link:
https://public.tableau.com/views/TheshipratingforthegameX4Foundations/Shiprating?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link

Description:
The ships are divided into segments by its purpose and dense ranking method was used to assign ranking points in increasing order to parameters a player can see on in-game ship-building or purchase screen.
How ranking was done: ships divided into categories - carriers, destroyers, fighters etc. For each parameter ship is awarded one point in ascending order, starting with 1 point for the last place, dense ranking was used (ships with the equal values have equal ranking points). Then, for each ship, the points scored for each parameter are summed up to get the total number of points.
Assumptions were made:
1) excluded ships that are single in their group like Teuta and Manticora;
2)Barbarossa assigned to freighters, Dragon Raider - to corvettes, Guppy assigned to carriers though it is not an XL ship.
3) excluded racing ships from DLC:Timelines

The changes to the previous version:
1.The previous version calculated only total ranking points across all parameters and as there was an abundance of parameters related to mass of a ship and its speed, the ships with lower mass and good speed accumulated more ranking points and other ships did not have "enough space" to reach them on other parameters.
Now the parameters were divided into 2 major groups - combat and flight parameters and the rating was calculated for the both groups. In addition, the combined rating was calculated based on the sum of all points gained by ship in a category for all parameters.

The group of combat parameters: hull, unit storage, max shield (computed on the base of the best shield a ship can use), aggregate defense (hull + max shield), the number of S/M docks, the capacity of S/M ships, the number of primary weapons, the number of L/M turrets, crew size (for M,L,XL ships).

The group of flight parameters: maximum speed (computed on the best engine the ship can use), maximum acceleration, time to reach max speed (lower value is the better), maximum travel speed(computed on the best travel version of engines a ship can use or if not travel version - on the engine with the best travel potential), strafe speed, strafe acceleration, yaw acceleration, maximum yaw speed, yaw sluggishness (time to reach max yaw speed, the lower value is better), pitch acceleration, maximum pitch speed, pitch sluggishness, roll acceleration, maximum roll speed, roll sluggishness, cargo volume (added here so that rating is suited better to compare trade ships and miners).

2. To avoid an overabundance of ships in the miner's segment all miners were split into mineral and gas subgroups(and actually the ore and gas versions of the same miner can have differences).
3. Armament parameters and the number of S/M docks and the capacity of S/M ships were added to calculations.
