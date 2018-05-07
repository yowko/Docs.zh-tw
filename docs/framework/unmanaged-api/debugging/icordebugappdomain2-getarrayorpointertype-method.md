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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb3f0ca6d930b22f30fe9bbc5b5a04bf1e034f34
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugappdomain2getarrayorpointertype-method"></a>ICorDebugAppDomain2::GetArrayOrPointerType 方法
取得指定的型別，或是指標或參考指定之類型的陣列。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetArrayOrPointerType (  
    [in]  CorElementType    elementType,  
    [in]  ULONG32           nRank,  
    [in]  ICorDebugType     *pTypeArg,  
    [out] ICorDebugType     **ppType  
);  
```  
  
#### <a name="parameters"></a>參數  
 `elementType`  
 [in]指定基礎原生類型 （陣列、 指標或參考） 來建立 CorElementType 列舉值。  
  
 `nRank`  
 [in]陣列陣序 （亦即，維度數目）。 此值必須是 0，如果`elementType`指定指標或參考類型。  
  
 `pTypeArg`  
 [in]ICorDebugType 物件代表的類型陣列的指標、 指標或建立參考。  
  
 `ppType`  
 [out]位址指標`ICorDebugType`代表建構的陣列、 指標類型或參考的物件類型。  
  
## <a name="remarks"></a>備註  
 值*elementType*必須是下列其中之一：  
  
-   ELEMENT_TYPE_PTR  
  
-   ELEMENT_TYPE_BYREF  
  
-   ELEMENT_TYPE_ARRAY 或 ELEMENT_TYPE_SZARRAY  
  
 如果值*elementType* ELEMENT_TYPE_PTR 或 ELEMENT_TYPE_BYREF， *nRank*必須為零。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
