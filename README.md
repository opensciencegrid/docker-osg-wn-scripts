# docker-osg-wn-scripts

These are scripts to maintain the opensciencegrid/docker-osg-wn GitHub repo.

## update-all
Update all branches that Docker images are automatically built from.
You must have push access to the opensciencegrid/docker-osg-wn repo to use this.

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

## genbranches
Create `Dockerfile.in` files for each branch we want to create. Files will be created as `./branches/$BRANCHNAME`.
Run once.
