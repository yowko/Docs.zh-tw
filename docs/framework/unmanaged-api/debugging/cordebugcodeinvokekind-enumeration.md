---
title: CorDebugCodeInvokeKind 列舉
ms.date: 03/30/2017
api_name:
- CorDebugCodeInvokeKind
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: e795e6a2-1008-4a81-af88-d777888e942e
topic_type:
- apiref
ms.openlocfilehash: 54332f5b3383f1c1513242a79cbd81eb8aa5c4f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179254"
---
# <a name="cordebugcodeinvokekind-enumeration"></a>CorDebugCodeInvokeKind 列舉
描述匯出函式如何叫用 Managed 程式碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum CorDebugCodeInvokeKind  
{  
    CODE_INVOKE_KIND_NONE,
    CODE_INVOKE_KIND_RETURN,
    CODE_INVOKE_KIND_TAILCALL,
} CorDebugCodeInvokeKind;  
```  
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`CODE_INVOKE_KIND_NONE`|如果這個方法叫用任何 Managed 程式碼，明確事件或中斷點稍後必須找到這些程式碼。<br /><br /> -或-<br /><br /> 我們可能只是遺漏這個方法呼叫的一些 Managed 程式碼，因為沒有簡單的方法可以在其上停止。<br /><br /> -或-<br /><br /> 這個方法可能永遠不會叫用 Managed 程式碼。|  
|`CODE_INVOKE_KIND_RETURN`|這個方法會透過傳回指令叫用 Managed 程式碼。 跳離應該會抵達下一個 Managed 程式碼。|  
|`CODE_INVOKE_KIND_TAILCALL`|這個方法會透過 tail 呼叫叫用 Managed 程式碼。 逐步執行和不進入任何呼叫指令應該會抵達 Managed 程式碼。|  
  
## <a name="remarks"></a>備註  
 [ICorDebugProcess6：：getExportStepInfo](icordebugprocess6-getexportstepinfo-method.md)方法使用此枚舉來提供有關單一步驟託管代碼的資訊。  
  
> [!NOTE]
> 這個列舉僅適用於 .NET Native 偵錯案例。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET 框架版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯列舉](debugging-enumerations.md)
- [偵錯](index.md)
