# A warning about Safari

Safari won't work with Jupyter and self-signed certificates, which is what
we use for secure access to remote notebooks.  There's no known workaround,
other than to use a different browser (e.g., Chrome or Firefox).

Note that Safari will work just fine as long as you're running your
notebooks locally.

See [this issue](https://github.com/jupyter/jupyterhub/issues/292) for a technical explanation.
