---
title: LockClrVersion 函式
ms.date: 03/30/2017
api_name:
- LockClrVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- LockClrVersion
helpviewer_keywords:
- LockClrVersion function [.NET Framework hosting]
ms.assetid: 1318ee37-c43b-40eb-bbe8-88fc46453d74
topic_type:
- apiref
ms.openlocfilehash: 216852f8f051440b2814619b843a1f25013e4042
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133769"
---
# <a name="lockclrversion-function"></a>LockClrVersion 函式
允許主機判斷在明確初始化 CLR 之前，將在進程中使用哪個版本的 common language runtime （CLR）。  
  
 此函式在 .NET Framework 4 中已被取代。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT LockClrVersion (  
    [in] FLockClrVersionCallback   hostCallback,  
    [in] FLockClrVersionCallback  *pBeginHostSetup,  
    [in] FLockClrVersionCallback  *pEndHostSetup  
);  
```  
  
## <a name="parameters"></a>參數  
 `hostCallback`  
 在要在初始化時由 CLR 呼叫的函式。  
  
 `pBeginHostSetup`  
 在主機要呼叫的函式，以通知 CLR 初始化正在啟動。  
  
 `pEndHostSetup`  
 在主機要呼叫的函式，以通知 CLR 初始化已完成。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回標準 COM 錯誤碼（如 Winerror.h 中所定義），以及下列值。  
  
|傳回碼|描述|  
|-----------------|-----------------|  
|S_OK|已成功完成命令。|  
|E_INVALIDARG|一或多個引數為 null。|  
  
## <a name="remarks"></a>備註  
 主機會在初始化 CLR 之前呼叫 `LockClrVersion`。 `LockClrVersion` 採用三個參數，這些都是[FLockClrVersionCallback](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md)類型的回呼。 此類型的定義如下。  
  
```cpp  
typedef HRESULT ( __stdcall *FLockClrVersionCallback ) ();  
```  
  
 初始化執行時間時，會發生下列步驟：  
  
1. 主機會呼叫[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)或其中一個其他執行時間初始化函數。 或者，主機也可以使用 COM 物件啟用來初始化執行時間。  
  
2. 執行時間會呼叫 `hostCallback` 參數所指定的函數。  
  
3. `hostCallback` 所指定的函式會執行下列一連串的呼叫：  
  
    - `pBeginHostSetup` 參數所指定的函數。  
  
    - `CorBindToRuntimeEx` （或另一個執行時間初始化函數）。  
  
    - [ICLRRuntimeHost：： SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md)。  
  
    - [ICLRRuntimeHost：： Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)。  
  
    - `pEndHostSetup` 參數所指定的函數。  
  
 所有從 `pBeginHostSetup` 到 `pEndHostSetup` 的呼叫都必須在具有相同邏輯堆疊的單一執行緒或光纖上發生。 這個執行緒可以與呼叫 `hostCallback` 的執行緒不同。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** Mscoree.dll .dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [已被取代的 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
