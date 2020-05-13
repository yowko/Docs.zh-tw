---
title: ICorDebugFunction::GetModule 方法
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetModule
helpviewer_keywords:
- ICorDebugFunction::GetModule method [.NET Framework debugging]
- GetModule method, ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: 5031a5d3-2564-412a-9007-e36d4631308a
topic_type:
- apiref
ms.openlocfilehash: 41ad10fecca2ba1831d9e0d1120d3d1be0be92ad
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212954"
---
# <a name="icordebugfunctiongetmodule-method"></a>ICorDebugFunction::GetModule 方法
取得定義此函數的模組。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetModule (  
    [out] ICorDebugModule **ppModule  
);  
```  
  
## <a name="parameters"></a>參數  
 `ppModule`  
 脫銷ICorDebugModule 物件位址的指標，表示定義此函數的模組。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
