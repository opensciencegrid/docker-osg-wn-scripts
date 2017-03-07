# docker-osg-wn-scripts

These are scripts to maintain the opensciencegrid/docker-osg-wn GitHub repo.

The primary script is `update-all`. After a release, once the osg repo on
repo.grid.iu.edu has been updated with the new release, check out this repo and
the opensciencegrid/docker-osg-wn repo, point `update-all` at your clone of
docker-osg-wn, and follow the instructions it prints to push the updates back
to GitHub, where they will be automatically used to build new Docker images..



## update-all
Update all branches that Docker images are automatically built from.
You must have push access to the opensciencegrid/docker-osg-wn repo to use this.
For safety reasons, this does not automatically push the branches to GitHub,
but it gives you the instructions on how to do so after verifying that the
updates look correct.

Usage:
```
git clone git@github.com:opensciencegrid/docker-osg-wn-scripts.git
git clone git@github.com:opensciencegrid/docker-osg-wn.git
docker-osg-wn-scripts/update-all docker-osg-wn
```

## update-one
Regenerate the `Dockerfile` from the `Dockerfile.in` template in the current branch and commit the changes.
Typically called by `update-all`.

Usage:
```
git clone git@github.com:opensciencegrid/docker-osg-wn-scripts.git
git clone git@github.com:opensciencegrid/docker-osg-wn.git
cd docker-osg-wn
git checkout BRANCH
../docker-osg-wn-scripts/update-one "."
```

## osg-wn-nightly-build / osg-wn-nightly-build.service
Update the branches that nightly Docker images are automatically built from.
This is run periodically via the systemd service `osg-wn-nightly-build.service`.
Ensure the user has a deploy key with push access to the
opensciencegrid/docker-osg-wn repository.

## genbranches
Create `Dockerfile.in` files for each branch we want to create. Files will be created as `./branches/$BRANCHNAME`.
Run once.
