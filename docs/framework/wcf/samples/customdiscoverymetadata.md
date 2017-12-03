---
title: CustomDiscoveryMetadata
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c42455fd-3652-4b7e-b698-ab3a2bb52e48
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4b4a68204d8ae5d2a338d60498522810a557e575
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="customdiscoverymetadata"></a>CustomDiscoveryMetadata
這個範例示範如何將自訂 XML 中繼資料插入服務公開之可探索端點的探索中繼資料。 接著在範例中會示範用戶端如何搜尋服務及擷取這項自訂資料。 這個範例包含二個專案，也就是服務和用戶端。  
  
## <a name="service"></a>服務  
 在 `main` 方法中，範例會示範填入 <xref:System.Xml.Linq.XElement> 型別的物件中必要的欄位，並且將該物件加入至 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>。 這個 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> 會加入至特殊端點。 探索特殊端點時，探索中繼資料會包含加入此處的自訂資料。  
  
## <a name="client"></a>用戶端  
 這個範例會示範在 <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> 上呼叫 <xref:System.ServiceModel.Discovery.DiscoveryClient> 方法。 接著會查詢產生的 <xref:System.ServiceModel.Discovery.FindResponse> 中適當的預期 XML 項目。 然後會將這些項目列印至主控台。  
  
#### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  在 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 中載入專案方案，然後建立專案。  
  
2.  首先執行 [方案基底目錄]\service\bin\debug 中產生的 Service 應用程式，然後執行 [方案基底目錄]\Client\bin\debug 中產生的 Client 應用程式。  
  
3.  請注意，服務會連線，用戶端則會尋找服務並且列印端點中發行的中繼資料。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DiscoveryExtensibility\CustomDiscoveryMetadata`  
  
## <a name="see-also"></a>另請參閱
