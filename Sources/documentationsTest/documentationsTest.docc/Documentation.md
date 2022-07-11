# ``documentationsTest``


## Overview

Some project for test DocC

For creat DocC files 
Ill use 
xcodebuild docbuild \                 
-scheme documentationsTest \                                 
-derivedDataPath ~/Desktop \
-destination 'platform=iOS Simulator,name=iPhone 13'

For creat files in docs/ 
Ill use (xcrun --find docc) process-archive \
transform-for-static-hosting documentationsTest.doccarchive \
--output-path docs \
--hosting-base-path documentationsTest

