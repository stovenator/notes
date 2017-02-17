# Software Quality Assurance

As a background, pretty much all of my thinking was reset when I met David Black. Go ahead
and read the [ource](https://smile.amazon.com/Software-Quality-Assurance-Building-Better-ebook/dp/B009TAMNHA/ref=sr_1_1?ie=UTF8&qid=1487331667&sr=8-1&keywords=david+black+software+quality)

My slight addition to this is an even higher focus on live production testing, open source style:
* Real Users
* Real Environment

But -- heresy -- live production testing? Yes, but with a very specific notion of *controlled impact*.

## Impact
So, this is my really simple formula for the impact of any piece of software:

```
Scope * Scale * Duration = Impact
```

The impact can be positive or nagative, and measured by any metric you see fit. In business, we use the
holy trinity (Makes Money / Saves Money / Everything Else), but anything you can measure can work as
your impact.

Now to the component parts.

### Scope
Scope is the set of software features, anything from as small as a one line `css` change of color, to as
large as an entire enterprise application. The real requirement to have a scope -- be a scope -- is that
you can isolate it in order to measure it.

### Scale
Scale is the set of users you reach. Most of the time, this is going to be your biggest factor, and
is really the defining characteristic of *software*, which is everywhere and always about scale.

### Duration
Software, like all things, has a lifespan, and can only make an impact during that lifespan. Longer lived
software accumulate more of an impact.

## Quality
So then -- what is quality? Hah! It is the impact, that's it and all. Software quality is only
the extent to which a piece of software can be measured to the desired impact.

### Defects
So then -- by negation -- a sofware defect is any aspect of scope, scale, or duration that lowers
the measureable impact of the software.

If you cannot measure a negative impact, it is not a defect. The straightfoward and reliable method
of measurement being simply removing -- deleting -- the supposed defect, and measuring if the desired
impact goes up.

### Excess
This is likely a new concept when talking about sofware quality. Excess is the subset of the *Scope*
that has no measurable *Impact*. It is, in a nutshell, all the things that sounded good, or reasonable,
or expected, but that you cannot prove matter. Excess is the product of compromise and tradition.

Excess is as simple to detect as a defect. If you suspect a thing to be excess -- delete it -- and
measure your impact. If there is no change in the imact, you are the proud owner of excess!

Why do we care? Simply, the excess was not and is not "free" not matter that many developers, while
sitting at work being paid, will often declare a thing so. A thing with no provable imact, and a real cost,
is a real economic loss.

## Quality Assurance
So quality assurance is then simply minimizing the set of measurable negative impacts and maximizing the set
of measureable positive impacts. The word measurable twice in the last sentence probably doesn't make
the point firmly enough:
* **MEASURABLE**
* **MEASURABLE**
* **MEASURABLE**

So as a foil, quality is not the bug count. Quality is not the number of unit tests. Quality is not code coverage.
Quality is not adherence to requirements. Quality is not intuitive ease. Quality is not a set of test cases.

## Testing
So then -- what is testing? Simply the proedures you choose to assess a new *Scope* to measure positive or
negative impact. And here are the practices.

### Define Impact
Do not even pretend you are engaged in productive software development unless you have a clear
and measurable impact laid out before you begin. This measurable goal is the superior form of
the ancient approach of requirements.

### Limit Negative Impact
This is really as simple as it sounds. You don't need to be, are not, and will not be perfect. But what
you can do is limit the potential negative impact of defects. The ancient approach is test planning,
testing, or even test automation.

The modern approach is simple -- put it in production and measure *Impact*!

Which likely sounds shocking on a first read, until you adopt four practices.

### Limit Scope
Place items into production for measurement in the smallest amount possible, single features, or even
subsets of features are ideal. A single commit of a single line of code captures the zen.

Limiting scope limits the total amount of negative impact. 

### Limit Scale
Place items into production to a subset of users, ideally starting with 1, measuring impact, and then ramping up.

Even relatively mind boggling, negative impact defects of scope, when limited to a single user cannot cause great 
harm. If you are in a situation where you actually have only one user, this will not seem like a helpful practice. However
in this case, I would steer you toward another software project. Software is everywhere and always about scale, if you are
programming for a single user, you are engaged in macroeconomic waste of your programming talent that is in great demand elsewhere.

### Limit Duration
Place items into production with limited timeframes, very specifically with the ability to roll back and remove a change,
returning to the prior state, effectively erasing a defect by deleting it.

### Automate Deployment
The three other practices make for many releases, so unless you have an express goal of creating employment, automating
deployment is mandatory. There are many ways to automate, but the standard for truly automated is:
* One way to deploy, ideally `git push`
* One way to undeploy, ideally `git revert; git push`
* Continuous backup of your data and code, ideally point in time restore
