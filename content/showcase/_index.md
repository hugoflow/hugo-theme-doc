---
title: 案例展示
description: "使用 Hugo 构建的精选文档网站"
type: landing
date: 2025-06-03

sections:
  - block: hero
    content:
      title: |
        <span class="text-3xl sm:text-4xl md:text-5xl">优秀站点展示</span>
      text: "探索使用 Hugo 构建的精彩网站，获取灵感，开启您的建站之旅 ⚡️"
      primary_action:
        text: "提交您的网站"
        url: "https://github.com/hugoflow/hugo-theme-doc/issues/new"
        icon: "rocket-launch"
      secondary_action:
        text: "查看更多案例"
        url: ""
      announcement:
        text: "寻找优秀的 Hugo 网站案例"
        link:
          text: "立即投稿"
          url: "https://github.com/hugoflow/hugo-theme-doc/issues/new"
    design:
      spacing:
        padding: [0, 0, 0, 0]
        margin: [0, 0, 0, 0]
      css_class: "min-h-[70vh] bg-cover bg-center relative"
      background:
        image:
          filename: "showcase-background.webp"  # 需要在 assets/media/ 添加一张适合的背景图
          filters:
            brightness: 0.7
        gradient:
          start: "rgba(0,0,0,0.6)"
          end: "rgba(0,0,0,0.3)"

  - block: collection
    content:
      title: "精选案例"
      text: "这些优秀的网站展示了 Hugo 强大的功能和灵活的定制能力。从个人博客到企业官网，从文档系统到作品集，Hugo 都能胜任。"
      filters:
        folders:
          - showcase
      sort_by: 'Date'
      sort_ascending: false
    design:
      view: card
      columns: "2"
      spacing:
        padding: ['3rem', 0, '6rem', 0]
      flip_alt_rows: true
      background:
        color: "gray.50"
---