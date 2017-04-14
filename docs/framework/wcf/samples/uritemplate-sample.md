---
title: "UriTemplate 範例 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0aaf91d0-ce18-468d-8006-bc9bc2e48231
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# UriTemplate 範例
<xref:System.UriTemplate> 類別提供可使用一組共用通用結構之 URI 的方法。本範例會示範下列與 `UriTemplate` 有關的主要概念：  
  
-   建立範本的語法。  
  
-   從使用 <xref:System.UriTemplate.BindByName%2A> 和 <xref:System.UriTemplate.BindByPosition%2A> 的 `UriTemplate` 產生 URI。  
  
-   <xref:System.UriTemplateTable.Match%2A> 是 `BindByName` 和 `BindByPosition` 的反向作業。  
  
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
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplate`  
  
## 請參閱  
 [UriTemplate 表](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)   
 [UriTemplate 表發送器](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)