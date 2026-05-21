# bci

BCI data from Brain Health Lab.

## How to Download

### Initial Setup (one time only)

#### 1. Install DataLad and git-annex

**Linux:**
```bash
sudo apt install git-annex
pip install datalad
```

**Windows (run as Administrator):**
```powershell
pip install datalad-installer datalad
datalad-installer git-annex -m datalad/packages
# close and reopen terminal
```

**Mac:**
```bash
pip install datalad-installer datalad
datalad-installer git-annex -m datalad/packages
echo 'export PATH="/Applications/git-annex.app/Contents/MacOS:$PATH"' >> ~/.zshrc
source ~/.zshrc
```

#### 2. Install and configure rclone

**Linux:**
```bash
sudo apt install rclone
```

**Windows:**
```powershell
Invoke-WebRequest -Uri https://downloads.rclone.org/rclone-current-windows-amd64.zip -OutFile rclone.zip
Expand-Archive rclone.zip -DestinationPath "$env:USERPROFILE\rclone"
$rclonePath = (Get-ChildItem "$env:USERPROFILE\rclone" -Directory | Select-Object -First 1).FullName
$oldPath = (Get-Item "HKCU:\Environment").GetValue("Path", "", "DoNotExpandEnvironmentNames")
[Environment]::SetEnvironmentVariable("PATH", "$oldPath;$rclonePath", "User")
# close and reopen terminal
```

**Mac:**
```bash
curl https://rclone.org/install.sh | sudo bash
```

Then configure Google Drive access (all platforms):
```bash
rclone config create gdrive drive scope drive shared_with_me true
rclone config reconnect gdrive:
```
When prompted, press **Enter** twice to accept the defaults. Your browser will open — sign in with the Google account that has access to the shared Drive folder and click **Allow**. Then type **n** for Shared Drive and press **Enter**.

To verify it worked:
```bash
rclone lsd gdrive:
```
You should see your Google Drive folders listed.

---

### Get the Data

After the initial setup, this is all you need:

```bash
datalad clone https://github.com/trissdent/bci
cd bci
git annex enableremote gdrive
datalad get -J 4 .
```

## Access

You need a Google account with access to the shared Drive folder. Contact the lab for access.
