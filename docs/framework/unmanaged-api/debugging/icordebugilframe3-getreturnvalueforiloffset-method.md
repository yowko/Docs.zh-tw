---
title: "ICorDebugILFrame3::GetReturnValueForILOffset 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- csharp
- vb
api_name: ICorDebugILFrame3.GetReturnValueForILOffset
api_location: mscordbi.dll
api_type: COM
ms.assetid: 06522727-5f64-4391-9331-11386883c352
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c58319de99bdd8d7cce0ea55ccb3140a31a39bd0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
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
  
#### <a name="parameters"></a>參數  
 `ILOffset`  
 IL 位移。 請參閱＜備註＞一節。  
  
 `ppReturnValue`  
 「 ICorDebugValue 」 介面物件，提供函式呼叫的傳回值的相關資訊的位址指標。  
  
## <a name="remarks"></a>備註  
 這個方法會用於[icordebugcode3:: Getreturnvalueliveoffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)方法來取得方法的傳回值。 它是在其傳回值會被忽略，如下列兩個程式碼範例所示的方法的情況下特別有用。 第一個範例會呼叫<xref:System.Int32.TryParse%2A?displayProperty=nameWithType>方法，但會忽略方法的傳回值。  
  
 [!code-csharp[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv1.cs#1)]
 [!code-vb[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv1.vb#1)]  
  
 第二個範例說明如何在偵錯更常見的問題。 當做方法呼叫中引數使用的方法，因為它的傳回值存取。 只有在偵錯工具逐步執行呼叫的方法時，才 在許多情況下，特別是當外部程式庫中定義呼叫的方法不可行。  
  
 [!code-csharp[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv2.cs#2)]
 [!code-vb[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv2.vb#2)]  
  
 如果您要傳入[icordebugcode3:: Getreturnvalueliveoffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) IL 位移函式呼叫位置的方法，它會傳回一或多個原生位移。 偵錯工具然後可以在這些原生位移函式中設定中斷點。 當偵錯工具叫用的其中一個中斷點時，然後您可以傳遞相同的 IL 位移傳遞到這個方法，以取得傳回值。 偵錯工具應再清除它所設定的所有中斷點。  
  
> [!WARNING]
>  [Icordebugcode3:: Getreturnvalueliveoffset 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)和`ICorDebugILFrame3::GetReturnValueForILOffset`方法可讓您取得只參考類型的傳回值資訊。 傳回值的資訊擷取實值類型 (也就是所有的型別衍生自<xref:System.ValueType>) 不支援。  
  
 所指定的 IL 位移`ILOffset`參數應該是位於函式呼叫位置，以及偵錯項目應該停止於中斷點，在所傳回的原生位移設定[icordebugcode3:: Getreturnvalueliveoffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)方法針對相同的 IL 位移。 如果指定的 IL 位移的正確位置在不停止偵錯項目時，API 將會失敗。  
  
 如果函式呼叫不會傳回值，此 API 將會失敗。  
  
 `ICorDebugILFrame3::GetReturnValueForILOffset`方法是僅可在 x86 型和 AMD64 系統。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [GetReturnValueLiveOffset 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)  
 [ICorDebugILFrame3 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)
