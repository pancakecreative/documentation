# The Tools We Use @ Pancake
 
## Software

### Mac OS

We use Mac OS because walled garden and we're familar with the thing.

#### Mac OS full screen spaces

Here's some helpful info about this thing.

#### Mac OS Hot Corners

You should have Mac OS Hot Corners configured on your laptop so you can easily access spaces.

### Magnet

Window management in OS X (MacOS) is pretty annoying and difficult. To get around this use full screen spaces and Magnet to manage your windows and software clients. The goal here is to effectively set spaces that correspond with a specific context.

Magnet allows you to more quickly and efficiently manage window sizes, and allows more rapid migration of windows about the screen. Set your shortcuts like this and memorize them. This will save you time and speed up your window organization process. It's much easier to use the keyboard shortcuts than it is to use the window snapping, so go that route instead.

### Toby

Use Toby to navigate to and define the web applications and websites that you're using consistently, and to effectively manage tabs. The Pancake Toby Implementation has a number of collections already defined, please feel free to create new ones and share them with relevant team members as appropriate.

#### Tab management

It's super easy for tabs to get out of control quickly. Try to limit the number of things your brain has to manage by keeping just the tabs you need open.

A few best practices:  

- When creating a collection, make sure that you're using the Pancake naming convention so we don't end up 
Other relevant tabs, as pertains to role/job description
Working tabs
- Maintain as few tabs as possible.
- Take time to maintain/remove tabs, as necessary.
- Maintain a "working" Chrome window with tabs related only to the task at hand.
- [Use "Toby" to manage frequently-used tabs](http://www.gettoby.com/how-to-use) and to switch contexts effectively and manage working window.
	- Save working sessions in your Toby "My Collections" section for later use.
	- Define sessions in Toby for switching role contexts.
	- Clean up tabs you don't need right now into a "Temp" collection in Toby
- Use the shared Pancake Toby shortcuts to access commonly featured items. Make sure that these have been shared with you.

### Alfred

Alfred is an epicenter for all our workflows, so it's critical that you take the time you need to set it up correctly, and to learn how to use it. If you're not familiar with Alfred, choose to learn to use it effectively, as it's an extremely powerful tool, and we're writing new workflows for Alfred each and every day. 

#### Configuration

Set your Alfred sync folder to ~/Google Drive/Alfred Preferences, in doing so you'll inherit all the Alfred snippets that we've already defined. If you haven't had the "Alfred Preferences" folder shared with you already, request such a share before configuring your Alfred sync preferences!

How?

- Configure Google Drive (Or Google Backup & Sync)
- Navigate to drive.google.com
- Drag shared folders you want to sync (Alfred Preferences) to your "My Drive" folder
- Navigate to Alfred Sync preferences
- Set ~/Google Drive/Alfred Preferences/ as your Alfred Preferences Sync folder.

#### Text Expansion/Snippets
Set the Alfred hotkey to Option + Space, Cmd + Space, or Control + Space. Review the Alfred snippets functionality, and add your snippets to the shared Alfred preferences document.

Read through the snippets currently availabe in Alfred, memorize them, and use them. Snippets can also be searched through the use of the "snip" keyword after invoking Alfred.

#### Workflows

Alfred Workflows you should be using:

- Colors
	- Do cool things with colors
- Flush DNS
- IP Address
	- Get your dang IP address
- Kill Process
	- Kill that pesky process
- Doing (**Requires Toggl-CLI, Doing, and Slack Webhook CLI**)
	- Track your hours, and log your tasks all in the same command!
- Lorem Ipsum
	- Broken and deprecated. This used to be super useful, but the API has changed the Alfred workflow is now broken broken broken.
- Go
	- Typing `go` and the name of the web app will navigate you to the appropriate Pancake version of that tool automatically. Super useful!
- Stack Overflow
	- Search Stack Overflow for the question you have!
- Terminal Finder
	- This workflow allows you to quickly open a Finder window that points to the path you have in the Terminal, or vice versa.

#### Clipboard history!
CMD + Shift + V invokes Alfred to the clipboard manager view, and allows you to go back into your clipboard history after using them. You'll need to enable this on your own (Alfred preferences doesn't sync it over), and it's vital that you do.

### [Doing CLI](http://brettterpstra.com/projects/doing/)

#### Installation

In the terminal, type:

```$ [sudo] gem install doing```

#### Configuration

In the terminal, type:

```$ doing config```

You may encounter an issue where the editor on your setup hasn't been configured. If you do get this issue, type:

```$ export EDITOR="/usr/bin/nano"```

Make sure you have access to the "Team" folder in Google Drive. If you don't, request access.
And input the following snippet (Make sure to update "YOURUSERNAME" with the correct username):

```
---
doing_file: ~/Google Drive/Team/doing-YOURUSERNAME.md
current_section: Currently
default_template: '%date: %title%note'
default_date_format: '%Y-%m-%d %H:%M'
editor_app: TaskPaper
views:
  color:
    date_format: '%F %_I:%M%P'
    section: Currently
    count: 10
    wrap_width: 0
    template: '%boldblack%date %boldgreen| %boldwhite%title%default%note'
    order: desc
templates:
  default:
    date_format: '%Y-%m-%d %H:%M'
    template: '%date | %title%note'
    wrap_width: 0
  today:
    date_format: '%_I:%M%P'
    template: '%date: %title%odnote'
    wrap_width: 0
  last:
    date_format: '%_I:%M%P on %a'
    template: '%title (at %date)%odnote'
    wrap_width: 0
  recent:
    date_format: '%_I:%M%P'
    template: '%date > %title%odnote'
    wrap_width: 50
:include_notes: true
marker_tag: flagged
marker_color: red
```

### [Toggl CLI](https://www.npmjs.com/package/toggl-cli)


#### Installation

In the terminal, type:

```npm install -g toggl-cli```

#### Configuration

- Navigate to your Toggl profile
- Copy your API token
- In the terminal type:

```
toggl --save-token YOURAPITOKEN
toggl --set-background light 

(change "light" to "dark" if you're using a dark background in terminal)
```

Start your new timer!

### CloudApp
https://www.getcloudapp.com/

Download CloudApp.
Create as many screenshots as you can to give clients and colleagues context as to what you're seeing.

Set shortcut key CMD + Shift + 1 for screenshots.

(Pro tip: if you hit spacebar while hovering over a window, you'll only take a screenshot of that window!)

### 1Password
1Password is our password management tool, and critical to our workflows. It's also accessible from Alfred. Make sure that you've configured the 1Password/Alfred configuration. 

### Slack

### Sketch

### Sip

### Tower

### GitUp

### Git
