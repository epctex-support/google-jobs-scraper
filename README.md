[https://apify.com/epctex/google-jobs-scraper?fpr=yhdrb](https://apify.com/epctex/google-jobs-scraper?fpr=yhdrb)

# Actor - Google Jobs Scraper

## Google Jobs scraper

The Google Jobs data scraper supports the following features:

-   Search any keyword and job title - Seach any keyword or job title on Google Jobs. Retrieve extensive set of results in seconds.

-   Target your job results - Enable filtering, sorting or targeting your results by country, language. Even pin point location and draw a radius.

-   Extremely detailed and enriched output, better visibility - Very detailed output with all the sections included. Salary, qualifications, social links, apply links and many more!

-   Highly configurable, easy to use - Flexible configuration enables you to easily use the actor without hassle, and focus only on your needs.

-   Optional CSV Friendly Output - Use the actor for data retrieval or API purposes. Optional CSV-Friendly field enables you to get all the results in one item or multiple items. Easy integration.

- Daily maintenance, fast support - We offer daily maintenance and a blazing fast customer support. Your satisfaction is the number one priority.

## Bugs, fixes, updates, and changelog

This scraper is under active development. If you have any feature requests you can create an issue from [here](https://github.com/epctex/google-jobs-scraper/issues).


## Input Parameters

The input of this scraper should be JSON containing the list of pages on Google Jobs that should be visited. Required fields are:

- `startUrls`: (Optional) (Array) List of Google Jobs URLs. URLs to start with. It should be Job Listing URL.

- `maxItems`: (Optional) (Number) You can limit scraped items. This should be useful when you search through the big lists or search results.

- `endPage`: (Optional) (Number) Final number of page that you want to scrape. The default is `Infinite`. This applies to all `search` requests and `startUrls` individually.

- `queries`: (Optional) (Array) The keywords/queries you want to search on Google Jobs. This field is required whenever `startUrls` is not present.

- `countryCode`: (Optional) (String) Country determines the Google Jobs search domain (e.g. google.es for Spain). This setting only applies to Search queries.

- `languageCode`: (Optional) (String)  This code specifies the precise location for Google Jobs searches. It's used as the 'uule' query parameter in Google Jobs Search URLs. Generate the UULE code using this generator: [https://padavvan.github.io/](https://padavvan.github.io/).

- `radius`: (Optional) (Number) Enables job searching within a specified radius, in kilometers.

- `filterParam`: (Optional) (String) Filter job results using the format 'categories.param:categories.options.value'. Example: 'date_posted:today,employment_type:FULLTIME' for specific filters.

- `includeUnfilteredResults`: (Optional) (Boolean) If checked, the lower-quality results that Google normally filters out will be included. This usually consists of a few hundred extra results.

- `csvFriendlyOutput`: (Optional) (Boolean) If checked, the crawler will return results in a structure suitable for CSV format. Only 'googleJobs' results are included. CSV headers would be: title, companyName, location, description, and more.

- `proxy`: (Required) (Proxy Object) Proxy configuration.

- `extendOutputFunction`: (Optional) (String) Function that takes a JQuery handle ($) as an argument and returns an object with data.

- `customMapFunction`: (Optional) (String) Function that takes each object's handle as an argument and returns the object with executing the function.

This solution requires the use of **Proxy servers**, either your own proxy servers or you can use [Apify Proxy](https://www.apify.com/docs/proxy).

### Tip

When you want to scrape over a specific list URL, just copy and paste the link as one of the **startUrl**.

If you would like to scrape only the first page of a list then put the link for the page and have the `endPage` as 1.

With the last approach that is explained above you can also fetch any interval of pages. If you provide the 5th page of a list and define the `endPage` parameter as 6 then you'll have the 5th and 6th pages only.

### Compute Unit Consumption

The actor is optimized to run blazing fast and scrape as many items as possible. Therefore, it forefronts all the detailed requests. If the actor doesn't block very often it'll scrape 100 jobs in 2.5 minutes with ~0.1-0.15 compute units.

### Google Jobs Scraper Input example

```json
{
    "startUrls": [
        "https://www.google.com/search?sca_esv=593729410&q=Software+Engineer+jobs&uds=AMIYvT8-5jbJIP1-CbwNj1OVjAm_ezkS5e9c6xL1Cc4ifVo4bFIMuuQemtnb3giV7cKava9luZMDXVTS5p4powtoyb0ACtDGDu9unNkXZkFxC0i7ZSwrZd_aHgim6pFgOWgs0dte0pnb&sa=X&ictx=0&biw=1621&bih=648&dpr=2&ibp=htl;jobs&ved=2ahUKEwjt-4-Y6KyDAxUog4kEHSJ8DjQQudcGKAF6BAgRECo"
    ],
    "queries": [
        "teacher"
    ],
    "countryCode": "us",
    "languageCode": "en",
    "locationUule": "w+CAIQICIIaXN0YW5idWw=",
    "radius": 300,
    "includeUnfilteredResults": false,
    "csvFriendlyOutput": true,
    "proxy": {
        "useApifyProxy": true
    },
    "endPage": 5,
    "maxItems": 100
}
```

## During the Run

During the run, the actor will output messages letting you know what is going on. Each message always contains a short label specifying which page from the provided list is currently specified.
When items are loaded from the page, you should see a message about this event with a loaded item count and total item count for each page.

If you provide incorrect input to the actor, it will immediately stop with a failure state and output an explanation of what is wrong.

## Google Jobs Export

During the run, the actor stores results into a dataset. Each item is a separate item in the dataset.

You can manage the results in any language (Python, PHP, Node JS/NPM). See the FAQ or <a href="https://www.apify.com/docs/api" target="blank">our API reference</a> to learn more about getting results from this Google Jobs actor.

## Google Jobs Output

### CSV Friendly

```json
{
	"title": "Software Developer",
	"companyName": "New York University",
	"location": "New York, NY",
	"via": "via ICIMS - NYU Jobs",
	"description": "Position Summary\n\nDevelop applications using current technologies to support business processes in an agile (scrum) development environment. Troubleshoot and debug existing applications. Participate in the design, development, testing, and deployment of upgrades and enhancements for the capital project management application. Prepare technical specifications; design, develop and test technical... solutions; and provide technical expertise upon request. Write documentation and online help systems for newly developed applications. Develop and implement innovative ways to improve quality and functionality of applications and share suggestions and knowledge capital with application owners and team members. Participate in peer code review processes. Mentor and develop student employees.\n\nQualifications\n\nRequired Education:Bachelor's Degree or equivalent in Computer Science or Computer Systems Engineering or equivalent combination of education and experience.Required Experience:3+ years of full-time related experience. Demonstrated programming experience in a scrum environment. 3+ years of full-time related experience in developing and maintaining complex enterprise applications in a construction management application with Oracle Unifier, Oracle Primavera, Kahua, eBuilder or ProCore.Required Skills, Knowledge and Abilities:C#, Javascript, Typescript, CSS, HTML, React.JS,, SQL,, and full stack .NET experience. Strong technical knowledge, written and verbal communication and good interpersonal skills. Strong analytical ability.Preferred Skills, Knowledge and Abilities:Experience with Oracle uDesigner, Kahua kBuilder, or similar. Experience building api integrations using an integration platform such as MuleSoft or similar. Knowledge of Database architecture and data manipulation techniques. Experience with developing microservice applications. Experience with big data analytics. Experience with Jelly.\n\nAdditional Information\n\nIn compliance with NYC's Pay Transparency Act, the annual base salary range for this position is USD $85,500.00 to USD $104,500.00. New York University considers factors such as (but not limited to) scope and responsibilities of the position, candidate's work experience, education/training, key skills, internal peer equity, as well as, market and organizational considerations when extending an offer. This pay range represents base pay only and excludes any additional items such as incentives, bonuses, clinical compensation, or other items. NYU aims to be among the greenest urban campuses in the country and carbon neutral by 2040. Learn more at nyu.edu/nyugreen.EOE/AA/Minorities/Females/Vet/Disabled/Sexual Orientation/Gender Identity",
	"jobHighlights": [
		{
			"title": "Qualifications",
			"items": [
				"Required Education:Bachelor's Degree or equivalent in Computer Science or Computer Systems Engineering or equivalent combination of education and experience",
				"Required Experience:3+ years of full-time related experience",
				"Demonstrated programming experience in a scrum environment",
				"3+ years of full-time related experience in developing and maintaining complex enterprise applications in a construction management application with Oracle Unifier, Oracle Primavera, Kahua, eBuilder or ProCore",
				"Required Skills, Knowledge and Abilities:C#, Javascript, Typescript, CSS, HTML, React.JS,, SQL,, and full stack .NET experience",
				"Strong technical knowledge, written and verbal communication and good interpersonal skills"
			]
		},
		{
			"title": "Responsibilities",
			"items": [
				"Develop applications using current technologies to support business processes in an agile (scrum) development environment",
				"Troubleshoot and debug existing applications",
				"Participate in the design, development, testing, and deployment of upgrades and enhancements for the capital project management application",
				"Prepare technical specifications; design, develop and test technical solutions; and provide technical expertise upon request",
				"Write documentation and online help systems for newly developed applications",
				"Develop and implement innovative ways to improve quality and functionality of applications and share suggestions and knowledge capital with application owners and team members"
			]
		},
		{
			"title": "Qualifications",
			"items": [
				"Required Education:Bachelor's Degree or equivalent in Computer Science or Computer Systems Engineering or equivalent combination of education and experience",
				"Required Experience:3+ years of full-time related experience",
				"Demonstrated programming experience in a scrum environment",
				"3+ years of full-time related experience in developing and maintaining complex enterprise applications in a construction management application with Oracle Unifier, Oracle Primavera, Kahua, eBuilder or ProCore",
				"Required Skills, Knowledge and Abilities:C#, Javascript, Typescript, CSS, HTML, React.JS,, SQL,, and full stack .NET experience",
				"Strong technical knowledge, written and verbal communication and good interpersonal skills",
				"Strong analytical ability",
				"Experience building api integrations using an integration platform such as MuleSoft or similar",
				"Knowledge of Database architecture and data manipulation techniques",
				"Experience with developing microservice applications",
				"Experience with big data analytics"
			]
		},
		{
			"title": "Responsibilities",
			"items": [
				"Develop applications using current technologies to support business processes in an agile (scrum) development environment",
				"Troubleshoot and debug existing applications",
				"Participate in the design, development, testing, and deployment of upgrades and enhancements for the capital project management application",
				"Prepare technical specifications; design, develop and test technical solutions; and provide technical expertise upon request",
				"Write documentation and online help systems for newly developed applications",
				"Develop and implement innovative ways to improve quality and functionality of applications and share suggestions and knowledge capital with application owners and team members",
				"Participate in peer code review processes",
				"Mentor and develop student employees"
			]
		}
	],
	"applyLink": [
		{
			"title": "icims.com",
			"link": "https://uscareers-nyu.icims.com/jobs/12183/software-developer/job"
		},
		{
			"title": "higheredjobs.com",
			"link": "https://www.higheredjobs.com/admin/details.cfm?JobCode=178439960"
		},
		{
			"title": "hercjobs.org",
			"link": "https://main.hercjobs.org/jobs/19449282/software-developer"
		},
		{
			"title": "mendeley.com",
			"link": "https://www.mendeley.com/careers/job/software-developer-25672393"
		},
		{
			"title": "simplyhired.com",
			"link": "https://www.simplyhired.com/job/wE0SSrM3o-ZJ4mqRmgyl5sYYOAcN8FIF79yQHjQcpaVHKHgDamVrYg"
		},
		{
			"title": "magazine.org",
			"link": "https://jobs.magazine.org/jobs/rss/19449282/software-developer"
		},
		{
			"title": "getwork.com",
			"link": "https://getwork.com/details/a175ebab149668617a0480a36cc7e03b"
		},
		{
			"title": "adzuna.com",
			"link": "https://www.adzuna.com/details/4170656790"
		}
	],
	"relatedLinks": [],
	"extras": [
		"7 days ago",
		"Full-time",
		"Health insurance"
	],
	"metadata": {
		"postedAt": "7 days ago",
		"scheduleType": "Full-time"
	}
}
```

### Non-CSV Friendly

```json
{
	"searchQuery": {
		"term": "Software Engineer jobs",
		"page": 1,
		"type": "SEARCH",
		"domain": "https://www.google.com",
		"countryCode": "US",
		"locationUule": null,
		"resultsPerPage": 10
	},
	"url": "https://www.google.com/search?sca_esv=593729410&q=Software+Engineer+jobs&uds=AMIYvT8-5jbJIP1-CbwNj1OVjAm_ezkS5e9c6xL1Cc4ifVo4bFIMuuQemtnb3giV7cKava9luZMDXVTS5p4powtoyb0ACtDGDu9unNkXZkFxC0i7ZSwrZd_aHgim6pFgOWgs0dte0pnb&sa=X&ictx=0&biw=1621&bih=648&dpr=2&ibp=htl%3Bjobs&ved=2ahUKEwjt-4-Y6KyDAxUog4kEHSJ8DjQQudcGKAF6BAgRECo&lrad=null&chips=null&start=0",
	"googleJobs": [...],
	"categories": [
		{
			"type": "Company type",
			"param": "industry.id",
			"options": [
				{
					"text": "All",
					"value": null
				},
				{
					"text": "Information",
					"value": "/business/naics2007/51"
				}
			]
		},
	]
}
```


## Contact
Please visit us through [epctex.com](https://epctex.com) to see all the products that are available for you. If you are looking for any custom integration or so, please reach out to us through the chat box in [epctex.com](https://epctex.com). In need of support? [devops@epctex.com](mailto:devops@epctex.com) is at your service.
