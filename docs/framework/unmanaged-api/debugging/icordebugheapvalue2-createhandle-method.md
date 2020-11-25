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
ms.openlocfilehash: 278120c6e1bc87a061a3f81f71bdb7b89cd421be
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726557"
---
# <a name="icordebugheapvalue2createhandle-method"></a>ICorDebugHeapValue2::CreateHandle 方法

針對這個 ICorDebugHeapValue2 物件所表示的堆積值，建立指定之類型的控制碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CreateHandle (  
    [in] CorDebugHandleType      type,
    [out] ICorDebugHandleValue   **ppHandle  
);  
```  
  
## <a name="parameters"></a>參數  

 `type`  
 在CorDebugHandleType 列舉的值，這個值會指定要建立之控制碼的類型。  
  
 `ppHandle`  
 擴展ICorDebugHandleValue 物件位址的指標，該物件表示這個堆積值的新控制碼。  
  
## <a name="remarks"></a>備註  

 系統會在與堆積值相關聯的應用程式域中建立控制碼，如果已卸載應用程式域，則會變成無效。  
  
 對相同堆積值的這個函式有多個呼叫會建立多個控制碼。 由於處理常式會影響垃圾收集行程的效能，因此偵錯工具應該將其本身限制為相對較少的控制碼數目， (大約每次使用中的 256) 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
