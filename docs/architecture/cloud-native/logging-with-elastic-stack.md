---
title: 使用彈性堆疊記錄
description: 使用彈性堆疊、Logstash 和 Kibana 進行記錄
ms.date: 09/23/2019
ms.openlocfilehash: b3fd3ea30f46914e6513be79f7d949499142b381
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182829"
---
# <a name="logging-with-elastic-stack"></a><span data-ttu-id="e32d2-103">使用彈性堆疊記錄</span><span class="sxs-lookup"><span data-stu-id="e32d2-103">Logging with Elastic Stack</span></span> 

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="e32d2-104">有許多良好的集中式記錄工具，其成本會因免費的開放原始碼工具而有所不同，以提供更昂貴的選項。</span><span class="sxs-lookup"><span data-stu-id="e32d2-104">There are many good centralized logging tools and they vary in cost from being free, open-source tools, to more expensive options.</span></span> <span data-ttu-id="e32d2-105">在許多情況下，免費的工具會比付費供應專案更好或更好。</span><span class="sxs-lookup"><span data-stu-id="e32d2-105">In many cases, the free tools are as good as or better than the paid offerings.</span></span> <span data-ttu-id="e32d2-106">其中一項工具是三個開放原始碼元件的組合：彈性搜尋、Logstash 和 Kibana。</span><span class="sxs-lookup"><span data-stu-id="e32d2-106">One such tool is a combination of three open-source components: Elastic search, Logstash, and Kibana.</span></span> <span data-ttu-id="e32d2-107">這些工具統稱為彈性堆疊或 ELK 堆疊。</span><span class="sxs-lookup"><span data-stu-id="e32d2-107">Collectively these tools are known as the Elastic Stack or ELK stack.</span></span>

## <a name="what-are-the-advantages-of-elastic-stack"></a><span data-ttu-id="e32d2-108">彈性堆疊有哪些優點？</span><span class="sxs-lookup"><span data-stu-id="e32d2-108">What are the advantages of Elastic Stack?</span></span>

<span data-ttu-id="e32d2-109">彈性堆疊以低成本、可擴充且可供雲端使用的方式來提供集中式記錄。</span><span class="sxs-lookup"><span data-stu-id="e32d2-109">Elastic Stack provides centralized logging in a low-cost, scalable, cloud-friendly manner.</span></span> <span data-ttu-id="e32d2-110">其使用者介面可簡化資料分析，讓您可以花時間從資料中搜集深入解析，而不是使用沒錯笨拙介面來對抗。</span><span class="sxs-lookup"><span data-stu-id="e32d2-110">Its user interface streamlines data analysis so you can spend your time gleaning insights from your data instead of fighting with a clunky interface.</span></span> <span data-ttu-id="e32d2-111">它支援各種不同的輸入，因此當您的分散式應用程式跨越更多類型的服務時，您可以預期會繼續將記錄和計量資料摘要到系統中。</span><span class="sxs-lookup"><span data-stu-id="e32d2-111">It supports a wide variety of inputs so as your distributed application spans more and different kinds of services, you can expect to continue to be able to feed log and metric data into the system.</span></span> <span data-ttu-id="e32d2-112">彈性堆疊也支援跨大型資料集的快速搜尋，因此甚至可以讓大型應用程式記錄詳細資料，而且仍然能夠以高效能的方式來查看它。</span><span class="sxs-lookup"><span data-stu-id="e32d2-112">The Elastic Stack also supports fast searches even across large data sets, making it possible to for even large applications to log detailed data and still be able to have visibility into it in a performant fashion.</span></span>

## <a name="logstash"></a><span data-ttu-id="e32d2-113">Logstash</span><span class="sxs-lookup"><span data-stu-id="e32d2-113">Logstash</span></span>

<span data-ttu-id="e32d2-114">第一個元件是[Logstash](https://www.elastic.co/products/logstash)。</span><span class="sxs-lookup"><span data-stu-id="e32d2-114">The first component is [Logstash](https://www.elastic.co/products/logstash).</span></span> <span data-ttu-id="e32d2-115">這項工具是用來從各種不同的來源收集記錄資訊。</span><span class="sxs-lookup"><span data-stu-id="e32d2-115">This tool is used to gather log information from a large variety of different sources.</span></span> <span data-ttu-id="e32d2-116">例如，Logstash 可以從磁片讀取記錄，也會接收來自記錄程式庫（例如[Serilog](https://serilog.net/)）的訊息。</span><span class="sxs-lookup"><span data-stu-id="e32d2-116">For instance, Logstash can read logs from disk and also receive messages from logging libraries like [Serilog](https://serilog.net/).</span></span> <span data-ttu-id="e32d2-117">Logstash 可以在記錄檔抵達時，對其進行一些基本的篩選和擴充。</span><span class="sxs-lookup"><span data-stu-id="e32d2-117">Logstash can do some basic filtering and expansion on the logs as they arrive.</span></span> <span data-ttu-id="e32d2-118">例如，如果您的記錄包含 IP 位址，則 Logstash 可能會設定為執行地理查閱，並取得該訊息的國家/地區或甚至是來源的城市。</span><span class="sxs-lookup"><span data-stu-id="e32d2-118">For instance, if your logs contain IP addresses then Logstash may be configured to do a geographical lookup and obtain a country or even city of origin for that message.</span></span> 

<span data-ttu-id="e32d2-119">Serilog 是 .NET 語言的記錄程式庫，可讓您進行參數化記錄。</span><span class="sxs-lookup"><span data-stu-id="e32d2-119">Serilog is a logging library for .NET languages, which allows for parameterized logging.</span></span> <span data-ttu-id="e32d2-120">不會產生內嵌欄位的文字記錄訊息，而是會個別保留參數。</span><span class="sxs-lookup"><span data-stu-id="e32d2-120">Instead of generating a textual log message that embeds fields, parameters are kept separate.</span></span> <span data-ttu-id="e32d2-121">這可讓您進行更聰明的篩選和搜尋。</span><span class="sxs-lookup"><span data-stu-id="e32d2-121">This allows for more intelligent filtering and searching.</span></span> <span data-ttu-id="e32d2-122">[圖 7-2] 顯示寫入 Logstash 的範例 Serilog 設定。</span><span class="sxs-lookup"><span data-stu-id="e32d2-122">A sample Serilog configuration for writing to Logstash appears in Figure 7-2.</span></span>

```csharp
var log = new LoggerConfiguration()   
         .WriteTo.Http("http://localhost:8080")
         .CreateLogger();
```

<span data-ttu-id="e32d2-123">**圖 7-2**Serilog config，用於透過 HTTP 將記錄資訊直接寫入 logstash</span><span class="sxs-lookup"><span data-stu-id="e32d2-123">**Figure 7-2** Serilog config for writing log information directly to logstash over HTTP</span></span>

<span data-ttu-id="e32d2-124">Logstash 會使用如圖7-3 所示的設定。</span><span class="sxs-lookup"><span data-stu-id="e32d2-124">Logstash would use a configuration like the one shown in Figure 7-3.</span></span> 

```
input {
    http {
        #default host 0.0.0.0:8080
        codec => json
    }
}

output {
    elasticsearch {
        hosts => "elasticsearch:9200"
        index=>"sales-%{+xxxx.ww}"
    }
}
```

<span data-ttu-id="e32d2-125">**圖 7-3** -從 Serilog 取用記錄的 Logstash 設定</span><span class="sxs-lookup"><span data-stu-id="e32d2-125">**Figure 7-3** - A Logstash configuration for consuming logs from Serilog</span></span>

<span data-ttu-id="e32d2-126">在不需要大量記錄操作的情況下，Logstash 稱為「[節拍](https://www.elastic.co/products/beats)」的替代方法。</span><span class="sxs-lookup"><span data-stu-id="e32d2-126">For scenarios where extensive log manipulation isn't needed there's an alternative to Logstash known as [Beats](https://www.elastic.co/products/beats).</span></span> <span data-ttu-id="e32d2-127">節拍是一系列的工具，可從記錄收集各種不同的資料到網路資料和執行時間資訊。</span><span class="sxs-lookup"><span data-stu-id="e32d2-127">Beats is a family of tools that can gather a wide variety of data from logs to network data and uptime information.</span></span> <span data-ttu-id="e32d2-128">許多應用程式都會使用 Logstash 和節拍。</span><span class="sxs-lookup"><span data-stu-id="e32d2-128">Many applications will use both Logstash and Beats.</span></span>

<span data-ttu-id="e32d2-129">Logstash 收集到記錄檔之後，就需要在某個位置放置它們。</span><span class="sxs-lookup"><span data-stu-id="e32d2-129">Once the logs have been gathered by Logstash, it needs somewhere to put them.</span></span> <span data-ttu-id="e32d2-130">雖然 Logstash 支援許多不同的輸出，但其中一個較令人興奮的是彈性搜尋。</span><span class="sxs-lookup"><span data-stu-id="e32d2-130">While Logstash supports many different outputs, one of the more exciting ones is Elastic search.</span></span>

## <a name="elastic-search"></a><span data-ttu-id="e32d2-131">彈性搜尋</span><span class="sxs-lookup"><span data-stu-id="e32d2-131">Elastic search</span></span>

<span data-ttu-id="e32d2-132">彈性搜尋是一種功能強大的搜尋引擎，可在記錄檔抵達時編制索引。</span><span class="sxs-lookup"><span data-stu-id="e32d2-132">Elastic search is a powerful search engine that can index logs as they arrive.</span></span> <span data-ttu-id="e32d2-133">它會對記錄檔快速執行查詢。</span><span class="sxs-lookup"><span data-stu-id="e32d2-133">It makes running queries against the logs quick.</span></span> <span data-ttu-id="e32d2-134">彈性搜尋可以處理大量的記錄檔，而且在極端的情況下，可以跨多個節點相應放大。</span><span class="sxs-lookup"><span data-stu-id="e32d2-134">Elastic search can handle huge quantities of logs and, in extreme cases, can be scaled out across many nodes.</span></span> 

<span data-ttu-id="e32d2-135">已製作成包含參數或已透過 Logstash 處理將參數從它們分割的記錄訊息，可以直接查詢，因為 Elasticsearch 會保留此資訊。</span><span class="sxs-lookup"><span data-stu-id="e32d2-135">Log messages that have been crafted to contain parameters or that have had parameters split from them through Logstash processing, can be queried directly as Elasticsearch preserves this information.</span></span>

<span data-ttu-id="e32d2-136">`jill@example.com`如圖7-4 所示，搜尋流覽過前10頁的查詢。</span><span class="sxs-lookup"><span data-stu-id="e32d2-136">A query that searches for the top 10 pages visited by `jill@example.com`, appears in Figure 7-4.</span></span>

```
"query": {
    "match": {
      "user": "jill@example.com"
    }
  },
  "aggregations": {
    "top_10_pages": {
      "terms": {
        "field": "page",
        "size": 10
      }
    }
  }
```

<span data-ttu-id="e32d2-137">**圖 7-4** -用來尋找使用者所造訪前10頁的 Elasticsearch 查詢</span><span class="sxs-lookup"><span data-stu-id="e32d2-137">**Figure 7-4** - An Elasticsearch query for finding top 10 pages visited by a user</span></span>

## <a name="visualizing-information-with-kibana-web-dashboards"></a><span data-ttu-id="e32d2-138">使用 Kibana web 儀表板將資訊視覺化</span><span class="sxs-lookup"><span data-stu-id="e32d2-138">Visualizing information with Kibana web dashboards</span></span>

<span data-ttu-id="e32d2-139">堆疊的最後一個元件是 Kibana。</span><span class="sxs-lookup"><span data-stu-id="e32d2-139">The final component of the stack is Kibana.</span></span> <span data-ttu-id="e32d2-140">這項工具是用來在 web 儀表板中提供互動式視覺效果。</span><span class="sxs-lookup"><span data-stu-id="e32d2-140">This tool is used to provide interactive visualizations in a web dashboard.</span></span> <span data-ttu-id="e32d2-141">即使是非技術的使用者，也可以製作儀表板。</span><span class="sxs-lookup"><span data-stu-id="e32d2-141">Dashboards may be crafted even by users who are non-technical.</span></span> <span data-ttu-id="e32d2-142">大部分位於 Elasticsearch 索引中的資料都可以包含在 Kibana 儀表板中。</span><span class="sxs-lookup"><span data-stu-id="e32d2-142">Most data that is resident in the Elasticsearch index, can be included in the Kibana dashboards.</span></span> <span data-ttu-id="e32d2-143">個別使用者可能會有不同的儀表板需求，而 Kibana 可透過允許使用者特定的儀表板來進行這項自訂。</span><span class="sxs-lookup"><span data-stu-id="e32d2-143">Individual users may have different dashboard desires and Kibana enables this customization through allowing user-specific dashboards.</span></span> 

## <a name="installing-elastic-stack-on-azure"></a><span data-ttu-id="e32d2-144">在 Azure 上安裝彈性堆疊</span><span class="sxs-lookup"><span data-stu-id="e32d2-144">Installing Elastic Stack on Azure</span></span>

<span data-ttu-id="e32d2-145">彈性堆疊可以透過數種方式安裝在 Azure 上。</span><span class="sxs-lookup"><span data-stu-id="e32d2-145">The Elastic stack can be installed on Azure in a number of ways.</span></span> <span data-ttu-id="e32d2-146">一如往常，您可以布建[虛擬機器，並直接在其上安裝彈性堆疊](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-elasticsearch)。</span><span class="sxs-lookup"><span data-stu-id="e32d2-146">As always, it's possible to [provision virtual machines and install Elastic Stack on them directly](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-elasticsearch).</span></span> <span data-ttu-id="e32d2-147">這是一些經驗豐富的使用者慣用的選項，因為它提供最高程度的自訂能力。</span><span class="sxs-lookup"><span data-stu-id="e32d2-147">This option is preferred by some experienced users as it offers the highest degree of customizability.</span></span> <span data-ttu-id="e32d2-148">在基礎結構即服務上部署時，會帶來顯著的管理額外負荷，以強制採用該路徑的人員取得與基礎結構即服務相關聯之所有工作的擁有權，例如保護機器安全，以及保持最新的修補程式。</span><span class="sxs-lookup"><span data-stu-id="e32d2-148">Deploying on infrastructure as a service introduces significant management overhead forcing those who take that path to take ownership of all the tasks associated with infrastructure as a service such as securing the machines and keeping up-to-date with patches.</span></span> 

<span data-ttu-id="e32d2-149">較少額外負荷的選項是使用已設定彈性堆疊的其中一個 Docker 容器。</span><span class="sxs-lookup"><span data-stu-id="e32d2-149">An option with less overhead is to make use of one of the many Docker containers on which the Elastic Stack has already been configured.</span></span> <span data-ttu-id="e32d2-150">這些容器可以放入現有的 Kubernetes 叢集中，並與應用程式程式碼一起執行。</span><span class="sxs-lookup"><span data-stu-id="e32d2-150">These containers can be dropped into an existing Kubernetes cluster and run alongside application code.</span></span> <span data-ttu-id="e32d2-151">[Sebp/elk](https://elk-docker.readthedocs.io/)容器是記載良好且經過測試的彈性堆疊容器。</span><span class="sxs-lookup"><span data-stu-id="e32d2-151">The [sebp/elk](https://elk-docker.readthedocs.io/) container is a well-documented and tested Elastic Stack container.</span></span>

<span data-ttu-id="e32d2-152">另一個選項是[最近宣佈的 ELK 即服務](https://devops.com/logz-io-unveils-azure-open-source-elk-monitoring-solution/)供應專案。</span><span class="sxs-lookup"><span data-stu-id="e32d2-152">Another option is a [recently announced ELK-as-a-service offering](https://devops.com/logz-io-unveils-azure-open-source-elk-monitoring-solution/).</span></span>

## <a name="references"></a><span data-ttu-id="e32d2-153">reference</span><span class="sxs-lookup"><span data-stu-id="e32d2-153">References</span></span>

- [<span data-ttu-id="e32d2-154">在 Azure 上安裝彈性堆疊</span><span class="sxs-lookup"><span data-stu-id="e32d2-154">Install Elastic Stack on Azure</span></span>](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-elasticsearch)

>[!div class="step-by-step"]
><span data-ttu-id="e32d2-155">[上一頁](observability-patterns.md)
>[下一頁](monitoring-azure-kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="e32d2-155">[Previous](observability-patterns.md)
[Next](monitoring-azure-kubernetes.md)</span></span>
