---
title: ICorDebugModule2 介面
ms.date: 03/30/2017
api_name:
- ICorDebugModule2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2
helpviewer_keywords:
- ICorDebugModule2 interface [.NET Framework debugging]
ms.assetid: 0847e64f-fdbe-4c96-8168-da20fdc84d80
topic_type:
- apiref
ms.openlocfilehash: 32774aacecf3e56510bc6f0670538a44fde794c9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792980"
---
# <a name="icordebugmodule2-interface"></a>ICorDebugModule2 介面

作為 ICorDebugModule 介面的邏輯擴充。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[ApplyChanges 方法](icordebugmodule2-applychanges-method.md)|將中繼資料中的變更和 Microsoft 中繼語言（MSIL）程式碼中的變更套用至執行中的進程。|  
|[GetJITCompilerFlags 方法](icordebugmodule2-getjitcompilerflags-method.md)|取得旗標，可控制此 `ICorDebugModule2`的即時（JIT）編譯。|  
|[ResolveAssembly 方法](icordebugmodule2-resolveassembly-method.md)|解析指定的元資料標記所參考的元件。|  
|[SetJITCompilerFlags 方法](icordebugmodule2-setjitcompilerflags-method.md)|設定用來控制此 `ICorDebugModule2`之 JIT 編譯的旗標。|  
|[SetJMCStatus 方法](icordebugmodule2-setjmcstatus-method.md)|將此 `ICorDebugModule2` 中所有類別的所有方法的 Just My Code （JMC）狀態設定為指定的值，但在 `pTokens` 陣列中，它會設定為相反的值。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯介面](debugging-interfaces.md)
