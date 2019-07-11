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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a6f0ed843f72d3f1e1575da15776a94a9097fd02
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771096"
---
# <a name="icordebugthreadenumeratechains-method"></a>ICorDebugThread::EnumerateChains 方法
ICorDebugChainEnum 列舉值，其中包含這個 ICorDebugThread 物件中的所有堆疊鏈結中取得的介面指標。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumerateChains (  
    [out] ICorDebugChainEnum **ppChains  
);  
```  
  
## <a name="parameters"></a>參數  
 `ppChains`  
 [out]位址指標`ICorDebugChainEnum`這個執行緒，開始使用 （也就是最新的） 鏈結中的鏈結，這個物件可讓所有堆疊的列舉型別。  
  
## <a name="remarks"></a>備註  
 堆疊鏈結代表執行緒的實體呼叫堆疊。 在下列情況下建立堆疊鏈結界限：  
  
- 在 managed 至 unmanaged 或非受控--受管理的轉換。  
  
- 內容切換。  
  
- 偵錯工具攔截使用者往來文章。  
  
 在單一的內容中執行純粹是 managed 程式碼的執行緒簡單案例中，執行緒和堆疊鏈結之間會有一對一的對應關係。  
  
 偵錯工具可能想要重新排列成邏輯呼叫堆疊的所有執行緒的實體呼叫堆疊。 這會牽涉到排序依據其呼叫端/被呼叫端的關聯性的所有執行緒的鏈結，並且重新分組。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
