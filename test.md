IceCandidateParserTests (10)

ValidCandidate_ParsesSuccessfully — normal candidate string parses correctly
ValidCandidate_WithNonZeroMLineIndex — candidate with video line index parses correctly
MissingCandidateKey_ReturnsFalse — no 'candidate' key → returns false, no crash
NullCandidateValue_ReturnsFalse — candidate key exists but value is null → false
EmptyCandidateString_ReturnsFalse — empty string is WebRTC's "done" signal → false
WhitespaceCandidateString — spaces aren't empty, parser accepts it → true
MissingSdpMid_DefaultsToZeroString — missing sdpMid defaults to "0"
MissingSdpMLineIndex_DefaultsToZero — missing sdpMLineIndex defaults to 0
MalformedJson_ReturnsFalseWithoutThrowing — broken JSON is caught, logs error, returns false
EmptyJsonObject_ReturnsFalse — {} has no candidate → false

SignalingMessageTests (12)

MessageWithoutDataKey_IsIgnored — no 'data' field → silently dropped
MessageWithoutTypeField_IsIgnored — no 'type' inside data → dropped
EmptyJsonMessage_IsIgnoredWithoutThrowing — {} doesn't crash
MessageForDifferentRoom_IsIgnored — wrong room ID → ignored
MessageForCorrectRoom_IsNotIgnored — correct room → processed
MessageWithNoRoomField_IsNotFilteredOut — system messages with no room pass through
CallAccepted_TypeIsRecognized — "call-accepted" type identified correctly
CallDeclined_TypeIsRecognized — "call-declined" type identified correctly
AnswerMessage_ExtractsSdpCorrectly — SDP string survives JSON round-trip unchanged
IceCandidate_TypeIsRecognized — "ice-candidate" recognized, carries candidate field
UnknownType_ParsesWithoutError — future unknown types don't crash the parser
AnswerMessage_MissingSdp_DoesNotThrow — answer with no SDP key doesn't throw


PlayMode — 13 tests
PassthroughManagerTests (4)

IsReady_IsFalseOnAwake — IsReady is false before anything starts
StartPassthrough_WithNoCamera_TimesOutWithoutCrash — no camera assigned, coroutine crashes with expected error, IsReady stays false
OnPassthroughReady_NotFired_BeforeTimeout — event never fires when no camera present
IsReady_TrueAfterCameraStreams — ⏭️ skipped, needs real Quest hardware

VideoCompositorTests (9)

IsReady_IsFalseBeforeStart — IsReady false before StartCompositor called
Track_IsNullBeforeStart — VideoStreamTrack is null before pipeline starts
OnTrackReady_CanSubscribeAndUnsubscribeWithoutError — event subscribe/unsubscribe doesn't crash
StartCompositor_SubscribesToPassthroughEvent_WhenNotReady — calling StartCompositor triggers the chain, expected error acknowledged
StartCompositor_CalledTwice_DoesNotThrow — calling it twice handled gracefully
Destroy_BeforeStart_DoesNotThrow — destroying GameObject before start doesn't crash
Destroy_AfterStartCompositor_DoesNotThrow — destroying mid-init doesn't crash
IsReady_TrueAfterTrackCreated — ⏭️ skipped, needs real Quest hardware
Track_NotNull_AfterCompositorReady — ⏭️ skipped, needs real Quest hardware
