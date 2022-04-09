# Install zsh with git-bash on windows

## Why

Well, you certainlly can run WSL2 on windows 10/11 to get bash and then zsh. 
But after my testing, I find it quit slow to open up wsl2 and then run zsh, whereas
if you run zsh with git-bash, it's almost instantaneous. Plus I don't want to have 
that extra space occupied by a Linux system, if I want a full Linux experience, I'll
install a Linux distro myself.

It does require a bit of workaround, but I think it's worth it.

## Installation

1. Terminal emulator - Windows Terminal
	You should get windows terminal for this first, since bash/zsh will be running on
	this, it's also the most beautiful and customisable one on windows rightnow. I'm
	full aware of the existance of Alacritty, but it's quit difficult to set it up
	for beginners.

	I prefer to install it with winget:
	``` winget install Microsoft.WindowsTerminal```

2. Git
	Install Git for windows, we'll be using git-bash so this is a must.

	``` winget install git.git```

3. Open git-bash with Windows Terminal 
	add bash.exe's path to Windows terminal, so you can run git-bash within it.

4. patched fonts
	We need a patched font to display fancy glyphs on our prompt, What I usually use is
	a font called CaskaydiaCove NF. You can download from nerdfronts.com

5. Download zsh
	Download zsh package here: https://packages.msys2.org/package/zsh?repo=msys&variant=x86_64

	Extract the download package and paste the content in the directory where git-bash.exe is,
	it will replace some of the files in that directory. Don't worry, it's all part of the process.

6. bash to zsh
	Edit you .bashrc with your text editor of choice (or just copy the following in your bash)

	```notepad ~/.bashrc```

	notepad is the easiest one.
	
	copy the following to .bashrc

	# Launch Zsh
	if [ -t 1 ]; then
	exec zsh
	fi

	After that, save and close. Reopen bash, you should be able to automatically open zsh.
	You can type in:

	```zsh --version```

	You should be getting zsh 5.8(x86_64-pc-msys) as a result.

7. Install oh-my-zsh
	Now comes to the fancy part, oh-my-zsh
	sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

	use the following if you live in mainland China:
	REMOTE=https://gitee.com/mirrors/oh-my-zsh.git sh -c "$(wget https://gitee.com/mirrors/oh-my-zsh/raw/master/tools/install.sh -O -)"

8. More plugins
	To make zsh more functional, let's install two essential plugins: zsh-autosuggestions, zsh-syntaxhighlighting
	git clone git://github.com/zsh-users/zsh-autosuggestions $ZSH_CUSTOM/plugins/zsh-autosuggestions
	git clone git://github.com/zsh-users/zsh-syntax-highlighting $ZSH_CUSTOM/plugins/zsh-syntax-highlighting

	Then edit your .zshrc with:

	```notepad ~.zshrc```

	find the line where "plugins=" is, write the following:

	```plugins=(git zsh-autosuggestions zsh-syntax-highlighting)

	You can add more plugins later, just keep in mind the more plugins you add
	in, the slower zsh will get.

9. Theme
	oh-my-zsh comes with a lot of themes built-in, but the my favorite one
	(and the most popular one) is called powerlevel10k, it's fast and very much
	polished. Here's how to install it:

	```git clone --depth=1 https://gitee.com/romkatv/powerlevel10k.git ~/powerlevel10k
	echo 'source ~/powerlevel10k/powerlevel10k.zsh-theme' >>~/.zshrc
	source ~/.zshrc```

	The code above will automatically start your configure process, if you're not
	happy with what you end up with, you can always:

	```p10k configure```

	to reconfigure, it's pretty handy. 

10. Improve your .zshrc
	There are a lot can be done to make your zsh easier to use. I don't edit 
	a lot, but since I'm a lazy person, I would set some alias just to type 
	fewer letters. For example if you use the command "python" a lot, I would
	suggest you set "py" as an alias for "python" (4 letters less, isnt' that 
	cool?)

	I also use neovim as my default text editor, "nvim" is its command, but 
	I just type "v" to initiate it. So if you are lazy like me, you can copy
	my following code and add to your .zshrc:

	```alias py="python" 
	alias v="nvim" 
	alias vi="nvim" 
	alias vim="nvim"``` 

	You can certainly do more with these alias, but you get the basic idea, just
	don't go too crazy with alias in the beginning.

11. Set zsh as your default shell
	Simple, just open windows terminal and set the default shell as git-bash.
	
## Uninstallation

What, so soon?

Well, you can certainlly uninstall it of course.

If you are 100% about quiting programming entirely, uninstall git all together, otherwise
you just have to delete .bashrc .zshrc, delete .oh-my-zsh folder entirely, and then 
set back powershell as your default shell.












