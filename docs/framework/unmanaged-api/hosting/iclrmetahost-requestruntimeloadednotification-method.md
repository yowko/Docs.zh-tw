---
title: "ICLRMetaHost::RequestRuntimeLoadedNotification 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetaHost.RequestRuntimeLoadedNotification
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMetaHost::RequestRuntimeLoadedNotification
helpviewer_keywords:
- RequestRuntimeLoadedNotification method [.NET Framework hosting]
- ICLRMetaHost::RequestRuntimeLoadedNotification method [.NET Framework hosting]
ms.assetid: 0d5ccc4d-0193-41f5-af54-45d7b70d5321
topic_type: apiref
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 32eb92263685bc3be9f0c28dea88ecfa78c2b52c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="iclrmetahostrequestruntimeloadednotification-method"></a>ICLRMetaHost::RequestRuntimeLoadedNotification 方法
提供保證的 common language runtime (CLR) 版本是第一次載入，但尚未啟動時要呼叫的回呼函式。 這個方法會取代[LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)函式。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT RequestRuntimeLoadedNotification (  
    [in] RuntimeLoadedCallbackFnPtr pCallbackFunction);  
```  
  
#### <a name="parameters"></a>參數  
 `pCallbackFunction`  
 [in]在載入新的執行階段時，會叫用回呼函式。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT 以及 HRESULT 錯誤，以指出方法失敗。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功完成命令。|  
|E_POINTER|`pCallbackFunction` 為 null。|  
  
## <a name="remarks"></a>備註  
 回呼的運作方式如下：  
  
-   只有在第一次載入執行階段時，會叫用回呼。  
  
-   可重新進入相同的執行階段載入不會叫用回呼。  
  
-   不可重新進入執行階段載入的回呼函式的呼叫已序列化的。  
  
 回呼函式具有下列原型：  
  
```  
typedef void (__stdcall *RuntimeLoadedCallbackFnPtr)(  
                     ICLRRuntimeInfo *pRuntimeInfo,  
                     CallbackThreadSetFnPtr pfnCallbackThreadSet,  
                     CallbackThreadUnsetFnPtr pfnCallbackThreadUnset);  
```  
  
 回呼函式原型如下所示：  
  
-   `pfnCallbackThreadSet`:  
  
    ```  
    typedef HRESULT (__stdcall *CallbackThreadSetFnPtr)();  
    ```  
  
-   `pfnCallbackThreadUnset`:  
  
    ```  
    typedef HRESULT (__stdcall *CallbackThreadUnsetFnPtr)();  
    ```  
  
 如果主應用程式所要載入，或導致另一個執行階段要載入的方式可重新進入，`pfnCallbackThreadSet`和`pfnCallbackThreadUnset`會提供在回呼函式必須以下列方式使用的參數：  
  
-   `pfnCallbackThreadSet`必須先嘗試這類載入可能會導致執行階段載入的執行緒所呼叫。  
  
-   `pfnCallbackThreadUnset`必須先呼叫時，執行緒將不會再造成執行階段負載 （和從初始回呼傳回之前）。  
  
-   `pfnCallbackThreadSet`和`pfnCallbackThreadUnset`兩者都不可重新進入。  
  
> [!NOTE]
>  裝載應用程式不能呼叫`pfnCallbackThreadSet`和`pfnCallbackThreadUnset`範圍以外的`pCallbackFunction`參數。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MetaHost.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICLRMetaHost 介面](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [裝載](../../../../docs/framework/unmanaged-api/hosting/index.md)
