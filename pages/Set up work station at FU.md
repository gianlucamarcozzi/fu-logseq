tags:: first-day

- Activate account
	- Bittl sent an email to someone to activate my new account (for students this is not necessary)
- Check that the LAN socket is active
	- If not, go the Zedat IT help in Trakt 4 and give them the number of the socket and the IP address of the computer as shown on the screen
- Note: a lot of the software is already installed in the Debian distribution (git, flatpak, ...)
- Install logseq from flatpak
	- Plugins: Awesome UI, Tabs, Bullet threading, git
- Set up the FU-Box using Nextcloud Desktop App (already installed)
	- It says that the synchronized folder on the computer has only 5GB available. On the settings it says that the server space is 200GB though. I hope this will not be a problem.
- Install Zotero from flatpak
	- Plugins: better bibtex, better notes, doi manager, scite, zotfile, zutilo
	- Link to Zotero
	- Problem connecting Zotero with Box.FU through webdav
	  type:: next-action
- Set up Thunderbird (already installed)
- Set up Matlab 2022b (already installed)
- TexStudio (already installed)
	- If you want to use svg images remember to go to Options>Configure TexStudio>Commands>PdfLatex and add "--shell-escape" before the %.tex
	- Otherwise what I ended up doing is use pdf images and saving them directly as pdf from matlab using the export_fig package
		- I hope I will never have to use ppt again otherwise I will have to find a solution. Does libre office have the same problem with pdfs?
- DONE Problem with windows virtual machine
  xfreerdp /d:FU-BERLIN /v:term.imp.fu-berlin.de /dynamic-resolution
-