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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4f9d20eda8684a9a5ae43c6240d0f8a9722c4d97
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59076831"
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
 [in][ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md)列舉的成員，指定在分析工具 ReJIT 檢測中加入的變數是否包含在框架中。  
  
 `ppValueEnum`  
 [out]在此框架中區域變數的列舉值 」 ICorDebugValueEnum"物件的位址指標。  
  
## <a name="remarks"></a>備註  
 這個方法很類似[EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md)方法，但是它會選擇性地存取加入分析工具 ReJIT 檢測中的變數。 設定`flags`要`ILCODE_ORIGINAL_IL`相當於呼叫[icordebugilframe:: Enumeratelocalvariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md)。 將 `flags` 設為 `ILCODE_REJIT_IL` 可允許偵錯工具存取加入在分析工具 ReJIT 檢測中的區域變數。 如果未檢測中繼語言 (IL)，則列舉空白，且該方法會傳回 `S_OK`。  
  
 列舉程式可能不會包含執行中方法的所有區域變數，因為有些變數可能不在使用中。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugILFrame4 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [ReJIT:操作說明指南](https://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
