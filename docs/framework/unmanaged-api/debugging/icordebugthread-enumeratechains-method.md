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
ms.openlocfilehash: 76b231f00651186518d3bccfafa5780f258c4f75
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688181"
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
 擴展物件位址的指標， `ICorDebugChainEnum` 該物件允許列舉這個執行緒中所有堆疊鏈的，從作用中的 (開始，也就是最新的) 鏈。  
  
## <a name="remarks"></a>備註  

 堆疊鏈表示執行緒的實體呼叫堆疊。 下列情況會建立堆疊鏈界限：  
  
- 受控對非受控或非受控對管理的轉換。  
  
- 內容切換。  
  
- 使用者執行緒的偵錯工具劫持。  
  
 在單一內容中執行單純 managed 程式碼的執行緒的簡單案例中，會線上程與堆疊鏈之間存在一對一的對應。  
  
 偵錯工具可能會想要將所有線程的實體呼叫堆疊重新排列成邏輯呼叫堆疊。 這會牽涉到依呼叫端/被呼叫端關聯性排序所有線程的鏈，並加以 regrouping。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
