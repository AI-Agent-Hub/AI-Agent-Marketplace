# Introduction to APIs of AI Agent Marketplace | AI Agent Directory | AI Agent Index


## Registration

If you want to list your AI agent in the public available AI Agent Marketplace | AI Agent Directory | AI Agent Index, 
you can register on [http://www.deepnlp.org/workspace/my_ai_services](http://www.deepnlp.org/workspace/my_ai_services) and generate
your ${ACCESS_KEY} for free. After you get your ${API_KEY}, you can start list your AI agent in the public marketplace and start get more users' traffic and visibility to the community.


### 1.0 API to Add New AI Agent Service

You can call the API to register the meta information of your AI Agents. Alternatively, you can also use the web page (http://www.deepnlp.org/workspace/my_ai_services) to list your 
AI Agent.

```

import ai_agent_marketplace as aa
import json

def publish_your_agent():
    """
        access_key can be obtained from your personal page:
        www.deepnlp.orgworkspace/my_ai_services
        once you submit, it's pending approval and you can track the data then
        get your access_key from http://www.deepnlp.org/workspace/my_ai_services
    """
    access_key = "${your_access_key}"
    name = "My First AI Agent"

    item_info = {}
    item_info["content"] = "This AI Agent can do complicated programming work for humans"
    item_info["website"] = "https://www.my_first_agent.com"
    item_info["field"] = "AI AGENT"
    item_info["subfield"] = "Coding Agent"
    item_info["content_tag_list"] = "coding,python"
    result = aa.add(access_key=access_key, name="My First Agent", item_info=item_info)
    url = result["url"] if "url" in result else ""
    msg = result["msg"] if "msg" in result else ""
    print ("## DEBUG: AI Agent Marketplace Post msg is|%s" % str(msg))
    print ("## DEBUG: AI Agent Marketplace Post url is|%s" % str(url))


publish_your_agent()

```

#### Field Description

|  Field  | DataType | Required | Description  |
|  -------- | --------  | --------  | --------  |
|  **user_id** | string | required | Your registered user id at http://www.deepnlp.org/store/ai-agent |
|  **api_key** | string | required |  The API Key generated AI Services tab at http://www.deepnlp.org/workspace/my_ai_services |
|  **name** | string | required | The name of your AI Agent, such as 'My First Agent' |
|  **content** | string | required | The description of your AI Agent functionality, features, etc. |
|  **website** | string | optional | The website URL of your AI Agent if users want to explore |
|  **field** | string/enum | optional | Category field. You can choose 'AI AGENT' as main category or field |
|  **subfield** | string/enum | optional | Sub-Category field. You can choose 'AI Search Agent', 'Law Agent', etc as secondary category or subfield|
|  **content_tag_list** | string | optional | tags describing your AI Agent, separated by comma |
|  **github** | string | optional | Github Address |
|  **price** | string | optional | price of your AI Agent, such as free, $100/1m tokens, etc |
|  **api** | string | optional | API Endpoint Address of your AI Agent |
|  **thumbnail_picture** | string | optional | The static file URL of your AI Agent for listing, only one static file accepted |
|  **upload_image_files** | string | optional | The URL lists of static files of multiple images or screenshots of your AI Agents for the detail page |

#### Submission and Approval 

One your submit your AI Agent, you can visit the detail address of your agent. It will be pending mode.
And once it's approved by administrators, it will go public and indexed by the AI Agent Directory and all major search engine, such as Google/Bing.
You can also track the SEO/daily traffic performance of your registered AI agent.

![AI Agent Index for tracking Daily Search Metric](https://raw.githubusercontent.com/AI-Agent-Hub/AI-Agent-Marketplace/refs/heads/main/docs/ai_search_ranking_chart.jpg)


### 2.0 API to Track and Compare AI Agent's Web Traffic Data of your Industry


You can call the search API to track and compare AI Agents' web traffic data, such as Google/Bing Search Result, Github Stars, etc.
You can visit the search API from the url also. (http://www.deepnlp.org/api/ai_agent_marketplace/v1?q=coding%20agent)


```

import ai_agent_marketplace as aa
import json

def search_ai_agent_traffic_data():

    result = aa.search(q="Coding Agent Jetbrains")
    print ("## DEBUG: search result is|%s" % str(result))

    result2 = aa.search(q="Coding Agent", limit=20, timeout=5)
    print ("## DEBUG: search result is|%s" % str(result2))

    result3 = aa.search(q="", limit=20, timeout=5)
    print ("## DEBUG: Mock search result is|%s" % str(result3))


search_ai_agent_traffic_data()

```


#### Field Description

|  Field  | DataType | Required | Description  |
|  -------- | --------  | --------  | --------  |
|  **q** | string | required | your search query |
|  **limit** | string | optional | Limit of total items returned, maximum to 100 |
|  **timeout** | int | optional | Timeout for the requests |




