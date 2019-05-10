---
title: ICLRMetaHost::RequestRuntimeLoadedNotification 方法
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.RequestRuntimeLoadedNotification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::RequestRuntimeLoadedNotification
helpviewer_keywords:
- RequestRuntimeLoadedNotification method [.NET Framework hosting]
- ICLRMetaHost::RequestRuntimeLoadedNotification method [.NET Framework hosting]
ms.assetid: 0d5ccc4d-0193-41f5-af54-45d7b70d5321
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 87afb19736a484d24bde56cc34854dcd26c6b53b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64755705"
---
# <a name="iclrmetahostrequestruntimeloadednotification-method"></a>ICLRMetaHost::RequestRuntimeLoadedNotification 方法
提供保證的 common language runtime (CLR) 版本是第一次載入，但尚未開始時要呼叫的回呼函式。 這個方法會取代[LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)函式。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT RequestRuntimeLoadedNotification (  
    [in] RuntimeLoadedCallbackFnPtr pCallbackFunction);  
```  
  
## <a name="parameters"></a>參數  
 `pCallbackFunction`  
 [in]已載入新的執行階段時，會叫用回呼函式。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功完成命令。|  
|E_POINTER|`pCallbackFunction` 為 null。|  
  
## <a name="remarks"></a>備註  
 回呼的運作方式如下：  
  
- 只有在第一次載入執行階段時，會叫用回呼。  
  
- 回呼不會叫用相同的執行階段的可重新進入的負載。  
  
- 不可重新進入執行階段載入的序列化回呼函式的呼叫。  
  
 回呼函式具有下列原型：  
  
```  
typedef void (__stdcall *RuntimeLoadedCallbackFnPtr)(  
                     ICLRRuntimeInfo *pRuntimeInfo,  
                     CallbackThreadSetFnPtr pfnCallbackThreadSet,  
                     CallbackThreadUnsetFnPtr pfnCallbackThreadUnset);  
```  
  
 回呼函式原型如下所示：  
  
- `pfnCallbackThreadSet`：  
  
    ```  
    typedef HRESULT (__stdcall *CallbackThreadSetFnPtr)();  
    ```  
  
- `pfnCallbackThreadUnset`：  
  
    ```  
    typedef HRESULT (__stdcall *CallbackThreadUnsetFnPtr)();  
    ```  
  
 如果主機想要載入，或導致另一個執行階段要載入的方式可重新進入，則`pfnCallbackThreadSet`和`pfnCallbackThreadUnset`參數所提供的回呼函式必須使用方式如下：  
  
- `pfnCallbackThreadSet` 必須由之前嘗試這類載入可能會導致執行階段載入的執行緒呼叫。  
  
- `pfnCallbackThreadUnset` 必須先呼叫時，執行緒將不會再造成執行階段負載 （以及從初始的回呼傳回之前）。  
  
- `pfnCallbackThreadSet` 和`pfnCallbackThreadUnset`兩者都是不可重新進入。  
  
> [!NOTE]
>  裝載應用程式必須呼叫`pfnCallbackThreadSet`並`pfnCallbackThreadUnset`的範圍外`pCallbackFunction`參數。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MetaHost.h  
  
 **LIBRARY:** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRMetaHost 介面](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [裝載](../../../../docs/framework/unmanaged-api/hosting/index.md)
