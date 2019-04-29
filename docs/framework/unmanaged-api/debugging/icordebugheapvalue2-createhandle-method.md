---
title: ICorDebugHeapValue2::CreateHandle 方法
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue2.CreateHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue2::CreateHandle
helpviewer_keywords:
- CreateHandle method [.NET Framework debugging]
- ICorDebugHeapValue2::CreateHandle method [.NET Framework debugging]
ms.assetid: fbc418e8-fa22-420d-84ec-e0e1800db041
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 078dfd7162c250f0279b8bc372aeb39662aa0119
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61779882"
---
# <a name="icordebugheapvalue2createhandle-method"></a>ICorDebugHeapValue2::CreateHandle 方法
建立堆積值，這個 ICorDebugHeapValue2 物件所表示的指定類型的控制代碼。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CreateHandle (  
    [in] CorDebugHandleType      type,   
    [out] ICorDebugHandleValue   **ppHandle  
);  
```  
  
## <a name="parameters"></a>參數  
 `type`  
 [in]CorDebugHandleType 列舉，指定要建立的控制代碼的型別值。  
  
 `ppHandle`  
 [out]ICorDebugHandleValue 物件，表示此堆積值的新控制代碼的位址指標。  
  
## <a name="remarks"></a>備註  
 控制代碼會在堆積的值，與相關聯的應用程式定義域中建立，而且會變成無效，如果應用程式定義域卸載。  
  
 此函式相同的堆積值的多個呼叫會建立多個控制代碼。 控制代碼會影響記憶體回收行程的效能，因為偵錯工具應限制本身相對較小的數字，一次是作用中的控制代碼 (大約 256)。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
