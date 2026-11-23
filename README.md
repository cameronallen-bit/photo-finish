# Photo Finish

Five live Connections photo games in one GitHub Pages app. Players open one link and enter a first name. The host uses a private console link and shares the separate big-screen view in Teams.

## Host a game

1. Choose **Host a live game**. Bookmark the console link for this room.
2. In **Setup**, save the lineup and open uploads. Choose one round for a standalone game or several for a combined game. Caption Contest can use a host photo, a team upload or any approved photo.
3. Copy the invite or download the QR code. Use **Photos** to approve submissions and edit prices or place names.
4. Open the live lobby and share the big screen. Wait for players to select **Join the game**. Start rounds from **Show controls**.
5. Show **Final results**, then confirm **Clear photos** once you have finished with the images. The podium keeps its scores.

**Practice on this device** runs in your browser. Open the practice room's player link and big-screen link in separate tabs. Use a different player tab for each practice player.

## Deployment

The only runtime file is `index.html`. Publish the repository root of the `main` branch through GitHub Pages. All rooms use the existing `price-is-fright` Firebase Realtime Database. Players do not need a login or a separate account setup.

- In Firebase Authentication, enable the **Anonymous** sign-in provider if it is currently disabled. It assigns a temporary Firebase identity to the browser.
- In Realtime Database Rules, merge only the value at `rules.photoFinish` from [firebase.rules.json](firebase.rules.json) into the existing `rules` object. Preserve the older game branches. The database root must have no broad read or write grant because parent grants also cover descendants.
- Use a live room with two devices to verify that a pending photo is visible to its owner and host, an approved photo appears during the round, and final scores survive **Clear photos**.

Combined rooms scale each round's top score to 1,000 by default. One-round rooms use that game's raw scoring. The host can select raw scoring for a combined lineup.

Font and QR code notices are in [THIRD-PARTY-NOTICES.txt](THIRD-PARTY-NOTICES.txt).

