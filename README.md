# bci
 
BCI data from Brain Health Lab.
 
## How to Download
 
### Step 1: Install DataLad and git-annex
 
**Linux:**
```bash
sudo apt install git-annex
pip install datalad
```
 
**Windows:**
```bash
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
 
### Step 2: Install Google Drive remote
```bash
pip install git-annex-remote-googledrive
git-annex-remote-googledrive setup -o token.json
```
This opens your browser — sign in with the Google account that has access to the shared Drive folder.
 
### Step 3: Clone and download
```bash
datalad clone https://github.com/trissdent/bci
cd bci
git annex enableremote gdrive externaltype=googledrive
datalad get .
```
 
## Access
You need a Google account with access to the shared Drive folder. Contact the lab for access.
