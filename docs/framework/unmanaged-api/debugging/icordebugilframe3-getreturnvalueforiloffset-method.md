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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5832ec095ea0e96327f6a9636193da9c0c8a5dd2
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988262"
---
# <a name="icordebugilframe3getreturnvalueforiloffset-method"></a>ICorDebugILFrame3::GetReturnValueForILOffset 方法
取得 "ICorDebugValue" 物件, 它會封裝函式的傳回值。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetReturnValueForILOffset(  
    ULONG32 ILoffset,   
    [out] ICorDebugValue **ppReturnValue  
);  
```  
  
## <a name="parameters"></a>參數  
 `ILOffset`  
 IL 位移。 請參閱＜備註＞一節。  
  
 `ppReturnValue`  
 「ICorDebugValue」介面物件位址的指標, 提供函式呼叫傳回值的相關資訊。  
  
## <a name="remarks"></a>備註  
 這個方法會與[ICorDebugCode3:: GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)方法搭配使用, 以取得方法的傳回值。 這在忽略傳回值的方法中特別有用, 如下列兩個程式碼範例所示。 第一個範例會呼叫<xref:System.Int32.TryParse%2A?displayProperty=nameWithType>方法, 但會忽略方法的傳回值。  
  
 [!code-csharp[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv1.cs#1)]
 [!code-vb[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv1.vb#1)]  
  
 第二個範例說明更常見的調試問題。 因為方法是當做方法呼叫中的引數使用, 所以只有在偵錯工具逐步執行被呼叫的方法時, 才可存取它的傳回值。 在許多情況下, 尤其是在外部程式庫中定義被呼叫的方法時, 這是不可能的。  
  
 [!code-csharp[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv2.cs#2)]
 [!code-vb[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv2.vb#2)]  
  
 如果您將[ICorDebugCode3:: GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)方法傳遞至函式呼叫網站的 IL 位移, 它會傳回一或多個原生位移。 然後偵錯工具可以在函式中的這些原生位移上設定中斷點。 當偵錯工具到達其中一個中斷點時, 您就可以傳遞傳遞給這個方法的相同 IL 位移, 以取得傳回值。 偵錯工具應該會清除它所設定的所有中斷點。  
  
> [!WARNING]
> [ICorDebugCode3:: GetReturnValueLiveOffset 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)和`ICorDebugILFrame3::GetReturnValueForILOffset`方法可讓您只取得參考型別的傳回值資訊。 不支援從實數值型別 (也就是衍生自<xref:System.ValueType>的所有類型) 中抓取傳回值資訊。  
  
 `ILOffset`參數所指定的 IL 位移應該位於函式呼叫位置, 而且偵錯工具應該在針對相同 IL 位移的[ICorDebugCode3:: GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)方法所傳回的原生位移上設定的中斷點停止。 如果偵錯工具未在指定 IL 位移的正確位置停止, API 將會失敗。  
  
 如果函式呼叫未傳回值, API 將會失敗。  
  
 `ICorDebugILFrame3::GetReturnValueForILOffset`方法僅適用于 x86 型和 AMD64 系統。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [GetReturnValueLiveOffset 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)
- [ICorDebugILFrame3 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)
