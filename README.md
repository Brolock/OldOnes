# OldOnes

Developed with Unreal Engine 4

Important:
Cards are assumed to ALWAYS be in Draw pile at start of a game for initialization of View and so on. Be careful not to add cards to Discard before the game has started. They should be sent there on first turn

TOOD make a view of cards when right clicking them AND when right clicking a pile show all cards in there.

More advanced hovering that show card text ability, cards in deck etc

Make an UI to show where the pointer is at for targeting enemies / investigables

Right now there is a HARD delay of 1 second on BP_CardMode::BeginPlay to make sure that all characters had time to instanciate and do their BeginPlay. This should be changed later probably by having all characters notify their BeginPlay and count down that they all did before BP_CardMode::BeginPlays

There is no queueing of animation for anything. Should probably make the widget movement manager have its own internal clock such that each new animation starts with a tick of -0.5 compared to the previous one

Enemy Icons only show the first Ability in the Ability Manager they own. Either we are ok with this. Or we change the Icon.

Known Issues:

Enemies are still being deleted as soon as they are killed. That can cause cards that were still queuing for damage to refer to nullptr targets. (for example multiple iteration of damage on a single target). This should get better with animations on death that will make the Enemy wait a bit before being deleted. But with attack animations I am not sure the problem can be solved this way and gameplay should be looked at

Sometimes Releasing a card from a grab doesn't work
Sometimes Cards don't turn up when being drawn

Cards are not Hoverable (they dont zoom in and shine) while outside of the hand this will be an issue when cards can be picked from other places (BP_View::CardHovering)

There can be only one Specifically targetable ability per cards. A queue need to be implemented: BP_AbilityTargetingManager::EventGraph > GoToNextTargetManagementInQueue
