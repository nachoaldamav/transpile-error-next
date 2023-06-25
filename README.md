# Next doesn't refresh components when the directory is not fully symlinked

> This repo is a reproduction of a bug in Next.js. The Node_modules directory is being uploaded to make the reproduction easier.

In this repo I show how Next.js doesn't refresh the page when a component is recompiled and the directory is not fully symlinked. (Only the `index.tsx` file is symlinked, and the other files in the component (package) are generated in the `node_modules/@acme/my-component` directory).

## Steps to reproduce

1. Clone this repo
2. Run `cd node_modules/@acme/my-component` and `pnpm dev` to start the component compilation (Don't install the dependencies as it will break the reproduction)
3. In another terminal, run `pnpm dev` in the root directory to start the Next.js app
4. Open `http://localhost:3000` in your browser
5. Edit the `my-awesome-component/index.tsx` file and save it
6. The component should be recompiled, but the page is not refreshed

## Expected behavior

The page should be refreshed when the component is recompiled. Next compiles something, but it's not the component.