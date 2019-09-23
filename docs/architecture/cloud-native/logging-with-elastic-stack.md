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
# <a name="logging-with-elastic-stack"></a>使用彈性堆疊記錄 

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

有許多良好的集中式記錄工具，其成本會因免費的開放原始碼工具而有所不同，以提供更昂貴的選項。 在許多情況下，免費的工具會比付費供應專案更好或更好。 其中一項工具是三個開放原始碼元件的組合：彈性搜尋、Logstash 和 Kibana。 這些工具統稱為彈性堆疊或 ELK 堆疊。

## <a name="what-are-the-advantages-of-elastic-stack"></a>彈性堆疊有哪些優點？

彈性堆疊以低成本、可擴充且可供雲端使用的方式來提供集中式記錄。 其使用者介面可簡化資料分析，讓您可以花時間從資料中搜集深入解析，而不是使用沒錯笨拙介面來對抗。 它支援各種不同的輸入，因此當您的分散式應用程式跨越更多類型的服務時，您可以預期會繼續將記錄和計量資料摘要到系統中。 彈性堆疊也支援跨大型資料集的快速搜尋，因此甚至可以讓大型應用程式記錄詳細資料，而且仍然能夠以高效能的方式來查看它。

## <a name="logstash"></a>Logstash

第一個元件是[Logstash](https://www.elastic.co/products/logstash)。 這項工具是用來從各種不同的來源收集記錄資訊。 例如，Logstash 可以從磁片讀取記錄，也會接收來自記錄程式庫（例如[Serilog](https://serilog.net/)）的訊息。 Logstash 可以在記錄檔抵達時，對其進行一些基本的篩選和擴充。 例如，如果您的記錄包含 IP 位址，則 Logstash 可能會設定為執行地理查閱，並取得該訊息的國家/地區或甚至是來源的城市。 

Serilog 是 .NET 語言的記錄程式庫，可讓您進行參數化記錄。 不會產生內嵌欄位的文字記錄訊息，而是會個別保留參數。 這可讓您進行更聰明的篩選和搜尋。 [圖 7-2] 顯示寫入 Logstash 的範例 Serilog 設定。

```csharp
var log = new LoggerConfiguration()   
         .WriteTo.Http("http://localhost:8080")
         .CreateLogger();
```

**圖 7-2**Serilog config，用於透過 HTTP 將記錄資訊直接寫入 logstash

Logstash 會使用如圖7-3 所示的設定。 

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

**圖 7-3** -從 Serilog 取用記錄的 Logstash 設定

在不需要大量記錄操作的情況下，Logstash 稱為「[節拍](https://www.elastic.co/products/beats)」的替代方法。 節拍是一系列的工具，可從記錄收集各種不同的資料到網路資料和執行時間資訊。 許多應用程式都會使用 Logstash 和節拍。

Logstash 收集到記錄檔之後，就需要在某個位置放置它們。 雖然 Logstash 支援許多不同的輸出，但其中一個較令人興奮的是彈性搜尋。

## <a name="elastic-search"></a>彈性搜尋

彈性搜尋是一種功能強大的搜尋引擎，可在記錄檔抵達時編制索引。 它會對記錄檔快速執行查詢。 彈性搜尋可以處理大量的記錄檔，而且在極端的情況下，可以跨多個節點相應放大。 

已製作成包含參數或已透過 Logstash 處理將參數從它們分割的記錄訊息，可以直接查詢，因為 Elasticsearch 會保留此資訊。

`jill@example.com`如圖7-4 所示，搜尋流覽過前10頁的查詢。

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

**圖 7-4** -用來尋找使用者所造訪前10頁的 Elasticsearch 查詢

## <a name="visualizing-information-with-kibana-web-dashboards"></a>使用 Kibana web 儀表板將資訊視覺化

堆疊的最後一個元件是 Kibana。 這項工具是用來在 web 儀表板中提供互動式視覺效果。 即使是非技術的使用者，也可以製作儀表板。 大部分位於 Elasticsearch 索引中的資料都可以包含在 Kibana 儀表板中。 個別使用者可能會有不同的儀表板需求，而 Kibana 可透過允許使用者特定的儀表板來進行這項自訂。 

## <a name="installing-elastic-stack-on-azure"></a>在 Azure 上安裝彈性堆疊

彈性堆疊可以透過數種方式安裝在 Azure 上。 一如往常，您可以布建[虛擬機器，並直接在其上安裝彈性堆疊](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-elasticsearch)。 這是一些經驗豐富的使用者慣用的選項，因為它提供最高程度的自訂能力。 在基礎結構即服務上部署時，會帶來顯著的管理額外負荷，以強制採用該路徑的人員取得與基礎結構即服務相關聯之所有工作的擁有權，例如保護機器安全，以及保持最新的修補程式。 

較少額外負荷的選項是使用已設定彈性堆疊的其中一個 Docker 容器。 這些容器可以放入現有的 Kubernetes 叢集中，並與應用程式程式碼一起執行。 [Sebp/elk](https://elk-docker.readthedocs.io/)容器是記載良好且經過測試的彈性堆疊容器。

另一個選項是[最近宣佈的 ELK 即服務](https://devops.com/logz-io-unveils-azure-open-source-elk-monitoring-solution/)供應專案。

## <a name="references"></a>reference

- [在 Azure 上安裝彈性堆疊](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-elasticsearch)

>[!div class="step-by-step"]
>[上一頁](observability-patterns.md)
>[下一頁](monitoring-azure-kubernetes.md)
