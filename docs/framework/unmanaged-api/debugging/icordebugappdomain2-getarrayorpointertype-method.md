---
title: ICorDebugAppDomain2::GetArrayOrPointerType 方法
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain2.GetArrayOrPointerType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain2::GetArrayOrPointerType
helpviewer_keywords:
- GetArrayOrPointerType method [.NET Framework debugging]
- ICorDebugAppDomain2::GetArrayOrPointerType method [.NET Framework debugging]
ms.assetid: 97e493f5-3a62-4ec7-b42f-4af57bf71f57
topic_type:
- apiref
ms.openlocfilehash: 166f6bb50849df8550871958d7034fdf2a841abb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73089120"
---
# <a name="icordebugappdomain2getarrayorpointertype-method"></a>ICorDebugAppDomain2::GetArrayOrPointerType 方法
取得指定類型的陣列，或指定之類型的指標或參考。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetArrayOrPointerType (  
    [in]  CorElementType    elementType,  
    [in]  ULONG32           nRank,  
    [in]  ICorDebugType     *pTypeArg,  
    [out] ICorDebugType     **ppType  
);  
```  
  
## <a name="parameters"></a>參數  
 `elementType`  
 在CorElementType 列舉的值，指定要建立的基礎原生類型（陣列、指標或參考）。  
  
 `nRank`  
 在陣列的順位（也就是維度的數目）。 如果 `elementType` 指定指標或參考型別，這個值必須是0。  
  
 `pTypeArg`  
 在ICorDebugType 物件的指標，代表要建立的陣列、指標或參考的類型。  
  
 `ppType`  
 脫銷表示結構化陣列、指標類型或參考型別之 `ICorDebugType` 物件的位址指標。  
  
## <a name="remarks"></a>備註  
 *ElementType*的值必須是下列其中一項：  
  
- ELEMENT_TYPE_PTR  
  
- ELEMENT_TYPE_BYREF  
  
- ELEMENT_TYPE_ARRAY 或 ELEMENT_TYPE_SZARRAY  
  
 如果*elementType*的值是 ELEMENT_TYPE_PTR 或 ELEMENT_TYPE_BYREF，則*nRank*必須為零。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
