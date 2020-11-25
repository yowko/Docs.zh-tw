---
title: ICorDebugThread::GetCurrentException 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetCurrentException
helpviewer_keywords:
- ICorDebugThread::GetCurrentException method [.NET Framework debugging]
- GetCurrentException method [.NET Framework debugging]
ms.assetid: 331ed465-a195-4359-8584-b82c6098b29b
topic_type:
- apiref
ms.openlocfilehash: c21be7b062b7e2d4129bafabae004351442ab853
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728052"
---
# <a name="icordebugthreadgetcurrentexception-method"></a>ICorDebugThread::GetCurrentException 方法

取得 ICorDebugValue 物件的介面指標，該物件代表 managed 程式碼目前正在擲回的例外狀況。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetCurrentException (  
    [out] ICorDebugValue **ppExceptionObject  
);  
```  
  
## <a name="parameters"></a>參數  

 `ppExceptionObject`  
 擴展物件位址的指標 `ICorDebugValue` ，該物件代表 managed 程式碼目前擲回的例外狀況。  
  
## <a name="remarks"></a>備註  

 例外狀況物件將存在於擲回例外狀況的時間，直到區塊結束為止 `catch` 。 函數評估（由 ICorDebugEval 方法執行）將會清除安裝程式上的例外狀況物件，並在完成時將其還原。  
  
 例外狀況可以是嵌套 (例如，如果在篩選中擲回例外狀況，或在函式評估) 中擲回例外狀況，因此單一線程上可能會有多個未處理的例外狀況。 `GetCurrentException` 傳回最新的例外狀況。  
  
 例外狀況物件和類型可能會在例外狀況的整個存留期間變更。 例如，在擲回 x 類型的例外狀況之後，common language runtime (CLR) 可能會用盡記憶體，並將其升級為記憶體不足的例外狀況。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
