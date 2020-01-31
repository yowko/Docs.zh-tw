---
title: ICLRDebugging 介面
ms.date: 03/30/2017
api_name:
- ICLRDebugging
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging
helpviewer_keywords:
- ICLRDebugging interface [.NET Framework debugging]
ms.assetid: 429d8fce-b1b1-49d7-895c-28c1c1aa2dbd
topic_type:
- apiref
ms.openlocfilehash: 9a768535c3bf69b5127777de4cee27054943091d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793634"
---
# <a name="iclrdebugging-interface"></a>ICLRDebugging 介面
提供處理載入及卸載模組以進行偵錯的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[OpenVirtualProcess 方法](iclrdebugging-openvirtualprocess-method.md)|取得對應至在進程中載入之 common language runtime （CLR）模組的 "ICorDebugProcess" 介面。|  
|[CanUnloadNow 方法](iclrdebugging-canunloadnow-method.md)|判斷[ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md)介面所提供的程式庫是否仍在使用中，或是否可以卸載。|  
  
## <a name="remarks"></a>備註  
 您可以使用[CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md)函數來取得 `ICLRDebugging` 介面的實例。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯介面](debugging-interfaces.md)
- [偵錯](index.md)
