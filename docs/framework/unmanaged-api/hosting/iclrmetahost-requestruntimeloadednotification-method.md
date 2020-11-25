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
ms.openlocfilehash: ac40e203cf7d32c1fe30c9915bac3171139403e0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723277"
---
# <a name="iclrmetahostrequestruntimeloadednotification-method"></a>ICLRMetaHost::RequestRuntimeLoadedNotification 方法

提供回呼函式，保證在第一次載入 common language runtime (CLR) 版本，但尚未啟動時，會呼叫此函式。 這個方法會取代 [LockClrVersion](lockclrversion-function.md) 函數。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT RequestRuntimeLoadedNotification (  
    [in] RuntimeLoadedCallbackFnPtr pCallbackFunction);  
```  
  
## <a name="parameters"></a>參數  

 `pCallbackFunction`  
 在載入新執行時間時叫用的回呼函數。  
  
## <a name="return-value"></a>傳回值  

 這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功完成命令。|  
|E_POINTER|`pCallbackFunction` 為 null。|  
  
## <a name="remarks"></a>備註  

 回呼的運作方式如下：  
  
- 只有在第一次載入執行時間時，才會叫用回呼。  
  
- 針對相同執行時間的可重新進入載入，不會叫用回呼。  
  
- 針對非重新進入執行時間載入，會序列化回呼函數的呼叫。  
  
 回呼函數具有下列原型：  
  
```cpp  
typedef void (__stdcall *RuntimeLoadedCallbackFnPtr)(  
                     ICLRRuntimeInfo *pRuntimeInfo,  
                     CallbackThreadSetFnPtr pfnCallbackThreadSet,  
                     CallbackThreadUnsetFnPtr pfnCallbackThreadUnset);  
```  
  
 回呼函數原型如下所示：  
  
- `pfnCallbackThreadSet`:  
  
    ```cpp  
    typedef HRESULT (__stdcall *CallbackThreadSetFnPtr)();  
    ```  
  
- `pfnCallbackThreadUnset`:  
  
    ```cpp  
    typedef HRESULT (__stdcall *CallbackThreadUnsetFnPtr)();  
    ```  
  
 如果主機打算載入或導致另一個執行時間以重新進入的方式載入，則在回呼函式中 `pfnCallbackThreadSet` 提供的和 `pfnCallbackThreadUnset` 參數必須以下列方式使用：  
  
- `pfnCallbackThreadSet` 必須由可能會導致執行時間載入的執行緒呼叫，然後再嘗試這類載入。  
  
- `pfnCallbackThreadUnset` 當執行緒不再造成執行時間載入 (，以及從初始回呼) 傳回之前，都必須呼叫。  
  
- `pfnCallbackThreadSet` 和 `pfnCallbackThreadUnset` 都是不可重新進入的。  
  
> [!NOTE]
> 主機應用程式不得在 `pfnCallbackThreadSet` `pfnCallbackThreadUnset` 參數的範圍之外呼叫和 `pCallbackFunction` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** MetaHost。h  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRMetaHost 介面](iclrmetahost-interface.md)
- [裝載](index.md)
