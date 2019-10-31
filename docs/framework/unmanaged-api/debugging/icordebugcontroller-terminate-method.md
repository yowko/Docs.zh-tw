---
title: ICorDebugController::Terminate 方法
ms.date: 03/30/2017
api_name:
- ICorDebugController.Terminate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Terminate
helpviewer_keywords:
- Terminate method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Terminate method [.NET Framework debugging]
ms.assetid: 4275af0c-b5a7-4e4c-97c9-7e41f36b2dd8
topic_type:
- apiref
ms.openlocfilehash: fb8cfb2d1c5902ecd0d5858ef21ba48b65b12506
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125325"
---
# <a name="icordebugcontrollerterminate-method"></a>ICorDebugController::Terminate 方法
使用指定的結束代碼終止進程。  
  
> [!NOTE]
> 這個方法是 Win32 `TerminateProcess` 函數的包裝函式。 因此，`Terminate` 會以 Win32 `TerminateProcess` 函式使用的相同方式來使用結束代碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Terminate (  
    [in] UINT exitCode  
);  
```  
  
## <a name="parameters"></a>參數  
 `exitCode`  
 在表示結束代碼的數值。 有效的數值定義于 Winbase 中。  
  
## <a name="remarks"></a>備註  
 如果在呼叫 `Terminate` 時停止進程，則應該使用[ICorDebugController：： Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)方法繼續處理，讓偵錯工具能夠透過 ICorDebugManagedCallback 來接收終止確認[：：ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md)或[ICorDebugManagedCallback：： ExitAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md)回呼。  
  
> [!NOTE]
> 這個方法不是由應用程式域所執行。 也就是說，它不會在 <xref:System.AppDomain> 層級執行。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱
