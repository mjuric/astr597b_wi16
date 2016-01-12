# How to connect to you notebooks remotely, from outside the department

Our department's servers are protected by a firewall; if you're not in the
building and on UW wireless, you may not be able to directly connect to your
`Jupyter` notebooks.

However, there's a way around this using an [SSH
tunnel](http://blog.trackets.com/2014/05/17/ssh-tunnel-local-and-remote-port-forwarding-explained-with-examples.html).
You use SSH to virtually "connect" a port on the remote machine (e.g.,
`magneto`) to a port on your local machine (e.g., your laptop).

To know this, you need to know the port on which your `Jupyter` notebook
will be listening on the remote machine.  This port is selected (almost) at
random on startup (you can see it in the output when you run
`~/jupyter-profile-nbserver/start`), but you can also specify it in the
`~/jupyter-profile-nbserver/jupyter_notebook_config.py`, for example:
```
c.NotebookApp.port = 9999
```

Once you know the port, run this:
```
ssh -nNT -L 9999:localhost:9999 magneto.astro.washington.edu
```
on your local machine (e.g., laptop). This will instruct ssh to virtually
connect port 9999 on your laptop, to port 9999 on magneto (don't forget to
use the port number you've chosen; mine just happens to be 9999). You can
then start your `Jupyter` notebook server, and access the notebooks by going
to:
```
https://localhost:9999
```
