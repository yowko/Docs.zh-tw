---
title: "ICLRRuntimeHost::ExecuteApplication 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7b765f020bd15fa94fb18a6fd7d81cf66c534639
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimehostexecuteapplication-method"></a>ICLRRuntimeHost::ExecuteApplication 方法
在資訊清單為主的 ClickOnce 部署案例中用來指定要啟動新的網域中的應用程式。 如需有關這些案例的詳細資訊，請參閱[ClickOnce 安全性和部署](/visualstudio/deployment/clickonce-security-and-deployment)。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT ExecuteApplication(  
    [in] LPCWSTR   pwzAppFullName,  
    [in] DWORD     dwManifestPaths,  
    [in] LPCWSTR   *ppwzManifestPaths,  
    [in] DWORD     dwActivationData,  
    [in] LPCWSTR   *ppwzActivationData,  
    [out] int      *pReturnValue  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pwzAppFullName`  
 [in]為所定義的應用程式的完整名稱<xref:System.ApplicationIdentity>。  
  
 `dwManifestPaths`  
 [in]字串中包含的數字`ppwzManifestPaths`陣列。  
  
 `ppwzManifestPaths`  
 [in] 選用。 字串陣列，其中包含應用程式資訊清單的路徑。  
  
 `dwActivationData`  
 [in]字串中包含的數字`ppwzActivationData`陣列。  
  
 `ppwzActivationData`  
 [in] 選用。 字串陣列，其中包含應用程式的啟用資料，例如透過 Web 部署的應用程式的 URL 查詢字串部分。  
  
 `pReturnValue`  
 [out]從應用程式的進入點傳回的值。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`ExecuteApplication`已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫已逾時。|  
|HOST_E_NOT_OWNER|呼叫端未擁有鎖定。|  
|HOST_E_ABANDONED|事件已取消時封鎖的執行緒或 fiber 等候它。|  
|E_FAIL|發生未知的嚴重失敗。 若方法會傳回 E_FAIL，CLR 就不會再處理序內。 裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  
 `ExecuteApplication`用來啟動新建立的應用程式定義域中的 ClickOnce 應用程式。  
  
 `pReturnValue`輸出參數設定為應用程式所傳回的值。 如果您提供的 null 值`pReturnValue`，`ExecuteApplication`不會失敗，但不會傳回值。  
  
> [!IMPORTANT]
>  請勿呼叫[啟動方法](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)方法之前先呼叫`ExecuteApplication`方法來啟動資訊清單為基礎的應用程式。 如果`Start`首先，呼叫方法`ExecuteApplication`方法呼叫將會失敗。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 <xref:System.ActivationContext>  
 <xref:System.AppDomainManager>  
 <xref:System.ApplicationIdentity>  
 [ICLRRuntimeHost 介面](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 [SetAppDomainManager 方法](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-setappdomainmanager-method.md)  
 [逐步解說：依需求使用設計工具以 ClickOnce 部署 API 下載組件](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer)
