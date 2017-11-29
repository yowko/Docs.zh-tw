---
title: "ICorDebug::DebugActiveProcess 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebug.DebugActiveProcess
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebug::DebugActiveProcess
helpviewer_keywords:
- DebugActiveProcess method [.NET Framework debugging]
- ICorDebug::DebugActiveProcess method [.NET Framework debugging]
ms.assetid: fdab0ade-7f56-4fa2-b3ef-f7a1d2852bba
topic_type: apiref
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c17345caaec71e4d4b057bdcfc2cc395014cbf82
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugdebugactiveprocess-method"></a>ICorDebug::DebugActiveProcess 方法
將偵錯工具附加至現有的處理序。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT DebugActiveProcess (  
    [in]  DWORD               id,  
    [in]  BOOL                win32Attach,  
    [out] ICorDebugProcess    **ppProcess  
);  
```  
  
#### <a name="parameters"></a>參數  
 `id`  
 [in]是要附加偵錯工具處理序的識別碼。  
  
 `win32Attach`  
 [in]布林值，設為`true`如果偵錯工具時應做為 Win32 偵錯工具處理序的行為及分派 unmanaged 的回呼中; 否則`false`。  
  
 `ppProcess`  
 [out]表示要附加偵錯工具的程序的"ICorDebugProcess 」 物件的位址指標。  
  
## <a name="remarks"></a>備註  
 在 Win9x 和非 x86 平台，例如 IA 64 型和 amd64 平台上不支援 interop 偵錯。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorDebug 介面](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
