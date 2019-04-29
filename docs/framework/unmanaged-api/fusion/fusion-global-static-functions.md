---
title: 融合全域靜態函式
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged global static functions [.NET Framework], fusion
- fusion global static functions [.NET Framework]
- global static functions [.NET Framework fusion]
ms.assetid: 229b2188-9168-4b44-a987-e1f515494688
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 86cb59c0935c193a9865d5ace5fe11c96226d9e8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697715"
---
# <a name="fusion-global-static-functions"></a>融合全域靜態函式
本節說明的 unmanaged 全域靜態函式融合 API 使用。  
  
## <a name="in-this-section"></a>本節內容  
 [ClearDownloadCache 函式](../../../../docs/framework/unmanaged-api/fusion/cleardownloadcache-function.md)  
 清除已下載的組件的全域組件快取。  
  
 [CompareAssemblyIdentity 函式](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md)  
 比較兩個組件身分識別，以判斷它們是否相等。  
  
 [CreateApplicationContext 函式](../../../../docs/framework/unmanaged-api/fusion/createapplicationcontext-function.md)  
 僅供內部使用。 （此函式支援.NET Framework 基礎結構並不是直接從您的程式碼使用）。  
  
 [CreateAssemblyCache 函式](../../../../docs/framework/unmanaged-api/fusion/createassemblycache-function.md)  
 取得新指標[IAssemblyCache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)表示全域組件快取執行個體。  
  
 [CreateAssemblyEnum 函式](../../../../docs/framework/unmanaged-api/fusion/createassemblyenum-function.md)  
 取得指標[IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)執行個體，表示物件存在於指定的組件中的清單。  
  
 [CreateAssemblyNameObject 函式](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md)  
 取得指標[IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)執行個體，表示具有指定名稱的組件的唯一識別。  
  
 [CreateHistoryReader 函式](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)  
 建立記錄讀取器指定的檔案。  
  
 [CreateInstallReferenceEnum 函式](../../../../docs/framework/unmanaged-api/fusion/createinstallreferenceenum-function.md)  
 取得指標[IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)執行個體，表示指定的組件的應用程式的參考清單。  
  
 [GetAppIdAuthority 函式](../../../../docs/framework/unmanaged-api/fusion/getappidauthority-function.md)  
 取得指標[IAppIdAuthority](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md)管理應用程式身分識別和參考的索引鍵的執行個體。  
  
 [GetAssemblyIdentityFromFile 函式](../../../../docs/framework/unmanaged-api/fusion/getassemblyidentityfromfile-function.md)  
 取得指標`IUnknown`使用指定的物件`IID`中指定的檔案路徑中的組件。  
  
 [GetCachePath 函式](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)  
 取得快取的組件，並使用指定的旗標的路徑。  
  
 [GetHistoryFileDirectory 函式](../../../../docs/framework/unmanaged-api/fusion/gethistoryfiledirectory-function.md)  
 擷取應用程式記錄目錄的路徑。  
  
 [GetIdentityAuthority 函式](../../../../docs/framework/unmanaged-api/fusion/getidentityauthority-function.md)  
 取得指標[IIdentityAuthority](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md)管理程式碼物件的索引鍵的執行個體。  
  
 [IsFrameworkAssembly 函式](../../../../docs/framework/unmanaged-api/fusion/isframeworkassembly-function.md)  
 取得值，指出指定的組件是否為 managed。  
  
 [NukeDownloadedCache 函式](../../../../docs/framework/unmanaged-api/fusion/nukedownloadedcache-function.md)  
 刪除通用語言執行階段下載快取。  
  
 [PreBindAssemblyEx 函式](../../../../docs/framework/unmanaged-api/fusion/prebindassemblyex-function.md)  
 取得組件的原則後顯示名稱。  
  
## <a name="related-sections"></a>相關章節  
 [融合介面](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
  
 [融合列舉](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)  
  
 [融合結構](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)  
  
 [全域組件快取](../../../../docs/framework/app-domains/gac.md)
