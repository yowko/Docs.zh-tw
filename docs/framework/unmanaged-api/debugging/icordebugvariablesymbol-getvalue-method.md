---
title: ICorDebugVariableSymbol::GetValue Method
ms.date: 03/30/2017
ms.assetid: 90abece1-392e-4ade-94a1-30c75b0f7074
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 186d9eec0aa6ad9e327b1dd4d0f19e251c79ecf9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59147273"
---
# <a name="icordebugvariablesymbolgetvalue-method"></a>ICorDebugVariableSymbol::GetValue Method
取得變數的值做為位元組陣列。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetValue(  
   [in] ULONG32 offset,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [out] ULONG32 *pcbValue,  
   [out, size_is(cbValue), length_is(*pcbValue)] BYTE pValue[]  
);  
```  
  
## <a name="parameters"></a>參數  
 `offset`  
 [in] 要從中讀取值之變數的開始位移。 讀取物件中的成員欄位時，會使用這個參數。  
  
 `cbContext`  
 [in] 以位元組為單位的 `context` 引數大小。  
  
 `context`  
 [in] 用來讀取值的執行緒內容。  
  
 `cbValue`  
 [in] 以位元組為單位的 `pValue` 緩衝區大小。  
  
 `pcbValue`  
 [out] 實際寫入至 `pValue` 緩衝區的位元組數目。  
  
 `pValue`  
 [out] 包含變數值的位元組陣列。  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  這個方法僅適用於 .NET Native。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugVariableSymbol 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
