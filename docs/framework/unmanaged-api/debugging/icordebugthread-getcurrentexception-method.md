---
title: "ICorDebugThread::GetCurrentException 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.GetCurrentException
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::GetCurrentException
helpviewer_keywords:
- ICorDebugThread::GetCurrentException method [.NET Framework debugging]
- GetCurrentException method [.NET Framework debugging]
ms.assetid: 331ed465-a195-4359-8584-b82c6098b29b
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c18e2dfa68d425e5ec23d4573428018bc971f8b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthreadgetcurrentexception-method"></a>ICorDebugThread::GetCurrentException 方法
ICorDebugValue 物件，表示目前由 managed 程式碼擲回的例外狀況取得的介面指標。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetCurrentException (  
    [out] ICorDebugValue **ppExceptionObject  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppExceptionObject`  
 [out]位址指標`ICorDebugValue`物件，代表目前由擲回的例外狀況 managed 程式碼。  
  
## <a name="remarks"></a>備註  
 例外狀況物件將會存在直到結束擲回例外狀況的時間從`catch`區塊。 函式評估，ICorDebugEval 方法執行時，會清除在安裝程式的例外狀況物件，還原完成。  
  
 （例如，如果在篩選中，或在函式評估擲回例外狀況），可以巢狀例外狀況，因此可能會在單一執行緒上的多個未處理例外狀況。 `GetCurrentException`傳回最新的例外狀況。  
  
 例外狀況物件和型別可能會變更整個生命週期的例外狀況。 例如，擲回例外狀況的類型 x 之後，common language runtime (CLR) 可能會用盡記憶體，並將它升級記憶體不足例外狀況。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
