# ReposadoAutopromote

## What is Reposado?
[Reposado](https://github.com/wdas/reposado) allows you to download and serve out Apple updates but also to segment the updates out into branches. This allows you to still serve deprecated updates to your clients. It also means you can test updates in one testing branch before moving the update to a production branch.

## Why would I want to use ReposadoAutopromote with Reposado?
Reposado includes **repo_sync** to get new updates from Apple's servers and also **repoutil**, which allows you to manipulate your branches. My general assumption is that almost all of Apple updates will be fine and not break people's working systems, so it's helpful to be able to automate moving updates from testing to production after a certain period of time.

By default, ReposadoAutopromote has a grace period of 4 days for you to test updates. That should be plenty of time, but you can easily adjust the threshold period to be longer (5 days, a week, 10 days) to suit the needs of your organization. That will give you time to remove any troublesome updates from even the testing branch so those updates won't autopromote to production.

## How do I install ReposadoAutopromote?
It's really just one Python file. If you want, you can put it in **/usr/local/reposado** alongside **repo_sync** and **repoutil**.

## How do I use ReposadoAutopromote?
After you've downloaded **repopromote**, edit the following variables to match your environment:
```
# Name of testing branch
testing_name='testing'

# Name of production branch
production_name='production'

# Threshold of days between moving testing to production
days_between_promotion=4
```

So if your production name is actually **release**, you would change the production branch line accordingly:
```
# Name of production branch
production_name='release'
```
Then, make **repopromote** executable...
```
sudo chmod +x /usr/local/reposado/repopromote
```
... and you should be able to go ahead and use it
```
/usr/local/reposado/repopromote
```

## How can I schedule Reposado?
It really will depend on what operating system you use Reposado on. Linux has cron jobs, and Mac OS X has launchd.
