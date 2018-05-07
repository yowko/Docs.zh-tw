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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c7a95f09d1baebed65bae994550431d88ba0dfc9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugcontrollerterminate-method"></a>ICorDebugController::Terminate 方法
終止與指定的結束代碼的程序。  
  
> [!NOTE]
>  這個方法是 Win32 的包裝函式`TerminateProcess`函式。 因此，`Terminate`使用結束碼，在相同的方式來 Win32`TerminateProcess`函式會使用它。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Terminate (  
    [in] UINT exitCode  
);  
```  
  
#### <a name="parameters"></a>參數  
 `exitCode`  
 [in]結束代碼數字值。 Winbase.h 中定義之有效的數字值。  
  
## <a name="remarks"></a>備註  
 如果處理程序已停止時`Terminate`是呼叫，處理程序應該繼續使用[icordebugcontroller:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)方法以便偵錯工具會收到確認透過終止[Icordebugmanagedcallback:: Exitprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md)或[icordebugmanagedcallback:: Exitappdomain](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md)回呼。  
  
> [!NOTE]
>  由應用程式定義域不實作這個方法。 也就是說，不會實作在<xref:System.AppDomain>層級。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 
