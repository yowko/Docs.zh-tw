---
title: ICorDebugEval::NewObject 方法
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewObject
helpviewer_keywords:
- NewObject method [.NET Framework debugging]
- ICorDebugEval::NewObject method [.NET Framework debugging]
ms.assetid: ce3025e8-defa-4c5e-8298-f49d71fa5736
topic_type:
- apiref
ms.openlocfilehash: a4d6dd0df9f38561ab5014d7ab65fde6793c9846
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729742"
---
# <a name="icordebugevalnewobject-method"></a>ICorDebugEval::NewObject 方法

配置新的物件實例，並呼叫指定的函式方法。  
  
 此方法在 .NET Framework 版本2.0 中已淘汰。 請改用 [ICorDebugEval2：： NewParameterizedObject](icordebugeval2-newparameterizedobject-method.md) 。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT NewObject (  
    [in] ICorDebugFunction  *pConstructor,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a>參數  

 `pConstructor`  
 在要呼叫的函式。  
  
 `nArgs`  
 [in] `ppArgs` 陣列的大小。  
  
 `ppArgs`  
 在ICorDebugValue 物件的陣列，每個物件都代表要傳遞給函式的引數。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：** 1.1、1。0  
  
## <a name="see-also"></a>另請參閱

- [NewParameterizedObject 方法](icordebugeval2-newparameterizedobject-method.md)
