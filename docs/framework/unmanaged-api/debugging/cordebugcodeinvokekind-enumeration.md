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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf777214c015f0bbc434e3123d3ec7ef7f723549
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cordebugcodeinvokekind-enumeration"></a>CorDebugCodeInvokeKind 列舉
描述匯出函式如何叫用 Managed 程式碼。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum CorDebugCodeInvokeKind  
{  
    CODE_INVOKE_KIND_NONE,       
    CODE_INVOKE_KIND_RETURN,     
    CODE_INVOKE_KIND_TAILCALL,   
} CorDebugCodeInvokeKind;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`CODE_INVOKE_KIND_NONE`|如果這個方法叫用任何 Managed 程式碼，明確事件或中斷點稍後必須找到這些程式碼。<br /><br /> -或-<br /><br /> 我們可能只是遺漏這個方法呼叫的一些 Managed 程式碼，因為沒有簡單的方法可以在其上停止。<br /><br /> -或-<br /><br /> 這個方法可能永遠不會叫用 Managed 程式碼。|  
|`CODE_INVOKE_KIND_RETURN`|這個方法會透過傳回指令叫用 Managed 程式碼。 跳離應該會抵達下一個 Managed 程式碼。|  
|`CODE_INVOKE_KIND_TAILCALL`|這個方法會透過 tail 呼叫叫用 Managed 程式碼。 逐步執行和不進入任何呼叫指令應該會抵達 Managed 程式碼。|  
  
## <a name="remarks"></a>備註  
 這個列舉型別由[icordebugprocess6:: Getexportstepinfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md)方法以提供資訊逐步執行 managed 程式碼。  
  
> [!NOTE]
>  這個列舉僅適用於 .NET 原生偵錯案例。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [偵錯列舉](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
