---
title: CLR_DEBUGGING_PROCESS_FLAGS 列舉
ms.date: 03/30/2017
api_name:
- CLR_DEBUGGING_PROCESS_FLAGS
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CLR_DEBUGGING_PROCESS_FLAG
helpviewer_keywords:
- CLR_DEBUGGING_PROCESS_FLAGS enumeration [.NET Framework debugging]
ms.assetid: 85b85fde-1f87-490b-ba8d-d604670959c3
topic_type:
- apiref
ms.openlocfilehash: b9185600d9d8b2a33830d86642727ac54b87a9cf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099648"
---
# <a name="clr_debugging_process_flags-enumeration"></a>CLR_DEBUGGING_PROCESS_FLAGS 列舉
提供[ICLRDebugging：： OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md)方法所使用的值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum CLR_DEBUGGING_PROCESS_FLAGS  
{  
   CLR_DEBUGGING_MANAGED_EVENT_PENDING = 1,  
   CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH = 2  
}  CLR_DEBUGGING_PROCESS_FLAGS;  
```  
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`CLR_DEBUGGING_MANAGED_EVENT_PENDING`|這個執行時間有一個要傳送的非 catch managed 偵錯工具事件。 請參閱備註一節，以瞭解追趕和非 catch 事件之間的區別。|  
|`CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH`|暫止的 managed 事件是 <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> 要求。|  
  
## <a name="remarks"></a>備註  
 捕捉事件包括進程、應用程式域、元件、模組，以及執行緒建立通知，可讓偵錯工具在附加至進程之後回到目前狀態。 非捕捉事件（由 `CLR_DEBUGGING_MANAGED_EVENT_PENDING` 旗標表示）包含所有其他偵錯工具事件，例如例外狀況和 managed 偵錯工具（MDA）通知。  
  
 `CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH` 旗標可讓執行時間區別終止的例外狀況和要求，以附加可取消的 managed 偵錯工具。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Metahost .idl，Metahost。h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯列舉](debugging-enumerations.md)
- [偵錯](index.md)
