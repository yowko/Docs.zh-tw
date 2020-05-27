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
ms.openlocfilehash: 09bcebfdcfea3d5728d404cdb6b5fb170a5432c3
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008491"
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
 主機會在 `LockClrVersion` 初始化 CLR 之前呼叫。 `LockClrVersion`採用三個參數，這些都是[FLockClrVersionCallback](flockclrversioncallback-function-pointer.md)類型的回呼。 此類型的定義如下。  
  
```cpp  
typedef HRESULT ( __stdcall *FLockClrVersionCallback ) ();  
```  
  
 初始化執行時間時，會發生下列步驟：  
  
1. 主機會呼叫[CorBindToRuntimeEx](corbindtoruntimeex-function.md)或其中一個其他執行時間初始化函數。 或者，主機也可以使用 COM 物件啟用來初始化執行時間。  
  
2. 執行時間會呼叫參數所指定的函式 `hostCallback` 。  
  
3. 所指定的函式 `hostCallback` 會進行下列一連串的呼叫：  
  
    - 參數所指定的函式 `pBeginHostSetup` 。  
  
    - `CorBindToRuntimeEx`（或另一個執行時間初始化函數）。  
  
    - [ICLRRuntimeHost：： SetHostControl](iclrruntimehost-sethostcontrol-method.md)。  
  
    - [ICLRRuntimeHost：： Start](iclrruntimehost-start-method.md)。  
  
    - 參數所指定的函式 `pEndHostSetup` 。  
  
 所有從到的呼叫都 `pBeginHostSetup` `pEndHostSetup` 必須在具有相同邏輯堆疊的單一執行緒或光纖上發生。 這個執行緒可以與呼叫的執行緒不同 `hostCallback` 。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** Mscoree.dll .dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [已被取代的 CLR 裝載函式](deprecated-clr-hosting-functions.md)
