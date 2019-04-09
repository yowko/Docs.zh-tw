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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03ee275336d3ae71f63d82add694fe1308efbe8b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125928"
---
# <a name="icordebugcode3getreturnvalueliveoffset-method"></a>ICorDebugCode3::GetReturnValueLiveOffset 方法
指定的 IL 位移，取得原生位移的中斷點應放置的位置，讓偵錯工具可以從函式取得的傳回值。  
  
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
 IL 位移。 它必須是函式呼叫位置，或函式呼叫將會失敗。  
  
 `bufferSize`  
 可用來儲存的位元組數目`pOffsets`。  
  
 `pFetched`  
 實際傳回之位移數指標。 通常，其值為 1，不過一個 IL 指令可對應至多個`CALL`組譯碼指令。  
  
 `pOffsets`  
 原生位移陣列。 通常`pOffsets`包含單一位移，不過一個 IL 指令可對應至多個對應至多個`CALL`組譯碼指令。  
  
## <a name="remarks"></a>備註  
 這個方法會用於[ICorDebugILFrame3::GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)方法來取得傳回參考類型的方法的傳回值。 傳遞的 IL 位移到函式呼叫位置，這個方法會傳回一或多個原生位移。 偵錯工具則可以在這些函式中的原生位移上設定中斷點。 當偵錯工具叫用其中一個中斷點時，您可以將相同的 IL 位移傳遞給這個方法[ICorDebugILFrame3::GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)方法，以取得傳回值。 偵錯工具應接著清除它所設定的所有中斷點。  
  
> [!WARNING]
>  `ICorDebugCode3::GetReturnValueLiveOffset`並[ICorDebugILFrame3::GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)方法可讓您取得僅參考型別傳回值資訊。 傳回值資訊擷取實值型別 (也就是所有的型別衍生自<xref:System.ValueType>) 不支援。  
  
 此函數會傳回`HRESULT`下表所示的值。  
  
|`HRESULT` value|描述|  
|---------------------|-----------------|  
|`S_OK`|成功。|  
|`CORDBG_E_INVALID_OPCODE`|指定的 IL 位移的位置不是呼叫指令，或函式會傳回`void`。|  
|`CORDBG_E_UNSUPPORTED`|指定的 IL 位移是適當的呼叫，但傳回的型別不支援取得傳回值。|  
  
 `ICorDebugCode3::GetReturnValueLiveOffset`方法是僅適用於 x86 架構和 AMD64 系統。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [GetReturnValueForILOffset 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)
- [ICorDebugCode3 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
