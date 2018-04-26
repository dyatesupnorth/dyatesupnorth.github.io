---
layout: post
title:  Easy Authentication and Password Resets in Laravel 5
date:   2018-04-10 09:49:23
categories: laravel
author: dave
---
Laravel makes it really easy to add authentication to your app. So easy in fact it pretty much ships out of the box. all you have to do is run `php artisan make:auth` from your project root and Laravel scaffolds out everything for you: Routes, Migrations, the lot.

After you've run the `make:auth` command, run `php artisan migrate` to get those database tables in there. Easy peasy.

With that done, head over to [Mailtrap](https://mailtrap.io/) and make an account. Delete the default inbox and create a new one, then click on the settings icon next to your inbox name and copy paste the inbox settings over to your `.env` file. Replace the `MAIL_USERNAME` and `MAIL_PASSWORD` settings and you're good to go, remember to make sure the `MAIL_HOST` is set to `smtp.mailtrap.io`.
