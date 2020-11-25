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
ms.openlocfilehash: 796c6aa4c42a037fe612b4b1ee5267a678cf5224
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729638"
---
# <a name="icordebugeval2newparameterizedobjectnoconstructor-method"></a>ICorDebugEval2::NewParameterizedObjectNoConstructor 方法

將指定類別的新參數化型別物件具現化，而不會嘗試呼叫函式方法。  
  
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
 在ICorDebugClass 物件的指標，代表要具現化之物件的類別。  
  
 `nTypeArgs`  
 在傳遞的型別引數數目。  
  
 `ppTypeArgs`  
 在指標的陣列，每個指標都會指向 ICorDebugType 物件，該物件代表要具現化之物件的型別引數。  
  
## <a name="remarks"></a>備註  

 `NewParameterizedObjectNoConstructor`如果傳遞的類型引數數目不正確或類型引數的類型不正確，此方法將會失敗。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
