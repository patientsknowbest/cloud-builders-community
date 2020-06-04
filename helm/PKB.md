## PKB

From Martin: 
I removed the helm.bash script, as it is mostly concerned with authenticating kubectl and we should do that by default in our deployment scripts anyway
I also neglect to define an entrypoint into the Dockerfile, since we'll be passing it a bash script anyway.
Finally, I pre-installed helm diff in the Dockerfile itself
