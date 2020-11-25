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
ms.openlocfilehash: 8c91296bd4185fd98962d49f611a3cdcb5f0ad28
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729651"
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
 在ICorDebugFunction 物件的指標，代表要具現化之物件的函式。  
  
 `nTypeArgs`  
 在傳遞的型別引數數目。  
  
 `ppTypeArgs`  
 在指標的陣列，每個指標都會指向 ICorDebugType 物件，該物件代表要具現化之物件的型別引數。  
  
 `nArgs`  
 在傳遞至函式的引數數目。  
  
 `ppArgs`  
 在指標的陣列，每個指標都會指向代表傳遞給函式之引數值的 ICorDebugValue 物件。  
  
## <a name="remarks"></a>備註  

 物件的函式可能會採用 <xref:System.Type> 參數。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
