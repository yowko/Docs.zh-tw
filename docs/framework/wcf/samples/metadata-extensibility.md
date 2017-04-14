---
title: "中繼資料擴充性 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f92fcc76-0806-4c84-9d63-7aae0d3899de
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 中繼資料擴充性
本節包含示範自訂中繼資料的範例。  
  
## 在本節中  
 [自訂安全中繼資料端點](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)  
 示範如何實作具有使用其中一個非中繼資料交換繫結的安全中繼資料端點的服務，以及如何設定 [ServiceModel 中繼資料公用程式工具 \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) 或用戶端從這類中繼端點取得中繼資料。  
  
 [自訂 WSDL 發行物](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md)  
 除了其他功能之外，還會示範如何在自訂 <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=fullName> 屬性 \(Attribute\) 上實作 <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=fullName>，以便將屬性 \(Attribute\) 的屬性 \(Property\) 匯出為 WSDL 附註。