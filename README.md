# OldOnes

Developed with Unreal Engine 4

On release buid Important:
DO enable *actor Hidden in game* for the BP_RoomSetup Object before release as it will improve loading performance.

Important:
DO NOT EVER touch the CardID attribute in the DataTable

Create Socket Called WidgetSocket were you want the UI of 3D actors to attach to

Cards cannot be in the hand at the start of the game they would need to be drawn

When making a card in the DataTable that targets Cards:
Targets Restrictions on Location and type do not need a value. The tags can all be gathered with the action.
For actions such as CardPick, Discard and Exile the attribute value of the action will always be the same on the Action Tag and the TargetingStyle Tag. They can, and should, be kept in the same AttributeTag (DataTable creation)
On the note of CardTarget Restriction. Location and Type are both mandatory (there is an Any tag if you don't want any restriction)
CardLocation Attribute must all be in the same AttributeTags slot (in DataTable Card creation). Since there is no value attached to those it should not cause any issue
Same Goes for the CardType 
It is true even for Cards you get by name (you will have to give the type of the card (or any)). This is due to the underlying card search system which first has to get all valid cards from Type and Location restrictions before looking into more restrictive conditions

I do not support restrictive conditions as of yet (only card types, location and name)

For invest; abilities that have a negative value will consume invest points. To have those invest be points being mandatory for play use the *TargetsRestiction->AllTargetsValid*. In this case it will prevent the player from using that ability (from card or relic) if they don't have enough invest points to pay.
Allows for invest to be used as a secondary resource.


TODO:
====
You can still activate multiple relics at the same time and so on. This is also due to the inner ability system not taking into account the run wide / rewards nature of the game yet when checking for playability.

make a view of cards when right clicking them

More advanced hovering that show card text ability, cards in deck etc

Make an UI to show where the pointer is at for targeting enemies / investigables

There is no queueing of animation. Just a small delay for widget movements. This means that a widget will not finish an animation before starting another. It can cause bugs like the one where a card doesnt get to flip before being drawn.

Known Issues:

Sometimes Releasing a card from a grab doesn't work
Sometimes Cards don't turn up when being drawn: This has been temporarly fixed by forcing cards in hand to be face up

There can be only one Specifically targetable ability per cards. A queue need to be implemented: BP_AbilityTargetingManager::EventGraph > GoToNextTargetManagementInQueue
===

!!! Big optimization!!!
When restarting the game the player UI the card views for them to be refiled later by the game instance. This could be optimized with more thinking of what cards and views can be kept.
It goes similarly for the Enemy actors that could be kept in memory at the end of a fight to have just their skeleton changed and their stats reseted
!!! !!!

Size of 2DArtAssets:
Cards are 1440x2560 with no border
Frames are 2160x3840 with 6 white border on top 10 bottom 32 on sides (tentacules)
Pure frame: 194 top 200 botton 137 sides
Mana / Card Types Icons are 600x600 circle shaped with 10 pixels on extremities
EnemyHealthbar container: 1920x461. Bar starts at: Left: 181, Top: 155, bottom 300, right: 1741
