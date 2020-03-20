---
title: ICorDebugILFrame4::GetLocalVariableEx 方法
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.GetCodeEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 0c8676f8-ca0d-4998-b64d-fefac7e38912
topic_type:
- apiref
ms.openlocfilehash: ee263e8c49cd6da7278bd2299557336629720d2f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178771"
---
# <a name="icordebugilframe4getlocalvariableex-method"></a>ICorDebugILFrame4::GetLocalVariableEx 方法
[.NET Framework 4.5.2 與更新版本提供支援]  
  
 從此中繼語言 (IL) 堆疊框架中取得指定區域變數的值，並選擇是否要存取加入分析工具 ReJIT 測試設備中的變數。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetLocalVariableEx(  
   [in] ILCodeKind flags,
   [in] DWORD dwIndex,
   [out] ICorDebugValue **ppValue  
);  
```  
  
## <a name="parameters"></a>參數  
 `flags`  
 [在][ILCodeKind](ilcodekind-enumeration.md)枚舉成員，用於指定在探測器 ReJIT 檢測中添加的變數是否包含在幀中。  
  
 `dwIndex`  
 [in] IL 堆疊框架中之區域變數的索引。  
  
 `ppValue`  
 [出]指向表示檢索值的"ICorDebugValue"物件位址的指標。  
  
## <a name="remarks"></a>備註  
 此方法類似于[GetLocalvariable](icordebugilframe-getlocalvariable-method.md)方法，只不過它可以選擇訪問在探測器 ReJIT 檢測中添加的變數。 使用`flags`的值`ILCODE_ORIGINAL_IL`調用此方法等效于調用[GetLocalvariable](icordebugilframe-getlocalvariable-method.md);如果使用其他區域變數檢測該方法，則無法訪問這些變數。 `ILCODE_REJIT_IL` 允許偵錯程式存取加入分析工具 ReJIT 測試設備中的區域變數。 若測試設備不是 IL，此方法會傳回 `E_INVALIDARG`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugILFrame4 介面](icordebugilframe4-interface.md)
- [偵錯介面](debugging-interfaces.md)
- [ReJIT：指南](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
