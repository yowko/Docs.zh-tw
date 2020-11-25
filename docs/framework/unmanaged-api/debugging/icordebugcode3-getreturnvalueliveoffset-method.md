---
title: ICorDebugCode3::GetReturnValueLiveOffset 方法
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugCode3.GetReturnValueLiveOffset
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode3::GetReturnValueLiveOffset
helpviewer_keywords:
- ICorDebugCode3::GetReturnValueLiveOffset method [.NET Framework debugging]
- GetReturnValueLiveOffset method [.NET Framework debugging]
ms.assetid: 8c2ff5d8-8c04-4423-b1e1-e1c8764b36d3
topic_type:
- apiref
ms.openlocfilehash: 6153ebf24ae939a50d71cad2d4323090aa905851
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720811"
---
# <a name="icordebugcode3getreturnvalueliveoffset-method"></a>ICorDebugCode3::GetReturnValueLiveOffset 方法

針對指定的 IL 位移，取得應放置中斷點的原生位移，讓偵錯工具可以從函式取得傳回值。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetReturnValueLiveOffset(  
    [in] ULONG32 ILoffset,  
    [in] ULONG32 bufferSize,
    [out] ULONG32 *pFetched,
    [out, size_is(buffersize), length_is(*pFetched)] ULong32 pOffsets[]  
);  
```  
  
## <a name="parameters"></a>參數  

 `ILoffset`  
 IL 位移。 它必須是函式呼叫網站，否則函式呼叫將會失敗。  
  
 `bufferSize`  
 可儲存的位元組數目 `pOffsets` 。  
  
 `pFetched`  
 實際傳回之位移數目的指標。 通常，其值為1，但單一 IL 指令可以對應至多個 `CALL` 元件指令。  
  
 `pOffsets`  
 原生位移的陣列。 通常 `pOffsets` 會包含單一位移，雖然單一 IL 指令可對應至多個元件指令的多個對應 `CALL` 。  
  
## <a name="remarks"></a>備註  

 這個方法會搭配 [ICorDebugILFrame3：： GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) 方法使用，以取得傳回參考型別之方法的傳回值。 將 IL 位移傳遞給這個方法的函式呼叫網站，會傳回一或多個原生位移。 然後，偵錯工具可以在函式中的這些原生位移上設定中斷點。 當偵錯工具到達其中一個中斷點時，您可以將傳遞給這個方法的相同 IL 位移傳遞給 [ICorDebugILFrame3：： GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) 方法，以取得傳回值。 偵錯工具接著應清除其設定的所有中斷點。  
  
> [!WARNING]
> `ICorDebugCode3::GetReturnValueLiveOffset`和[ICorDebugILFrame3：： GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md)方法可讓您只取得參考型別的傳回值資訊。 從實值型別中取出傳回值資訊 (也就是說，不支援衍生自) 的所有類型 <xref:System.ValueType> 。  
  
 函數會傳回 `HRESULT` 下表所示的值。  
  
|`HRESULT` 值|描述|  
|---------------------|-----------------|  
|`S_OK`|成功。|  
|`CORDBG_E_INVALID_OPCODE`|給定的 IL 位移網站不是呼叫指令，或函數傳回 `void` 。|  
|`CORDBG_E_UNSUPPORTED`|給定的 IL 位移是適當的呼叫，但不支援取得傳回值的傳回型別。|  
  
 `ICorDebugCode3::GetReturnValueLiveOffset`只有 x86 型和 AMD64 系統才能使用此方法。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [GetReturnValueForILOffset 方法](icordebugilframe3-getreturnvalueforiloffset-method.md)
- [ICorDebugCode3 介面](icordebugcode3-interface.md)
