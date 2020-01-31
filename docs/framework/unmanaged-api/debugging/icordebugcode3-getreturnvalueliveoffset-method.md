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
ms.openlocfilehash: dc03365b72a5f3613402faf1aed44b5683e9892c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777830"
---
# <a name="icordebugcode3getreturnvalueliveoffset-method"></a>ICorDebugCode3::GetReturnValueLiveOffset 方法
針對指定的 IL 位移，取得應放置中斷點的原生位移，讓偵錯工具可以從函數取得傳回值。  
  
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
 可用來儲存 `pOffsets`的位元組數目。  
  
 `pFetched`  
 實際傳回之位移數目的指標。 通常，其值為1，但單一 IL 指令可以對應到多個 `CALL` 元件指令。  
  
 `pOffsets`  
 原生位移的陣列。 一般來說，`pOffsets` 包含單一位移，雖然單一 IL 指令可以對應至多個對應至多個 `CALL` 元件指令。  
  
## <a name="remarks"></a>備註  
 這個方法會與[ICorDebugILFrame3：： GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md)方法搭配使用，以取得傳回參考型別之方法的傳回值。 將 IL 位移傳遞給這個方法的函式呼叫網站，會傳回一或多個原生位移。 然後偵錯工具可以在函式中的這些原生位移上設定中斷點。 當偵錯工具到達其中一個中斷點時，您就可以將傳遞給這個方法的相同 IL 位移傳遞給[ICorDebugILFrame3：： GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md)方法，以取得傳回值。 偵錯工具應該會清除它所設定的所有中斷點。  
  
> [!WARNING]
> `ICorDebugCode3::GetReturnValueLiveOffset` 和[ICorDebugILFrame3：： GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md)方法可讓您只取得參考型別的傳回值資訊。 不支援從實數值型別（也就是衍生自 <xref:System.ValueType>的所有類型）中抓取傳回值資訊。  
  
 函數會傳回下表所示的 `HRESULT` 值。  
  
|`HRESULT` 值|描述|  
|---------------------|-----------------|  
|`S_OK`|成功。|  
|`CORDBG_E_INVALID_OPCODE`|給定的 IL 位移網站不是呼叫指示，或函數會傳回 `void`。|  
|`CORDBG_E_UNSUPPORTED`|給定的 IL 位移是適當的呼叫，但不支援傳回類型來取得傳回值。|  
  
 `ICorDebugCode3::GetReturnValueLiveOffset` 方法僅適用于 x86 型和 AMD64 系統。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [GetReturnValueForILOffset 方法](icordebugilframe3-getreturnvalueforiloffset-method.md)
- [ICorDebugCode3 介面](icordebugcode3-interface.md)
