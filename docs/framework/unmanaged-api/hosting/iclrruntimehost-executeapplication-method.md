---
title: ICLRRuntimeHost::ExecuteApplication 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteApplication
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteApplication
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteApplication method [.NET Framework hosting]
- ExecuteApplication method [.NET Framework hosting]
ms.assetid: 5f28cc4e-7176-4e00-aa1f-58ae6ee52fe4
topic_type:
- apiref
ms.openlocfilehash: 924d032c42dca95b253acea167d55dd6e2b811e5
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703330"
---
# <a name="iclrruntimehostexecuteapplication-method"></a>ICLRRuntimeHost::ExecuteApplication 方法
在以資訊清單為基礎的 ClickOnce 部署案例中使用，以指定要在新的網域中啟動的應用程式。 如需這些案例的詳細資訊，請參閱[ClickOnce 安全性和部署](/visualstudio/deployment/clickonce-security-and-deployment)。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ExecuteApplication(  
    [in] LPCWSTR   pwzAppFullName,  
    [in] DWORD     dwManifestPaths,  
    [in] LPCWSTR   *ppwzManifestPaths,  
    [in] DWORD     dwActivationData,  
    [in] LPCWSTR   *ppwzActivationData,  
    [out] int      *pReturnValue  
);  
```  
  
## <a name="parameters"></a>參數  
 `pwzAppFullName`  
 在應用程式的完整名稱，如所定義 <xref:System.ApplicationIdentity> 。  
  
 `dwManifestPaths`  
 在陣列中包含的字串數目 `ppwzManifestPaths` 。  
  
 `ppwzManifestPaths`  
 [in] 選用。 字串陣列，其中包含應用程式的資訊清單路徑。  
  
 `dwActivationData`  
 在陣列中包含的字串數目 `ppwzActivationData` 。  
  
 `ppwzActivationData`  
 [in] 選用。 字串陣列，其中包含應用程式的啟用資料，例如透過 Web 部署之應用程式的 URL 查詢字串部分。  
  
 `pReturnValue`  
 脫銷從應用程式的進入點傳回的值。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|說明|  
|-------------|-----------------|  
|S_OK|`ExecuteApplication`已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|已封鎖的執行緒或光纖在等候時取消了事件。|  
|E_FAIL|發生不明的嚴重失敗。 如果方法傳回 E_FAIL，就無法在進程內使用 CLR。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  
 `ExecuteApplication`是用來在新建立的應用程式域中啟動 ClickOnce 應用程式。  
  
 `pReturnValue`輸出參數會設定為應用程式所傳回的值。 如果您提供的值為 null，則不會 `pReturnValue` `ExecuteApplication` 失敗，但不會傳回值。  
  
> [!IMPORTANT]
> 在呼叫方法來啟動以資訊清單為基礎的應用程式之前，請不要呼叫[Start 方法](iclrruntimehost-start-method.md)方法 `ExecuteApplication` 。 如果 `Start` 先呼叫方法， `ExecuteApplication` 方法呼叫將會失敗。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ActivationContext>
- <xref:System.AppDomainManager>
- <xref:System.ApplicationIdentity>
- [ICLRRuntimeHost 介面](iclrruntimehost-interface.md)
- [SetAppDomainManager 方法](ihostcontrol-setappdomainmanager-method.md)
- [逐步解說：使用設計工具依 ClickOnce 部署 API 的要求下載元件](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer)
