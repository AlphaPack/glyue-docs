# 6. Wrapping Up

#### Final tests

Re-run the integration with this input (use a real email address whose inbox can be accessed):

```
{
  "email": "example@example.com",
  "limitQuery": 100,
  "limitEmail": 10
}
```

The integration should take several seconds or up to a minute (it is calling the story API 100 times after all). After it completes, check the email inbox and see if it arrived (it may have gone to spam)!

Hopefully the email was received and looks a little like this:

```
I queried the latest 100 articles from Hacker news.
Here are the top 10:

Boston mayor announces residential conversion program for office buildings
https://www.bostonplans.org/news-calendar/news-updates/2023/07/10/mayor-wu-announces-residential-conversion-program
Posted by [toss1] on 07/13/2023, 20:27 (131 points, 100 comments)
Discussion: https://news.ycombinator.com/item?id=36715504

Actors say Hollywood studios want their AI replicas – for free, forever
https://www.theverge.com/2023/7/13/23794224/sag-aftra-actors-strike-ai-image-rights
Posted by [mfiguiere] on 07/13/2023, 20:41 (66 points, 94 comments)
Discussion: https://news.ycombinator.com/item?id=36715686

...
```

:tada: :tada: :tada: Huzzah! The integration is now complete and functional. :tada: :tada: :tada:

{% hint style="info" %}
Try re-running the integration from the **Run History** page with various different inputs. Play around a little bit and have fun!
{% endhint %}

This concludes the tutorial. We hope that the concepts learned in this article will lay the foundation for the reader’s Glyue integration building journey.

{% content-ref url="extra-credit/" %}
[extra-credit](extra-credit/)
{% endcontent-ref %}
