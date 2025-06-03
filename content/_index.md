---
title: '首页'
date: 2025-06-03
type: landing

design:
  spacing: "6rem"

sections:
  - block: hero
    content:
      title: "打造完美的 Hugo 静态网站"
      text: "专注分享 Hugo 主题教程与静态博客部署实践，让建站变得简单有趣 ⚡️"
      primary_action:
        text: "开始探索"
        url: "/docs/"
        icon: "rocket-launch"
      secondary_action:
        text: "查看教程"
        url: "/tutorial/"
      announcement:
        text: "新增 Hugo 主题开发教程"
        link:
          text: "立即查看"
          url: "/blog/hugo-theme-development/"
    design:
      spacing:
        padding: [0, 0, 0, 0]
        margin: [0, 0, 0, 0]
      css_class: "min-h-screen"
      background:
        color: ""
        image:
          filename: "hero-background.jpg"  # 您需要在 assets/media/ 添加一张适合的背景图
          filters:
            brightness: 0.7

  - block: stats
    content:
      items:
        - statistic: "50+"
          description: |
            精选 Hugo 主题  
            详细教程
        - statistic: "100+"
          description: |
            建站技巧  
            实战分享
        - statistic: "24/7"
          description: |
            持续更新  
            技术支持
    design:
      css_class: "bg-gray-100 dark:bg-gray-800"
      spacing:
        padding: ["1rem", 0, "1rem", 0]

  - block: features
    id: features
    content:
      title: "网站特色"
      text: "提供全面的 Hugo 主题教程与静态博客部署指南，助您轻松打造专业的个人网站。包含从入门到进阶的完整教程，让建站变得简单有趣。"
      items:
        - name: "Hugo 主题精选"
          icon: "palette"
          description: "精心挑选并详细介绍优质 Hugo 主题，包含主题安装、配置和自定义教程，助您找到最适合的主题。"
        
        - name: "部署教程"
          icon: "cloud"
          description: "提供 GitHub Pages、Netlify、Vercel 等多平台的详细部署指南，手把手教您完成网站上线。"
        
        - name: "性能优化"
          icon: "bolt"
          description: "分享 Hugo 网站优化技巧，包括图片处理、CDN 配置、缓存策略等，让您的网站加载更快。"
        
        - name: "实用技巧"
          icon: "light-bulb"
          description: "提供评论系统集成、SEO 优化、自定义短代码等实用教程，助您打造功能完善的博客。"
        
        - name: "问题解决"
          icon: "wrench"
          description: "收集整理常见问题和解决方案，提供详细的故障排除指南，帮您快速解决建站过程中的困难。"
        
        - name: "持续更新"
          icon: "arrow-path"
          description: "定期更新最新的 Hugo 主题资讯和建站技巧，及时分享新功能使用方法和最佳实践。"

  - block: cta-card
    content:
      title: "开启您的 Hugo 建站之旅"
      text: "从零基础到成功部署，从主题选择到性能优化，我们提供完整的 Hugo 建站解决方案。现在就开始您的建站之旅，创建一个独特的个人网站！"
      button:
        text: "立即开始"
        url: "/getting-started/"    # 指向您的入门指南页面
    design:
      card:
        css_class: "bg-primary-700"
        css_style: ""
---