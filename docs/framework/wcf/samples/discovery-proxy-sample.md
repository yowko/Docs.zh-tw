---
title: "探索 Proxy 範例 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1dfa02df-15b1-4e97-9c8e-f5f2772711b0
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# 探索 Proxy 範例
此範例示範如何建立探索 Proxy 的實作以儲存現有服務的相關資訊，以及用戶端如何查詢該 Proxy 的資訊。此範例包含三個專案：  
  
-   **服務**：簡易的 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 計算機服務，可向探索 Proxy 登錄其本身。  
  
-   **探索 Proxy**：探索 Proxy 服務的實作。  
  
-   **用戶端**：呼叫探索 Proxy 搜尋服務的 WCF 用戶端應用程式。  
  
## 示範  
 探索 Proxy 實作  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryProxy`  
  
## DiscoveryProxy  
 在 Program.cs 檔案的 `Main` 方法中，此範例會示範如何裝載 <xref:System.ServiceModel.Discovery.DiscoveryProxy> 類型的服務。它會公開兩個端點，其中一個屬於 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> 類型，而另一個屬於 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> 類型。兩個端點都使用 TCP 做為傳輸。<xref:System.ServiceModel.Discovery.DiscoveryEndpoint> 會接聽 `probeEndpointAddress` 參數所指定的 URI，這是用戶端可以傳送探查訊息以查詢 Proxy 中之資料的位置。<xref:System.ServiceModel.Discovery.AnnouncementEndpoint> 會接聽 `announcementEndpointAddress` 參數所指定的 URI。這是 Proxy 為公告所接聽的位置。收到線上公告時，Proxy 會將服務加入至其快取，而收到離線公告時，則會從其快取移除服務。  
  
 DiscoveryProxy.cs 包含 <xref:System.ServiceModel.Discovery.DiscoveryProxy> 的實作。Proxy 必須繼承自 <xref:System.ServiceModel.Discovery.DiscoveryProxyBase> 類別，而且需要 <xref:System.Runtime.Remoting.Messaging.AsyncResult> 的實作。在具現化時，Proxy 會建立新的 <xref:Systems.Collections.Generic.Dictionary%601>，用來儲存它所知道的項目。  
  
 此檔案分成兩個區域，分別是「Proxy 快取方法」和「探索 Proxy 實作」。「Proxy 快取方法」區域包含用來更新 <xref:Systems.Collections.Generic.Dictionary%601>、針對 <xref:Systems.Collections.Generic.Dictionary%601> 執行查詢，以及為使用者列印資料的方法。「探索 Proxy 實作」區域包含「公告」和「探查」功能所需的覆寫方法。這些方法會定義 Proxy 收到線上公告、離線公告或探查訊息後所採取的動作。  
  
## 服務  
 在服務專案的 Program.cs 檔案中，相同的 URI 用於其公告端點，做為探索 Proxy。這是因為服務使用端點傳送公告，而 Proxy 使用端點接收公告。服務會使用 <xref:System.ServiceModel.Discovery.DiscoveryBehavior>，並在其中加入公告端點。  
  
## 用戶端  
 用戶端專案會針對其探查端點使用相同的 URI 做為 Proxy。這是因為此案例中的探查也正在明確地單點傳送到 Proxy 上可用的端點。用戶端會連接至這個已知的位址，然後針對服務進行查詢。一旦找到服務，就會連接至該服務。  
  
#### 若要使用這個範例  
  
1.  載入 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 中的專案方案，然後建立專案。  
  
2.  請先執行探索 Proxy 應用程式，這通常位於 \[方案基底目錄\]\\DiscoveryProxy\\bin\\debug。探索 Proxy 必須先執行，因為 TCP 公告端點必須為服務啟動，才能傳送其公告。  
  
3.  接著，執行服務應用程式，這通常位於 \[方案基底目錄\]\\Service\\bin\\debug。啟動時，服務會將公告傳送至探索 Proxy 的公告端點，並在 Proxy 的快取中登錄。  
  
4.  再來，執行用戶端應用程式，這通常位於 \[方案基底目錄\]\\Client\\bin\\debug。用戶端會查詢 Proxy、取得服務位址，然後連接至該服務。  
  
5.  最後，終止用戶端、服務，以及 Proxy。Proxy 必須一直執行，才能接收服務的離線公告。  
  
## 請參閱