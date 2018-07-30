# folder\_structure

## Motivations

* Clear feature ownership
* Module usage predictibility \(refactoring, maintainence, you know

  what's shared, what's not, prevents accidental regressions,

  avoids huge directories of not-actually-reusable modules, etc\)

* CI runs only the tests that matter \(future\)
* Code splitting \(future\)

It's inverted from the model that we've used in other systems. If we consider all folders being either a "generic" or a "feature" folder, we only have one "feature" folder but many "generic" folders.

## Structure

```text
app
└── .vscode
    ├── (bin)
    ├── (build)
    ├── config
    ├── docs
    ├── (node_modules)
    ├── src
    │   ├── __test__
    │   ├── base
    │   ├── client
    │   │   ├── __test__
    │   │   ├── actions
    │   │   ├── apps
    │   │   ├── base
    │   │   ├── config
    │   │   ├── services
    │   │   ├── stores
    │   │   └── views
    │   ├── middlewares
    │   ├── models
    │   ├── public
    │   ├── routes
    │   └── services
    ├── .babelrc
    ├── .bowerrc
    ├── .deployment
    ├── .editorconfig
    ├── .env-sample
    ├── .eslintignore
    ├── .eslintrc
    ├── .gitattributes
    ├── .gitignore
    ├── app.json
    ├── deploy.cmd
    ├── gulpfile.js
    ├── iisnode.yml
    ├── LICENSE
    ├── package-lock.json
    ├── package.json
    ├── README.md
    ├── tsconfig.json
    ├── tslint.json
    └── webpack.config.js
```

