# OldOnes

Developed with Unreal Engine 4

Important:
Cards are assumed to ALWAYS be in Draw pile at start of a game for initialization of View and so on. Be careful not to add cards to Discard before the game has started. They should be sent there on first turn

When making a card in the DataTable that targets Cards:
Targets Restrictions on Location and type do not need a value. The tags can all be gathered with the action.
For actions such as CardPick, Discard and Exile the attribute value of the action will always be the same on the Action Tag and the TargetingStyle Tag. They can, and should, be kept in the same AttributeTag (DataTable creation)
On the note of CardTarget Restriction. Location and Type are both mandatory (there is an Any tag if you don't want any restriction)
CardLocation Attribute must all be in the same AttributeTags slot (in DataTable Card creation). Since there is no value attached to those it should not cause any issue
Same Goes for the CardType 
It is true even for Cards you get by name (you will have to give the type of the card (or any)). This is due to the underlying card search system which first has to get all valid cards from Type and Location restrictions before looking into more restrictive conditions

I do not support restrictive conditions as of yet (only card types, location and name)



TOOD make a view of cards when right clicking them

More advanced hovering that show card text ability, cards in deck etc

Make an UI to show where the pointer is at for targeting enemies / investigables

Right now there is a HARD delay of 1 second on BP_CardMode::BeginPlay to make sure that all characters had time to instanciate and do their BeginPlay. This should be changed later probably by having all characters notify their BeginPlay and count down that they all did before BP_CardMode::BeginPlays

There is no queueing of animation for anything. Should probably make the widget movement manager have its own internal clock such that each new animation starts with a tick of -0.5 compared to the previous one

Enemy Icons only show the first Ability in the Ability Manager they own. Either we are ok with this. Or we change the Icon.

Known Issues:

Sometimes Releasing a card from a grab doesn't work
Sometimes Cards don't turn up when being drawn

Cards are not Hoverable (they dont zoom in and shine) while outside of the hand this will be an issue when cards can be picked from other places (BP_View::CardHovering)

There can be only one Specifically targetable ability per cards. A queue need to be implemented: BP_AbilityTargetingManager::EventGraph > GoToNextTargetManagementInQueue
