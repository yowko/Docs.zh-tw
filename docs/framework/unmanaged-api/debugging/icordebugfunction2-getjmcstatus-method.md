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
ms.openlocfilehash: 747f165a98dfd1264ea58d61aaa1615c6d71e073
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726285"
---
# <a name="icordebugfunction2getjmcstatus-method"></a>ICorDebugFunction2::GetJMCStatus 方法

取得值，這個值會指出這個 ICorDebugFunction2 物件所代表的函式是否標記為使用者程式碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetJMCStatus (  
    [out] BOOL   *pbIsJustMyCode  
);  
```  
  
## <a name="parameters"></a>參數  

 `pbIsJustMyCode`  
 擴展布林值的指標， `true` 如果這個函式標示為使用者程式碼，則為，否則值為 `false` 。  
  
## <a name="remarks"></a>備註  

 如果無法進行調試所表示的函式 `ICorDebugFunction2` ， `pbIsJustMyCode` 則一律為 `false` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
