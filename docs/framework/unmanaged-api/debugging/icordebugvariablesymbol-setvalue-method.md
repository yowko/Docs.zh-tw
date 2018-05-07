---
title: ICorDebugVariableSymbol::SetValue Method
ms.date: 03/30/2017
ms.assetid: 4609418d-71fa-44bc-9618-4d529d25cabb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1ccdb78e522cb037821135c52bf762707f7de76c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugvariablesymbolsetvalue-method"></a>ICorDebugVariableSymbol::SetValue Method
指派位元組陣列的值給變數。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT SetValue(  
   [in] ULONG32 offset,  
   [in] DWORD threadID,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [in, size_is(cbValue)] BYTE pValue[]  
);  
```  
  
#### <a name="parameters"></a>參數  
 `offset`  
 [in] 變數中要設定該值的開始位移。 寫入物件中的成員欄位時，會使用這個參數。  
  
 `threadID`  
 [in] 執行緒識別碼，此執行緒的內容必須更新，以反映新的值。  
  
 `cbContext`  
 [in] 以位元組為單位的執行緒內容大小。  
  
 `context`  
 [in] 用來將值寫入的執行緒內容。  
  
 `cbValue`  
 [in] 以位元組為單位的 `pValue` 緩衝區大小。  
  
 `pValue`  
 [in] 包含要設定之值的緩衝區。  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  本方法只適用於 .NET 原生。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorDebugVariableSymbol 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
