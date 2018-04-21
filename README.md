# django-cool-pagination

[![Build Status](https://travis-ci.org/joe513/django-cool-pagination.svg?branch=master)](https://travis-ci.org/joe513/django-cool-pagination)
[![Coverage Status](https://coveralls.io/repos/github/joe513/django-cool-pagination/badge.svg?branch=master)](https://coveralls.io/github/joe513/django-cool-pagination?branch=master)
[![PyPI version](https://badge.fury.io/py/django-cool-pagination.svg)](https://badge.fury.io/py/django-cool-pagination)

*django-cool-pagination* is simple pagination app that saves your time.

## WARNING:
 **The project is still on development stage, some things may not work properly.**
 
 
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/8/87/Old_book_bindings.jpg/1280px-Old_book_bindings.jpg" />

## Prerequisites
Currently it supports Bootstrap 4.x only. So that you have to add [Bootstrap4](https://getbootstrap.com/docs/4.1/getting-started/download) to your project.
## Features
   - _Dynamic query string creation_
   - _Length auto control_
   - _Fully customizable_ (aspiring)
   
## Installing
### pip

    pip install django-cool-pagination
### setup.py
    git clone https://github.com/joe513/django-cool-pagination.git
    cd django-cool-pagination
    python setup.py install

## Using

### View
#### FBV (Function based view)

    def listing(request):
        contact_list = Contacts.objects.all()
        paginator = Paginator(contact_list, 25)

        page = request.GET.get('page')
        page_obj = paginator.get_page(page)
        return render(request, 'list.html', {'page_obj': page_obj})

#### CBV (Class based view)

    class Listing(ListView):
        model = Item
        paginate_by = 5

### Template
    {% load cool_paginate %}
    
    {% for contact in page_obj %}
        ...
    {% endfor %}
    
    {% cool_paginate %}

## Customization
You can customize it so that it works as you want. Customize it by defining settings either in setting.py or 
inside of `{% cool_paginate %} `

#### setting.py

`COOL_PAGINATOR_NEXT_NAME` - Name for "next" button in pagination bar. <br/>
`COOL_PAGINATOR_PREVIOUS_NAME` - Name for "prevous" button in pagination bar <br/>
`COOL_PAGINATOR_SIZE` - Size of pagination bar (choose: "LARGE" or "SMALL") <br/>


#### {% cool_paginate page_obj='' next_name='' previous_name='' size='' %}
`page_obj` - Type here your 'page' object. <br/>
`next_name` - Name for "next" button in pagination bar. <br/>
`previous_name` - Name for "prevous" button in pagination bar <br/>
`size` - Size of pagination bar (choose: "LARGE" or "SMALL") <br/>


> **Note:**
> {% cool_paginate %} has a priority, _django-cool-pagination_ will firstly look at this, after at setting.py

## License
This project is licensed under the MIT License - see the LICENSE file for details
