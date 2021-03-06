# MYOB Api

[MYOB Api](https://github.com/davidlumley/myob-api) is an interface for accessing [MYOB](http://developer.myob.com/api/accountright/v2/)'s  AccountRight Live API.

## Installation

Add this line to your application's Gemfile:

    gem 'myob-api'

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install myob-api

## Usage

### API Client Setup

Create an api_client:

    api_client = Myob::Api::Client.new({
      :consumer => {
        :key    => YOUR_CONSUMER_KEY,
        :secret => YOUR_CONSUMER_SECRET,
      },
      :access_token => YOUR_OAUTH_ACCESS_TOKEN,
    })

Or if you know which Company File you want to access too:

    api_client = Myob::Api::Client.new({
      :consumer => {
        :key    => YOUR_CONSUMER_KEY,
        :secret => YOUR_CONSUMER_SECRET,
      },
      :access_token => YOUR_OAUTH_ACCESS_TOKEN,
      :company_file => {
        :id       => COMPANY_FILE_ID,
        :username => COMPANY_FILE_USERNAME,
        :password => COMPANY_FILE_PASSWORD,
      },
    })

### API Methods

Before using the majority of API methods you will need to have selected a Company File. If you've already selected one when creating the client, feel free to ignore this.

#### Company Files

Return a list of company files

    api_client.company_file.all

Select a company file to work with

    api_client.select_company_file({
      :id       => COMPANY_FILE_ID,
      :username => COMPANY_FILE_USERNAME,
      :password => COMPANY_FILE_PASSWORD,
    })

####  Contacts

Return a list of all contacts

    api_client.contact.all

#### Customers

Return a list of all customers (a subset of contacts)

    api_client.customer.all


## Todo

* Expand API methods
* Refactor client factory architecture
* Tests


## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request
