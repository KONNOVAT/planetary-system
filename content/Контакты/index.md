---
title: Контакты
date: 2025-04-12

type: landing

sections:
  - block: contact
    content:
      title: Contact
      text: |-
        Добро пожаловать на страницу нашей команды! Мы — группа из пяти увлеченных исследователей, объединенных общей целью: изучение модели формирования планетной системы на основе теоретического анализа и численного моделирования. Наша работа направлена на понимание процессов, которые привели к образованию планет, их спутников и других небесных тел в нашей и других звездных системах.
      address:
        street: Орджоникидзе, 3
        city: Москва
        region: Москва
        postcode: '94305'
        country: Россия
        country_code: RU
      coordinates:
        latitude: '37.4275'
        longitude: '-122.1697'
      directions: Enter Building 1 and take the stairs to Office 200 on Floor 2
      office_hours:
        - 'Понедельник 10:00 to 13:00'
        - 'Четверг 09:00 to 10:00'
      appointment_url: 'https://calendly.com'
      #contact_links:
      #  - icon: comments
      #    icon_pack: fas
      #    name: Discuss on Forum
      #    link: 'https://discourse.gohugo.io'
    
      # Automatically link email and phone or display as text?
      autolink: true
    
      # Email form provider
      form:
        provider: netlify
        formspree:
          id:
        netlify:
          # Enable CAPTCHA challenge to reduce spam?
          captcha: false
    design:
      columns: '1'

  - block: markdown
    content:
      title:
      subtitle: ''
      text:
    design:
      columns: '1'
      background:
        image: 
          filename: contact.jpg
          filters:
            brightness: 1
          parallax: false
          position: center
          size: cover
          text_color_light: true
      spacing:
        padding: ['20px', '0', '20px', '0']
      css_class: fullscreen
---
