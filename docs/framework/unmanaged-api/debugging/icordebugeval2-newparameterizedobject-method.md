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
ms.openlocfilehash: 5d01ab0b6b5d489b2181056129e22661a50108a3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084849"
---
# <a name="icordebugeval2newparameterizedobject-method"></a>ICorDebugEval2::NewParameterizedObject 方法
具現化新的參數化型別物件，並呼叫物件的函式方法。  
  
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
 在ICorDebugFunction 物件的指標，表示要具現化之物件的構造函式。  
  
 `nTypeArgs`  
 在傳遞的型別引數數目。  
  
 `ppTypeArgs`  
 在指標的陣列，其中每一個都會指向 ICorDebugType 物件，代表正在具現化之物件的型別引數。  
  
 `nArgs`  
 在傳遞至此函式的引數數目。  
  
 `ppArgs`  
 在指標的陣列，其中每一個都會指向 ICorDebugValue 物件，代表傳遞至此函式的引數值。  
  
## <a name="remarks"></a>備註  
 物件的函式可能會採用 <xref:System.Type> 參數。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
