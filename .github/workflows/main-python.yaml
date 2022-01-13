name: Main

on:
  workflow_call:
    inputs:
      python-version:
        description: 'The Python version to download (if necessary) and use.'
        default: '3.8'
        required: false
        type: string
    secrets:
      # User name associated with the PAT.
      ghcr-username:
        description: 'Username associated with the PAT used to authenticate to GHCR.'
        required: true
      # PAT for authenticating to GHCR, we cannot use the GITHUB_TOKEN because it would not
      # trigger subsequent actions necessary for continuous deployment.
      ghcr-password:
        description: 'PAT token used to authenticate to GHCR.'
        required: true

jobs:

  # Builds and pushes images to GHCR.
  deploy:
    name: Deploy
    runs-on: ubuntu-latest
    steps:
    - name: Checkout
      uses: actions/checkout@v2

    - name: Build and Push
      uses: gramLabs/.github/.github/actions/build-push@main
      with:
        ghcr-username: '${{ secrets.ghcr-username }}'
        ghcr-password: '${{ secrets.ghcr-password }}'
