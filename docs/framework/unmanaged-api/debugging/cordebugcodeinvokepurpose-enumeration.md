---
title: CorDebugCodeInvokePurpose 列舉
ms.date: 03/30/2017
api_name:
- CorDebugInvokePurpose
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 31833a2d-a0d6-48a1-b05f-995ca307a08f
topic_type:
- apiref
ms.openlocfilehash: 2e59d02093b9c2e2bda72c45de25975cbbdb7a29
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82796011"
---
# <a name="cordebugcodeinvokepurpose-enumeration"></a>CorDebugCodeInvokePurpose 列舉
描述匯出函式呼叫 Managed 程式碼的原因。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum CorDebugCodeInvokePurpose  
{  
    CODE_INVOKE_PURPOSE_NONE,  
    CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION,
    CODE_INVOKE_PURPOSE_CLASS_INIT,  
    CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH,  
} CorDebugCodeInvokePurpose;  
```  
  
## <a name="members"></a>成員  
  
|member|說明|  
|------------|-----------------|  
|`CODE_INVOKE_PURPOSE_NONE`|無或未知。|  
|`CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION`|Managed 程式碼會執行任何 Managed 進入點，例如反向 p-invoke。 執行階段不知道其他任何詳細目的。|  
|`CODE_INVOKE_PURPOSE_CLASS_INIT`|Managed 程式碼會執行靜態建構函式。|  
|`CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH`|Managed 程式碼會執行所呼叫之一些介面方法的實作。|  
  
## <a name="remarks"></a>備註  
 [ICorDebugProcess6：： GetExportStepInfo](icordebugprocess6-getexportstepinfo-method.md)方法會使用這個列舉來提供有關逐步執行 managed 程式碼的資訊。  
  
> [!NOTE]
> 這個列舉僅適用於 .NET Native 偵錯案例。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯列舉](debugging-enumerations.md)
- [偵錯](index.md)
