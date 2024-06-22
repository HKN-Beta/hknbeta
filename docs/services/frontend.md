# Frontend/`storefront`

The `storefront` is the part of the point-of-sale software that members interact with daily.  It offers the following interfaces: 
- Regular POS interface where customers can purchase things, with cash or tabs.
- Manage customer tabs - creation or updation.
- Manage inventory - add, remove, or update items.
- Create special orders for the ECE department or other special events.
- Report statistics on sales, inventory, and other metrics.

The storefront was written in Nuxt, and the code is hosted on GitHub at [HKN-Beta/storefront](https://github.com/HKN-Beta/hknpos-frontend).  The storefront can be accessed by navigating to the website at `/pos`.

## Development instructions

### Set up your environment

After cloning the `storefront` repository to your local machine, you can install the necessary dependencies by simply running `npm i`.  This will install all the necessary packages to run the storefront locally.

### Run the storefront locally

You can run the storefront locally by running `npm run dev`.  This will start a local server that you can access by navigating to the URL that gets printed out.

To ensure separation of development "orders" from real ones, the backend URL **must** be set to something other than the hknbeta website.  Creating your own Medusa backend is your best bet.  You can do this by setting the `MEDUSA_BACKEND` environment variable to the URL of your Medusa backend when executing `npm run dev`.

### Push your changes

Pushing your changes to `main`, currently, will automatically build and deploy a Docker image with the compiled storefront to hknbeta, but **not** automatically deploy it.  This is a security measure to ensure that the storefront is not accidentally exposed to the internet before it's ready.  You will need to manually restart the Traefik service to get it to recognize the new storefront.

As we re-enter regular semesters, we'll increase restrictions to ensure no one can just push code to `main` without careful review.