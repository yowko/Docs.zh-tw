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
ms.openlocfilehash: 7ac90473a0bf15173683c45abc8e4a840ea7e733
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946428"
---
# <a name="icordebugilframe3getreturnvalueforiloffset-method"></a>ICorDebugILFrame3::GetReturnValueForILOffset 方法
取得封裝函式的傳回值的"ICorDebugValue 」 物件。  
  
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
 提供函式呼叫的傳回值的詳細資訊 」 ICorDebugValue 」 介面物件的位址指標。  
  
## <a name="remarks"></a>備註  
 這個方法會用於[ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)方法來取得方法的傳回值。 它是在方法的傳回值會被忽略，如下列兩個程式碼範例所示的情況下特別有用。 第一個範例會呼叫<xref:System.Int32.TryParse%2A?displayProperty=nameWithType>方法，但是忽略方法的傳回值。  
  
 [!code-csharp[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv1.cs#1)]
 [!code-vb[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv1.vb#1)]  
  
 第二個範例說明一個更常見的問題，在偵錯。 因為方法用來當做方法呼叫中引數，其傳回值只在偵錯工具逐步執行呼叫的方法時，才是可存取。 在許多情況下，特別是當被呼叫的方法定義在外部程式庫，這不可能。  
  
 [!code-csharp[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv2.cs#2)]
 [!code-vb[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv2.vb#2)]  
  
 如果您傳遞[ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) il 位移函式呼叫位置的方法，它會傳回一或多個原生位移。 偵錯工具則可以在這些函式中的原生位移上設定中斷點。 當偵錯工具叫用其中一個中斷點時，您可以將相同的 IL 位移傳遞給這個方法，以取得傳回值。 偵錯工具應接著清除它所設定的所有中斷點。  
  
> [!WARNING]
>  [ICorDebugCode3::GetReturnValueLiveOffset 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)和`ICorDebugILFrame3::GetReturnValueForILOffset`方法可讓您取得僅參考型別傳回值資訊。 傳回值資訊擷取實值型別 (也就是所有的型別衍生自<xref:System.ValueType>) 不支援。  
  
 所指定的 IL 位移`ILOffset`參數應該是在函式呼叫站台，以及偵錯項目應停止於中斷點，設定所傳回之原生位移[ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)方法相同的 IL 位移。 如果未在指定的 IL 位移的正確位置停止偵錯項目，則 API 將會失敗。  
  
 如果函式呼叫沒有傳回值，則 API 將會失敗。  
  
 `ICorDebugILFrame3::GetReturnValueForILOffset`方法是僅適用於 x86 架構和 AMD64 系統。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [GetReturnValueLiveOffset 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)
- [ICorDebugILFrame3 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)
