---
title: Associate Membership form

form:
    name: contact

    fields:
        first name:
          label: First name
          placeholder: First name
          autocomplete: on
          type: text
          validate:
            required: true
            
        Surname:
          label: Surname
          placeholder: Surname
          autocomplete: on
          type: text
          validate:
            required: true
            
        Email:
          label: Email
          placeholder: Enter your email address
          type: email
          validate:
            required: true
        
        Contact number:
          label: phone number
          type: text
          validate:
            required: true
            
        Current Employer:
          label: employer
          type: text

    buttons:
        submit:
          type: submit
          value: Submit

    process:
        save:
            fileprefix: contact-
            dateformat: Ymd-His-u
            extension: txt
            body: "{% include 'forms/data.txt.twig' %}"
        email:
            subject: "[Site Contact Form] {{ form.value.name|e }}"
            body: "{% include 'forms/data.html.twig' %}"
        message: Thank you for getting in touch!
        display: thankyou
---

# Membership information
The membership year runs from 1st September until 31st August annually.

The annual rate for 2019-2020 is £28.00 and is renewable on or before the 31st of August each year.

If you are applying for membership part way through the membership year, you are only required to pay for those months until the new year membership begins in september. 

Monthly rates are £2.50 per full month. The below table displays the membership prices for each month of the year.



