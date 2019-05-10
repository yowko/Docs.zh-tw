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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aab3a2a367f6af1deeb1201d391af271a4bd45ac
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64584998"
---
# <a name="lockclrversion-function"></a>LockClrVersion 函式
可讓主機判斷哪個版本的 common language runtime (CLR) 會在程序中使用之前先明確初始化 CLR。  
  
 此函式中的過時[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT LockClrVersion (  
    [in] FLockClrVersionCallback   hostCallback,  
    [in] FLockClrVersionCallback  *pBeginHostSetup,  
    [in] FLockClrVersionCallback  *pEndHostSetup  
);  
```  
  
## <a name="parameters"></a>參數  
 `hostCallback`  
 [in]在初始化時，clr 會呼叫的函式。  
  
 `pBeginHostSetup`  
 [in]正在啟動初始設定來通知 CLR 主機會呼叫的函式。  
  
 `pEndHostSetup`  
 [in]函式由主機呼叫，來通知 CLR 初始化已完成。  
  
## <a name="return-value"></a>傳回值  
 中所定義 WinError.h，除了下列的值，這個方法會傳回標準的 COM 錯誤代碼。  
  
|傳回碼|描述|  
|-----------------|-----------------|  
|S_OK|已成功完成命令。|  
|E_INVALIDARG|一或多個引數為 null。|  
  
## <a name="remarks"></a>備註  
 主機會呼叫`LockClrVersion`之前初始化 CLR。 `LockClrVersion` 採用三個參數，全部都是類型的回呼[FLockClrVersionCallback](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md)。 此類型定義，如下所示。  
  
```  
typedef HRESULT ( __stdcall *FLockClrVersionCallback ) ();  
```  
  
 在執行階段初始化時，會執行下列步驟：  
  
1. 主機會呼叫[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)或其中一個其他執行階段初始化函式。 或者，主應用程式無法初始化執行階段使用 COM 物件啟動。  
  
2. 在執行階段呼叫所指定的函數`hostCallback`參數。  
  
3. 所指定的函數`hostCallback`接著會將下列呼叫順序：  
  
    - 所指定的函數`pBeginHostSetup`參數。  
  
    - `CorBindToRuntimeEx` （或另一個執行階段初始化函式）。  
  
    - [Iclrruntimehost:: Sethostcontrol](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md)。  
  
    - [Iclrruntimehost:: Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)。  
  
    - 所指定的函數`pEndHostSetup`參數。  
  
 所有的來電`pBeginHostSetup`至`pEndHostSetup`必須發生在單一執行緒或 fiber，使用相同的邏輯堆疊。 這個執行緒可以不同的執行緒`hostCallback`呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** MSCorEE.dll  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [已被取代的 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
