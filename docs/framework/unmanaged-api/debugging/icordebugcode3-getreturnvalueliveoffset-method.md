---
title: "ICorDebugCode3::GetReturnValueLiveOffset 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorDebugCode3.GetReturnValueLiveOffset
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode3::GetReturnValueLiveOffset
helpviewer_keywords:
- ICorDebugCode3::GetReturnValueLiveOffset method [.NET Framework debugging]
- GetReturnValueLiveOffset method [.NET Framework debugging]
ms.assetid: 8c2ff5d8-8c04-4423-b1e1-e1c8764b36d3
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4516f2244b72bd4f254c5090b09d6d90579f1ae6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugcode3getreturnvalueliveoffset-method"></a>ICorDebugCode3::GetReturnValueLiveOffset 方法
針對指定的 IL 位移，取得原生位移中斷點放置的位置，讓偵錯工具可以從函式取得傳回值。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetReturnValueLiveOffset(  
    [in] ULONG32 ILoffset,  
    [in] ULONG32 bufferSize,   
    [out] ULONG32 *pFetched,   
    [out, size_is(buffersize), length_is(*pFetched)] ULong32 pOffsets[]  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ILoffset`  
 IL 位移。 它必須是函式呼叫位置或函式呼叫將會失敗。  
  
 `bufferSize`  
 可用來儲存的位元組數目`pOffsets`。  
  
 `pFetched`  
 實際傳回的位移數指標。 通常，其值為 1，但是單一的 IL 指令可以對應至多個`CALL`組譯碼指令。  
  
 `pOffsets`  
 原生位移的陣列。 一般而言，`pOffsets`包含單一的位移，但是單一的 IL 指令可以對應至多個對應至多個`CALL`組譯碼指令。  
  
## <a name="remarks"></a>備註  
 這個方法會用於[icordebugilframe3:: Getreturnvalueforiloffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)方法來取得傳回參考類型的方法的傳回值。 傳遞的 IL 位移站可將函式呼叫這個方法會傳回一或多個原生位移。 偵錯工具然後可以在這些原生位移函式中設定中斷點。 當偵錯工具叫用的其中一個中斷點時，然後您可以傳遞相同的 IL 位移傳遞到此方法以[icordebugilframe3:: Getreturnvalueforiloffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)方法來取得傳回值。 偵錯工具應再清除它所設定的所有中斷點。  
  
> [!WARNING]
>  `ICorDebugCode3::GetReturnValueLiveOffset`和[icordebugilframe3:: Getreturnvalueforiloffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)方法可讓您取得只參考類型的傳回值資訊。 傳回值的資訊擷取實值類型 (也就是所有的型別衍生自<xref:System.ValueType>) 不支援。  
  
 此函數會傳回`HRESULT`下表所示的值。  
  
|`HRESULT` 值|說明|  
|---------------------|-----------------|  
|`S_OK`|成功。|  
|`CORDBG_E_INVALID_OPCODE`|給定的 IL 位移的網站不是呼叫的指示，或函式會傳回`void`。|  
|`CORDBG_E_UNSUPPORTED`|指定的 IL 位移有適當的呼叫，但傳回型別不支援以取得傳回值。|  
  
 `ICorDebugCode3::GetReturnValueLiveOffset`方法是僅可在 x86 型和 AMD64 系統。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [GetReturnValueForILOffset 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)  
 [ICorDebugCode3 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
