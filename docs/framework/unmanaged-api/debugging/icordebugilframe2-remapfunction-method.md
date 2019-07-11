---
title: ICorDebugILFrame2::RemapFunction 方法
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame2.RemapFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame2::RemapFunction
helpviewer_keywords:
- ICorDebugILFrame2::RemapFunction method [.NET Framework debugging]
- RemapFunction method [.NET Framework debugging]
ms.assetid: dd639ba0-f77b-426d-9ff6-f92706840348
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bdcc2eccbb24a92643415db8e5d267033ac1ca0a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758745"
---
# <a name="icordebugilframe2remapfunction-method"></a>ICorDebugILFrame2::RemapFunction 方法
將編輯過的函式藉由指定新的 Microsoft intermediate language (MSIL) 位移重新對應  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT RemapFunction (  
    [in] ULONG32      newILOffset  
);  
```  
  
## <a name="parameters"></a>參數  
 `newILOffset`  
 [in]堆疊框架的新 MSIL 位移應該放置指令指標。 此值必須是序列點。  
  
 是以確保此值之有效性的呼叫者的責任。 比方說，MSIL 位移不超出界限的函式是否有效。  
  
## <a name="remarks"></a>備註  
 偵錯工具時已編輯框架的函式，可以呼叫`RemapFunction`交換中框架的函式的最新版本，因此可以執行的方法。 執行程式碼將會在指定的 MSIL 位移開始。  
  
> [!NOTE]
>  呼叫`RemapFunction`，例如呼叫[icordebugilframe:: Setip](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)，將會立即失效與產生的執行緒堆疊追蹤相關的所有偵錯介面。 這些介面包括[ICorDebugChain](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md)，ICorDebugILFrame、 ICorDebugInternalFrame 和 ICorDebugNativeFrame。  
  
 `RemapFunction`可以呼叫方法，只在目前的框架的內容中，而且只用於下列案例之一：  
  
- 之後的回條[ICorDebugManagedCallback2::FunctionRemapOpportunity](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md)已不還繼續執行的回呼。  
  
- 因為停止執行程式碼時[icordebugmanagedcallback:: Editandcontinueremap](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md)這個框架的事件。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
