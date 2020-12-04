---
title: 載入器和系結器運行時間事件
description: 請參閱收集載入器的特定診斷資訊和系結器 ETW 事件的 .NET 運行時間事件，這些事件會收集組件載入器和系結器的相關資訊。
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- Assembly Loader events (CoreCLR)
- Assembly Binder events (CoreCLR)
- ETW, EventPipe, LTTng assembly loader and binder events (CoreCLR)
ms.openlocfilehash: 2284c580482f6b93a77f44649225ff7e5485666a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96586657"
---
# <a name="net-runtime-loader-and-binder-events"></a>.NET 執行時間載入器和系結器事件

這些事件會收集載入和卸載元件和模組的相關資訊。 如需如何基於診斷目的使用這些事件的詳細資訊，請參閱[記錄和追蹤 .net 應用程式](../../core/diagnostics/logging-tracing.md)。

|引發事件的關鍵字|事件|層級|
|-----------------------------------|-----------|-----------|
|`LoaderKeyword` (0x8)|`DomainModuleLoad_V1`|告知性 (4)|

|事件|事件識別碼|描述|
|-----------|--------------|-----------------|
|`DomainModuleLoad_V1`|151|針對應用程式定義域載入模組時引發。|

## <a name="moduleload_v2-event"></a>ModuleLoad_V2 事件

|引發事件的關鍵字|事件|層級|
|-----------------------------------|-----------|-----------|
|`LoaderKeyword` (0x8)|`DomainModuleLoad_V1`|告知性 (4)|

|事件|事件識別碼|描述|
|-----------|--------------|-----------------|
|`ModuleLoad_V2`|152|在處理序的存留期間載入模組時引發。|

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`ModuleID`|`win:UInt64`|模組的唯一 ID。|
|`AssemblyID`|`win:UInt64`|這個模組所在之組件的 ID。|
|`ModuleFlags`|`win:UInt32`|0x1：定義域中性模組。<br /><br /> 0x2：模組具有原生映像。<br /><br /> 0x4：動態模組。<br /><br /> 0x8：資訊清單模組。|
|`Reserved1`|`win:UInt32`|保留的欄位。|
|`ModuleILPath`|`win:UnicodeString`|模組的通用中繼語言 (的) 影像的路徑，或動態模組名稱（如果它是動態元件 (以 null 終止的) ）。|
|`ModuleNativePath`|`win:UnicodeString`|模組原生映像的路徑 (如果存在的話 (以 Null 終止))。|
|`ClrInstanceID`|`win:UInt16`|CLR 或 CoreCLR 執行個體的唯一 ID。|
|`ManagedPdbSignature`|`win:GUID`|符合此模組的受管理程式資料庫 (PDB) 的 GUID 簽章。|
|`ManagedPdbAge`|`win:UInt32`|寫入至受管理 PDB 並符合此模組的保留時間數值。|
|`ManagedPdbBuildPath`|`win:UnicodeString`|符合此模組之受管理 PDB 建立位置的目標路徑。 在某些情況下，這可能只是檔案名稱。|
|`NativePdbSignature`|`win:GUID`|符合此模組之原生映像產生器 (NGen) PDB 的 GUID 簽章 (如果有的話)。|
|`NativePdbAge`|`win:UInt32`|寫入符合本模組之 NGen PDB 的的保留時間數值 (如果有的話)。|
|`NativePdbBuildPath`|`win:UnicodeString`|符合此模組之 NGen PDB 建立位置的目標路徑。 在某些情況下，這可能只是檔案名稱。|

## <a name="moduleunload_v2-event"></a>ModuleUnload_V2 事件

|引發事件的關鍵字|事件|層級|
|-----------------------------------|-----------|-----------|
|`LoaderKeyword` (0x8)|`DomainModuleLoad_V1`|告知性 (4)|

|事件|事件識別碼|描述|
|-----------|--------------|-----------------|
|`ModuleUnload_V2`|153|在處理序的存留期間卸載模組時引發。|

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`ModuleID`|`win:UInt64`|模組的唯一 ID。|
|`AssemblyID`|`win:UInt64`|這個模組所在之組件的 ID。|
|`ModuleFlags`|`win:UInt32`|0x1：定義域中性模組。<br /><br /> 0x2：模組具有原生映像。<br /><br /> 0x4：動態模組。<br /><br /> 0x8：資訊清單模組。|
|`Reserved1`|`win:UInt32`|保留的欄位。|
|`ModuleILPath`|`win:UnicodeString`|模組的通用中繼語言 (的) 影像的路徑，或動態模組名稱（如果它是動態元件 (以 null 終止的) ）。|
|`ModuleNativePath`|`win:UnicodeString`|模組原生映像的路徑 (如果存在的話 (以 Null 終止))。|
|`ClrInstanceID`|``win:UInt16``|CLR 或 CoreCLR 執行個體的唯一 ID。|
|`ManagedPdbSignature`|`win:GUID`|符合此模組的受管理程式資料庫 (PDB) 的 GUID 簽章。|
|`ManagedPdbAge`|`win:UInt32`|寫入至受管理 PDB 並符合此模組的保留時間數值。|
|`ManagedPdbBuildPath`|`win:UnicodeString`|符合此模組之受管理 PDB 建立位置的目標路徑。 在某些情況下，這可能只是檔案名稱。|
|`NativePdbSignature`|`win:GUID`|符合此模組之原生映像產生器 (NGen) PDB 的 GUID 簽章 (如果有的話)。|
|`NativePdbAge`|`win:UInt32`|寫入符合本模組之 NGen PDB 的的保留時間數值 (如果有的話)。|
|`NativePdbBuildPath`|`win:UnicodeString`|符合此模組之 NGen PDB 建立位置的目標路徑。 在某些情況下，這可能只是檔案名稱。|

## <a name="moduledcstart_v2-event"></a>ModuleDCStart_V2 事件

|引發事件的關鍵字|事件|層級|
|-----------------------------------|-----------|-----------|
|`LoaderKeyword` (0x8)|`DomainModuleLoad_V1`|告知性 (4)

|事件|事件識別碼|描述
|-----------|--------------|-----------------|
|`ModuleDCStart_V2`|153|在開始取消期間列舉模組。|

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`ModuleID`|`win:UInt64`|模組的唯一 ID。|
|`AssemblyID`|`win:UInt64`|這個模組所在之組件的 ID。|
|`ModuleFlags`|`win:UInt32`|0x1：定義域中性模組。<br /><br /> 0x2：模組具有原生映像。<br /><br /> 0x4：動態模組。<br /><br /> 0x8：資訊清單模組。|
|`Reserved1`|`win:UInt32`|保留的欄位。|
|`ModuleILPath`|`win:UnicodeString`|模組的通用中繼語言 (的) 影像的路徑，或動態模組名稱（如果它是動態元件 (以 null 終止的) ）。|
|`ModuleNativePath`|`win:UnicodeString`|模組原生映像的路徑 (如果存在的話 (以 Null 終止))。|
|`ClrInstanceID`|`win:UInt16`|CLR 或 CoreCLR 執行個體的唯一 ID。|
|`ManagedPdbSignature`|`win:GUID`|符合此模組的受管理程式資料庫 (PDB) 的 GUID 簽章。|
|`ManagedPdbAge`|`win:UInt32`|寫入至受管理 PDB 並符合此模組的保留時間數值。|
|`ManagedPdbBuildPath`|`win:UnicodeString`|符合此模組之受管理 PDB 建立位置的目標路徑。 在某些情況下，這可能只是檔案名稱。|
|`NativePdbSignature`|`win:GUID`|符合此模組之原生映像產生器 (NGen) PDB 的 GUID 簽章 (如果有的話)。|
|`NativePdbAge`|`win:UInt32`|寫入符合本模組之 NGen PDB 的的保留時間數值 (如果有的話)。|
|`NativePdbBuildPath`|`win:UnicodeString`|符合此模組之 NGen PDB 建立位置的目標路徑。 在某些情況下，這可能只是檔案名稱。|

## <a name="moduledcend_v2-event"></a>ModuleDCEnd_V2 事件

|引發事件的關鍵字|事件|層級|
|-----------------------------------|-----------|-----------|
|`LoaderKeyword` (0x8)|`DomainModuleLoad_V1`|告知性 (4)|

|事件|事件識別碼|描述|
|-----------|--------------|-----------------|
|`ModuleDCEnd_V2`|154|在結束取消期間列舉模組。|

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`ModuleID`|`win:UInt64`|模組的唯一 ID。|
|`AssemblyID`|`win:UInt64`|這個模組所在之組件的 ID。|
|`ModuleFlags`|`win:UInt32`|0x1：定義域中性模組。<br /><br /> 0x2：模組具有原生映像。<br /><br /> 0x4：動態模組。<br /><br /> 0x8：資訊清單模組。|
|`Reserved1`|`win:UInt32`|保留的欄位。|
|`ModuleILPath`|`win:UnicodeString`|模組的通用中繼語言 (的) 影像的路徑，或動態模組名稱（如果它是動態元件 (以 null 終止的) ）。|
|`ModuleNativePath`|`win:UnicodeString`|模組原生映像的路徑 (如果存在的話 (以 Null 終止))。|
|`ClrInstanceID`|`win:UInt16`|CLR 或 CoreCLR 執行個體的唯一 ID。|
|`ManagedPdbSignature`|`win:GUID`|符合此模組的受管理程式資料庫 (PDB) 的 GUID 簽章。|
|`ManagedPdbAge`|`win:UInt32`|寫入至受管理 PDB 並符合此模組的保留時間數值。|
|`ManagedPdbBuildPath`|`win:UnicodeString`|符合此模組之受管理 PDB 建立位置的目標路徑。 在某些情況下，這可能只是檔案名稱。|
|`NativePdbSignature`|`win:GUID`|符合此模組之原生映像產生器 (NGen) PDB 的 GUID 簽章 (如果有的話)。|
|`NativePdbAge`|`win:UInt32`|寫入符合本模組之 NGen PDB 的的保留時間數值 (如果有的話)。|
|`NativePdbBuildPath`|`win:UnicodeString`|符合此模組之 NGen PDB 建立位置的目標路徑。 在某些情況下，這可能只是檔案名稱。|

## <a name="assemblyload_v1-event"></a>AssemblyLoad_V1 事件

|引發事件的關鍵字|事件|層級|
|-----------------------------------|-----------|-----------|
|`LoaderKeyword` (0x8)|`DomainModuleLoad_V1`|告知性 (4)|

|事件|事件識別碼|描述|
|-----------|--------------|-----------------|
|`AssemblyLoad_V1`|154|載入組件時引發。|

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`AssemblyID`|`win:UInt64`|組件的唯一 ID。|
|`AppDomainID`|`win:UInt64`|這個組件之定義域的 ID。|
|`BindingID`|`win:UInt64`|可唯一識別組件繫結的 ID。|
|`AssemblyFlags`|`win:UInt32`|0x1：定義域中性組件。<br /><br /> 0x2：動態組件。<br /><br /> 0x4：組件具有原生映像。<br /><br /> 0x8：可回收組件。|
|`AssemblyName`|`win:UnicodeString`|完整的組件名稱。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR 實例的唯一識別碼。

## <a name="assemblyunload_v1-event"></a>AssemblyUnload_V1 事件

|引發事件的關鍵字|事件|層級|
|-----------------------------------|-----------|-----------|
|`LoaderKeyword` (0x8)|`DomainModuleLoad_V1`|告知性 (4)|

|事件|事件識別碼|描述|
|-----------|--------------|-----------------|
|`FireAssemblyUnload_V1`|155|載入組件時引發。|

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`AssemblyID`|`win:UInt64`|組件的唯一 ID。|
|`AppDomainID`|`win:UInt64`|這個組件之定義域的 ID。|
|`BindingID`|`win:UInt64`|可唯一識別組件繫結的 ID。|
|`AssemblyFlags`|`win:UInt32`|0x1：定義域中性組件。<br /><br /> 0x2：動態組件。<br /><br /> 0x4：組件具有原生映像。<br /><br /> 0x8：可回收組件。|
|`AssemblyName`|`win:UnicodeString`|完整的組件名稱。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR 實例的唯一識別碼。|

## <a name="assemblydcstart_v1-event"></a>AssemblyDCStart_V1 事件

|引發事件的關鍵字|事件|層級|
|-----------------------------------|-----------|-----------|
|`LoaderKeyword` (0x8)|`DomainModuleLoad_V1`|告知性 (4)|

|事件|事件識別碼|描述|
|-----------|--------------|-----------------|
|`AssemblyDCStart_V1`|155|在開始取消期間列舉組件。|

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`AssemblyID`|`win:UInt64`|組件的唯一 ID。|
|`AppDomainID`|`win:UInt64`|這個組件之定義域的 ID。|
|`BindingID`|`win:UInt64`|可唯一識別組件繫結的 ID。|
|`AssemblyFlags`|`win:UInt32`|0x1：定義域中性組件。<br /><br /> 0x2：動態組件。<br /><br /> 0x4：組件具有原生映像。<br /><br /> 0x8：可回收組件。|
|`AssemblyName`|`win:UnicodeString`|完整的組件名稱。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR 實例的唯一識別碼。|

## <a name="assemblyloadstart-event"></a>AssemblyLoadStart 事件

|引發事件的關鍵字|事件|層級|
|-----------------------------------|-----------|-----------|
|`Binder` (0x4) |`AssemblyLoadStart`|告知性 (4)|

|事件|事件識別碼|描述|
|-----------|--------------|-----------------|
|`AssemblyLoadStart`|290|已要求元件載入。

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`AssemblyName`|`win:UnicodeString`|元件名稱的名稱。|
|`AssemblyPath`|`win:UnicodeString`|元件名稱的路徑。|
|`RequestingAssembly`|`win:UnicodeString`|要求 ( "parent" ) 元件的名稱。|
|`AssemblyLoadContext`|`win:UnicodeString`|載入元件的內容。|
|`RequestingAssemblyLoadContext`|`win:UnicodeString`|載入要求 ( "parent" ) 元件的內容。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR 實例的唯一識別碼。|

## <a name="assemblyloadstop-event"></a>AssemblyLoadStop 事件

|引發事件的關鍵字|事件|層級|
|-----------------------------------|-----------|-----------|
|`Binder` (0x4) |`AssemblyLoadStart`|告知性 (4)|

|事件|事件識別碼|描述|
|-----------|--------------|-----------------|
|`AssemblyLoadStart`|291|已要求元件載入。

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`AssemblyName`|`win:UnicodeString`|元件名稱的名稱。|
|`AssemblyPath`|`win:UnicodeString`|元件名稱的路徑。|
|`RequestingAssembly`|`win:UnicodeString`|要求 ( "parent" ) 元件的名稱。|
|`AssemblyLoadContext`|`win:UnicodeString`|載入元件的內容。|
|`RequestingAssemblyLoadContext`|`win:UnicodeString`|載入要求 ( "parent" ) 元件的內容。|
|`Success`|`win:Boolean`|元件載入是否成功。|
|`ResultAssemblyName`|`win:UnicodeString`|載入的元件名稱。|
|`ResultAssemblyPath`|`win:UnicodeString`|從載入的元件路徑。|
|`Cached`|`win:UnicodeString`|是否快取負載。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR 實例的唯一識別碼。|

## <a name="resolutionattempted-event"></a>ResolutionAttempted 事件

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|-----------|
|`Binder` (0x4) |告知性 (4)|

|事件|事件識別碼|描述|
|-----------|--------------|-----------------|
|`ResolutionAttempted`|292|已要求元件載入。

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`AssemblyName`|`win:UnicodeString`|元件名稱的名稱。|
|`Stage`|`win:UInt16`|解決階段。<br/><br/>0：在載入中尋找。<br/><br/>1：元件載入內容</br><br/>2：應用程式元件。<br/><br/>3：預設元件載入內容回退。 <br/><br/>4：解析附屬元件。 <br/><br/>5：元件載入內容解析。<br/><br/>6： AppDomain 元件解析。
|`AssemblyLoadContext`|`win:UnicodeString`|載入元件的內容。|
|`Result`|`win:UInt16`|解析嘗試的結果。<br/><br/>0：成功<br/><br/>1：元件 NotFound<br/><br/>2：不相容的版本<br/><br/>3：不相符的元件名稱<br/><br/>4：失敗<br/><br/>5：例外狀況|
|`ResultAssemblyName`|`win:UnicodeString`|已解析的元件名稱。|
|`ResultAssemblyPath`|`win:UnicodeString`|從中解析的元件路徑。|
|`ErrorMessage`|`win:UnicodeString`|如果發生例外狀況，則為錯誤訊息。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR 實例的唯一識別碼。|

## <a name="assemblyloadcontextresolvinghandlerinvoked-event"></a>AssemblyLoadCoNtextResolvingHandlerInvoked 事件

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|-----------|
|`Binder` (0x4) |告知性 (4)|

|事件|事件識別碼|描述|
|-----------|--------------|-----------------|
|`AssemblyLoadContextResolvingHandlerInvoked`|293|已叫用 [AssemblyLoadCoNtext 解析](xref:System.Runtime.Loader.AssemblyLoadContext.Resolving) 處理常式。|

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`AssemblyName`|`win:UnicodeString`|元件名稱的名稱。|
|`HandlerName`|`win:UnicodeString`|叫用的處理常式名稱。|
|`AssemblyLoadContext`|`win:UnicodeString`|載入元件的內容。|
|`ResultAssemblyName`|`win:UnicodeString`|已解析的元件名稱。|
|`ResultAssemblyPath`|`win:UnicodeString`|從中解析的元件路徑。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR 實例的唯一識別碼。|

## <a name="appdomainassemblyresolvehandlerinvoked-event"></a>AppDomainAssemblyResolveHandlerInvoked 事件

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|-----------|
|`Binder` (0x4) |告知性 (4)|

|事件|事件識別碼|描述|
|-----------|--------------|-----------------|
|`AppDomainAssemblyResolveHandlerInvoked`|294|已叫用 <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> 處理常式。|

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`AssemblyName`|`win:UnicodeString`|元件名稱的名稱。|
|`HandlerName`|`win:UnicodeString`|叫用的處理常式名稱。|
|`ResultAssemblyName`|`win:UnicodeString`|已解析的元件名稱。|
|`ResultAssemblyPath`|`win:UnicodeString`|從中解析的元件路徑。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR 實例的唯一識別碼。|

## <a name="assemblyloadfromresolvehandlerinvoked-event"></a>AssemblyLoadFromResolveHandlerInvoked 事件

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|-----------|
|`Binder` (0x4) |告知性 (4)|

|事件|事件識別碼|描述|
|-----------|--------------|-----------------|
|`AssemblyLoadFromResolveHandlerInvoked`|295|已叫用 <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> 處理常式。|

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`AssemblyName`|`win:UnicodeString`|元件名稱的名稱。|
|`IsTrackedLoad`|`win:Boolean`|是否追蹤元件載入。|
|`RequestingAssemblyPath`|`win:UnicodeString`|要求元件的路徑。|
|`ComputedRequestedAssemblyPath`|`win:UnicodeString`|所要求元件的路徑。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR 實例的唯一識別碼。|

## <a name="knownpathprobed-event"></a>KnownPathProbed 事件

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|-----------|
|`Binder` (0x4) |告知性 (4)|

|事件|事件識別碼|描述|
|-----------|--------------|-----------------|
|`KnownPathProbed`|296|探查元件的已知路徑。|

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`FilePath`|`win:UnicodeString`|探查的路徑。|
|`Source`|`win:UInt16`|探查之路徑的來源。<br/><br/>0x0：應用程式元件。<br/><br/>0x1：應用程式原生映射路徑。<br/><br/>0x2：應用程式路徑。</br><br/>0x3：平臺資源根目錄。<br/><br/>0x4：附屬子目錄。</br>|
|`Result`|`win:UInt32`|探查的 HRESULT。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR 實例的唯一識別碼。|
