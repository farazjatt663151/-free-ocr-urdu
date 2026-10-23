# Free OCR Urdu — Android starter

A minimal Android app starter for extracting text from images using Tesseract4Android.
It includes:
- Choose an image from Gallery
- Capture a camera preview
- OCR language selection: English, Urdu, or both
- Copy recognized text
- Share recognized text
- GitHub Actions workflow that builds a debug APK and uploads it as a 7-day artifact

## Important notes

- **Urdu support:** Uses the open-source Tesseract Urdu model (`urd.traineddata`) from `tesseract-ocr/tessdata_fast`. The app downloads language data on first use, so the first scan needs internet. OCR processing itself is on-device once the model is downloaded.
- **English support:** Uses `eng.traineddata` from the same public repository, downloaded on first use.
- **Camera limitation:** The starter uses Android's preview camera contract, which returns a small preview image. This is convenient for a starter but less accurate than full-resolution capture. Upgrade to CameraX for a production scanner.
- **No paid API:** No paid OCR API or subscription is used. GitHub Actions usage is subject to GitHub's current account/repository limits. Public repositories generally have free Actions usage; private repositories have a monthly allowance depending on plan.
- This project has not been compiled in this environment. First GitHub Actions run is the build check; if a dependency or SDK issue appears, open the workflow log and share the error.

## Build APK from mobile only

1. Download and extract this ZIP on your Android phone.
2. Open https://github.com and create a new repository named `free-ocr-urdu`. Public is the easiest option for free Actions usage, but means your source code is visible to everyone.
3. In the new repository, use **Add file → Upload files** and upload the extracted project files and folders. Make sure `.github/workflows/build-apk.yml` is included. On mobile, the GitHub web interface may be awkward for folders; if folder upload is difficult, use an Android archive/file manager plus a Git client/editor, or create the files individually in GitHub.
4. Commit the files to the `main` branch.
5. Open the repository's **Actions** tab. If asked, enable workflows.
6. Select **Build free OCR APK** and press **Run workflow**. A push to `main` also triggers the build.
7. Wait for the run to finish with a green check. Open the run and find **Artifacts** near the bottom.
8. Download `Free-OCR-debug-APK`, extract the ZIP, and install `app-debug.apk`. Android may ask you to allow installing unknown apps for the browser/file manager you used.
9. Open the app. On the first scan, keep internet on so it can download the selected language model. Later scans for that model can work offline.

## If build fails

Open Actions → failed run → `Build debug APK`, copy the first meaningful error message and ask for help. Don't share account tokens or passwords.

## Licenses

Tesseract4Android is Apache-2.0. The Tesseract language data has its own upstream license/terms; check the upstream repository before redistributing models.
