---
title: ICorDebugReferenceValue::IsNull 方法
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.IsNull
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::IsNull
helpviewer_keywords:
- IsNull method, ICorDebugReferenceValue interface [.NET Framework debugging]
- ICorDebugReferenceValue::IsNull method [.NET Framework debugging]
ms.assetid: 99e8c8d7-a1c0-47c8-9dbd-03e0b2bcb4d5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ed37e6eae3ec4f6e69215be6a42afe7fe86ff393
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768662"
---
# <a name="icordebugreferencevalueisnull-method"></a>ICorDebugReferenceValue::IsNull 方法
取得值，指出此 ICorDebugReferenceValue 是否為 null 值，在此情況下`ICorDebugReferenceValue`未指向物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT IsNull (  
    [out] BOOL   *pbNull  
);  
```  
  
## <a name="parameters"></a>參數  
 `pbNull`  
 [out]布林值的指標`true`如果這個`ICorDebugReferenceValue`物件是 null，否則`pbNull`是`false`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
