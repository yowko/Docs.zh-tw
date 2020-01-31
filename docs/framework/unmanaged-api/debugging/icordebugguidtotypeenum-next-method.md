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
ms.openlocfilehash: 76cab0b8b5f16f24c62e31be2707c95c7e557034
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777634"
---
# <a name="icordebugguidtotypeenumnext-method"></a>ICorDebugGuidToTypeEnum::Next 方法
取得將 Guid 對應至類型資訊的指定[CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md)實例數目。  
  
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
 在要抓取的 GUID 型別對應物件的數目。  
  
 `values`  
 脫銷指標的陣列，其中每一個都會指向[CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md)物件，它會將 Windows 執行階段 GUID 對應至其相對應的 ICorDebugType 物件。  
  
 `pceltFetched`  
 脫銷`values`中實際傳回之[CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md)物件數目的指標。  
  
## <a name="remarks"></a>備註  
  
## <a name="requirements"></a>需求  
 **平臺：** Windows 執行階段  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugGuidToTypeEnum 介面](icordebugguidtotypeenum-interface.md)
- [偵錯介面](debugging-interfaces.md)
