---
title: "中繼資料擴充性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f92fcc76-0806-4c84-9d63-7aae0d3899de
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 36eb5940fa1d869948a94fcbbb1945aea1c534ac
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="metadata-extensibility"></a>中繼資料擴充性
本節包含示範自訂中繼資料的範例。  
  
## <a name="in-this-section"></a>本章節內容  
 [自訂安全中繼資料端點](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)  
 示範如何實作使用安全的中繼資料端點，使用其中一個是非中繼資料交換繫結的服務，以及如何設定[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)或擷取的中繼資料的用戶端這類中繼資料端點。  
  
 [自訂 WSDL 發行物](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md)  
 除了其他功能之外，還會示範如何在自訂 <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> 屬性 (Attribute) 上實作 <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>，以便將屬性 (Attribute) 的屬性 (Property) 匯出為 WSDL 附註。
