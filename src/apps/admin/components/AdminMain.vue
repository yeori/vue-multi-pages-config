<template>
  <div>
    <p>
      It has two SPAs, MAIN and ADMIN
    </p>
    <textarea class="form-control" rows="20" v-model="vue_config_js">
    </textarea>
    <textarea class="form-control" rows="20" v-model="desc">
    </textarea>
  </div>
</template>

<script>
export default {
  data() {
    return {
      desc: `<template>
  <div>
    <div>
      <router-link to="/">HOME(router link)</router-link> |
      <router-link to="/desc">Description(router link)</router-link> |
      <a href="/admin">ADMIN(anchor)</a>
    </div>
    <h3>main page</h3>
    <router-view/>
  </div>
</template>`,
      vue_config_js: `const path = require('path');

function resolve(dir) {
  return path.join(__dirname, dir);
}
module.exports = {
  pages: {
    index: {
      entry: './src/apps/main/index.js',
      template: 'public/main.html',
      filename: 'index.html',
      title: 'HOME',
    },
    admin: {
      entry: './src/apps/admin/index.js',
      template: 'public/admin.html',
      filename: 'admin/index.html',
      title: 'ADMIN',
    },
  },
  chainWebpack: (config) => {
    config.resolve.alias
      .set('@', resolve('src'))
      .set('@admin', resolve('src/apps/admin'))
      .set('@main', resolve('src/apps/main'));
  },
};
    `,
    };
  },
};
</script>
