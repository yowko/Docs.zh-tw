---
title: CreateCordbObject 函式
ms.date: 03/30/2017
api_name:
- CreateCoredbObject
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CreateCordbObject
helpviewer_keywords:
- remote debugging API [Silverlight]
- CreateCordbObject function
- Silverlight, remote debugging
ms.assetid: b259821d-4fa7-464d-85cf-304dfffc8089
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 12898f75d2575e539b018ea367bc870a3dc738a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="createcordbobject-function"></a>CreateCordbObject 函式
建立偵錯工具介面 ([ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)) 針對受管理的偵錯工作階段，在遠端處理序上具現化提供的功能。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CordbCreateObject (  
       [in]  int         iDebuggerVersion,   
       [out] IUnknown**  ppCordb  
);  
```  
  
#### <a name="parameters"></a>參數  
 `iDebuggerVersion`  
 [in] 目標處理序的偵錯工具版本。 這個參數必須是 CorDebugVersion_2_0，才能進行遠端偵錯。  
  
 `ppCordb`  
 [out]指標可以轉換成物件的指標[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)介面，並傳回。  
  
## <a name="return-value"></a>傳回值  
 S_OK  
 已成功確定處理序中的 CLR 數目，並且已正確填入對應的控制代碼和路徑陣列。  
  
 E_INVALIDARG  
 `ppCordb` 為 null，或 `iDebuggerVersion` 不是 CorDebugVersion_2_0。  
  
 E_OUTOFMEMORY  
 無法為 `ppCordb` 配置足夠的記憶體。  
  
 E_FAIL (或其他 E_ 傳回碼)  
 其他失敗。  
  
## <a name="remarks"></a>備註  
 [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)中傳回的介面`ppCordb`是所有受管理的偵錯服務的最上層的偵錯介面。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CoreClrRemoteDebuggingInterfaces.h  
  
 **程式庫：** mscordbi_macx86.dll  
  
 **.NET framework 版本：** 3.5 SP1
