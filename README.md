# Docker

### Step 1: Compose a Dockerfile that includes all essential instructions

**DockerFile**

### Step 2: Create a .dockerignore file and include node_modules in it.

### Step 3: Build and Run Docker

```shell
docker build -t react-docker
```

#### Running Docker with Vite for React Development

##### Docker Port Mapping

When running your React application inside a Docker container, it's essential to map ports correctly to ensure your services are accessible from outside the container. Use the following command to run your Docker container with port mapping:

```shell
docker run -p 5173:5173 react-docker
```

This command maps port 5173 on the host machine to port 5173 in the Docker container.

In your project's package.json, ensure your "dev" script includes the --host flag:

```json
{
	"scripts": {
		"dev": "vite --host"
	}
}
```

This script instructs Vite to use the host specified in your environment variables or configuration

### Useful commands

```shell
docker ps
docker ps -a
docker stop [FIRST_3_DIGHTS_CONTAINER_ID OR CONTAINER_NAME]
docker container prune
docker rm [FIRST_3_DIGHTS_CONTAINER_ID OR CONTAINER_NAME] --force
```

#### Docker Port Mapping and Volume Mounting

To ensure local changes reflect in the UI when running your React app in Docker, use the following command:

```shell
docker run -p 5173:5173 -v "$(pwd):/app" -v /app/node_modules react-docker
```

\*docker run: This command is used to run a Docker container.

-p 5173:5173: This option maps port 5173 on the host machine to port 5173 in the Docker container. It allows communication between the host and the container via this port.

-v "$(pwd):/app": This option mounts the current working directory (retrieved using $(pwd)) on the host machine to the /app directory inside the Docker container. This allows files in your local project directory to be accessible within the container, enabling live updates when changes are made locally.

-v /app/node_modules: This option mounts the node_modules directory inside the Docker container. It's important to mount this directory separately to ensure that the dependencies installed within the container are not overwritten by those installed locally.

react-docker: This is the name of the Docker image used to create the container. It specifies the image to be used as the base for the container.\*

##### Debugging

> Unable to find image 'react-docker:latest' locally
> docker: Error response from daemon: pull access denied for react-docker, repository does not exist or may require 'docker login': denied: requested access to the resource is denied.
> See 'docker run --help'.

Comment these commands:

```shell
RUN addgroup app && adduser -S -G app app
RUN chown -R app:app .
USER app
```

### Step 4: Login and Publish Image

```shell
docker login
```

```shell
docker tag react-docker mrtyagi07/react-docker
```

~~Published~~

# React + TypeScript + Vite

This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

Currently, two official plugins are available:

-   [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react/README.md) uses [Babel](https://babeljs.io/) for Fast Refresh
-   [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh

## Expanding the ESLint configuration

If you are developing a production application, we recommend updating the configuration to enable type aware lint rules:

-   Configure the top-level `parserOptions` property like this:

```js
export default {
	// other rules...
	parserOptions: {
		ecmaVersion: "latest",
		sourceType: "module",
		project: ["./tsconfig.json", "./tsconfig.node.json"],
		tsconfigRootDir: __dirname,
	},
};
```

-   Replace `plugin:@typescript-eslint/recommended` to `plugin:@typescript-eslint/recommended-type-checked` or `plugin:@typescript-eslint/strict-type-checked`
-   Optionally add `plugin:@typescript-eslint/stylistic-type-checked`
-   Install [eslint-plugin-react](https://github.com/jsx-eslint/eslint-plugin-react) and add `plugin:react/recommended` & `plugin:react/jsx-runtime` to the `extends` list
