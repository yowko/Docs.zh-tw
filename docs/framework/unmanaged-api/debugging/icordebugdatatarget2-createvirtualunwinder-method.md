---
title: "ICorDebugDataTarget2::CreateVirtualUnwinder 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 354c8b4c-7d23-45c6-a7d7-3be4c2a5b772
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 421cff28e84106c0859889e6f9e99e870b469a98
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdatatarget2createvirtualunwinder-method"></a>ICorDebugDataTarget2::CreateVirtualUnwinder 方法
建立新的堆疊 unwinder，以從初始內容 (不一定是執行緒的分葉) 開始回溯。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CreateVirtualUnwinder(  
    [in] DWORD nativeThreadID,  
    [in] ULONG32 contextFlags,  
    [in] ULONG32 cbContext,  
    [in, size_is(cbContext)] BYTE initialContext[],  
    [out] ICorDebugVirtualUnwinder ** ppUnwinder);  
};  
```  
  
#### <a name="parameters"></a>參數  
 nativeThreadID  
 [in] 其堆疊未回溯之執行緒的原生執行緒 ID。  
  
 contextFlags  
 [in] 指定哪些內容部分會在 `initialContext` 中定義的旗標。  
  
 cbContext  
 [in] `initialContext` 的大小。  
  
 initialContext  
 [in] 內容中的資料。  
  
 ppUnwinder  
 [out] ICorDebugVirtualUnwinder 介面物件的位址指標。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則為 `S_OK`。 其他任何 `HRESULT` 表示失敗。 任何失敗`HRESULT`mscordbi 所接收之被視為嚴重，並造成[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)方法，以傳回`CORDBG_E_DATA_TARGET_ERROR`。  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  這個方法僅適用於 .NET 原生。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorDebugDataTarget2 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
