---
title: ICorDebugILFrame4::EnumerateLocalVariablesEx 方法
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.EnumerateLocalVariablesEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6f60aae6-70ec-4c4c-963a-138df98c4668
topic_type:
- apiref
ms.openlocfilehash: 341a86f4c1c8367f979e193a6284bf89f1b03ca0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178795"
---
# <a name="icordebugilframe4enumeratelocalvariablesex-method"></a>ICorDebugILFrame4::EnumerateLocalVariablesEx 方法
[.NET Framework 4.5.2 與更新版本提供支援]  
  
 在框架中取得區域變數的列舉程式，並選擇性地包含在分析工具 ReJIT 檢測中加入的變數。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT EnumerateLocalVariablesEx(  
   [in] ILCodeKind flags,
   [out] ICorDebugValueEnum **ppValueEnum  
);  
```  
  
## <a name="parameters"></a>參數  
 `flags`  
 [在][ILCodeKind](ilcodekind-enumeration.md)枚舉成員，用於指定在探測器 ReJIT 檢測中添加的變數是否包含在幀中。  
  
 `ppValueEnum`  
 [出]指向"ICorDebugValueEnum"物件的位址的指標，該物件是此幀中區域變數的枚舉器。  
  
## <a name="remarks"></a>備註  
 此方法類似于[枚舉本地變數](icordebugilframe-enumeratelocalvariables-method.md)方法，只不過它可以選擇訪問探測器 ReJIT 檢測中添加的變數。 設置為`flags``ILCODE_ORIGINAL_IL`等效于調用[ICorDebugILFrame：：枚舉本地變數](icordebugilframe-enumeratelocalvariables-method.md)。 將 `flags` 設為 `ILCODE_REJIT_IL` 可允許偵錯工具存取加入在分析工具 ReJIT 檢測中的區域變數。 如果未檢測中繼語言 (IL)，則列舉空白，且該方法會傳回 `S_OK`。  
  
 列舉程式可能不會包含執行中方法的所有區域變數，因為有些變數可能不在使用中。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugILFrame4 介面](icordebugilframe4-interface.md)
- [偵錯介面](debugging-interfaces.md)
- [ReJIT：指南](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
