# creator-deployer-cos

cocos creator 自动部署腾讯云 COS 的脚本
魔改自 hexo 部署腾讯云 COS 的脚本
https://github.com/75k/hexo-deployer-cos-enhanced
感谢 75k

用法:

- 首先在你的游戏项目根目录执行 `npm i creator-deployer-cos` 或 `yarn add creator-deployer-cos`

- 在项目根目录里新建 deploy.js, 填写你的 COS 配置信息

```js
const deployer = require("creator-deployer-cos");

const config = {
  url: "http://yoursite.com",

  deploy: {
    type: "cos",
    bucket: "yourBucket",
    region: "yourRegion",
    secretId: "yourSecretId",
    secretKey: "yourSecretKey"
  }
};

deployer.cosDeploy(config);
```

- 在 `package.json` 添加脚本

```json
// ...
"scripts": {
  // ...
    "deploy": "node deploy"
    // ...
  }
  // ...
```

- 根目录执行 `npm run deploy` 或 `yarn deploy`(习惯用 yarn 的同学)即可完成一键部署

得益于原 repo 的能力, 令此部署工具自动进行文件哈希比对,只上传变动部分
