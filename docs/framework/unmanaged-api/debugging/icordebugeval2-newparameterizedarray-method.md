---
title: ICorDebugEval2::NewParameterizedArray 方法
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedArray
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedArray
helpviewer_keywords:
- ICorDebugEval2::NewParameterizedArray method [.NET Framework debugging]
- NewParameterizedArray method [.NET Framework debugging]
ms.assetid: 45efb8ba-c4de-4109-945f-e734d376b43c
topic_type:
- apiref
ms.openlocfilehash: 14274932461fa7a5278c9a09b421f50be098cb91
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729658"
---
# <a name="icordebugeval2newparameterizedarray-method"></a>ICorDebugEval2::NewParameterizedArray 方法

配置指定元素類型和維度的新陣列。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT NewParameterizedArray(  
    [in] ICorDebugType          *pElementType,  
    [in] ULONG32                rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
## <a name="parameters"></a>參數  

 `pElementType`  
 在ICorDebugType 物件的指標，代表儲存在陣列中的元素類型。  
  
 `rank`  
 在陣列的維度數目。 在 .NET Framework 2.0 版中，此值必須是1。  
  
 `dims`  
 在陣列每個維度的大小（以位元組為單位）。  
  
 `lowBounds`  
 [in] 選用。 陣列的每個維度下限。 如果省略此值，則會針對每個維度採用零下限。  
  
## <a name="remarks"></a>備註  

 陣列的元素可以是泛型型別的實例。 陣列一律會建立線上程目前執行所在的應用程式域中。 在 .NET Framework 2.0 中，的值 `rank` 必須是1。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
