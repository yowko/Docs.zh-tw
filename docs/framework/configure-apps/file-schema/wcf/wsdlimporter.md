---
title: "&lt;wsdlImporter&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 986b2165-8430-4dba-b1b8-00396841bb96
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# &lt;wsdlImporter&gt;
指定所有 WSDL 匯入工具，此工具會使用 WS\-Policy 附件匯入 Web 服務描述語言 \(WSDL\) 1.1 中繼資料。  
  
## 語法  
  
```  
  
<metadata>  
      <wsdlImporters>  
      <wsdlImporter type="string" />  
   </wsdlImporters>  
</metadata>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`type`|此項目的型別。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<wsdlImporters\>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdlimporters.md)|指定所有 WSDL 匯入工具，此工具會使用 WS\-Policy 附件匯入 Web 服務描述語言 \(WSDL\) 1.1 中繼資料。|  
  
## 備註  
 WSDL 匯入工具是用來匯入中繼資料，以及將該資訊轉換成表示合約和端點資訊的各種不同類別。  它可以選擇性地匯入合約和端點資訊，以及可公開 \(Expose\) 任何匯入錯誤並接受與匯入和轉換處理有關聯之型別資訊的屬性。  此外，它也支援匯入繫結資訊，以及可提供存取任何原則文件、WSDL 文件、WSDL 延伸和 XML 結構描述文件的屬性。  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.WsdlImporterElement>   
 <xref:System.ServiceModel.Configuration.MetadataElement>   
 <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>   
 <xref:System.ServiceModel.Description.MetadataImporter>   
 <xref:System.ServiceModel.Description.WsdlImporter>   
 [WCF 用戶端組態](../../../../../docs/framework/wcf/feature-details/client-configuration.md)   
 [用戶端](../../../../../docs/framework/wcf/feature-details/clients.md)