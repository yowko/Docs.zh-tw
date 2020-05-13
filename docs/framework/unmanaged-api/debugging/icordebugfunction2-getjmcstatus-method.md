---
title: ICorDebugFunction2::GetJMCStatus 方法
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.GetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::GetJMCStatus
helpviewer_keywords:
- ICorDebugFunction2::GetJMCStatus method [.NET Framework debugging]
- GetJMCStatus method [.NET Framework debugging]
ms.assetid: 840a71ed-bf5a-4f5e-8ed6-762222b34493
topic_type:
- apiref
ms.openlocfilehash: 56dc5f87b32b3aaa0bfbb69541d5a01ae26606ab
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213227"
---
# <a name="icordebugfunction2getjmcstatus-method"></a>ICorDebugFunction2::GetJMCStatus 方法
取得值，指出這個 ICorDebugFunction2 物件所代表的函式是否標示為使用者程式碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetJMCStatus (  
    [out] BOOL   *pbIsJustMyCode  
);  
```  
  
## <a name="parameters"></a>參數  
 `pbIsJustMyCode`  
 脫銷布林值的指標 `true` ，如果此函式標示為使用者程式碼，則為，否則值為 `false` 。  
  
## <a name="remarks"></a>備註  
 如果無法調試這個所表示的函式 `ICorDebugFunction2` ， `pbIsJustMyCode` 則一律為 `false` 。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
