# Houdini_Print_Cache_Stats
A simple tool that allows easy acces to relevant data of a file cache or render on disk from within houdini.
The tool uses simple python logic to access the files on disk and prints out a handy summary of this information.
NOTE that once the tool has found your files it will check if they are all written sequencially, i.e frame 1 was made before frame 2, frame 2 was made before frame 3 etc. If any previous frame was written later than the next frame the tool assumes that files from that point on are from an old cache and does not count them towards any of the stats (frame count, time taken, start frame or end frame).

In honesty I had not intended to publish tool because it is so simple, but after noticing how often I have ended up using it lately I've decided up put it up. Never knew how handy I would find it to have a tool that simply gives me the time a cache has taken and how many frames it has compleeted.

Video overview: vimeo link



## Instalation:

After downloading, copy the .shelf files to this folder on your machine:

Windows: C:\Program Files\Side Effects Software\Houdini xx.x.xxx\houdini\toolbar

Mac: Libary/Frameworks/Houdini Framework/Versions/xx.x.xxx/Resources/hodini/toolbar (Note that I am unfamiliar with Mac and don't know if this path is correct)

Linux: /opt/hfs xx.x.xxx/houdini/toolbar

After restarting houdini the "MB_Shelf" should be avalible to add to your shelf tray by clicking the "+" button next to your shelves titles, hovering over the "Shelves" option and scrolling down to "MB_Shelf".

This is simply an empty shelf I have included where the tools can be placed. Feel free to make your own shelf or place my tools in one of the existing shelfs.

After selecting a shelf to place the tools in, right click on the shelf tab or on an empty part of the shelf and select "Edit shelf tab".
In the new window select the "Tools" tab and scroll down the list. All my tools are prefixed with "MB" so they should show up there.
Simply select the tool you want in the shelf and click "Apply" and then "Accept" and the tool should be ready for use.



##Usage:

To use the tool select the node you wish to read the stats from in the network view and click the button in the shelf. A new window will appear with the stats. You can also do this with multiple nodes. Selecting four or less nodes will give you the stats in a simple houdini pop up message window. Any number of nodes higher than four will print all the stats to the terminal and display them there.

Stats printed include:
- Path to the file to easily identify the cache when printing multiple nodes at once
- The time in Hours:Minutes:Seconds (HH:MM:SS) it took to create the entire cache
- The size of the entire cache in MB
- The length of the cache in frames (NOTE: That this tool will check to make sure that all the frames are written out in sequence, meaning that if frame 1 is written later than frame 2 the tool will ignore frame 2 assuming it has not been written yet or that the cache failed)
- The start time of the cache
- The end time of the cache

This tool works with the following nodes:
- File nodes
- File cache nodes
- Rop Geometry nodes
- Rop Alembic nodes
- Mantra render nodes
- Flipbook nodes
- Redshift Proxy Output nodes
- Redshipt render nodes