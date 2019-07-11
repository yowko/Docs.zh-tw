---
title: ICorDebugEval2::NewParameterizedObjectNoConstructor 方法
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedObjectNoConstructor
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedObjectNoConstructor
helpviewer_keywords:
- NewParameterizedObjectNoConstructor method [.NET Framework debugging]
- ICorDebugEval2::NewParameterizedObjectNoConstructor method [.NET Framework debugging]
ms.assetid: f15b5b78-94f4-4eb9-b3b3-a621272f357c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e4434f5d0eaa45c9cfcbadb20b29564f0643a2dc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754442"
---
# <a name="icordebugeval2newparameterizedobjectnoconstructor-method"></a>ICorDebugEval2::NewParameterizedObjectNoConstructor 方法
產生指定類別的新參數化型的別物件，而不會嘗試呼叫建構函式方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT NewParameterizedObjectNoConstructor (  
    [in] ICorDebugClass        *pClass,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[]  
);  
```  
  
## <a name="parameters"></a>參數  
 `pClass`  
 [in]ICorDebugClass 物件，表示要具現化物件類別的指標。  
  
 `nTypeArgs`  
 [in]傳遞的類型引數數目。  
  
 `ppTypeArgs`  
 [in]指標的陣列，其中每一個指向 ICorDebugType 物件，表示要具現化的物件型別引數。  
  
## <a name="remarks"></a>備註  
 `NewParameterizedObjectNoConstructor`方法將會失敗，如果型別引數數目不正確或錯誤類型的類型引數會傳遞。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
