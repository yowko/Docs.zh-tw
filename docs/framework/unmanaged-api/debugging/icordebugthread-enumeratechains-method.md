---
title: "ICorDebugThread::EnumerateChains 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8e6a9637edb4a846b4d10dd6565533a9219ad558
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthreadenumeratechains-method"></a>ICorDebugThread::EnumerateChains 方法
ICorDebugChainEnum 列舉值，其中包含這個 ICorDebugThread 物件中的所有堆疊鏈結中取得的介面指標。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT EnumerateChains (  
    [out] ICorDebugChainEnum **ppChains  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppChains`  
 [out]位址指標`ICorDebugChainEnum`鏈結這個執行緒開始作用中 （也就是最新的） 鏈結中的物件，可讓所有堆疊的列舉。  
  
## <a name="remarks"></a>備註  
 堆疊鏈結代表執行緒的實際呼叫堆疊。 在下列情況下建立堆疊鏈結界限：  
  
-   管理至 unmanaged 或 unmanaged--受管理的轉換。  
  
-   內容切換。  
  
-   A 劫持使用者執行緒偵錯工具。  
  
 簡單案例中的單一內容中執行純粹是 managed 程式碼的執行緒，執行緒與堆疊鏈結之間會有一對一的對應。  
  
 偵錯工具可能想要重新排列成邏輯呼叫堆疊的所有執行緒的實際呼叫堆疊。 這會牽涉到排序依據其呼叫端/被呼叫端的關聯性的所有執行緒的鏈結，並且重新分組。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
