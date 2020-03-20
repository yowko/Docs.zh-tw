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
ms.openlocfilehash: 34d543dd76de05bdf55d8187cf192455d1387a9f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178946"
---
# <a name="icordebugcode3getreturnvalueliveoffset-method"></a>ICorDebugCode3::GetReturnValueLiveOffset 方法
對於指定的 IL 偏移量，獲取應放置中斷點的本機偏移，以便調試器可以從函數獲取傳回值。  
  
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
 IL 偏移量。 它必須是函式呼叫網站，否則函式呼叫將失敗。  
  
 `bufferSize`  
 可用於存儲`pOffsets`的位元組數。  
  
 `pFetched`  
 指向實際返回的偏移量數的指標。 通常，其值為 1，但單個 IL 指令可以映射到`CALL`多個程式集指令。  
  
 `pOffsets`  
 本機偏移的陣列。 通常，`pOffsets`包含單個偏移量，儘管單個 IL 指令可以映射到多個映射到多個`CALL`程式集指令。  
  
## <a name="remarks"></a>備註  
 此方法與[ICorDebugILFrame3：：getReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md)方法一起使用，以獲取返回參考型別的方法的傳回值。 將 IL 偏移傳遞到函式呼叫網站到此方法返回一個或多個本機偏移。 然後，調試器可以在函數中的這些本機偏移設置中斷點。 當調試器到達其中一個中斷點時，您可以將傳遞給此方法的相同 IL 偏移傳遞給[ICorDebugILFrame3：：：：getReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md)方法以獲得傳回值。 然後，調試器應清除它設置的所有中斷點。  
  
> [!WARNING]
> 和`ICorDebugCode3::GetReturnValueLiveOffset` [ICorDebugILFrame3：：獲取回歸價值ForIL偏移](icordebugilframe3-getreturnvalueforiloffset-method.md)方法允許您僅獲取參考類型的傳回值資訊。 不支援從數值型別（即派生自<xref:System.ValueType>的所有類型）檢索傳回值資訊。  
  
 函數返回下表中顯示的`HRESULT`值。  
  
|`HRESULT` 值|描述|  
|---------------------|-----------------|  
|`S_OK`|成功。|  
|`CORDBG_E_INVALID_OPCODE`|給定的 IL 偏移網站不是呼叫指令，或函數返回`void`。|  
|`CORDBG_E_UNSUPPORTED`|給定的 IL 偏移量是適當的調用，但返回類型對於獲取傳回值不受支援。|  
  
 該方法`ICorDebugCode3::GetReturnValueLiveOffset`僅適用于基於 x86 和 AMD64 的系統。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [GetReturnValueForILOffset 方法](icordebugilframe3-getreturnvalueforiloffset-method.md)
- [ICorDebugCode3 介面](icordebugcode3-interface.md)
