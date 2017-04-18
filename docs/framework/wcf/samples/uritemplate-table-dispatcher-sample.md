---
title: "UriTemplate 表發送器範例 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3b32975d-ba90-4c5c-83bc-2fbb48f11c0c
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# UriTemplate 表發送器範例
<xref:System.UriTemplateTable> 類別會提供可用來處理 <xref:System.UriTemplate> 執行個體集合的字典式關聯表結構。這個範例示範使用 `UriTemplateTable` 建置的基本分派引擎，這是 `UriTemplateTable` 類別的常用案例。  
  
 這個範例會示範 `UriTemplateTable` 類別的下列主要概念：  
  
-   在 `UriTemplateTable` 中將委派與 `UriTemplates` 加以關聯。  
  
-   使用 <xref:System.UriTemplateTable.MatchSingle%2A> 取得特定 URI 的正確處理常式委派。  
  
-   叫用處理常式委派以處理要求。  
  
### 若要安裝、建立及執行範例  
  
1.  若要建立方案的 C\# 或 Visual Basic .NET 版本，請遵循[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示進行。  
  
2.  若要在單一或跨機器的組態中執行本範例，請遵循[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)中的指示進行。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateDispatcher`  
  
## 請參閱  
 [UriTemplate 表](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)   
 [UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-sample.md)