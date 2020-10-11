## firebase-deploy-directory

![npm](https://img.shields.io/npm/v/firebase-deploy-directory?style=flat-square)

Use firebase-deploy-directory as a replacement for `firebase deploy` if you use Firebase hosting and want to deploy different parts of your site from different repos or directories.

For example, if your main website is hosted at `https://example.com` and you have a separate repo for your blog hosted at `https://example.com/blog`.

In the repo for your main website, where you keep your `firebase.json`, you would run

```
firebase-deploy-directory \
  --project <firebase-project-name> \
  --replace-config \ 
  --directory <directory-that-contains-website-files e.g. build/> \
  --exclude-subpath blog \
  --commit
```

If you're running this from CI, then add `--token $FIREBASE_TOKEN`, where `$FIREBASE_TOKEN` is the token you got from `firebase login:ci`.

In the repo for your blog, run

```
firebase-deploy-directory \
  --project <firebase-project-name> \
  --directory <directory-that-contains-website-files e.g. build/> \
  --subpath blog \
  --commit
```

You can leave off the commit flag to do a dry run.

You can deploy from multiple directories, just add a new `--exclude-subpath` flag for each path. For example, if you're deploying `/blog` and `/changelog` from different repos, your deploy command for the main repo would be:

```
firebase-deploy-directory \
  --project <firebase-project-name> \
  --replace-config \ 
  --directory <directory-that-contains-website-files e.g. build/> \
  --exclude-subpath blog \
  --exclude-subpath changelog \  
  --commit
```

# Usage

Upload directory to firebase hosting 

```shell
firebase-deploy-directory --project <project-name> --subpath <subpath> --directory <directory-to-upload> --token <ci-token> --commit


Options:
  --version          Show version number                               [boolean]
  --project          The name of the Firebase project        [string] [required]
  --subpath          The subpath that the directory should be deployed to (e.g.
                     `schema` for `https://example.com/schema`)         [string]
  --exclude-subpath  If deploying everthing except subpaths, the subpaths to
                     ignore                                              [array]
  --directory        The directory to upload                 [string] [required]
  --commit           If not set, does a dry run                        [boolean]
  --token            Token to use to deploy                             [string]
  --replace-config   Set to true if you want to use the config from your
                     firebase.json, otherwise uses the config from the last
                     release                                           [boolean]
  --help             Show help                                         [boolean]
```
