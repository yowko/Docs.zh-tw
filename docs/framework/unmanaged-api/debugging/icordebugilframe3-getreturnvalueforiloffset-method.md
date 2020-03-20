---
title: ICorDebugILFrame3::GetReturnValueForILOffset 方法
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
api_name:
- ICorDebugILFrame3.GetReturnValueForILOffset
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 06522727-5f64-4391-9331-11386883c352
topic_type:
- apiref
ms.openlocfilehash: 0d1ef6c1369fd399f5b36b24a21c4b5d7f1e80fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178820"
---
# <a name="icordebugilframe3getreturnvalueforiloffset-method"></a>ICorDebugILFrame3::GetReturnValueForILOffset 方法
獲取封裝函數傳回值的"ICorDebugValue"物件。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetReturnValueForILOffset(  
    ULONG32 ILoffset,
    [out] ICorDebugValue **ppReturnValue  
);  
```  
  
## <a name="parameters"></a>參數  
 `ILOffset`  
 IL 偏移量。 請參閱＜備註＞一節。  
  
 `ppReturnValue`  
 指向"ICorDebugValue"介面物件的位址的指標，該物件提供有關函式呼叫的傳回值的資訊。  
  
## <a name="remarks"></a>備註  
 此方法與[ICorDebugCode3：：getReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md)方法一起使用，以獲得方法的傳回值。 對於傳回值被忽略的方法，它特別有用，如下兩個代碼示例所示。 第一個示例調用<xref:System.Int32.TryParse%2A?displayProperty=nameWithType>方法，但忽略該方法的傳回值。  
  
 [!code-csharp[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv1.cs#1)]
 [!code-vb[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv1.vb#1)]  
  
 第二個示例說明了調試中更常見的問題。 由於方法在方法調用中用作參數，因此僅當調試器通過調用的方法時，才能訪問其傳回值。 在許多情況下，尤其是在外部庫中定義被調用的方法時，這是不可能的。  
  
 [!code-csharp[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv2.cs#2)]
 [!code-vb[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv2.vb#2)]  
  
 如果將[ICorDebugCode3：：獲取返回ValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md)方法 IL 偏移傳遞給函式呼叫網站，它將返回一個或多個本機偏移。 然後，調試器可以在函數中的這些本機偏移設置中斷點。 當調試器到達其中一個中斷點時，可以傳遞傳遞給此方法的相同 IL 偏移量以獲得傳回值。 然後，調試器應清除它設置的所有中斷點。  
  
> [!WARNING]
> [ICorDebugCode3：：獲取回歸價值即時偏移法](icordebugcode3-getreturnvalueliveoffset-method.md)和方法`ICorDebugILFrame3::GetReturnValueForILOffset`允許您僅獲取參考類型的傳回值資訊。 不支援從數值型別（即派生自<xref:System.ValueType>的所有類型）檢索傳回值資訊。  
  
 `ILOffset`參數指定的 IL 偏移量應位於函式呼叫網站，調試器應在[ICorDebugCode3：getReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md)方法為同一 IL 偏移量返回的本機偏移器處的中斷點設置處停止。 如果調試器未停止在指定 IL 偏移的正確位置，則 API 將失敗。  
  
 如果函式呼叫不傳回值，API 將失敗。  
  
 該方法`ICorDebugILFrame3::GetReturnValueForILOffset`僅適用于基於 x86 和 AMD64 的系統。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [GetReturnValueLiveOffset 方法](icordebugcode3-getreturnvalueliveoffset-method.md)
- [ICorDebugILFrame3 介面](icordebugilframe3-interface.md)
