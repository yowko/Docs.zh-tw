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
ms.openlocfilehash: c7a1bf3cb10cbc8cdae2788b45e1badaf66a9dbd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178885"
---
# <a name="icordebugheapvalue2createhandle-method"></a>ICorDebugHeapValue2::CreateHandle 方法
為此 ICorDebugHeapValue2 物件表示的堆值創建指定類型的控制碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CreateHandle (  
    [in] CorDebugHandleType      type,
    [out] ICorDebugHandleValue   **ppHandle  
);  
```  
  
## <a name="parameters"></a>參數  
 `type`  
 [在]CorDebugHandleType 枚舉的值，用於指定要創建的控制碼的類型。  
  
 `ppHandle`  
 [出]指向 ICorDebugHandleValue 物件的位址的指標，該物件表示此堆值的新控制碼。  
  
## <a name="remarks"></a>備註  
 該控制碼將在與堆值關聯的應用程式域中創建，如果卸載應用程式域，該控制碼將變為無效。  
  
 對同一堆值的多次調用將創建多個控制碼。 由於控制碼會影響垃圾回收器的性能，調試器應將其限制為一次處於活動狀態的相對較少的控制碼（約 256）。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
