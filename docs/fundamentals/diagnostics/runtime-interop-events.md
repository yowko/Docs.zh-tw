---
title: Interop 運行時間事件
description: 請參閱收集 interop 特定診斷資訊的 .NET 運行時間事件。
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- Interop events (CoreCLR)
- ETW, EventPipe, LTTng interop events (CoreCLR)
ms.openlocfilehash: 5635fb55b3a6ffa3f5611da80cdb2909e226e2ea
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "96586636"
---
# <a name="net-runtime-interop-events"></a>.NET 執行時間 interop 事件

這些運行時間事件會捕獲一般中繼語言 (CIL) 存根產生的相關資訊。 如需如何基於診斷目的使用這些事件的詳細資訊，請參閱[記錄和追蹤 .net 應用程式](../../core/diagnostics/logging-tracing.md)。

## <a name="ilstubgenerated-event"></a>ILStubGenerated 事件

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`InteropKeyword` (0x2000)|Informational(4)|
  
|事件|事件識別碼|引發的時機|
|-----------|--------------|-----------------|
|`ILStubGenerated`|88|產生 IL 存根。|

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`ModuleID`|`win:UInt16`|模組識別碼。|
|`StubMethodID`|`win:UInt64`|虛設常式方法識別項。|
|`StubFlags`|`win:UInt32`|虛設常式的旗標：<br /><br /> `0x1` -反向 interop。<br /><br /> `0x2` -COM interop。<br /><br /> `0x4` -NGen.exe 產生的存根。<br /><br /> `0x8` 授權.<br /><br /> `0x10` -Variable 引數。<br /><br /> `0x20` -非受控被呼叫端。<br /><br /> `0x40` -結構封送處理|
|`ManagedInteropMethodToken`|`win:UInt32`|Managed interop 方法的語彙基元。|
|`ManagedInteropMethodNameSpace`|`win:UnicodeString`|Managed interop 方法的命名空間和封入類型。|
|`ManagedInteropMethodName`|`win:UnicodeString`|Managed interop 方法的名稱。|
|`ManagedInteropMethodSignature`|`win:UnicodeString`|Managed interop 方法的簽章。|
|`NativeMethodSignature`|`win:UnicodeString`|原生方法簽章。|
|`StubMethodSignature`|`win:UnicodeString`|虛設常式方法簽章。|
|`StubMethodILCode`|`win:UnicodeString`|存根方法的一般中繼語言 (CIL) 程式碼。|
|`ClrInstanceID`|`win:UInt16`|CLR 或 CoreCLR 執行個體的唯一 ID。|
