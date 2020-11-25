---
title: ICorDebugController::EnumerateThreads 方法
ms.date: 03/30/2017
api_name:
- ICorDebugController.EnumerateThreads
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::EnumerateThreads
helpviewer_keywords:
- ICorDebugController::EnumerateThreads method [.NET Framework debugging]
- EnumerateThreads method [.NET Framework debugging]
ms.assetid: 73f536f6-4668-4a4a-b3e4-ac7df862d5be
topic_type:
- apiref
ms.openlocfilehash: f98118f9206d9ccd7dc9dc9a943500c7b4cd676a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732654"
---
# <a name="icordebugcontrollerenumeratethreads-method"></a>ICorDebugController::EnumerateThreads 方法

取得進程中使用中 managed 執行緒的列舉值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumerateThreads (  
    [out] ICorDebugThreadEnum **ppThreads  
);  
```  
  
## <a name="parameters"></a>參數  

 `ppThreads`  
 擴展"ICorDebugThreadEnum" 物件位址的指標，表示進程中所有作用中之 managed 執行緒的列舉值。  
  
## <a name="remarks"></a>備註  

 在分派 [ICorDebugManagedCallback：： CreateThread](icordebugmanagedcallback-createthread-method.md) 回呼之後，以及在分派 [ICorDebugManagedCallback：： ExitThread](icordebugmanagedcallback-exitthread-method.md) 回呼之前，會將執行緒視為使用中。 Managed 執行緒不一定要在它的堆疊上有任何受控框架。 即使在 [ICorDebugManagedCallback：： CreateProcess](icordebugmanagedcallback-createprocess-method.md) 回呼之前也可以列舉執行緒。 列舉自然會是空的。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
