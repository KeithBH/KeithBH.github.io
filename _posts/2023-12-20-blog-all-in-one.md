---
layout: post
title:  "Keith 对 Blog 的汇总"
date:   2023-12-20 14:08:05 +0800
categories: Blog, Jekyll, Github Pages
---

# Keith 对 Blog 的汇总

---

## 使用 Jekyll 和 Github Pages 搭建博客

### 使用RVM管理Ruby，并安装Jekyll

#### 为什么要使用 RVM

方便管理 Ruby 的版本和 gem。vm对于ruby相当于anaconda对于python。

由于疑似使用了自带的ruby，出现了诸多令人不爽的小问题，遂安装[rvm](https://rvm.io)。

参考[为什么不要使用 sudo 安装 gem](https://www.moncefbelyamani.com/why-you-should-never-use-sudo-to-install-ruby-gems/)。

#### 在 M1 Mac 上安装 RVM 和 Ruby

**设备**：Macbook Air (M1 2020)

**系统**：14.2.1 (23C71)

1. 使用官方提供的办法可能报错`gpg: 从公钥服务器接收失败：No route to host`，参考[这个链接](https://www.jianshu.com/p/f82992ff0fc4#)可顺利配置。

2. RVM 安装完成后，运行以下命令将 RVM 添加到 shell 配置文件中：

    ```echo 'source /opt/homebrew/opt/rvm/scripts/rvm' >> ~/.zshrc```

3. 重启 Terminal 或运行 source ~/.zshrc 使更改生效。

4. 使用 RVM 安装最新的 Ruby：
    ```rvm install ruby```

    注意，这里可能遇到报错：

    ```There has been an error while running make install. Halting the installation.```

    尝试了 [Stackoverflow 上相关问题的诸多解决办法](https://stackoverflow.com/questions/27832732/error-running-rvm-make-install)，但都无效。最终 Le Chat 的回答解决了这一问题：

    ```rvm install ruby --with-openssl-dir=$(brew --prefix openssl@1.1)```

5. 安装完 Ruby 后，需要设置默认的 Ruby 版本
   
   `rvm use ruby --default`

6. 验证 Ruby 是否已成功安装，如果一切顺利，应该看到已安装的 Ruby 版本号
   
   `ruby -v`

#### 安装 Jekyll

1. 安装 Jekyll：

    `gem install jekyll bundler`

2. 创建网站
    
    创建一个用于存放网站的目录，并 cd 到该目录，然后创建网站

    ```
    mkdir mysite
    cd mysite
    jekyll new .
    ```

    也可参考[此教程](https://jekyllrb.com/docs/step-by-step/01-setup/)。

    在根目录下创建的`index.html`或`index.md`均可作为主页，且两种格式都可以结合`Liquid`使用。不必纠结选择Markdown和HTML来创建网页。我目前的方案是，使用Markdown格式来构建主页，并在必要时嵌入HTML代码。

3. 本地预览

    cd 到博客的目录，并运行

    `bundle exec jekyll serve`

    为了避免重复手动刷新，推荐使用`jekyll serve --livereload`实现本地实时预览。

### （不推荐）我尝试过的配置方法

在zsh中：
1. 安装 chruby。参考[此教程](https://stackoverflow.com/questions/51126403/you-dont-have-write-permissions-for-the-library-ruby-gems-2-3-0-directory-ma)安装 chruby， chruby 是用于管理 Ruby 版本的工具；
2. 安装 Ruby。同样参考上述教程，如果你遇到了问题，可以参考[此教程](https://www.moncefbelyamani.com/how-to-install-xcode-homebrew-git-rvm-ruby-on-mac/)
3. 安装 Jekyll 和 Bundler。参考[此教程](https://github.com/BillRaymond/install-jekyll-apple-silicon/blob/main/README.md)，可以从该文章的*Install Jekyll and Bundler*部分开始；
4. 你可能还需要运行`bundle install`来安装jekyll的依赖项；
5. 运行`jekyll -v`以检查是否安装完成；

可能会出现终端中运行 `jekyll serve` 后报错 LoadError：

```
/System/Library/Frameworks/Ruby.framework/Versions/2.6/usr/lib/ruby/2.6.0/rubygems/core_ext/kernel_require.rb:54:in `require': cannot load such file -- google/protobuf_c (LoadError)
```

可能会报错

    ```
    Could not find minima-2.5.1, jekyll-feed-0.17.0, i18n-1.14.1, jekyll-sass-converter-2.2.0, rouge-3.30.0, jekyll-seo-tag-2.8.0, sassc-2.4.0, listen-3.8.0 in locally installed gems
    Run `bundle install` to install missing gems.
    ```

尝试通过 `bundle exec jekyll serve` 替代 `jekyll serve`。不过还是推荐前面的配置方式。

---

## 撰写博客相关

### Markdown 相关

#### 在有序列表之间插入代码块造成序号错乱的问题

通过缩进解决，参考[此博文](https://blog.csdn.net/qq_15364915/article/details/54584755#:~:text=在有序列表中间插入文本、段落、代码块等等都会出现序号错乱的情况%E3%80%82%20应如下解决：%20如下所示：第一个标题,第一个小标题%20第一个小小标题第二个小小标题第三个小小标题第二个小标题第三个小标题第二个标题%20代码块第三个标题主要实现原则为：%20①数字加英文句号标点.)

---

## 配置博客相关

### 常用技巧

[48 个你需要知道的 Jekyll 使用技巧](https://crispgm.com/page/48-tips-for-jekyll-you-should-know.html)

---

## 初衷

### 为什么搭建博客？

1. 记录宝贵的经验，以便在任何时间、任何设备上查看；
2. 我的知识分享给有需要的人；
3. 一个展示的窗口。

### 为什么不使用现有的博客平台？

确实，搭建一个个人博客在2023年末看起来是一个投入产出比很低的做法，尤其是在各类博客平台已经如此成熟的情况下。但是它们具有部分或全部以下缺点：

1. 我所创作的内容有可能无法被免费获取；
2. 需要频繁登录，对我和看我博客的人都是如此；
3. 现有的博客平台的*部分/全部*--功能*已经/可能*收费；
4. 内容可能会被恶意删除，尤其是大陆平台；
5. 样式单一。

### 为什么使用 Github Pages + Jekyll 的方案？

1. 完全免费；
2. 在Github上托管内容相对安全；
3. 方便的版本控制；
4. Markdown适合作为笔记的语言；
5. 其他Github和Jekyll的公认优点。

### 这篇Post的目的？

关于[Jekyll](https://jekyllrb.com/docs/)和[Github Pages](https://docs.github.com/en/pages)，已有全面的官方说明文档。

这篇post的目的在于记录我配置博客的总体思路，在配置时遇到的问题，以及解决方法。

如果你和我一样懒，或来不及全面阅读官方文档，说不定我的踩坑经验可以帮到你。



