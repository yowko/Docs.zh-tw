---
title: "&lt;wsdlImporters&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 270c7f93-eab7-47b6-8b94-ac3f5b7f17e4
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# &lt;wsdlImporters&gt;
此組態項目會指定所有 WSDL 匯入工具，以匯入具有 WS\-Policy 附件的 Web 服務描述語言 \(WSDL\) 1.1 中繼資料。  每個子項目都是 \<`wsdlImporter`\>，可指定匯入中繼資料的方式，並且將該資訊轉換成表示合約和端點資訊的各種類別。  它可以選擇性地匯入合約和端點資訊，以及可公開 \(Expose\) 任何匯入錯誤並接受與匯入和轉換處理有關聯之型別資訊的屬性。  此外，它也支援匯入繫結資訊，以及可提供存取任何原則文件、WSDL 文件、WSDL 延伸和 XML 結構描述文件的屬性。  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.MetadataElement>   
 <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>   
 <xref:System.ServiceModel.Description.MetadataImporter>   
 <xref:System.ServiceModel.Description.WsdlImporter>   
 [WCF 用戶端組態](../../../../../docs/framework/wcf/feature-details/client-configuration.md)   
 [用戶端](../../../../../docs/framework/wcf/feature-details/clients.md)