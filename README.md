# Instructions

To run the project locally, navigate to the project directory and run:

```
bundle install
``` 

To start the Jekyll local development server.

```
bundle exec jekyll serve
bundle exec jekyll serve --livereload
``` 

To build static content

```
bundle exec jekyll build
```

Clean up your jekyll build and cache

```
bundle exec jekyll clean
```

## Working with a Local Git Repository

***added in netlify-cms@2.10.17 / netlify-cms-app@2.11.14***

You can connect Decap CMS to a local Git repository, instead of working with a live repo.

1. Navigate to a local Git repository configured with the CMS.
2. Add the top-level property `local_backend` configuration to your `config.yml`:

```yaml
backend:
  name: git-gateway

# when using the default proxy server port
local_backend: true
```

3. Run `npx netlify-cms-proxy-server` from the root directory of the above repository.

   * If the default port (8081) is in use, the proxy server won't start and you will see an error message. In this case, follow [these steps](#configure-the-netlify-cms-proxy-server-port-number) before proceeding.
4. Start your local development server (e.g. run `gatsby develop`).
5. Open `http://localhost:<port>/admin` to verify that your can administer your content locally. Replace `<port>` with the port of your local development server. For example Gatsby's default port is `8000`

**Note:** `netlify-cms-proxy-server` runs an unauthenticated express server. As any client can send requests to the server, it should only be used for local development. Also note that `editorial_workflow` is not supported in this environment.

### Configure the Decap CMS proxy server port number

1. Create a `.env` file in the project's root folder and define the PORT you'd like the proxy server to use

```ini
PORT=8082
```

2. Update the `local_backend` object in `config.yml` and specify a `url` property to use your custom port number

```yaml
backend:
  name: git-gateway

local_backend:
  # when using a custom proxy server port
  url: http://localhost:8082/api/v1
  # when accessing the local site from a host other than 'localhost' or '127.0.0.1'
  allowed_hosts: ['192.168.0.1']
```


I had that error when I run bundle exec jekyll serve --livereload --trace on Jekyll.4.2.1-Ruby.3.0.3p137(mingw)-Windows. I ran gem install eventmachine --platform=ruby and it compiled at C:\Ruby30-x64\lib\ruby\gems\3.0.0\gems\eventmachine-1.2.7 but when you run bundle install it creates also C:\Ruby30-x64\lib\ruby\gems\3.0.0\gems\eventmachine-1.2.7-x64-mingw32 🤔. The command bundle info eventmachine gives me C:/Ruby30-x64/lib/ruby/gems/3.0.0/gems/eventmachine-1.2.7-x64-mingw32 and that's confimed in the Gemfile.lock with the line eventmachine (1.2.7-x64-mingw32). So I changed that line for eventmachine (1.2.7) and then the output of bundle info eventmachine gives me C:/Ruby30-x64/lib/ruby/gems/3.0.0/gems/eventmachine-1.2.7 and finally the command bundle exec jekyll serve --livereload --trace worked ✔️
