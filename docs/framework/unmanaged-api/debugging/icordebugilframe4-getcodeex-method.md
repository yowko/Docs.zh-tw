---
title: ICorDebugILFrame4::GetCodeEx 方法
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.GetLocalVariableEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: aeda0e42-29ee-4ca8-9f21-ac4641677a62
topic_type:
- apiref
ms.openlocfilehash: ef2e4bc0caddd6b13c8dbe8edb59e0673519421b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178786"
---
# <a name="icordebugilframe4getcodeex-method"></a>ICorDebugILFrame4::GetCodeEx 方法
[.NET Framework 4.5.2 與更新版本提供支援]  
  
 取得此堆疊框架執行之程式碼的指標。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetCodeEx(  
   [in] ILCodeKind flags,
   [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a>參數  
 `flags`  
 [在][ILCodeKind](ilcodekind-enumeration.md)枚舉成員，用於指定探測器的 ReJIT 請求定義的中間語言 （IL） 是否包含在框架中。  
  
 `ppCode`  
 [出]指向"ICorDebugCode"物件位址的指標，該物件表示此堆疊幀正在執行的代碼。  
  
## <a name="remarks"></a>備註  
 此方法類似于[ICorDebugFrame：getCode](icordebugframe-getcode-method.md)方法，只不過它可以選擇訪問探測器的 ReJIT 請求定義的代碼。 使用`flags`的值`ILCODE_ORIGINAL_IL`調用此方法等效于調用[GetCode](icordebugframe-getcode-method.md)。如果檢測該方法，則無法訪問其 IL。 `ILCODE_REJIT_IL` 可讓偵錯工具存取分析工具的 ReJIT 要求所定義的 IL。 如果未檢測 IL ，`ppCode`則為**null，** 並且該方法返回`S_OK`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugILFrame4 介面](icordebugilframe4-interface.md)
- [偵錯介面](debugging-interfaces.md)
- [ReJIT：指南](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
