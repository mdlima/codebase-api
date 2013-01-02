# CodebaseApi

A gem to interact with the [Codebase](http://www.codebasehq.com) API.

## Installation

Add this line to your application's Gemfile:

    gem 'codebase_api'

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install codebase_api

## Usage

The Codebase API requires authentication using your account name & username along with your API Key.

In a Rails app, create a file called `config/initializers/codebase.rb` and fill it with this info (changing it for your account, etc)

```ruby
CodebaseApi.account_user = "account/user"
CodebaseApi.api_key = "apikey"
```

## Commands

The CodebaseApi gem is built to access all the Codebase API functions.


### Projects
#### Displays a list of all projects on your Codebase account
```ruby
CodebaseApi::Project.all
```

#### Shows a specific project
```ruby
CodebaseApi::Project.view("my-cool-project")
```

#### Create a new project
```ruby
CodebaseApi::Project.create("a new project")
```


### Project Groups
#### Display a list of all project groups
```ruby
CodebaseApi::ProjectGroup.all
```


### Project Users
#### Display a list of all users assigned to a project
```ruby
CodebaseApi::ProjectUser.all("my-cool-project")
```

#### Assign users to a project (currently broken)
```ruby
CodebaseApi::ProjectUser.assign("my-cool-project", [ :users => {:user => {:id => 123}, {:user => {:id => 123} } ])
```


### Repositories
#### Display a list of all repositories for a project
```ruby
CodebaseApi::Repository.all("my-cool-project")
```

#### View a specified repository
```ruby
CodebaseApi::Repository.show("my-cool-project", "test-repo")
```

#### Create a repository for a project
The types of repository are Git (git), Subversion (svn), Mercurial (hg) and Bazaar (bzr).
```ruby
CodebaseApi::Repository.create("my-cool-project", "new-repo-name", "git")
```


### Commits
#### Show a list of commits for a specific ref (short or long)
```ruby
CodebaseApi::Commit.show("my-cool-project", "test-repo", "abc123abc")
```

#### Show a list of commits for a specific ref (short or long) for a path
```ruby
CodebaseApi::Commit.show_path("my-cool-project", "test-repo", "abc123abc", "spec/features/admin_spec.rb")
```






















## Contributing

Fork this project, make any changes and create a pull request :)