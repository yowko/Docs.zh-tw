---
title: ICorDebugRemote::DebugActiveProcessEx 方法
ms.date: 03/30/2017
api_name:
- ICorDebugRemote.DebugActiveProcessEx
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::DebugActiveProcessEx
helpviewer_keywords:
- ICorDebugRemote::DebugActiveProcessEx method [.NET Framework debugging]
- DebugActiveProcessEx method, ICorDebugRemote interface [.NET Framework debugging]
ms.assetid: b0df5c5d-9a2e-47bf-894c-6f8a9fe24a1f
topic_type:
- apiref
ms.openlocfilehash: b95e9f3a0d584511a2bcf156ed2c50a98f96d071
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379067"
---
# <a name="icordebugremotedebugactiveprocessex-method"></a>ICorDebugRemote::DebugActiveProcessEx 方法
在偵錯工具下的遠端電腦上啟動進程。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT DebugActiveProcessEx (  
    [in]  ICorDebugRemoteTarget *   pRemoteTarget,  
    [in]  DWORD                     dwProcessId,  
    [in]  BOOL                      fWin32Attach,  
    [out] ICorDebugProcess **       ppProcess  
);  
```  
  
## <a name="parameters"></a>參數  
 `pRemoteTarget`  
 在[ICorDebugRemoteTarget 介面](icordebugremotetarget-interface.md)的指標。 這個參數是用來判斷進程執行所在的電腦。  
  
 `id`  
 在要附加偵錯工具之進程的識別碼。  
  
 `win32Attach`  
 [in] `true`如果偵錯工具的行為應該是進程的 Win32 偵錯工具，並分派非受控回呼，則為，否則為 `false` 。  
  
 `ppProcess`  
 脫銷"ICorDebugProcess" 物件位址的指標，表示已附加偵錯工具的進程。  
  
## <a name="return-value"></a>傳回值  
 S_OK  
 已成功連接到遠端電腦上的進程。  
  
 E_FAIL (或其他 E_ 傳回碼)  
 無法附加至遠端電腦上的進程。  
  
## <a name="remarks"></a>備註  
 Silverlight 中不支援混合模式的調試。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：** 4.5、4、3.5 SP1  
  
## <a name="see-also"></a>請參閱

- [ICorDebugRemote 介面](icordebugremote-interface.md)
- [ICorDebug 介面](icordebug-interface.md)

- [偵錯介面](debugging-interfaces.md)
