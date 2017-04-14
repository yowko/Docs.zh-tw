---
title: "摘要格式器 (JSON) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f9c0b295-55e7-48ea-b308-ba51c7d31143
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# 摘要格式器 (JSON)
這個範例會示範如何使用自訂 <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> 和 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>，序列化採用 JavaScript 物件標記法 \(JSON\) 格式的 <xref:System.ServiceModel.Syndication.SyndicationFeed> 類別執行個體。  
  
## 範例架構  
 此範例會實作繼承自 <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> 且名為 `JsonFeedFormatter` 的類別。  `JsonFeedFormatter` 類別會倚賴 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 來讀取和寫入採用 JSON 格式的資料。  對內部而言，此格式器會使用名為 `JsonSyndicationFeed` 和 `JsonSyndicationItem` 的自訂資料合約類型集合，控制序列化程序所產生的 JSON 格式資料。  這些實作細節已隱藏起來不讓使用者看到，而是允許針對標準 <xref:System.ServiceModel.Syndication.SyndicationFeed> 和 <xref:System.ServiceModel.Syndication.SyndicationItem> 類別進行呼叫。  
  
## 寫入 JSON 摘要  
 搭配 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 使用 `JsonFeedFormatter` \(已實作於這個範例\) 即可寫入 JSON 摘要，如下列範例程式碼所示。  
  
```  
//Basic feed with sample data  
SyndicationFeed feed = new SyndicationFeed("Custom JSON feed", "A Syndication extensibility sample", null);  
feed.LastUpdatedTime = DateTime.Now;  
feed.Items = from s in new string[] { "hello", "world" }  
select new SyndicationItem()  
{  
    Summary = SyndicationContent.CreatePlaintextContent(s)  
};  
  
//Write the feed out to a MemoryStream in JSON format  
DataContractJsonSerializer writeSerializer = new DataContractJsonSerializer(typeof(JsonFeedFormatter));  
writeSerializer.WriteObject(stream, new JsonFeedFormatter(feed));  
  
```  
  
## 讀取 JSON 摘要  
 使用 `JsonFeedFormatter`，即可從 JSON 格式化的資料流中取得 <xref:System.ServiceModel.Syndication.SyndicationFeed>，如下列程式碼所示。  
  
 `//Read in the feed using the DataContractJsonSerializer`  
  
 `DataContractJsonSerializer readSerializer = new DataContractJsonSerializer(typeof(JsonFeedFormatter));`  
  
 `JsonFeedFormatter formatter = readSerializer.ReadObject(stream) as JsonFeedFormatter;`  
  
 `SyndicationFeed feedRead = formatter.Feed;`  
  
#### 若要安裝、建置及執行範例  
  
1.  請確定您已執行 [Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  若要建置方案的 C\# 或 Visual Basic .NET 版本，請遵循[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3.  若要在單一或跨機器的組態中執行本範例，請遵循[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)中的指示進行。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。  請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[適用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。  此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\JsonFeeds`  
  
## 請參閱