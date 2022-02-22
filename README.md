<a href="https://gohugo.io" target="_blank" rel="noopener noreffer"><img src="https://img.shields.io/badge/Frame-Hugo-blue?style=flat&logo=Hugo&color=FF4088"></a> <a href="https://github.com/HEIGE-PCloud/DoIt" target="_blank" rel="noopener noreffer"><img src="https://img.shields.io/badge/Theme-DoIt-blue?style=flat&logo=CSS3&logoColor=0594CB&color=0594CB"></a> <a href="https://github.com/BahuangShanren/blog/blob/master/.github/workflows/gh-pages.yml" target="_blank" rel="noopener noreffer"><img src="https://img.shields.io/badge/Build-GitHub_Actions-blue?style=flat&logo=GitHub%20Actions&logoColor=FFFFFF&color=33BA91"></a> <a href="https://www.cloudflare.com/" target="_blank" rel="noopener noreffer"><img src="https://img.shields.io/badge/CDN-Cloudflare-blue?style=flat&logo=Cloudflare&color=F38020"></a> <a href="https://gitee.com/BahuangShanren/blog" target="_blank" rel="noopener noreffer"><img src="https://img.shields.io/badge/Mirror-Gitee-blue?style=flat&logo=Gitee&logoColor=C71D23&color=C71D23"></a>

## 博客结构

| 框架                      | 主题                                         | 托管                                             | 构建                                                         | CDN                                       | 镜像                                           |
| ------------------------- | -------------------------------------------- | ------------------------------------------------ | ------------------------------------------------------------ | ----------------------------------------- | ---------------------------------------------- |
| [Hugo](https://gohugo.io) | [DoIt](https://github.com/HEIGE-PCloud/DoIt) | [GitHub](https://github.com/BahuangShanren/blog) | [GitHub Actions](https://github.com/BahuangShanren/blog/blob/master/.github/workflows/gh-pages.yml) | [Cloudflare](https://www.cloudflare.com/) | [Gitee](https://gitee.com/BahuangShanren/blog) |

## DoIt主题

- 并非通过[Submodule](https://github.com/HEIGE-PCloud/DoIt#migrate-from-loveit)方式引用的主题，而是下载使用了截止到[212597d](https://github.com/HEIGE-PCloud/DoIt/tree/212597df6973aea569ed085af51ac839448c4c6f)这个commit的版本

- Twikoo Failed to transform，参考[Issue](https://github.com/HEIGE-PCloud/DoIt/issues/469)

- 自定义社交链接模板`E:\GitRepo\blog\themes\DoIt\assets\data\social.yml`，引用图标链接位于`themes\DoIt\assets\svg\icons`

- 修复keywords不生效，参考[链接](https://www.bahuangshanren.tech/2021-2/#keywords%E4%B8%8D%E7%94%9F%E6%95%88)。然而大部分搜索引擎和网站都放弃使用meta keyword了，参考[Pull request](https://github.com/HEIGE-PCloud/DoIt/pull/473)
