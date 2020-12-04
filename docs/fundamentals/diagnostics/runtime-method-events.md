---
title: 方法運行時間事件
description: 請參閱收集方法特定診斷資訊的 .NET 運行時間事件，例如 CLR 方法事件、CLR 方法標記或 CLR 方法詳細資訊事件，以及 MethodJittingStarted。
ms.date: 11/13/2020
helpviewer_keywords:
- Method events (CoreCLR)
- ETW, EventPipe, LTTng method events (CoreCLR)
ms.openlocfilehash: f9d08efa420670cf7a8c863f115ff270998f2dca
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "96586634"
---
# <a name="net-runtime-method-events"></a>.NET 執行時間方法事件

這些事件會收集方法的特定資訊。 若要進行符號解析，需使用這些事件的承載。 此外，這些事件會提供有用的資訊，例如載入和卸載的方法。 如需如何基於診斷目的使用這些事件的詳細資訊，請參閱[記錄和追蹤 .net 應用程式](../../core/diagnostics/logging-tracing.md)。

所有方法事件都具「告知性 (4)」的層級。 所有方法的詳細資訊事件都具「詳細資訊 (5)」的層級。

所有方法事件都是由執行階段提供者下的 `JITKeyword` (0x10) 關鍵字或 `NGenKeyword` (0x20) 關鍵字，或由取消提供者下的 `JitRundownKeyword` (0x10) 或 `NGENRundownKeyword` (0x20) 所引發。

這些事件的 V2 版本包含 ReJITID，V1 版本則否。

## <a name="methodload_v1-event"></a>MethodLoad_V1 事件

下表說明事件資訊：

|事件|事件識別碼|描述|
|-----------|--------------|-----------------|
|`MethodLoad_V1`|141|在 Just-In-Time 載入 (JIT 載入) 方法或 NGEN 映像載入時引發。 動態和泛型的方法並不會使用這個版本的方法載入。 JIT Helper 永遠不會使用這個版本。|

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`JITKeyword` (0x10) 執行階段提供者|告知性 (4)|
|`NGenKeyword` (0x20) 執行階段提供者|告知性 (4)|

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|方法的唯一識別碼。 若是 JIT Helper 方法，其設為方法的起始位址。|
|`ModuleID`|`win:UInt64`|這個方法所屬之模組的識別碼 (0 代表 JIT Helper)。|
|`MethodStartAddress`|`win:UInt64`|方法的起始位址。|
|`MethodSize`|`win:UInt32`|方法的大小。|
|`MethodToken`|`win:UInt32`|0 代表動態方法和 JIT Helper。|
|`MethodFlags`|`win:UInt32`|0x1：動態方法。<br /><br /> 0x2：泛型方法。<br /><br /> 0x4：JIT 編譯的程式碼方法 (否則為 NGEN 原生映像程式碼)。<br /><br /> 0x8：Helper 方法。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR 實例的唯一識別碼。|

## <a name="methodload_v2-event"></a>MethodLoad_V2 事件

|事件|事件識別碼|描述|
|----------------|---------------|-----------------|
|`MethodLoad_V2`|141|在 Just-In-Time 載入 (JIT 載入) 方法或 NGEN 映像載入時引發。 動態和泛型的方法並不會使用這個版本的方法載入。 JIT Helper 永遠不會使用這個版本。|

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`JITKeyword` (0x10) 執行階段提供者|告知性 (4)|
|`NGenKeyword` (0x20) 執行階段提供者|告知性 (4)|

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|方法的唯一識別碼。 若是 JIT Helper 方法，其設為方法的起始位址。|
|`ModuleID`|`win:UInt64`|這個方法所屬之模組的識別碼 (0 代表 JIT Helper)。|
|`MethodStartAddress`|`win:UInt64`|方法的起始位址。|
|`MethodSize`|`win:UInt32`|方法的大小。|
|`MethodToken`|`win:UInt32`|0 代表動態方法和 JIT Helper。|
|`MethodFlags`|`win:UInt32`|0x1：動態方法。<br /><br /> 0x2：泛型方法。<br /><br /> 0x4：JIT 編譯的程式碼方法 (否則為 NGEN 原生映像程式碼)。<br /><br /> 0x8：Helper 方法。|
|`ReJITID`|`win:UInt64`|方法的 ReJIT 識別碼。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR 實例的唯一識別碼。|

## <a name="methodunload_v1-event"></a>MethodUnLoad_V1 事件

|事件|事件識別碼|描述|
|----------------|---------------|-----------------|
|`MethodUnLoad_V1`|142|在模組已卸載或應用程式定義域損毀時引發。 動態方法永遠不會使用這個版本的方法卸載。|

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`JITKeyword` (0x10)|告知性 (4)|
|`NGenKeyword` (0x20) |告知性 (4)|

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|方法的唯一識別碼。 若是 JIT Helper 方法，其設為方法的起始位址。|
|`ModuleID`|`win:UInt64`|這個方法所屬之模組的識別碼 (0 代表 JIT Helper)。|
|`MethodStartAddress`|`win:UInt64`|方法的起始位址。|
|`MethodSize`|`win:UInt32`|方法的大小。|
|`MethodToken`|`win:UInt32`|0 代表動態方法和 JIT Helper。|
|`MethodFlags`|`win:UInt32`|0x1：動態方法。<br /><br /> 0x2：泛型方法。<br /><br /> 0x4：JIT 編譯的程式碼方法 (否則為 NGEN 原生映像程式碼)。<br /><br /> 0x8：Helper 方法。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR 實例的唯一識別碼。|

## <a name="methodunload_v2-event"></a>MethodUnLoad_V2 事件

|事件|事件識別碼|描述|
|----------------|---------------|-----------------|
|`MethodUnLoad_V2`|142|在模組已卸載或應用程式定義域損毀時引發。 動態方法永遠不會使用這個版本的方法卸載。|

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`JITKeyword` (0x10)|告知性 (4)|
|`NGenKeyword` (0x20) |告知性 (4)|

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|方法的唯一識別碼。 若是 JIT Helper 方法，其設為方法的起始位址。|
|`ModuleID`|`win:UInt64`|這個方法所屬之模組的識別碼 (0 代表 JIT Helper)。|
|`MethodStartAddress`|`win:UInt64`|方法的起始位址。|
|`MethodSize`|`win:UInt32`|方法的大小。|
|`MethodToken`|`win:UInt32`|0 代表動態方法和 JIT Helper。|
|`MethodFlags`|`win:UInt32`|0x1：動態方法。<br /><br /> 0x2：泛型方法。<br /><br /> 0x4：JIT 編譯的程式碼方法 (否則為 NGEN 原生映像程式碼)。<br /><br /> 0x8：Helper 方法。|
|`ReJITID`|`win:UInt64`|方法的 ReJIT 識別碼。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR 實例的唯一識別碼。|

## <a name="r2rgetentrypoint-event"></a>R2RGetEntryPoint 事件

|事件|事件識別碼|描述|
|----------------|---------------|-----------------|
|`R2RGetEntryPoint`|159|在 R2R 進入點查閱結束時引發。|

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`JITKeyword` (0x10) |告知性 (4)|
|`NGenKeyword` (0x20)  |告知性 (4)|

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|R2R 方法的唯一識別碼。|
|`MethodNamespace`|`win:UnicodeString`|要查閱之方法的命名空間。|
|`MethodName`|`win:UnicodeString`|要查閱之方法的名稱。|
|`MethodSignature`|`win:UnicodeString`|方法的簽章 (以逗號分隔的類型名稱清單)。|
|`EntryPoint`|`win:UInt64`|R2R 方法進入點的指標|
|`ClrInstanceID`|`win:UInt16`|CoreCLR 實例的唯一識別碼。|

## <a name="r2rgetentrypointstart-event"></a>R2RGetEntryPointStart 事件

|事件|事件識別碼|描述|
|----------------|---------------|-----------------|
|`R2RGetEntryPointStart`|160|在 R2R 進入點查閱開始時引發。|

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`JITKeyword` (0x10) |告知性 (4)|
|`NGenKeyword` (0x20)  |告知性 (4)|

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|R2R 方法的唯一識別碼。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR 實例的唯一識別碼。|

## <a name="methodloadverbose_v1-event"></a>MethodLoadVerbose_V1 事件

|事件|事件識別碼|描述|
|-----------|--------------|-----------------|
|`MethodLoadVerbose_V1`|143|在 JIT 載入方法或 NGEN 映像載入時引發。 動態和泛型的方法一律會使用這個版本的方法載入。 JIT Helper 一律會使用這個版本。|

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`JITKeyword` (0x10) |告知性 (4)|
|`NGenKeyword` (0x20)  |告知性 (4)|

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|方法的唯一識別項。 若是 JIT Helper 方法，其設為方法的起始位址。|
|`ModuleID`|`win:UInt64`|這個方法所屬之模組的識別碼 (0 代表 JIT Helper)。|
|`MethodStartAddress`|`win:UInt64`|起始位址：|
|`MethodSize`|`win:UInt32`|方法的長度。|
|`MethodToken`|`win:UInt32`|0 代表動態方法和 JIT Helper。|
|`MethodFlags`|`win:UInt32`|0x1：動態方法。<br /><br /> 0x2：泛型方法。<br /><br /> 0x4：JIT 編譯方法 (否則由 NGen.exe 產生)<br /><br /> 0x8：Helper 方法。|
|`MethodNameSpace`|`win:UnicodeString`|與方法相關聯的完整命名空間名稱。|
|`MethodName`|`win:UnicodeString`|與方法相關聯的完整類別名稱。|
|`MethodSignature`|`win:UnicodeString`|方法的簽章 (以逗號分隔的類型名稱清單)。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR 實例的唯一識別碼。|

## <a name="methodloadverbose_v2-event"></a>MethodLoadVerbose_V2 事件

|事件|事件識別碼|描述|
|-----------|--------------|-----------------|
|`MethodLoadVerbose_V1`|143|在 JIT 載入方法或 NGEN 映像載入時引發。 動態和泛型的方法一律會使用這個版本的方法載入。 JIT Helper 一律會使用這個版本。|

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`JITKeyword` (0x10) |告知性 (4)|
|`NGenKeyword` (0x20)  |告知性 (4)|

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|方法的唯一識別項。 若是 JIT Helper 方法，其設為方法的起始位址。|
|`ModuleID`|`win:UInt64`|這個方法所屬之模組的識別碼 (0 代表 JIT Helper)。|
|`MethodStartAddress`|`win:UInt64`|起始位址：|
|`MethodSize`|`win:UInt32`|方法的長度。|
|`MethodToken`|`win:UInt32`|0 代表動態方法和 JIT Helper。|
|`MethodFlags`|`win:UInt32`|0x1：動態方法。<br /><br /> 0x2：泛型方法。<br /><br /> 0x4：JIT 編譯方法 (否則由 NGen.exe 產生)<br /><br /> 0x8：Helper 方法。|
|`MethodNameSpace`|`win:UnicodeString`|與方法相關聯的完整命名空間名稱。|
|`MethodName`|`win:UnicodeString`|與方法相關聯的完整類別名稱。|
|`MethodSignature`|`win:UnicodeString`|方法的簽章 (以逗號分隔的類型名稱清單)。|
|`ReJITID`|`win:UInt64`|方法的 ReJIT 識別碼。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR 實例的唯一識別碼。|

## <a name="methodunloadverbose_v1-event"></a>MethodUnLoadVerbose_V1 事件

|事件|事件識別碼|描述|
|-----------|--------------|-----------------|
|`MethodUnLoadVerbose_V1`|144|在動態方法損毀、模組已卸載或應用程式定義域損毀時引發。 動態方法永遠一律會使用這個版本的方法卸載。|

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`JITKeyword` (0x10) |告知性 (4)|
|`NGenKeyword` (0x20)  |告知性 (4)|

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|方法的唯一識別項。 若是 JIT Helper 方法，其設為方法的起始位址。|
|`ModuleID`|`win:UInt64`|這個方法所屬之模組的識別碼 (0 代表 JIT Helper)。|
|`MethodStartAddress`|`win:UInt64`|起始位址：|
|`MethodSize`|`win:UInt32`|方法的長度。|
|`MethodToken`|`win:UInt32`|0 代表動態方法和 JIT Helper。|
|`MethodFlags`|`win:UInt32`|0x1：動態方法。<br /><br /> 0x2：泛型方法。<br /><br /> 0x4：JIT 編譯方法 (否則由 NGen.exe 產生)<br /><br /> 0x8：Helper 方法。|
|`MethodNameSpace`|`win:UnicodeString`|與方法相關聯的完整命名空間名稱。|
|`MethodName`|`win:UnicodeString`|與方法相關聯的完整類別名稱。|
|`MethodSignature`|`win:UnicodeString`|方法的簽章 (以逗號分隔的類型名稱清單)。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR 實例的唯一識別碼。|

## <a name="methodunloadverbose_v2-event"></a>MethodUnLoadVerbose_V2 事件

|事件|事件識別碼|描述|
|-----------|--------------|-----------------|
|`MethodUnLoadVerbose_V2`|144|在動態方法損毀、模組已卸載或應用程式定義域損毀時引發。 動態方法永遠一律會使用這個版本的方法卸載。|

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`JITKeyword` (0x10) |告知性 (4)|
|`NGenKeyword` (0x20)  |告知性 (4)|

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|方法的唯一識別項。 若是 JIT Helper 方法，其設為方法的起始位址。|
|`ModuleID`|`win:UInt64`|這個方法所屬之模組的識別碼 (0 代表 JIT Helper)。|
|`MethodStartAddress`|`win:UInt64`|起始位址：|
|`MethodSize`|`win:UInt32`|方法的長度。|
|`MethodToken`|`win:UInt32`|0 代表動態方法和 JIT Helper。|
|`MethodFlags`|`win:UInt32`|0x1：動態方法。<br /><br /> 0x2：泛型方法。<br /><br /> 0x4：JIT 編譯方法 (否則由 NGen.exe 產生)<br /><br /> 0x8：Helper 方法。|
|`MethodNameSpace`|`win:UnicodeString`|與方法相關聯的完整命名空間名稱。|
|`MethodName`|`win:UnicodeString`|與方法相關聯的完整類別名稱。|
|`MethodSignature`|`win:UnicodeString`|方法的簽章 (以逗號分隔的類型名稱清單)。|
|`ReJITID`|`win:UInt64`|方法的 ReJIT 識別碼。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR 實例的唯一識別碼。|

## <a name="methodjittingstarted_v1-event"></a>MethodJittingStarted_V1 事件

下表說明關鍵字和層級：

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`JITKeyword` (0x10) |詳細資訊 (5)|
|`NGenKeyword` (0x20)  |詳細資訊 (5)|

|事件|事件識別碼|描述|
|-----------|--------------|-----------------|
|`MethodJittingStarted_V1`|145|當某個方法正在進行 JIT 編譯時引發。|

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|方法的唯一識別項。|
|`ModuleID`|`win:UInt64`|這個方法所屬之模組的識別碼。|
|`MethodToken`|`win:UInt32`|0 代表動態方法和 JIT Helper。|
|`MethodILSize`|`win:UInt32`|針對正在進行 JIT 編譯的方法，一般中繼語言 (CIL) 的大小。|
|`MethodNameSpace`|`win:UnicodeString`|與方法相關聯的完整類別名稱。|
|`MethodName`|`win:UnicodeString`|方法的名稱。|
|`MethodSignature`|`win:UnicodeString`|方法的簽章 (以逗號分隔的類型名稱清單)。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR 實例的唯一識別碼。|

## <a name="methodjitinliningsucceeded-event"></a>MethodJitInliningSucceeded 事件

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`JITTracingKeyword` (0x1000)  |詳細資訊 (5)|

|事件|事件識別碼|描述|
|-----------|--------------|-----------------|
|`MethodJitInliningSucceeded`|185|當 JIT 編譯程式成功內嵌方法時引發。|

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`MethodBeingCompiledNamespace`|`win:UnicodeString`|正在編譯之方法的命名空間。|
|`MethodBeingCompiledName`|`win:UnicodeString`|正在編譯之方法的名稱。|
|`MethodBeingCompiledNameSignature`|`win:UnicodeString`|方法的簽章 () 要編譯之類型名稱的逗號分隔清單。|
|`InlinerNamespace`|`win:UnicodeString`|章 ( "parent" ) 方法的命名空間。|
|`InlinerName`|`win:UnicodeString`|章 ( "parent" ) 方法的名稱。|
|`InlinerNameSignature`|`win:UnicodeString`|章 ( "parent" ) 方法的簽章 () 類型名稱的逗號分隔清單。|
|`InlineeNamespace`|`win:UnicodeString`|內嵌項 ( "child" ) 方法的命名空間。|
|`InlineeName`|`win:UnicodeString`|內嵌項 ( "child" ) 方法的名稱。|
|`InlineeNameSignature`|`win:UnicodeString`|內嵌項 ( "child" ) 方法的簽章 () 的類型名稱清單（以逗號分隔）。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR 實例的唯一識別碼。|

## <a name="methodjitinliningfailed-event"></a>MethodJitInliningFailed 事件

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`JITTracingKeyword` (0x1000)  |詳細資訊 (5)|

|事件|事件識別碼|描述|
|-----------|--------------|-----------------|
|`MethodJitInliningFailed`|192|當 JIT 編譯程式無法內嵌方法時引發。|

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`MethodBeingCompiledNamespace`|`win:UnicodeString`|正在編譯之方法的命名空間。|
|`MethodBeingCompiledName`|`win:UnicodeString`|正在編譯之方法的名稱。|
|`MethodBeingCompiledNameSignature`|`win:UnicodeString`|方法的簽章 () 要編譯之類型名稱的逗號分隔清單。|
|`InlinerNamespace`|`win:UnicodeString`|章 ( "parent" ) 方法的命名空間。|
|`InlinerName`|`win:UnicodeString`|章 ( "parent" ) 方法的名稱。|
|`InlinerNameSignature`|`win:UnicodeString`|章 ( "parent" ) 方法的簽章 () 類型名稱的逗號分隔清單。|
|`InlineeNamespace`|`win:UnicodeString`|內嵌項 ( "child" ) 方法的命名空間。|
|`InlineeName`|`win:UnicodeString`|內嵌項 ( "child" ) 方法的名稱。|
|`InlineeNameSignature`|`win:UnicodeString`|內嵌項 ( "child" ) 方法的簽章 () 的類型名稱清單（以逗號分隔）。|
|`FailAlways`|`win:Boolean`|方法是否標記為非內嵌。|
|`FailReason`|`win:UnicodeString`|內嵌失敗的原因。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR 實例的唯一識別碼。|

## <a name="methodjittailcallsucceeded-event"></a>MethodJitTailCallSucceeded 事件

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`JITTracingKeyword` (0x1000)  |詳細資訊 (5)|

|事件|事件識別碼|描述|
|-----------|--------------|-----------------|
|`MethodJitTailCallSucceeded`|192|當可以成功呼叫方法時，由 JIT 編譯程式引發。|

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`MethodBeingCompiledNamespace`|`win:UnicodeString`|正在編譯之方法的命名空間。|
|`MethodBeingCompiledName`|`win:UnicodeString`|正在編譯之方法的名稱。|
|`MethodBeingCompiledNameSignature`|`win:UnicodeString`|方法的簽章 () 要編譯之類型名稱的逗號分隔清單。|
|`CallerNamespace`|`win:UnicodeString`|呼叫端方法的命名空間。|
|`CallerName`|`win:UnicodeString`|呼叫端方法的名稱。|
|`CallerNameSignature`|`win:UnicodeString`|呼叫端方法的簽章 () 的型別名稱清單（以逗號分隔）。|
|`CalleeNamespace`|`win:UnicodeString`|被呼叫端方法的命名空間。|
|`CalleeName`|`win:UnicodeString`|被呼叫端方法的名稱。|
|`CalleeNameSignature`|`win:UnicodeString`|被呼叫端方法的簽章 () 類型名稱的逗號分隔清單。|
|`TailPrefix`|`win:Boolean`|是否為結尾前置詞指令。|
|`TailCallType`|`win:UInt32`|Tail 呼叫的類型。<br/><br/>0：優化的 tail 呼叫 (終解 + jmp) <br/><br/>1：遞迴 tail 呼叫 (方法 tail 呼叫本身) <br/><br/>2： Helper 輔助的 tail 呼叫|
|`ClrInstanceID`|`win:UInt16`|CoreCLR 實例的唯一識別碼。|

## <a name="methodjittailcallfailed-event"></a>MethodJitTailCallFailed 事件

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`JITTracingKeyword` (0x1000)  |詳細資訊 (5)|

|事件|事件識別碼|描述|
|-----------|--------------|-----------------|
|`MethodJitTailCallFailed`|191|當方法無法被呼叫時，由 JIT 編譯程式引發。|

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`MethodBeingCompiledNamespace`|`win:UnicodeString`|正在編譯之方法的命名空間。|
|`MethodBeingCompiledName`|`win:UnicodeString`|正在編譯之方法的名稱。|
|`MethodBeingCompiledNameSignature`|`win:UnicodeString`|方法的簽章 () 要編譯之類型名稱的逗號分隔清單。|
|`CallerNamespace`|`win:UnicodeString`|呼叫端方法的命名空間。|
|`CallerNam`e|`win:UnicodeString`|呼叫端方法的名稱。|
|`CallerNameSignature`|`win:UnicodeString`|呼叫端方法的簽章 () 的型別名稱清單（以逗號分隔）。|
|`CalleeNamespace`|`win:UnicodeString`|被呼叫端方法的命名空間。|
|`CalleeName`|`win:UnicodeString`|被呼叫端方法的名稱。|
|`CalleeNameSignature`|`win:UnicodeString`|被呼叫端方法的簽章 () 類型名稱的逗號分隔清單。|
|`TailPrefix`|`win:Boolean`|是否為結尾前置詞指令。|
|`FailReason`|`win:UnicodeString`|Tail 呼叫失敗的原因。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR 實例的唯一識別碼。|

## <a name="methodiltonativemap-event"></a>MethodILToNativeMap 事件

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`JittedMethodILToNativeMapKeyword` (0x20000)  |詳細資訊 (5)|

|事件|事件識別碼|描述|
|----------------|---------------|-----------------|
|`MethodILToNativeMap`|190|對應 JIT 編譯方法的 IL 對原生對應事件。|

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|方法的唯一識別碼。|
|`ReJITID`|`win:UInt64`|方法的 ReJIT 識別碼。|
|`MethodExtent`|`win:UInt8`|可編譯之方法的範圍。|
|`CountOfMapEntries`|`win:UInt8`|對應專案的數目|
|`ILOffsets`|`win:UInt32`|IL 位移。|
|`NativeOffsets`|`win:UInt32`|機器碼位移。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR 實例的唯一識別碼。|
