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
ms.openlocfilehash: 6956d73be0380baef96d94584f007e0683331784
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446080"
---
# <a name="lockclrversion-function"></a>LockClrVersion 函式
可讓主機判斷處理序中先明確初始化 CLR 使用的 common language runtime (CLR) 版本。  
  
 此函式中已被取代[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT LockClrVersion (  
    [in] FLockClrVersionCallback   hostCallback,  
    [in] FLockClrVersionCallback  *pBeginHostSetup,  
    [in] FLockClrVersionCallback  *pEndHostSetup  
);  
```  
  
#### <a name="parameters"></a>參數  
 `hostCallback`  
 [in]要由 CLR 在初始化時呼叫的函式。  
  
 `pBeginHostSetup`  
 [in]正在啟動初始設定主應用程式通知 CLR 所要呼叫函式。  
  
 `pEndHostSetup`  
 [in]函式由主機呼叫，通知 CLR 初始化已完成。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回標準的 COM 錯誤代碼，除了下列的值定義了 WinError.h 中。  
  
|傳回碼|描述|  
|-----------------|-----------------|  
|S_OK|已成功完成命令。|  
|E_INVALIDARG|一或多個引數為 null。|  
  
## <a name="remarks"></a>備註  
 主機會呼叫`LockClrVersion`之前初始化 CLR。 `LockClrVersion` 接受三個參數，都是類型的回呼[FLockClrVersionCallback](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md)。 此類型定義，如下所示。  
  
```  
typedef HRESULT ( __stdcall *FLockClrVersionCallback ) ();  
```  
  
 在執行階段初始化時，執行下列步驟：  
  
1.  主機會呼叫[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)或其他執行階段初始化函式的其中一個。 或者，主應用程式無法初始化執行階段使用 COM 物件啟動。  
  
2.  執行階段呼叫的函式所指定`hostCallback`參數。  
  
3.  所指定的函數`hostCallback`使下列呼叫順序：  
  
    -   所指定的函數`pBeginHostSetup`參數。  
  
    -   `CorBindToRuntimeEx` （或另一個執行階段初始化函式）。  
  
    -   [Iclrruntimehost:: Sethostcontrol](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md)。  
  
    -   [Iclrruntimehost:: Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)。  
  
    -   所指定的函數`pEndHostSetup`參數。  
  
 從所有的呼叫`pBeginHostSetup`至`pEndHostSetup`必須發生在單一執行緒或 fiber，具有相同的邏輯堆疊。 這個執行緒可以不同的執行緒`hostCallback`呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：** MSCorEE.dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [已被取代的 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
