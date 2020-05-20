---
title: ICLRDomainManager::SetAppDomainManagerType 方法
ms.date: 03/30/2017
api_name:
- ICLRDomainManager.SetAppDomainManagerType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDomainManager::SetAppDomainManagerType
helpviewer_keywords:
- SetAppDomainManagerType method, ICLRDomainManager interface [.NET Framework hosting]
- ICLRDomainManager::SetAppDomainManagerType method [.NET Framework hosting]
ms.assetid: ee91abb0-cb74-41dd-927b-e117fb8ffdf4
ms.openlocfilehash: 89b3f9f248a445cc0568236d6a1df14269de4187
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615692"
---
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a>ICLRDomainManager::SetAppDomainManagerType 方法
指定 <xref:System.AppDomainManager?displayProperty=nameWithType> 將用來初始化預設應用程式域之應用程式網域管理員的類型（衍生自類別）。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetAppDomainManagerType(  
    [in] LPCWSTR wszAppDomainManagerAssembly,  
    [in] LPCWSTR wszAppDomainManagerType,  
    [in] EInitializeNewDomainFlags dwInitializeDomainFlags  
);  
```  
  
## <a name="parameters"></a>參數  
 `wszAppDomainManagerAssembly`  
 在包含應用程式域管理員類型之元件的顯示名稱;例如： "AdMgrExample，Version = 1.0.0.0，Culture = 中性，PublicKeyToken = 6856bccf150f00b3"。  
  
 `wszAppDomainManagerType`  
 在應用程式域管理員的類型名稱，包括命名空間。  
  
 `dwInitializeDomainFlags`  
 在[EInitializeNewDomainFlags](einitializenewdomainflags-enumeration.md)列舉值的組合，可提供應用程式域管理員的相關資訊。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|說明|  
|-------------|-----------------|  
|S_OK|已成功完成命令。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
  
## <a name="remarks"></a>備註  
 目前，唯一定義的值 `dwInitializeDomainFlags` 是 `eInitializeNewDomainFlags_NoSecurityChanges` ，它會告知 common language RUNTIME （CLR），應用程式域管理員在方法執行期間將不會修改安全性設定 <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> 。 這可讓 CLR 優化具有條件式 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> （APTCA）屬性之元件的載入。 如果這組元件的可轉移關閉很大，這會導致啟動時間大幅改善。  
  
> [!IMPORTANT]
> 如果主機 `eInitializeNewDomainFlags_NoSecurityChanges` 為應用程式域管理員指定，則在 <xref:System.InvalidOperationException> 嘗試修改應用程式域的安全性時，就會擲回。  
  
 呼叫[ICLRControl：： SetAppDomainManagerType](iclrcontrol-setappdomainmanagertype-method.md)方法相當於 `ICLRDomainManager::SetAppDomainManagerType` 使用呼叫 `eInitializeNewDomainFlags_None` 。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** MetaHost。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載](index.md)
- [ICLRDomainManager 介面](iclrdomainmanager-interface.md)
- [EInitializeNewDomainFlags 列舉](einitializenewdomainflags-enumeration.md)
