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
ms.openlocfilehash: 8b3f6ae92e39f5385bf29f8b29abbb1726136088
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724763"
---
# <a name="icordebugappdomain2getarrayorpointertype-method"></a>ICorDebugAppDomain2::GetArrayOrPointerType 方法

取得指定類型的陣列，或指定類型的指標或參考。  
  
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
 在CorElementType 列舉的值，這個值會指定要建立之陣列、指標或參考)  (基礎原生類型。  
  
 `nRank`  
 在排名 (也就是陣列的維度) 數目。 如果 `elementType` 指定指標或參考型別，則這個值必須是0。  
  
 `pTypeArg`  
 在ICorDebugType 物件的指標，代表要建立之陣列、指標或參考的型別。  
  
 `ppType`  
 擴展物件位址的指標， `ICorDebugType` 該物件表示所結構化的陣列、指標類型或參考型別。  
  
## <a name="remarks"></a>備註  

 *ElementType* 的值必須是下列其中一項：  
  
- ELEMENT_TYPE_PTR  
  
- ELEMENT_TYPE_BYREF  
  
- ELEMENT_TYPE_ARRAY 或 ELEMENT_TYPE_SZARRAY  
  
 如果 *elementType* 的值為 ELEMENT_TYPE_PTR 或 ELEMENT_TYPE_BYREF， *nRank* 必須為零。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
