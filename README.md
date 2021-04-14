# Prerequisites

* [rbenv](https://github.com/rbenv/rbenv) (or Ruby 2.4 - 2.7)
* [bundler](https://bundler.io/)


## Setup rbenv/ruby/bundler (if needed)

1. Install rbenv - `brew install rbenv`
2. Init rbenv - `rbenv init`
3. Add to `~/.zshrc`:
    ```bash
    export PATH="$HOME/.rbenv/bin:$PATH"
    eval "$(rbenv init -)"
    ```
4. Verify no errors - `curl -fsSL https://github.com/rbenv/rbenv-installer/raw/master/bin/rbenv-doctor | bash`
5. Set ruby version - `rbenv local 2.7.3`
6. Verify correct version - `ruby --version`
7. Install bundler - `gem install bundler`
8. Run `bundle update` in root to sync.


# Fastlane

Copy [/ios/fastlane/example.env](/ios/fastlane/example.env) to `/ios/fastlane/.env` and fill in the required environment variables. Descriptions are in the file.

Fastlane configuration is defined in [/ios/fastlane/Fastfile](/ios/fastlane/Fastfile).

## Running Lanes
To run a lane first make sure you're in the `ios` dir (`android` currently not supported).

Running a lane is done by running `bundle exec fastlane <lane>`, for example `bundle exec fastlane beta` to run the iOS beta lane.

### Lanes
| Lane    | Description                                                                                                                    |
| ------- | ------------------------------------------------------------------------------------------------------------------------------ |
| `beta`  | Push a new beta build to TestFlight. This builds the app (using the **build** lane) and then pushes the build onto Testflight. |
| `build` | Build the app with correct distribution signing.                                                                               |