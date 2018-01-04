---
title: "融合全域靜態函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unmanaged global static functions [.NET Framework], fusion
- fusion global static functions [.NET Framework]
- global static functions [.NET Framework fusion]
ms.assetid: 229b2188-9168-4b44-a987-e1f515494688
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 126edd5f25b56a069a87cd1bd50cce955334a342
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="fusion-global-static-functions"></a>融合全域靜態函式
本章節描述的 unmanaged 全域靜態函式融合 API 使用。  
  
## <a name="in-this-section"></a>本節內容  
 [ClearDownloadCache 函式](../../../../docs/framework/unmanaged-api/fusion/cleardownloadcache-function.md)  
 清除已下載組件的全域組件快取。  
  
 [CompareAssemblyIdentity 函式](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md)  
 比較兩個組件識別，以判斷它們是否相等。  
  
 [CreateApplicationContext 函式](../../../../docs/framework/unmanaged-api/fusion/createapplicationcontext-function.md)  
 僅供內部使用。 （這個函式支援.NET Framework 基礎結構和不適用於直接從程式碼）。  
  
 [CreateAssemblyCache 函式](../../../../docs/framework/unmanaged-api/fusion/createassemblycache-function.md)  
 取得新的指標[IAssemblyCache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)代表全域組件快取的執行個體。  
  
 [CreateAssemblyEnum 函式](../../../../docs/framework/unmanaged-api/fusion/createassemblyenum-function.md)  
 取得指標[IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)執行個體，表示物件存在於指定的組件中的清單。  
  
 [CreateAssemblyNameObject 函式](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md)  
 取得指標[IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)執行個體，表示具有指定名稱的組件的唯一識別。  
  
 [CreateHistoryReader 函式](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)  
 建立指定的檔案歷程記錄讀取器。  
  
 [CreateInstallReferenceEnum 函式](../../../../docs/framework/unmanaged-api/fusion/createinstallreferenceenum-function.md)  
 取得指標[IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)執行個體，表示應用程式的參考指定組件的清單。  
  
 [GetAppIdAuthority 函式](../../../../docs/framework/unmanaged-api/fusion/getappidauthority-function.md)  
 取得指標[IAppIdAuthority](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md)管理應用程式識別與參考索引鍵的執行個體。  
  
 [GetAssemblyIdentityFromFile 函式](../../../../docs/framework/unmanaged-api/fusion/getassemblyidentityfromfile-function.md)  
 取得指標`IUnknown`物件具有指定`IID`中位於指定的檔案路徑的組件。  
  
 [GetCachePath 函式](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)  
 取得使用指定的旗標的快取組件的路徑。  
  
 [GetHistoryFileDirectory 函式](../../../../docs/framework/unmanaged-api/fusion/gethistoryfiledirectory-function.md)  
 擷取應用程式的歷程記錄目錄的路徑。  
  
 [GetIdentityAuthority 函式](../../../../docs/framework/unmanaged-api/fusion/getidentityauthority-function.md)  
 取得指標[IIdentityAuthority](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md)管理程式碼物件的索引鍵的執行個體。  
  
 [IsFrameworkAssembly 函式](../../../../docs/framework/unmanaged-api/fusion/isframeworkassembly-function.md)  
 取得值，指出指定的組件是否為 managed。  
  
 [NukeDownloadedCache 函式](../../../../docs/framework/unmanaged-api/fusion/nukedownloadedcache-function.md)  
 通用語言執行階段下載快取中刪除。  
  
 [PreBindAssemblyEx 函式](../../../../docs/framework/unmanaged-api/fusion/prebindassemblyex-function.md)  
 取得組件的原則後顯示名稱。  
  
## <a name="related-sections"></a>相關章節  
 [融合介面](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
  
 [融合列舉](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)  
  
 [融合結構](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)  
  
 [全域組件快取](../../../../docs/framework/app-domains/gac.md)
