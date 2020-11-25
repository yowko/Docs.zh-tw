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
ms.openlocfilehash: dd148d23d6e29f03052d3bbf1fcd5d02fb332a0a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729846"
---
# <a name="clr_debugging_process_flags-enumeration"></a>CLR_DEBUGGING_PROCESS_FLAGS 列舉

提供 [ICLRDebugging：： OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) 方法所使用的值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum CLR_DEBUGGING_PROCESS_FLAGS  
{  
   CLR_DEBUGGING_MANAGED_EVENT_PENDING = 1,  
   CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH = 2  
}  CLR_DEBUGGING_PROCESS_FLAGS;  
```  
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`CLR_DEBUGGING_MANAGED_EVENT_PENDING`|此執行時間具有要傳送的非 catch managed 偵錯工具事件。 請參閱「備註」一節，以瞭解追趕和非 catch 事件之間的差異。|  
|`CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH`|暫止的 managed 事件是 <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> 要求。|  
  
## <a name="remarks"></a>備註  

 追趕事件包括進程、應用程式域、元件、模組和執行緒建立通知，讓偵錯工具在附加至進程之後，最新的狀態。 旗標所指出的非 catch 事件 `CLR_DEBUGGING_MANAGED_EVENT_PENDING` 包含所有其他偵錯工具事件，例如例外狀況和 managed 偵錯工具事件 (MDA) 通知。  
  
 旗標能 `CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH` 讓執行時間區別終止的例外狀況，以及附加可取消之 managed 偵錯工具的要求。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Metahost .idl、Metahost。h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯列舉](debugging-enumerations.md)
- [偵錯](index.md)
