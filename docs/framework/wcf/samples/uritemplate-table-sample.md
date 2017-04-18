---
title: "UriTemplate 表範例 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5dd1d38f-1989-4c64-820d-821f5a02216a
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# UriTemplate 表範例
<xref:System.UriTemplateTable> 類別會提供可用來處理 `UriTemplate` 執行個體集合的字典式關聯表結構。這樣便可有效地針對表中的所有樣板比對特定的統一資源識別元 \(URI\)，並且擷取與符合樣板相關聯的資料。  
  
 這個範例會示範與 `UriTemplateTable` 類別有關的下列主要概念：  
  
-   具現化 `UriTemplateTable` 時的語法。  
  
-   將索引鍵\/值組集合填入 `UriTemplateTable`。  
  
-   使用 <xref:System.UriTemplateTable.MatchSingle%2A>，比對候選 URI 和此表。  
  
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
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateTable`  
  
## 請參閱  
 [UriTemplate 表發送器](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)   
 [UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-sample.md)