# 🤓Docker-Py-ReVanced

A little python script that will help you in building [Revanced](https://revanced.app/) [apps](#any-patch-apps) and sharing them anywhere.

**`Note`** - If you are a root user and want magisk module (Extended). Get them [here](https://github.com/nikhilbadyal/revanced-magisk-module)

 <a id="only-builder-support"></a>This is just a builder for revanced and not a revanced support. Please be
 understanding and refrain from asking about revanced features/bugs. Discuss those on proper relevant forums.

## Pre-Built APKs

You can get pre-built apks [here](https://revanced_apkss.t.me/)

## Facing issues? Click [here](https://github.com/nikhilbadyal/docker-py-revanced/issues/new/choose).<br>
## Build Yourself

You can use any of the following methods to build.

- 🚀 **GitHub** (**_`Recommended`_**)

     1. Click Star to support the project.<br>
       <img src="https://i.imgur.com/FFyXaWY.png" width="400" style="left"><br>
     2. Fork the project.<br>
     <img src="https://i.imgur.com/R5HdByI.png" width="400" style="left"><br>
     3. Add `ENVS` (**optional**) secret to the repo. Required only if you want to cook specific apps/versions.
         <details>
           <summary>🚶Detailed step by step guide</summary>

         - Go to the repo settings and then to actions->secret<br>
           <img src="https://i.imgur.com/Inj82KK.png" width="600" style="left"><br>
         - Add Repository secret<br>
           <img src="https://i.imgur.com/V2Wfx3J.png" width="600" style="left">

        </details>

     4. Go to actions tab. Select `Build & Release`.Click on `Run Workflow`.

        <details>
          <summary>🚶Detailed step by step guide</summary>

         - Go to actions tab<br>
           <img src="https://i.imgur.com/XSCvzav.png" width="600" style="left"><br>
         - Check the status of build, It should look green.<br>
           <img src="https://i.imgur.com/CsJt9W1.png" width="600" style="left">

        </details>

     5. If the building process is successful, you’ll get your APKs in the<br>
        <img src="https://i.imgur.com/S5d7qAO.png" width="700" style="left">
     6. Make sure to do below steps once in a while(daily or weekly) to keep the builder bug free.<br>
        <img src="https://i.imgur.com/CbdH7vM.png" width="700" style="left">

- 🐳 **_Docker Compose_**<br>

    1. Install [Docker Desktop](https://www.docker.com/products/docker-desktop/).
    2. Clone the repo
       ```bash
       git clone https://github.com/nikhilbadyal/docker-py-revanced
       ```
    3. cd to the cloned repo
       ```bash
       cd docker-py-revanced
       ```
    4. Update `.env` file if you want some customization(See notes)
    5. Run script with
       ```shell
       docker compose up --build
       ```

- 🐳With Docker

    1. Install Docker or [Docker Desktop](https://www.docker.com/products/docker-desktop/).
       ```bash
       curl -fsSL https://get.docker.com -o get-docker.sh
       sh get-docker.sh
       ```
    2. Run script with
       ```shell
       docker run -v "$(pwd)"/apks:/app/apks/  nikhilbadyal/docker-py-revanced
       ```
       You can pass the below environment variables (See notes) with the `-e` flag or use the `--env-file`
       [flag](https://docs.docker.com/engine/reference/commandline/run/#options).

- 🫠Without Docker

    1. Install Java >= 17
    2. Install Python >= 3.11
    3. Create virtual environment
       ```
       python3 -m venv venv
       ```
    4. Activate virtual environment
       ```
       source venv/bin/activate
       ```
    5. Install Dependencies with
       ```
       pip install -r requirements.txt
       ```
    6. Run the script with
       ```
       python main.py
       ```

## Configurations

### Global Config

| **Env Name**                                             |                  **Description**                  | **Default**                                                                                                           |
|:---------------------------------------------------------|:-------------------------------------------------:|:----------------------------------------------------------------------------------------------------------------------|
| [PATCH_APPS](#patch-apps)                                |                Apps to patch/build                | youtube                                                                                                               |
| [EXISTING_DOWNLOADED_APKS ](#existing-downloaded-apks)   |           Already downloaded clean apks           | []                                                                                                                    |
| [PERSONAL_ACCESS_TOKEN](#personal-access-token)          |              Github Token to be used              | None                                                                                                                  |
| DRY_RUN                                                  |                   Do a dry run                    | False                                                                                                                 |
| [GLOBAL_CLI_DL*](#global-resources)                      |     DL for CLI to be used for patching apps.      | [Revanced CLI](https://github.com/revanced/revanced-cli)                                                              |
| [GLOBAL_PATCHES_DL*](#global-resources)                  |   DL for Patches to be used for patching apps.    | [Revanced Patches](https://github.com/revanced/revanced-patches)                                                      |
| [GLOBAL_SPACE_FORMATTED_PATCHES*](#global-resources)     |       Whether patches are space formatted.        | True                                                                                                                  |
| [GLOBAL_PATCHES_JSON_DL*](#global-resources)             | DL for Patches Json to be used for patching apps. | [Revanced Patches](https://github.com/revanced/revanced-patches)                                                      |
| [GLOBAL_INTEGRATIONS_DL*](#global-resources)             | DL for Integrations to be used for patching apps. | [Revanced Integrations](https://github.com/revanced/revanced-integrations)                                            |
| [GLOBAL_KEYSTORE_FILE_NAME*](#global-keystore-file-name) |       Key file to be used for signing apps        | [Builder's own key](https://github.com/nikhilbadyal/docker-py-revanced/blob/main/apks/revanced.keystore)              |
| [GLOBAL_OLD_KEY*](#global-keystore-file-name)            | Whether key was generated with cli v4(new) or not | <br/>[Builder's v3(old) own key](https://github.com/nikhilbadyal/docker-py-revanced/blob/main/apks/revanced.keystore) |
| [GLOBAL_OPTIONS_FILE*](#global-options-file)             |              Options file to be used              | [Builder's default file](https://github.com/nikhilbadyal/docker-py-revanced/blob/main/apks/options.json)              |
| [GLOBAL_ARCHS_TO_BUILD*](#global-archs-to-build)         |         Arch to keep in the patched apk.          | All                                                                                                                   |
| REDDIT_CLIENT_ID                                         |       Reddit Client ID to patch reddit apps       | None                                                                                                                  |
| VT_API_KEY                                               |           Virus Total Key to scan APKs            | None                                                                                                                  |
| [TELEGRAM_CHAT_ID](#telegram-support)                    |            Receiver in Telegram upload            | None                                                                                                                  |
| [TELEGRAM_BOT_TOKEN](#telegram-support)                  |          APKs Sender for Telegram upload          | None                                                                                                                  |
| [TELEGRAM_API_ID](#telegram-support)                     |         Used for telegram Authentication          | None                                                                                                                  |
| [TELEGRAM_API_HASH](#telegram-support)                   |         Used for telegram Authentication          | None                                                                                                                  |
| [EXTRA_FILES](#extra-files)                              |    Extra files apk to upload in GitHub upload.    | None                                                                                                                  |
| [APPRISE_URL](#apprise)                                  |                   Apprise URL .                   | None                                                                                                                  |
| [APPRISE_NOTIFICATION_TITLE](#apprise)                   |           Apprise Notification Title .            | None                                                                                                                  |
| [APPRISE_NOTIFICATION_BODY](#apprise)                    |            Apprise Notification Body .            | None                                                                                                                  |

`*` - Can be overridden for individual app.
### App Level Config

| Env Name                                                    |                                         Description                                          | Default                        |
|:------------------------------------------------------------|:--------------------------------------------------------------------------------------------:|:-------------------------------|
| [*APP_NAME*_CLI_DL](#global-resources)                      |                       DL for CLI to be used for patching **APP_NAME**.                       | GLOBAL_CLI_DL                  |
| [*APP_NAME*_PATCHES_DL](#global-resources)                  |                     DL for Patches to be used for patching **APP_NAME**.                     | GLOBAL_PATCHES_DL              |
| [*APP_NAME*_PATCHES_JSON_DL](#global-resources)             |                  DL for Patches Json to be used for patching **APP_NAME**.                   | GLOBAL_PATCHES_JSON_DL         |
| [*APP_NAME*_SPACE_FORMATTED_PATCHES](#global-resources)     |                     Whether patches are space formatted.   **APP_NAME**.                     | GLOBAL_SPACE_FORMATTED_PATCHES |
| [*APP_NAME*_INTEGRATIONS_DL](#global-resources)             |                  DL for Integrations to be used for patching **APP_NAME**.                   | GLOBAL_INTEGRATIONS_DL         |
| [*APP_NAME*_KEYSTORE_FILE_NAME](#global-keystore-file-name) |                        Key file to be used for signing **APP_NAME**.                         | GLOBAL_KEYSTORE_FILE_NAME      |
| [*APP_NAME*_OLD_KEY](#global-keystore-file-name)            | Whether key used was generated with cli > v4(new) <br/><br/>**APP_NAME**.      <br/>   <br/> | GLOBAL_OLK_KEY                 |
| [*APP_NAME*_ARCHS_TO_BUILD](#global-archs-to-build)         |                          Arch to keep in the patched **APP_NAME**.                           | GLOBAL_ARCHS_TO_BUILD          |
| [*APP_NAME*_EXCLUDE_PATCH**](#custom-exclude-patching)      |                       Patches to exclude while patching  **APP_NAME**.                       | []                             |
| [*APP_NAME*_INCLUDE_PATCH**](#custom-include-patching)      |                       Patches to include while patching  **APP_NAME**.                       | []                             |
| [*APP_NAME*_VERSION](#app-version)                          |                          Version to use for download for patching.                           | Recommended by patch resources |
| [*APP_NAME*_PACKAGE_NAME***](#any-patch-apps)               |                            Package name of the app to be patched                             | None                           |
| [*APP_NAME*_DL_SOURCE***](#any-patch-apps)                  |                       Download source of any of the supported scrapper                       | None                           |
| [*APP_NAME*_DL***](#app-dl)                                 |                              Direct download Link for clean apk                              | None                           |

`**` - By default all patches for a given app are included.<br>
`**` - Can be used to included universal patch.
`***` - Can be used for unavailable apps in the repository (unofficial apps).

## Note

1. <a id="any-patch-apps"></a>**Officially** Supported values for **APP_NAME**** are :

    - [youtube](https://www.apkmirror.com/apk/google-inc/youtube/)
    - [youtube_music](https://www.apkmirror.com/apk/google-inc/youtube-music/)
    - [photos](https://www.apkmirror.com/apk/google-inc/photos)
    - [twitter](https://www.apkmirror.com/apk/twitter-inc/twitter/)
    - [reddit](https://www.apkmirror.com/apk/redditinc/reddit/)
    - [tiktok](https://www.apkmirror.com/apk/tiktok-pte-ltd/tik-tok-including-musical-ly/)
    - [warnwetter](https://www.apkmirror.com/apk/deutscher-wetterdienst/warnwetter/)
    - [spotify](https://spotify.en.uptodown.com/android)
    - [nyx-music-player](https://nyx-music-player.en.uptodown.com/android)
    - [icon_pack_studio](https://www.apkmirror.com/apk/smart-launcher-team/icon-pack-studio/)
    - [ticktick](https://www.apkmirror.com/apk/appest-inc/ticktick-to-do-list-with-reminder-day-planner/)
    - [twitch](https://www.apkmirror.com/apk/twitch-interactive-inc/twitch/)
    - [hex-editor](https://m.apkpure.com/hex-editor/com.myprog.hexedit)
    - [windy](https://www.apkmirror.com/apk/windy-weather-world-inc/windy-wind-weather-forecast/)
    - [my-expenses](https://my-expenses.en.uptodown.com/android)
    - [backdrops](https://backdrops.en.uptodown.com/android)
    - [expensemanager](https://apksos.com/app/com.ithebk.expensemanager)
    - [tasker](https://www.apkmirror.com/apk/joaomgcd/tasker-crafty-apps-eu/)
    - [irplus](https://irplus.en.uptodown.com/android)
    - [vsco](https://www.apkmirror.com/apk/vsco/vsco-cam/)
    - [meme-generator-free](https://meme-generator-free.en.uptodown.com/android)
    - [nova_launcher](https://www.apkmirror.com/apk/teslacoil-software/nova-launcher/)
    - [netguard](https://www.apkmirror.com/apk/marcel-bokhorst/netguard-no-root-firewall/)
    - [instagram](https://www.apkmirror.com/apk/instagram/instagram-instagram/)
    - [inshorts](https://www.apkmirror.com/apk/inshorts-formerly-news-in-shorts/)
    - [messenger](https://www.apkmirror.com/apk/facebook-/messenger/)
    - [grecorder](https://opnemer.en.uptodown.com/android)
    - [trakt](https://www.apkmirror.com/apk/trakt/trakt/)
    - [candyvpn](https://www.apkmirror.com/apk/liondev-io/candylink-vpn/)
    - [sonyheadphone](https://www.apkmirror.com/apk/sony-corporation/sony-headphones-connect/)
    - [androidtwelvewidgets](https://m.apkpure.com/android--widgets-twelve/com.dci.dev.androidtwelvewidgets)
    - [yuka](https://yuka.en.uptodown.com/android)
    - [relay](https://www.apkmirror.com/apk/dbrady/relay-for-reddit-/)
    - [boost](https://www.apkmirror.com/apk/ruben-mayayo/boost-for-reddit/)
    - [rif](https://www.apkmirror.com/apk/talklittle/reddit-is-fun/)
    - [sync](https://www.apkmirror.com/apk/red-apps-ltd/sync-for-reddit/)
    - [infinity](https://www.apkmirror.com/apk/red-apps-ltd/sync-for-reddit/)
    - [slide](https://www.apkmirror.com/apk/haptic-apps/slide-for-reddit/)
    - [bacon](https://www.apkmirror.com/apk/onelouder-apps/baconreader-for-reddit/)
    - [microg](https://github.com/inotia00/mMicroG/releases/)
    - [pixiv](https://www.apkmirror.com/apk/pixiv-inc/pixiv/)
    - [strava](https://www.apkmirror.com/apk/strava-inc/strava-running-and-cycling-gps/)
    - [solidexplorer](https://www.apkmirror.com/apk/neatbytes/solid-explorer-beta/)
    - [lightroom](https://www.apkmirror.com/apk/adobe/lightroom/)
    - [duolingo](https://www.apkmirror.com/apk/duolingo/duolingo-duolingo/)
    - [musically](https://www.apkmirror.com/apk/tiktok-pte-ltd/tik-tok-including-musical-ly/)
    - [photomath](https://www.apkmonk.com/app/com.microblink.photomath/)
    - [joey](https://www.apkmonk.com/app/o.o.joey/)
    - [vanced](https://www.apkmirror.com/apk/team-vanced/youtube-vanced/)
    - [spotify-lite](https://www.apkmonk.com/app/com.spotify.lite/)
    - [digitales](https://www.apkmonk.com/app/at.gv.oe.app/)
    - [scbeasy](https://www.apkmonk.com/app/com.scb.phone/)
    - [reddit-news](https://m.apkpure.com/relay-for-reddit/reddit.news)
    - [finanz-online](https://apksos.com/app/at.gv.bmf.bmf2go)
    - [tumblr](https://www.apkmirror.com/apk/tumblr-inc/tumblr/)
    - [fitnesspal](https://www.apkmirror.com/apk/myfitnesspal-inc/calorie-counter-myfitnesspal/)
    - [facebook](https://www.apkmirror.com/apk/facebook-2/facebook/)
    - [lemmy-sync](https://www.apkmirror.com/apk/sync-apps-ltd/sync-for-lemmy/)

    <br>`**` - You can also patch any other app which is **not** supported officially.To do so, you need to provide
   few more inputs to the tool which are mentioned below. These config will override the sources config from the tool.
   ```ini
   <APP_NAME>_DL_SOURCE=<apk-link-to-any-of-the-suppored-scrapper>
   <APP_NAME>_PACKAGE_NAME=<package-name-of-the-application>
   ```
   You can also provide DL to the clean apk instead of providing DL_SOURCES as mentioned in this [note](#app-dl).
   Supported Scrappers are:
   1. APKMIRROR - Supports downloading any available version
        1. Link Format - https://www.apkmirror.com/apk/<organisation-name>/app-name/
        2. Example Link - https://www.apkmirror.com/apk/google-inc/youtube/
   2. UPTODOWN - Supports downloading any available version
        1. Link Format - https://<app-name>.en.uptodown.com/android
        2. Example Link - https://spotify.en.uptodown.com/android
   3. APKSOS - Supports downloading any available version
       1. Link Format - https://apksos.com/download-app/<package-name>
       2. Example Link - https://apksos.com/download-app/com.expensemanager
   4. APKPURE - Supports downloading any available version
       1. Link Format - https://apkpure.net/-/<package-name>
       2. Example Link - https://apkpure.net/-/com.google.android.youtube
   5. APKMonk - Supports downloading any available version
       1. Link Format - https://www.apkmonk.com/app/<package-name>/
       2. Example Link - https://www.apkmonk.com/app/<package-name>/
   6. Google Drive - Supports downloading from Google Drive lint
       1. Link Format - https://drive.google.com/uc?<id>
       2. Example Link - https://drive.google.com/uc?id=1ad44UTghbDty8o36Nrp3ZMyUzkPckIqY

   <br>Please verify the source of original APKs yourself with links provided. I'm not responsible for any damage
    caused.If you know any better/safe source to download clean. Open a discussion.

2. By default, script build the latest version mentioned in `patches.json` file.
3. Remember to download the **_Microg_**. Otherwise, you may not be able to open YouTube/YouTube Music.
4. <a id="patch-apps"></a>By default, tool will build only `youtube,youtube_music`. To build other apps supported by patching
   resources.Add the apps you want to build in `.env` file or in `ENVS` in `GitHub secrets` in the format
   ```ini
   PATCH_APPS=<APP_NAME>
   ```
   Example:
   ```ini
   PATCH_APPS=youtube,twitter,reddit
   ```
   Tip - If for some reason you want to patch app but want to go through all this .env while running you can enter app
   name in <img src="https://i.imgur.com/DwhBH9H.png" width="300"
