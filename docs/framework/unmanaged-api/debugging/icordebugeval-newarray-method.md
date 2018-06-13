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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 38b00d903fdd7301415a8df7642e12366178fd10
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413936"
---
# <a name="icordebugevalnewarray-method"></a>ICorDebugEval::NewArray 方法
配置的指定項目類型和維度的新陣列。  
  
 這個方法是.NET Framework 2.0 版中已過時。 使用[icordebugeval2:: Newparameterizedarray](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md)改為。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT NewArray (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [in] ULONG32            rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
#### <a name="parameters"></a>參數  
 `elementType`  
 [in]CorElementType 列舉，指定陣列的項目類型的值。  
  
 `pElementClass`  
 [in]指定項目的類別 ICorDebugClass 物件的指標。 這個值可能是 null，如果項目型別是基本型別。  
  
 `rank`  
 [in]陣列維度的數目。 在.NET Framework 2.0 中，這個值必須是 1。  
  
 `dims`  
 [in]單位為位元組陣列的每個維度大小。  
  
 `lowBounds`  
 [in] 選用。 陣列的每個維度的下限。 如果省略此值，則會假設每個維度下限為零。  
  
## <a name="remarks"></a>備註  
 陣列一律建立所在的執行緒目前正在執行的應用程式定義域中。  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** 1.1、 1.0
