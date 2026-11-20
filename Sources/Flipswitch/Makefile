# Flipswitch bundle (control-center toggle).
#
# Compiles only the shared preference layer plus the switch itself: the toggle
# needs to read and write one preference, not the push pipeline.

# One architecture, matching the parent project: each scheme installs on one kind
# of device only, so building both doubles the work for a binary half of which is
# discarded.
ifeq ($(THEOS_PACKAGE_SCHEME),rootless)
	ARCHS = arm64
else ifeq ($(THEOS_PACKAGE_SCHEME),roothide)
	ARCHS = arm64e
else
$(error THEOS_PACKAGE_SCHEME must be set: use THEOS_PACKAGE_SCHEME=roothide (or =rootless). Building this subproject on its own would otherwise pick arm64e by default and produce a binary for the wrong layout)
endif

include $(THEOS)/makefiles/common.mk

BUNDLE_NAME = TextRelayFlipswitch
TextRelayFlipswitch_FILES = RelaySwitch.swift \
                         ../Core/TextRelayConstants.swift \
                         ../Shared/Prefs.swift \
                         ../Shared/PrefsStore.swift
TextRelayFlipswitch_SWIFT_BRIDGING_HEADER = TextRelayFlipswitch-Bridging-Header.h
TextRelayFlipswitch_FRAMEWORKS = UIKit Foundation
TextRelayFlipswitch_LIBRARIES = flipswitch
TextRelayFlipswitch_INSTALL_PATH = /Library/Switches

include $(THEOS_MAKE_PATH)/bundle.mk
