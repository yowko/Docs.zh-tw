---
title: ICorDebugFunction2 介面
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2
helpviewer_keywords:
- ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: 2b936bef-9b75-48bf-859f-42e419c65f1c
topic_type:
- apiref
ms.openlocfilehash: 5364e39f7e0a9b6c9cd10cd8f17bab4a03a4b7af
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794486"
---
# <a name="icordebugfunction2-interface"></a>ICorDebugFunction2 介面

以邏輯方式擴充 ICorDebugFunction 介面，以支援 Just My Code 的逐步執行偵測，這會略過非使用者程式碼。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[EnumerateNativeCode 方法](icordebugfunction2-enumeratenativecode-method.md)|（尚未執行）。取得 ICorDebugCodeEnum 的介面指標，其中包含這個 ICorDebugFunction2 物件所參考之函式中的機器碼語句。|  
|[GetJMCStatus 方法](icordebugfunction2-getjmcstatus-method.md)|取得值，指出此函式是否標示為使用者程式碼。|  
|[GetVersionNumber 方法](icordebugfunction2-getversionnumber-method.md)|取得此函式的編輯後繼續版本。|  
|[SetJMCStatus 方法](icordebugfunction2-setjmcstatus-method.md)|將此函數標示為 Just My Code 逐步執行。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯介面](debugging-interfaces.md)
