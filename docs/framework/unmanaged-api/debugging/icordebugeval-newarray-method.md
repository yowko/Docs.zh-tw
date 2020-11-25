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
ms.openlocfilehash: ef6cbe2cef3c52d9a4b47ff77e8aeb5159e89c76
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729755"
---
# <a name="icordebugevalnewarray-method"></a>ICorDebugEval::NewArray 方法

配置指定元素類型和維度的新陣列。  
  
 此方法在 .NET Framework 版本2.0 中已淘汰。 請改用 [ICorDebugEval2：： NewParameterizedArray](icordebugeval2-newparameterizedarray-method.md) 。  
  
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
 在CorElementType 列舉的值，這個值會指定陣列的元素類型。  
  
 `pElementClass`  
 在ICorDebugClass 物件的指標，該物件會指定元素的類別。 如果元素類型是基本類型，則這個值可能是 null。  
  
 `rank`  
 在陣列的維度數目。 在 .NET Framework 2.0 中，此值必須是1。  
  
 `dims`  
 在陣列每個維度的大小（以位元組為單位）。  
  
 `lowBounds`  
 [in] 選用。 陣列的每個維度下限。 如果省略此值，則會針對每個維度採用零下限。  
  
## <a name="remarks"></a>備註  

 陣列一律會建立線上程目前執行所在的應用程式域中。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：** 1.1、1。0
