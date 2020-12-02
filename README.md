# rubocop-inherited-extensions-bug

When RuboCop inherits config from a gem, it suggests that you install extensions that are already configured in the gem.

```console
$ git clone https://github.com/haines/rubocop-inherited-extensions-bug.git
$ cd rubocop-inherited-extensions-bug/project
$ bundle install
$ bundle exec rubocop
Inspecting 2 files
.C

Offenses:

spec/some_spec.rb:3:16: C: RSpec/DescribeClass: The first argument to describe should be the class or module being tested.
RSpec.describe 'offensive' do
               ^^^^^^^^^^^

2 files inspected, 1 offense detected

Tip: Based on detected gems, the following RuboCop extension libraries might be helpful:
  * rubocop-rspec (http://github.com/rubocop-hq/rubocop-rspec)

You can opt out of this message by adding the following to your config (see https://docs.rubocop.org/rubocop/extensions.html#extension-suggestions for more options):
  AllCops:
    SuggestExtensions: false
```

From the offense that's detected, it's clear that `rubocop-rspec` is configured, so the "Tip" shouldn't be displayed.
