---
title: 例外狀況運行時間事件
description: 請參閱收集例外狀況和例外狀況處理特定診斷資訊的 .NET 運行時間事件。
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- exception events (CoreCLR)
- exception handling events (CoreCLR)
- ETW, EventPipe, LTTng exception events (CoreCLR)
ms.openlocfilehash: f4f63c8469f9c734b872ddaec8d1d7f7f0427576
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96586655"
---
# <a name="net-runtime-exception-events"></a>.NET 執行時間例外狀況事件

這些運行時間事件會捕捉擲回之例外狀況的相關資訊。 如需如何基於診斷目的使用這些事件的詳細資訊，請參閱[記錄和追蹤 .net 應用程式](../../core/diagnostics/logging-tracing.md)。

## <a name="exceptionthrown_v1-event"></a>ExceptionThrown_V1 事件

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`ExceptionKeyword` (0x8000)|錯誤 (1)|

 下表顯示事件資訊。

|事件|事件識別碼|引發的時機|
|-----------|--------------|-----------------|
|`ExceptionThrown_V1`|80|擲回 Managed 例外狀況。|

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`ExceptionType`|`win:UnicodeString`|例外狀況類型，例如 `System.NullReferenceException`。|
|`ExceptionMessage`|`win:UnicodeString`|實際的例外狀況訊息。|
|`EIPCodeThrow`|`win:Pointer`|發生例外狀況的指令指標。|
|`ExceptionHR`|`win:UInt32`|例外狀況 [HRESULT](/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a)。|
|`ExceptionFlags`|`win:UInt16`|`0x01`: HasInnerException.<br /><br /> `0x02`: IsNestedException.<br /><br /> `0x04`: IsRethrownException.<br /><br /> `0x08`： IsCorruptedStateException (表示進程狀態已損毀;請參閱 [處理損毀狀態例外狀況](/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)) 。<br /><br /> `0x10`： IsCLSCompliant (衍生自的例外狀況 <xref:System.Exception> 符合 cls 標準，否則為不符合 cls 標準的) 。|
|`ClrInstanceID`|`win:UInt16`|CLR 或 CoreCLR 執行個體的唯一 ID。|

## <a name="exceptioncatchstart-event"></a>ExceptionCatchStart 事件

當 managed 例外狀況 catch 處理常式開始時，就會發出此事件。

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`ExceptionKeyword` (0x8000)|告知性 (4)|

 下表顯示事件資訊。

|事件|事件識別碼|引發的時機|
|-----------|--------------|-----------------|
|`ExceptionCatchStart`|250|Managed 例外狀況是由執行時間處理。|

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`EIPCodeThrow`|`win:Pointer`|發生例外狀況的指令指標。|
|`MethodID`|`win:Pointer`|發生例外狀況之方法上的方法描述元指標。|
|`MethodName`|`win:UnicodeString`|發生例外狀況之方法的名稱。|
|`ClrInstanceID`|`win:UInt16`|CLR 或 CoreCLR 執行個體的唯一 ID。|

## <a name="exceptioncatchstop-event"></a>ExceptionCatchStop 事件

當 managed 例外狀況 catch 處理常式結束時，就會發出這個事件。

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`ExceptionKeyword` (0x8000)|告知性 (4)|

 下表顯示事件資訊。

|事件|事件識別碼|引發的時機|
|-----------|--------------|-----------------|
|`ExceptionCatchStop`|251|Managed 例外狀況 catch 處理常式已完成。|

## <a name="exceptionfinallystart-event"></a>ExceptionFinallyStart 事件

當 managed 例外狀況的處理常式開始時，就會發出此事件。

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`ExceptionKeyword` (0x8000)|告知性 (4)|

 下表顯示事件資訊。

|事件|事件識別碼|引發的時機|
|-----------|--------------|-----------------|
|`ExceptionFinallyStart`|252|Managed 例外狀況是由執行時間處理。|

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`EIPCodeThrow`|`win:Pointer`|發生例外狀況的指令指標。|
|`MethodID`|`win:Pointer`|發生例外狀況之方法上的方法描述元指標。|
|`MethodName`|`win:UnicodeString`|發生例外狀況之方法的名稱。|
|`ClrInstanceID`|`win:UInt16`|CLR 或 CoreCLR 執行個體的唯一 ID。|

## <a name="exceptionfinallystop-event"></a>ExceptionFinallyStop 事件

當 managed 例外狀況 catch 處理常式結束時，就會發出這個事件。

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`ExceptionKeyword` (0x8000)|告知性 (4)|

 下表顯示事件資訊。

|事件|事件識別碼|引發的時機|
|-----------|--------------|-----------------|
|`ExceptionFinallyStop`|253|Managed 例外狀況 finally 處理常式已完成。|

## <a name="exceptionfilterstart-event"></a>ExceptionFilterStart 事件

當 managed 例外狀況篩選開始時，就會發出此事件。

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`ExceptionKeyword` (0x8000)|告知性 (4)|

 下表顯示事件資訊。

|事件|事件識別碼|引發的時機|
|-----------|--------------|-----------------|
|`ExceptionFilterStart`|254|Managed 例外狀況篩選會開始。|

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`EIPCodeThrow`|`win:Pointer`|發生例外狀況的指令指標。|
|`MethodID`|`win:Pointer`|發生例外狀況之方法上的方法描述元指標。|
|`MethodName`|`win:UnicodeString`|發生例外狀況之方法的名稱。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR 實例的唯一識別碼。|

## <a name="exceptionfilterstop-event"></a>ExceptionFilterStop 事件

Managed 例外狀況篩選結束時，就會發出此事件。

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`ExceptionKeyword` (0x8000)|告知性 (4)|

 下表顯示事件資訊。

|事件|事件識別碼|引發的時機|
|-----------|--------------|-----------------|
|`ExceptionFilteringStart`|255|Managed 例外狀況篩選會結束。|

## <a name="exceptionthrownstop-event"></a>ExceptionThrownStop 事件

當執行時間完成處理所擲回的 managed 例外狀況時，就會發出這個事件。

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`ExceptionKeyword` (0x8000)|告知性 (4)|
  
 下表顯示事件資訊。

|事件|事件識別碼|引發的時機|
|-----------|--------------|-----------------|
|`ExceptionThrownStop`|256|Managed 例外狀況篩選會結束。|
