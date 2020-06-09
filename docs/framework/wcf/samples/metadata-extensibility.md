---
title: 中繼資料擴充性
ms.date: 03/30/2017
ms.assetid: f92fcc76-0806-4c84-9d63-7aae0d3899de
ms.openlocfilehash: 1e8e7f511b38cf3326b9abbca57df769317a26a4
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84584619"
---
# <a name="metadata-extensibility"></a>中繼資料擴充性
本節包含示範自訂中繼資料的範例。  
  
## <a name="in-this-section"></a>本節內容  
 [自訂安全中繼資料端點](custom-secure-metadata-endpoint.md)  
 示範如何使用使用其中一個非中繼資料交換系結的安全中繼資料端點來執行服務，以及如何設定[System.servicemodel 中繼資料公用程式工具（Svcutil）](../servicemodel-metadata-utility-tool-svcutil-exe.md)或用戶端，以從這類中繼資料端點提取中繼資料。  
  
 [自訂 WSDL 發行物](custom-wsdl-publication.md)  
 除了其他功能之外，還會示範如何在自訂 <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> 屬性 (Attribute) 上實作 <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>，以便將屬性 (Attribute) 的屬性 (Property) 匯出為 WSDL 附註。
