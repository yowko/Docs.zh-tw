---
title: ICorDebugCode::GetFunction 方法
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetFunction
helpviewer_keywords:
- GetFunction method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetFunction method [.NET Framework debugging]
ms.assetid: c568b737-fdb2-4816-accd-051f5ab760f1
topic_type:
- apiref
ms.openlocfilehash: 99972c5840645c95b7b349daf2d8ea7173d0cc03
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674719"
---
# <a name="icordebugcodegetfunction-method"></a>ICorDebugCode::GetFunction 方法

取得與此 "ICorDebugCode" 相關聯的 "ICorDebugFunction"。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetFunction (  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
## <a name="parameters"></a>參數  

 `ppFunction`  
 擴展函數位址的指標。  
  
## <a name="remarks"></a>備註  

 `ICorDebugCode` 並 `ICorDebugFunction` 維護一對一的關聯性。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
