---
title: ICorDebugEval::NewArray 方法
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewArray
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewArray
helpviewer_keywords:
- NewArray method [.NET Framework debugging]
- ICorDebugEval::NewArray method [.NET Framework debugging]
ms.assetid: cc79a67d-5368-434d-a943-209db90491b9
topic_type:
- apiref
ms.openlocfilehash: ca0844e4d2b1cad65266d58c6cda74de203d1758
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137664"
---
# <a name="icordebugevalnewarray-method"></a>ICorDebugEval::NewArray 方法
配置指定之元素類型和維度的新陣列。  
  
 這個方法在 .NET Framework 版本2.0 中已過時。 請改用[ICorDebugEval2：： NewParameterizedArray](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md) 。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT NewArray (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [in] ULONG32            rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
## <a name="parameters"></a>參數  
 `elementType`  
 在CorElementType 列舉的值，指定陣列的元素類型。  
  
 `pElementClass`  
 在ICorDebugClass 物件的指標，指定元素的類別。 如果元素類型是基本類型，這個值可能是 null。  
  
 `rank`  
 在陣列的維度數目。 在 .NET Framework 2.0 中，此值必須是1。  
  
 `dims`  
 在陣列的每個維度大小（以位元組為單位）。  
  
 `lowBounds`  
 [in] 選用。 陣列的每個維度下限。 如果省略此值，則會假設每個維度的下限為零。  
  
## <a name="remarks"></a>備註  
 陣列一律會建立線上程目前執行所在的應用程式域中。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：** 1.1、1.0
