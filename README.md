# OldOnes

Developed with Unreal Engine 4

Important:
Cards are assumed to ALWAYS be in Draw pile at start of a game for initialization of View and so on. Be careful not to add cards to Discard before the game has started. They should be sent there on first turn

TOOD make a view of cards when right clicking them AND when right clicking a pile show all cards in there.
More advanced hovering that show card text ability, cards in deck etc
Make an UI to show where the pointer is at for targeting enemies / investigables

There is no queueing of animation for anything. Should probably make the widget movement manager have its own internal clock such that each new animation starts with a tick of -0.5 compared to the previous one


Known Issues:

Sometimes Releasing a card from a grab doesn't work
Sometimes Cards don't turn up when being drawn

Cards are not Hoverable (they dont zoom in and shine) while outside of the hand this will be an issue when cards can be picked from other places (BP_View::CardHovering)

There can be only one Specifically targetable ability per cards. A queue need to be implemented: BP_AbilityTargetingManager::EventGraph > GoToNextTargetManagementInQueue
