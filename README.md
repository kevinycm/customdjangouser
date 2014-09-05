django-customuser
=================

This is a basic Django project setup to use a custom user class instead of Django's default user class. To try it out, just clone the repo, create a superuser with ./manage.py createsuperuser and log into the administration panel to view, edit and create users. 

This is not a plug-and-play implementation. Rather, it is something one can use for reference when creating their own custom user model.

Currently I have the custom user model set up so that it authenticates by email instead of username, however if you want to switch it back to authenticate via username, just change the USERNAME_FIELD variable in the AuthUser model to = 'username' and use souths schemamigration --auto command to update the database. 

You can also edit/change any of the additional user fields as you see fit. So in other words, don't edit any of these fields below, as they are required, but you can change any of the other fields such as user_bio, profile_image etc.

Required Fields:<br/>
   alphanumeric = RegexValidator(r'^[0-9a-zA-Z]*$', message='Only alphanumeric characters are allowed.')<br/>

  username = models.CharField(unique=True, max_length=20, validators=[alphanumeric]) <br/>
  email = models.EmailField(verbose_name='email address', unique=True, max_length=255) <br/>
  first_name = models.CharField(max_length=30, null=True, blank=True)<br/>
  last_name = models.CharField(max_length=50, null=True, blank=True) <br/>
  date_joined = models.DateTimeField(auto_now_add=True)<br/>
  is_active = models.BooleanField(default=True, null=False)<br/>
  is_staff = models.BooleanField(default=False, null=False)<br/>
