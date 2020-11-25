---
title: ICorDebugEval::NewObjectNoConstructor 方法
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewObjectNoConstructor
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewObjectNoConstructor
helpviewer_keywords:
- NewObjectNoConstructor method [.NET Framework debugging]
- ICorDebugEval::NewObjectNoConstructor method [.NET Framework debugging]
ms.assetid: 80d509ca-b5e3-4c46-9c14-800db73d9bf7
topic_type:
- apiref
ms.openlocfilehash: bb27ec755fb83dc71af7dd48b5ed6e7699436335
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729725"
---
# <a name="icordebugevalnewobjectnoconstructor-method"></a>ICorDebugEval::NewObjectNoConstructor 方法

配置指定類型的新物件實例，而不嘗試呼叫函式方法。  
  
 此方法在 .NET Framework 版本2.0 中已淘汰。 請改用 [ICorDebugEval2：： NewParameterizedObjectNoConstructor](icordebugeval2-newparameterizedobjectnoconstructor-method.md) 。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT NewObjectNoConstructor (  
    [in] ICorDebugClass     *pClass  
);  
```  
  
## <a name="parameters"></a>參數  

 `pClass`  
 在ICorDebugClass 物件的指標，該物件代表要具現化之物件的類型。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：** 1.1、1。0  
  
## <a name="see-also"></a>另請參閱

- [NewParameterizedObjectNoConstructor 方法](icordebugeval2-newparameterizedobjectnoconstructor-method.md)
