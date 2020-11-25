---
title: ICLRRuntimeInfo::IsLoaded 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsLoaded
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsLoaded
helpviewer_keywords:
- IsLoaded method [.NET Framework hosting]
- ICLRRuntimeInfo::IsLoaded method [.NET Framework hosting]
ms.assetid: fdc5a3a7-71ff-4025-99a1-59e4ee0bfe1b
topic_type:
- apiref
ms.openlocfilehash: 66ae74deba9ceab9d1ea6b2c0b96a87bf44f32ab
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714922"
---
# <a name="iclrruntimeinfoisloaded-method"></a>ICLRRuntimeInfo::IsLoaded 方法

指出與 [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) 介面相關聯的 common language RUNTIME (CLR) 是否會載入至進程。 您也可以在不啟動的情況下載入執行時間。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT IsLoaded(  
[in]  HANDLE hndProcess,  
[out, retval] BOOL *pbLoaded);  
```  
  
## <a name="parameters"></a>參數  

 `hndProcess`  
 在進程的控制碼。  
  
 `pbLoaded`  
 [out] `true` 如果 CLR 已載入至進程，否則為 `false` 。  
  
## <a name="return-value"></a>傳回值  

 這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功完成命令。|  
|E_POINTER|`pbLoaded` 為 null。|  
  
## <a name="remarks"></a>備註  

 這個方法與下列函式和介面具有回溯相容性：  
  
- .NET Framework 第1版裝載 API) 中 ([ICorRuntimeHost](icorruntimehost-interface.md)介面。  
  
- .NET Framework 2.0 裝載 API) 中 ([ICLRRuntimeHost](iclrruntimehost-interface.md)介面。  
  
- 已淘汰的函式 `CorBindTo*` (在 .NET Framework 2.0 裝載 API) 中看到已被 [取代的 CLR 裝載](deprecated-clr-hosting-functions.md) 函式。  
  
 主機可以呼叫其中一個已被取代的函式（ `CorBindTo*` 例如 [CorBindToRuntime](corbindtoruntime-function.md) 函式），以具現化特定的 CLR 版本。 然後，主機可以呼叫 [ICLRMetaHost：： GetRuntime](iclrmetahost-getruntime-method.md) 方法，並指定相同的版本號碼來取得 [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) 介面。  
  
 如果主機接著在 `IsLoaded` 傳回的 [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) 介面上呼叫方法，則 `pbLoaded` 會傳回， `true` 否則會傳回 `false` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** MetaHost。h  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRRuntimeInfo 介面](iclrruntimeinfo-interface.md)
- [裝載介面](hosting-interfaces.md)
- [裝載](index.md)
