Description
===========

Pagination for RethinkDB queries in Django. Simple.


The folder structure of this repo is intended to simulate a real django application. However, if your application uses a different directory structure you will have to make the adjustments yourself.

Installation
============

1) Place the folders inside app/ and templates/ in to your current django application.

2) Add app.utils to the INSTALLED_APPS list in your settings file(s)
```
INSTALLED_APPS = {
 ...
 'gs.utils',
 ...
}
```
3) Have a nap.

Usage Example
=============

### Passing from Django view to a template
```
def my_reports(request):
  return render_to_response('combat/reports.html', {'reports':r.table('my_reports').order_by(r.desc('id'))}, context_instance=RequestContext(request))
```


### Template usage
```
{% extends "base.html" %}
{% load rdbpaginate %}
{% block content %}
  {% rdbpaginate reports 10 %}
  {% for report in reports %}
    <a href="/report/?id={{ report.id }}" class="report">
      View Report #{{ report.combat_id }}
    </a>
  {% endfor %}
  {% paginate %}
{% end block %}
```

License stuff
=============
It's free. I hope it helped. Enjoy.
