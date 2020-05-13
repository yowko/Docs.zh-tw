---
title: ICorDebugThread::EnumerateChains 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread.EnumerateChains
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::EnumerateChains
helpviewer_keywords:
- EnumerateChains method [.NET Framework debugging]
- ICorDebugThread::EnumerateChains method [.NET Framework debugging]
ms.assetid: ec00bc21-117e-4acd-9301-2cfafd5be8d3
topic_type:
- apiref
ms.openlocfilehash: 711fccd65379bc3e5e178869e7220dd84fd07fbe
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379708"
---
# <a name="icordebugthreadenumeratechains-method"></a>ICorDebugThread::EnumerateChains 方法
取得 ICorDebugChainEnum 列舉值的介面指標，其中包含這個 ICorDebugThread 物件中的所有堆疊鏈。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumerateChains (  
    [out] ICorDebugChainEnum **ppChains  
);  
```  
  
## <a name="parameters"></a>參數  
 `ppChains`  
 脫銷物件位址的指標 `ICorDebugChainEnum` ，允許在此執行緒中列舉所有堆疊鏈，從作用中（也就是最新的）鏈開始。  
  
## <a name="remarks"></a>備註  
 堆疊鏈代表執行緒的實體呼叫堆疊。 下列情況會建立堆疊鏈界限：  
  
- 受控對非受控或未受管理的轉換。  
  
- 內容切換。  
  
- 使用者執行緒的偵錯工具劫持。  
  
 在簡單的案例中，如果是在單一內容中執行純粹受控程式碼的執行緒，則執行緒與堆疊鏈之間會有一對一的對應關係。  
  
 偵錯工具可能會想要將所有線程的實體呼叫堆疊重新排列為邏輯呼叫堆疊。 這牽涉到以呼叫端/被呼叫端的關聯性來排序所有線程的鏈，並加以 regrouping。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
