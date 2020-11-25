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
ms.openlocfilehash: 5eb6299526d69624056961cfb7f0387ff8f873cf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725023"
---
# <a name="icordebugilframe2remapfunction-method"></a>ICorDebugILFrame2::RemapFunction 方法

藉由指定新的 Microsoft 中繼語言 (MSIL) 位移，重新對應已編輯的函式  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT RemapFunction (  
    [in] ULONG32      newILOffset  
);  
```  
  
## <a name="parameters"></a>參數  

 `newILOffset`  
 在應放置指令指標的堆疊框架新 MSIL 位移。 這個值必須是序列點。  
  
 呼叫端必須負責確保此值的有效性。 例如，如果 MSIL 位移超出函式的界限，則無效。  
  
## <a name="remarks"></a>備註  

 編輯方塊架的函式時，偵錯工具可以呼叫 `RemapFunction` 方法，以在最新版本的框架函式中交換，以便執行。 程式碼執行將從指定的 MSIL 位移開始。  
  
> [!NOTE]
> 呼叫 `RemapFunction` （例如呼叫 [ICorDebugILFrame：： SetIP](icordebugilframe-setip-method.md)）會立即使與產生執行緒的堆疊追蹤相關的所有偵錯工具失效。 這些介面包括 [ICorDebugChain](icordebugchain-interface.md)、ICorDebugILFrame、ICorDebugInternalFrame 和 ICorDebugNativeFrame。  
  
 只有在 `RemapFunction` 下列其中一個情況下，才能在目前框架的內容中呼叫方法：  
  
- 在收到尚未繼續的 [ICorDebugManagedCallback2：： FunctionRemapOpportunity](icordebugmanagedcallback2-functionremapopportunity-method.md) 回呼之後。  
  
- 由於此框架的 [ICorDebugManagedCallback：： EditAndContinueRemap](icordebugmanagedcallback-editandcontinueremap-method.md) 事件，程式碼執行已停止。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
