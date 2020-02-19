# Usage

Upload directory to firebase hosting


firebase-deploy-directory --project <project-name> --subpath <subpath> --directory <directory-to-upload> --token <ci-token> --commit

Options:
  --version    Show version number                                                                                   [boolean]
  --project    The name of the Firebase project                                                                      [string] [required]
  --subpath    The subpath that the directory should be deployed to (e.g. `schema` for `https://example.com/schema`) [string] [required]
  --directory  The directory to upload                                                                               [string] [required]
  --commit     If not set, does a dry run                                                                            [boolean]
  --token      Token to use to deploy                                                                                [string]
  --help       Show help                                                                                             [boolean]
