---
title: RecSoc Sign Up - Form

## Some test

form:
    name: my-nice-form
    action: /contact
    fields:
        - name: title
          id: title
          label: Title
          classes: form-control form-control-lg
          type: text
          validate:
            required: true
        - name: fname
          id: fname
          label: First Name
          classes: form-control form-control-lg
          placeholder: First name
          autocomplete: on
          type: text
          validate:
            required: true
        - name: sname
          id: sname
          label: Surname
          classes: form-control form-control-lg
          placeholder: Surname
          autocomplete: on
          type: text
          validate:
            required: true
        - name: gender
          type: radio
          label: Gender
          classes: form-control form-control-lg
          options:
            male: male
            female: female
            other: other
        - name: birthday
          type: date
          label: Date of Birth
          validate.min: "1900-01-01"
        - name: email
          id: email
          classes: form-control form-control-lg
          label: Email
          placeholder: Enter your email address
          type: email
          validate:
            rule: email
            required: true
        - name: cssc
          id: cssc
          classes: form-control form-control-lg
          label: CSSC Number
          placeholder: 0000-0000-0000-0000
          type: number
          validate:
            required: true
        - name: telephone
          id: telephone
          classes: form-control form-control-lg
          label: Telephone
          placeholder: 01234 567890
          type: telephone
          validate:
            rule: telephone
            required: true
    buttons:
        - type: submit
          value: Submit
          class: btn btn-primary btn-block
    process:
        - email:
            from: "{{ config.plugins.email.from }}"
            to:
              - "{{ config.plugins.email.from }}"
              - "{{ form.value.email }}"
            subject: "[Feedback] {{ form.value.name|e }}"
            body: "{% include 'forms/data.html.twig' %}"
        - save:
            fileprefix: feedback-
            dateformat: Ymd-His-u
            extension: txt
            body: "{% include 'forms/data.txt.twig' %}"
        - message: Thank you for your feedback!
        - display: thankyou

---
