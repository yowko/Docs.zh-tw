---
title: ICorDebugEval2::NewParameterizedObject 方法
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedObject
helpviewer_keywords:
- NewParameterizedObject method [.NET Framework debugging]
- ICorDebugEval2::NewParameterizedObject method [.NET Framework debugging]
ms.assetid: 3d705463-e640-4249-8036-4e8206d03cfe
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aae5f4c79acd6f92d42c2890ba64fa66e1b4bfbe
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753597"
---
# <a name="icordebugeval2newparameterizedobject-method"></a>ICorDebugEval2::NewParameterizedObject 方法
具現化新的參數化的型別物件，並呼叫物件的建構函式方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT NewParameterizedObject (  
    [in] ICorDebugFunction     *pConstructor,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a>參數  
 `pConstructor`  
 [in]ICorDebugFunction 物件，表示要具現化物件的建構函式指標。  
  
 `nTypeArgs`  
 [in]傳遞的類型引數數目。  
  
 `ppTypeArgs`  
 [in]指標的陣列，其中每一個指向 ICorDebugType 物件，表示要具現化的物件型別引數。  
  
 `nArgs`  
 [in]引數傳遞至建構函式。  
  
 `ppArgs`  
 [in]指標的陣列，其中每一個指向 ICorDebugValue 物件，表示傳遞至建構函式的引數值。  
  
## <a name="remarks"></a>備註  
 物件的建構函式可能需要<xref:System.Type>參數。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
