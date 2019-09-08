---
title: 融合介面
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework fusion]
- fusion interfaces [.NET Framework]
- unmanaged interfaces [.NET Framework], fusion
ms.assetid: e2cf98b7-40c1-4f74-86c7-8a76dd9da677
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1605605f8510f7ccf5f0bbf2f3f6b09050a16025
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795311"
---
# <a name="fusion-interfaces"></a>融合介面
本節說明融合 API 用來存取應用程式資源屬性的非受控介面，以及為應用程式找出這些資源的正確版本。  
  
## <a name="in-this-section"></a>本節內容  
 [IAppIdAuthority 介面](iappidauthority-interface.md)  
 提供方法，以產生並比較應用程式識別和參考的索引鍵。  
  
 [IAssemblyCache 介面](iassemblycache-interface.md)  
 提供全域組件快取的標記法。  
  
 [IAssemblyCacheItem 介面](iassemblycacheitem-interface.md)  
 代表全域組件快取中的單一元件。  
  
 [IAssemblyEnum 介面](iassemblyenum-interface.md)  
 表示物件陣列的`IAssemblyName`列舉值。  
  
 [IAssemblyName 介面](iassemblyname-interface.md)  
 提供方法來描述和使用元件的唯一身分識別。  
  
 [IDefinitionAppId 介面](idefinitionappid-interface.md)  
 表示在目前範圍中定義應用程式之程式碼的唯一識別碼。  
  
 [IDefinitionIdentity 介面](idefinitionidentity-interface.md)  
 表示在目前範圍中定義應用程式之程式碼的唯一簽章。  
  
 [IEnumDefinitionIdentity 介面](ienumdefinitionidentity-interface.md)  
 作為`IDefinitionIdentity`物件集合的列舉值。  
  
 [IEnumIDENTITY_ATTRIBUTE 介面](ienumidentity-attribute-interface.md)  
 作為目前範圍中程式碼物件屬性的列舉值。  
  
 [IEnumReferenceIdentity 介面](ienumreferenceidentity-interface.md)  
 作為物件集合的`IReferenceIdentity`列舉值。  
  
 [IIdentityAuthority 介面](iidentityauthority-interface.md)  
 管理程式碼物件的識別索引鍵。  
  
 [IInstallReferenceEnum 介面](iinstallreferenceenum-interface.md)  
 代表安裝在全域組件快取中參考元件的列舉值。  
  
 [IInstallReferenceItem 介面](iinstallreferenceitem-interface.md)  
 代表安裝在全域組件快取中的專案。  
  
 [IReferenceAppId 介面](ireferenceappid-interface.md)  
 代表目前範圍中應用程式的唯一識別碼參考。  
  
 [IReferenceIdentity 介面](ireferenceidentity-interface.md)  
 表示程式碼物件之唯一簽章的參考。  
  
## <a name="reference"></a>參考資料  
 <xref:System.Reflection>  
  
 <xref:System.Reflection.Emit>  
  
## <a name="related-sections"></a>相關章節  
 [融合全域靜態函式](fusion-global-static-functions.md)  
  
 [融合列舉](fusion-enumerations.md)  
  
 [融合結構](fusion-structures.md)
