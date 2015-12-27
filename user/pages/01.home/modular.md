---
cache_enable: false
content:
    items: @self.modular
    order:
        by: default
        dir: asc
        custom:
            - _about
            - _activity
            - _inquiry
            
form:
    name: inquiry
    action: /
    fields:
        - name: name
          label: お名前
          type: text
          validate:
            required: true

        - name: email
          label: メールアドレス
          type: email
          validate:
            required: true
            
        - name: address
          label: ご住所
          type: text
          
        - name: call_number
          label: 電話番号
          type: tel
        
        - name: contact_type
          label: お問合せの種類
          type: radio
          options:
            about_a: 勉強会について
            about_b: 運営組織について
            about_c: その他
        
        - name: inquiry_content
          label: お問い合わせ内容
          type: textarea
          validate:
            required: true

    buttons:
        - type: submit
          value: 送信
          classes: 'btn position_center'
    
    process:
        - email:
            to: 
              - "hishikawa@concrete5.co.jp"
              - "{{ form.value.email }}"
            subject: "[D2DRAFT へのお問い合わせ] {{ form.value.name|e }}"
            body: "{% include 'forms/data.html.twig' %}"
        - display: '/home/thankyou'
---

![気なること、本当に知りたいこと。ここにあります。](main_image.jpg)