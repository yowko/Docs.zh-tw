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
ms.openlocfilehash: 6eea7f6c222b8e30376ec72ee0c193a68c23f0d0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723554"
---
# <a name="iclrdebugging-interface"></a>ICLRDebugging 介面

提供處理載入及卸載模組以進行偵錯的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[OpenVirtualProcess 方法](iclrdebugging-openvirtualprocess-method.md)|取得 "ICorDebugProcess" 介面，這個介面會對應至在進程中載入 (CLR) 模組的 common language runtime。|  
|[CanUnloadNow 方法](iclrdebugging-canunloadnow-method.md)|判斷 [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) 介面所提供的程式庫是否仍在使用中，或是否可以卸載。|  
  
## <a name="remarks"></a>備註  

 您可以 `ICLRDebugging` 使用 [CLRCreateInstance](../hosting/clrcreateinstance-function.md) 函數取得介面的實例。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](debugging-interfaces.md)
- [偵錯](index.md)
