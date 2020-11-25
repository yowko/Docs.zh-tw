---
title: ICorDebugGuidToTypeEnum::Next 方法
ms.date: 03/30/2017
api_name:
- ICorDebugGuidToTypeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGuidToTypeEnum::Next
helpviewer_keywords:
- ICorDebugGuidToTypeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: c9937666-8e18-484d-9fe0-b9ac95199530
topic_type:
- apiref
ms.openlocfilehash: 68f548705213da7d715ae569116abae0cd24129d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705653"
---
# <a name="icordebugguidtotypeenumnext-method"></a>ICorDebugGuidToTypeEnum::Next 方法

取得將 Guid 對應至類型資訊的指定 [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) 實例數目。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched] CorDebugGuidToTypeMapping values[  ],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>參數  

 `celt`  
 在要抓取的 GUID 對類型對應物件數目。  
  
 `values`  
 擴展指標的陣列，每個指標都會指向 [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) 物件，該物件會將 Windows 執行階段 GUID 對應至其對應的 ICorDebugType 物件。  
  
 `pceltFetched`  
 擴展實際傳回的 [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) 物件數目指標 `values` 。  
  
## <a name="remarks"></a>備註  
  
## <a name="requirements"></a>需求  

 **平臺：** Windows 執行階段  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugGuidToTypeEnum 介面](icordebugguidtotypeenum-interface.md)
- [偵錯介面](debugging-interfaces.md)
