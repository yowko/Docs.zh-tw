---
title: 輸入系統運行時間事件
description: 請參閱收集 .NET 類型系統特定診斷資訊的 .NET 運行時間事件，例如 TypeLoadStart 和 TypeLoadStop。
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- type system events (CoreCLR)
- ETW, EventPipe, LTTng type system events (CoreCLR)
ms.openlocfilehash: 8eee89cddb0098da2cb449a4be21945adac725e3
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "96586633"
---
# <a name="net-runtime-type-events"></a>.NET 執行時間類型事件

這些事件會收集與載入類型相關的資訊。 如需如何基於診斷目的使用這些事件的詳細資訊，請參閱[記錄和追蹤 .net 應用程式](../../core/diagnostics/logging-tracing.md)。

## <a name="typeloadstart-event"></a>TypeLoadStart 事件

|引發事件的關鍵字|事件|層級|  
|-----------------------------------|-----------|-----------|  
|`TypeDiagnosticKeyword` (0x8000000000) |告知性 (4)|  

|事件|事件識別碼|描述|  
|-----------|--------------|-----------------|  
|`TypeLoadStart`|73|類型載入已開始。|

|欄位名稱|資料類型|描述|  
|----------------|---------------|-----------------|  
|`TypeLoadStartID`|`win:UInt32`|類型載入作業的識別碼。|
|`ClrInstanceID`|`win:UInt16`|CLR 或 CoreCLR 執行個體的唯一 ID。|  

## <a name="typeloadstop-event"></a>TypeLoadStop 事件

|引發事件的關鍵字|層級|  
|-----------------------------------|-----------|-----------|  
|`TypeDiagnosticKeyword` (0x8000000000) |告知性 (4)|  

|事件|事件識別碼|描述|  
|-----------|--------------|-----------------|  
|`TypeLoadStop`|74|類型載入已完成。|

|欄位名稱|資料類型|描述|  
|----------------|---------------|-----------------|  
|`TypeLoadStartID`|`win:UInt32`|類型載入作業的識別碼 (符合對應的 TypeLoadStart 事件的 TypeLoadStartID) 。|
|`LoadLevel`|`win:UInt16`|輸入負載層級。|
|`TypeID`|`win:UInt64`|型別控制碼的指標。|
|`TypeName`|`win:UnicodeString`|類型的名稱。|
|`ClrInstanceID`|`win:UInt16`|CLR 或 CoreCLR 執行個體的唯一 ID。|  
