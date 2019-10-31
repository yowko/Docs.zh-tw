---
title: ICorDebugStringValue::GetString 方法
ms.date: 03/30/2017
api_name:
- ICorDebugStringValue.GetString
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStringValue::GetString
helpviewer_keywords:
- ICorDebugStringValue::GetString method [.NET Framework debugging]
- GetString method, ICorDebugStringValue interface [.NET Framework debugging]
ms.assetid: 2b94bda7-09ee-435d-91b9-c4e31af1896c
topic_type:
- apiref
ms.openlocfilehash: c4b01b2c346d3173b2a5ecc144474d7fb1e6dce5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138977"
---
# <a name="icordebugstringvaluegetstring-method"></a>ICorDebugStringValue::GetString 方法
取得此 ICorDebugStringValue 所參考的字串。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetString (  
    [in] ULONG32    cchString,  
    [out] ULONG32   *pcchString,  
    [out, size_is(cchString), length_is(*pcchString)]   
        WCHAR       szString[]  
);  
```  
  
## <a name="parameters"></a>參數  
 `cchString`  
 [in] `szString` 陣列的大小。  
  
 `pcchString`  
 脫銷`szString` 陣列中傳回的字元數指標。  
  
 `szString`  
 脫銷儲存已抓取字串的陣列。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
