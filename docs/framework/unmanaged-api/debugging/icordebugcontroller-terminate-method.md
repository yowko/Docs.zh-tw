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
ms.openlocfilehash: eade3fd5d946c44ae4a77c571f762709de3cef40
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976560"
---
# <a name="icordebugcontrollerterminate-method"></a>ICorDebugController::Terminate 方法
使用指定的結束代碼終止進程。  
  
> [!NOTE]
> 這個方法是 Win32 `TerminateProcess`函數的包裝函式。 因此， `Terminate`會以 Win32 `TerminateProcess`函數使用結束代碼的相同方式來使用它。  
  
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
 `Terminate`如果呼叫時停止進程，則應該使用[ICorDebugController：： Continue](icordebugcontroller-continue-method.md)方法繼續處理，讓偵錯工具透過[ICorDebugManagedCallback：： ExitProcess](icordebugmanagedcallback-exitprocess-method.md)或[ICorDebugManagedCallback：： ExitAppDomain](icordebugmanagedcallback-exitappdomain-method.md)回呼接收終止的確認。  
  
> [!NOTE]
> 這個方法不是由應用程式域所執行。 也就是說，它不會在<xref:System.AppDomain>層級上執行。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
