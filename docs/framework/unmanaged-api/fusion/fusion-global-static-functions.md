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
ms.openlocfilehash: 6a8f15bc862c0486311960f7567c49424859846e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795323"
---
# <a name="fusion-global-static-functions"></a>融合全域靜態函式
本節說明融合 API 所使用的非受控全域靜態函式。  
  
## <a name="in-this-section"></a>本節內容  
 [ClearDownloadCache 函式](cleardownloadcache-function.md)  
 清除已下載元件的全域組件快取。  
  
 [CompareAssemblyIdentity 函式](compareassemblyidentity-function.md)  
 比較兩個元件識別，以判斷它們是否相等。  
  
 [CreateApplicationContext 函式](createapplicationcontext-function.md)  
 僅供內部之用。 （此函式支援 .NET Framework 的基礎結構，但不適合直接從您的程式碼使用）。  
  
 [CreateAssemblyCache 函式](createassemblycache-function.md)  
 取得代表全域組件快取之新[IAssemblyCache](iassemblycache-interface.md)實例的指標。  
  
 [CreateAssemblyEnum 函式](createassemblyenum-function.md)  
 取得[IAssemblyEnum](iassemblyenum-interface.md)實例的指標，表示存在於指定元件中的物件清單。  
  
 [CreateAssemblyNameObject 函式](createassemblynameobject-function.md)  
 取得[IAssemblyName](iassemblyname-interface.md)實例的指標，表示具有指定名稱之元件的唯一識別。  
  
 [CreateHistoryReader 函式](createhistoryreader-function.md)  
 為指定的檔案建立記錄讀取器。  
  
 [CreateInstallReferenceEnum 函式](createinstallreferenceenum-function.md)  
 取得[IInstallReferenceEnum](iinstallreferenceenum-interface.md)實例的指標，表示應用程式對指定元件的參考清單。  
  
 [GetAppIdAuthority 函式](getappidauthority-function.md)  
 取得[IAppIdAuthority](iappidauthority-interface.md)實例的指標，它會管理應用程式識別和參考的索引鍵。  
  
 [GetAssemblyIdentityFromFile 函式](getassemblyidentityfromfile-function.md)  
 取得具有指定之元件`IUnknown` `IID`中指定檔案路徑之物件的指標。  
  
 [GetCachePath 函式](getcachepath-function.md)  
 使用指定的旗標，取得快取元件的路徑。  
  
 [GetHistoryFileDirectory 函式](gethistoryfiledirectory-function.md)  
 抓取應用程式歷程記錄目錄的路徑。  
  
 [GetIdentityAuthority 函式](getidentityauthority-function.md)  
 取得[IIdentityAuthority](iidentityauthority-interface.md)實例的指標，它會管理程式碼物件的索引鍵。  
  
 [IsFrameworkAssembly 函式](isframeworkassembly-function.md)  
 取得值，指出指定的元件是否為 managed。  
  
 [NukeDownloadedCache 函式](nukedownloadedcache-function.md)  
 刪除 common language runtime 下載快取。  
  
 [PreBindAssemblyEx 函式](prebindassemblyex-function.md)  
 取得元件的後置原則顯示名稱。  
  
## <a name="related-sections"></a>相關章節  
 [融合介面](fusion-interfaces.md)  
  
 [融合列舉](fusion-enumerations.md)  
  
 [融合結構](fusion-structures.md)  
  
 [全域組件快取](../../app-domains/gac.md)
