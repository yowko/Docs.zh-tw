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
ms.openlocfilehash: 9f03d8c993be1ac83ca84275bcb94f1bb3cdf884
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugilframe2remapfunction-method"></a>ICorDebugILFrame2::RemapFunction 方法
藉由指定新的 Microsoft intermediate language (MSIL) 位移重新對應已編輯函式  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT RemapFunction (  
    [in] ULONG32      newILOffset  
);  
```  
  
#### <a name="parameters"></a>參數  
 `newILOffset`  
 [in]堆疊框架的新 MSIL 指令指標應該將放入其中的位移。 此值必須是序列點。  
  
 它是呼叫者的責任在於確保此值的有效性。 比方說，MSIL 位移不正確，如果它是函式的範圍外。  
  
## <a name="remarks"></a>備註  
 當已經編輯框架的函式時，偵錯工具可以呼叫`RemapFunction`交換中框架的函式的最新版本，讓它可以執行的方法。 執行程式碼將會開始於指定的 MSIL 位移。  
  
> [!NOTE]
>  呼叫`RemapFunction`、 like 呼叫[icordebugilframe:: Setip](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)，將會立即使產生執行緒的堆疊追蹤相關的所有偵錯介面。 這些介面包括[ICorDebugChain](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md)，ICorDebugILFrame、 ICorDebugInternalFrame 和 ICorDebugNativeFrame。  
  
 `RemapFunction`可呼叫方法，只在目前的框架，內容中，且只有在下列情況的其中一個：  
  
-   在回條之後[icordebugmanagedcallback2:: Functionremapopportunity](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md)具有未尚未已繼續的回呼。  
  
-   因為停止執行程式碼時[icordebugmanagedcallback:: Editandcontinueremap](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md)這個畫面格的事件。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
