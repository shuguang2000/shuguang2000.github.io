---
title: GitHub Pages中的自定义域
date: 2022-11-10 15:31:58
updated: {{ updated }}
categories:
- Blog
tags:
- GitHub Pages
author: shuguang2000
keywords: GitHub Pages自定义域
comments: true
---
- GitHub Pages 支持使用自定义域，或将站点 URL 的根从默认值（如`username.github.io`）更改为拥有的任何域（如`blog.octocat.com`）。

<!--more-->

------

### GitHub Pages中的自定义域简述

- 支持的自定义域
  - GitHub Pages 适用于两种类型的域：
    - 子域
      - www子域：`www.example.com`
      - 自定义子域：`blog.example.com`
    </br>
    - 顶级域（apex 域)：`example.com`
      - 顶点域是不包含子域的自定义域
      - 也称为基本域、裸域、裸域、根顶点或区域顶点域。
    </br>
    - 配置了自定义域后，自定义域将替换该帐户所拥有但未配置自定义域的任何**项目站点**的 username.github.io或organization.github.io部分 URL。(如`www.octocat.com/blog`)
</br>
- 为 GitHub Pages 站点使用子域
  - 子域通过 DNS 提供商配置有CNAME指向站点默认域（`username.github.io`）。
    - www子域
      - 最常用的子域类型。例如，www.example.com包括一个www子域。
      - www子域是**最稳定**的自定义域类型，因为www子域不受 GitHub **服务器 IP 地址**更改的影响。
    </br>
    - 自定义子域
      - 自定义子域是一种不使用标准www变体的子域。
</br>
- 为 GitHub Pages 站点使用顶级域
  - 顶级域通过 DNS 提供商配置有A、ALIAS或记录。
  </br>

  - 如果使用 apex 域作为自定义域名，**建议**还设置一个 www 子域。
  
  - 如果通过 DNS 提供程序配置每种域类型的正确记录，GitHub Pages 将自动在域之间创建重定向。
    - 例如，如果将 `www.example.com` 配置为站点的自定义域，并且为顶点和 www 域设置了 GitHub Pages DNS 记录，则 `example.com` 将重定向到 `www.example.com` 。（反之也一样） **注意**，自动重定向仅适用于 www 子域。
</br>
- 保护 GitHub Pages 站点的自定义域
  - 如果 GitHub Pages 站点已禁用，但设置了自定义域，则存在域接管的风险。
  - 验证自定义域可防止其他 GitHub 用户将你的域用于他们的存储库。
  - 验证的域会阻止其他 GitHub 用户接管的自定义域并使用它来发布他们自己的 GitHub Pages 站点。
</br>
- 建议始终使用www子域，即使还使用顶级域。
  - 当使用顶级域创建新站点时，会自动尝试保护www子域以在提供站点内容时使用，但需要更改 DNS 才能使用www子域。如果配置www子域，会自动尝试保护关联的顶级域。

------

#### 管理自定义域

- 可以设置或更新某些 DNS 记录和存储库设置，以将 GitHub Pages 站点的默认域指向自定义域。

- 配置子域
  - 在存储库中为站点配置自定义子域（如`www.octocat.com`）
  - 使用 DNS 提供商配置 CNAME 记录
    - 配置子域（如www）指向站点默认域名（如`username.github.io`）
  - 若要为站点强制实施 HTTPS 加密，请选择“强制实施 HTTPS”。（**可选**）
</br>
- 配置顶点域
  - 在存储库中为站点配置顶点域（如`octocat.com`）
  - 使用 DNS 提供商至少配置 一个ALIAS、ANAME或A 记录
    - 配置A记录指向站点ip
    - 配置AAAA记录指向站点ipv6
    - 若要为站点强制实施 HTTPS 加密，请选择“强制实施 HTTPS”。（**可选**）
    - 建议还设置一个 www 子域（GitHub Pages 将自动在域之间创建重定向）
    - 建议勿使用通配符 DNS 记录，例如 *.example.com。(通配符 DNS 记录将允许任何人在你的其中一个子域上托管 GitHub Pages 站点)
</br>
- 配置顶点域和www子域变体
  - 使用 DNS 提供商配置 A 记录
  - 使用 DNS 提供商配置 CNAME 记录
</br>
- 验证自定义域
  - 通过DNS TXT record验证自定义域
    - 使用 GitHub 提供 TXT 记录
    - 使用 DNS 提供商配置该 TXT 记录

- 更多操作参考：[GitHub Pages 管理自定义域](https://docs.github.com/cn/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site)

------

#### 自定义域相关问题

- 关于给项目站点添加自定义域
  - 使用 DNS 提供商配置一条CNAME记录，使用自定义域名(如：`blog.example.com`)指向GitHub Pages默认域（如`username.github.io`）即可。
    - 关于Hexo
      - 应手动在source目录添加CNAME文件并填写自定义域。
</br>
- 关于[GoDaddy](https://www.godaddy.com/)
  - 由于GoDaddy购买的域名默认是停放的（Parked），并且www子域名是默认指向顶级域。
    - 删除关于" A @ Parked" 的 A 记录
    - 建议更改www子域指向GitHub Pages 站点的默认域（`username.github.io.`）
</br>
- 关于使用强制 HTTPS
  - GitHub 不会颁发 TSL 证书，除非的 CNAME 记录www子域指向站点默认域（`username.github.io.`）
  - 关于项目站点：在站点默认域成功更改自定义域后，项目站点即可勾选强制HTTPS
</br>
- [更多 GitHub Pages 的证书问题](https://github.com/orgs/community/discussions/22052)

------

##### 致谢

- [GitHub Pages配置自定义域](https://docs.github.com/cn/pages/configuring-a-custom-domain-for-your-github-pages-site/about-custom-domains-and-github-pages#supported-custom-domains)
</br>

- [GitHub证书请求错误](https://github.com/orgs/community/discussions/22052)
