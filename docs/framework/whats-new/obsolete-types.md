---
title: .NET Framework 中過時的類型
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 4.5, obsolete types
- types, obsolete in .NET Framework 4.5
- obsolete types [.NET Framework]
ms.assetid: e636d024-0fac-45eb-b721-25a8c0ceca8f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6a1243ad856bc5f8cc104c9f2e08fce515a849d8
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2019
ms.locfileid: "66457064"
---
# <a name="obsolete-types-in-the-net-framework"></a>.NET Framework 中過時的類型
<a name="introduction"></a> 本文中的表格列出 .NET Framework 4.5 和 .NET Framework 4.6 中已淘汱類型 (依組件分組)。 使用下列連結查看每個組件中過時的型別和建議的替代方案。 因為這些型別已經過時，其所有成員也已經過時。 如需 .NET Framework 類別庫中其他過時成員的清單，請參閱[過時的成員](obsolete-members.md)。

- [系統組件中的過時類型](#obsolete_types_in_system_assemblies)

    - [mscorlib.dll](#mscorlib)

    - [System.Core.dll](#Core)

    - [System.Data.dll](#data)

    - [System.Data.OracleClient.dll](#oracleclient)

    - [System.Design.dll](#design)

    - [System.dll](#system)

    - [System.EnterpriseServices.dll](#enterpriseservices)

    - [System.Net.dll](#net)

    - [System.ServiceModel.dll](#servicemodel)

    - [System.Web.dll](#web)

    - [System.Web.Mobile.dll](#mobile)

    - [System.Workflow.Activities.dll](#workflow_activities)

    - [System.Workflow.ComponentModel.dll](#workflow_componentmodel)

    - [System.Workflow.Runtime.dll](#workflow_runtime)

    - [System.WorkflowServices.dll](#workflowservices)

    - [System.Xaml.dll](#xaml)

    - [System.Xml.dll](#xml)

    - [WindowsBase.dll](#WindowsBase)

- [Microsoft 組件中的過時類型](#obsolete_types_in_microsoft_assemblies)

    - [IEHost.dll 和 IEExec.exe](#IEHost)

    - [Microsoft.Build.Engine.dll](#Engine)

    - [Microsoft.JScript.dll](#jscript)

    - [Microsoft.VisualBasic.Compatibility.dll](#VBCompat)

    - [Microsoft.VisualBasic.Compatibility.Data.dll](#VBCompatData)

    - [Microsoft.VisualC.dll](#visualc)

<a name="obsolete_types_in_system_assemblies"></a>
## <a name="obsolete-types-in-system-assemblies"></a>系統組件中的過時型別
 下列表格將列出已經在系統組件中宣告為過時的型別。 這些組件是用於以 .NET Framework 為目標的一般用途應用程式開發。

<a name="mscorlib"></a>
### <a name="assembly-mscorlibdll"></a>組件：mscorlib.dll

|類型|訊息|
|----------|-------------|
|<xref:System.ExecutionEngineException?displayProperty=nameWithType>|這個型別先前會在執行階段中指出未指定的嚴重錯誤。 執行階段已不再引發這個例外狀況，因此這個型別已過時。|
|<xref:System.Collections.CaseInsensitiveHashCodeProvider?displayProperty=nameWithType>|請改用 <xref:System.StringComparer?displayProperty=nameWithType>。|
|<xref:System.Collections.IHashCodeProvider?displayProperty=nameWithType>|請改用 <xref:System.Collections.IEqualityComparer?displayProperty=nameWithType>。|
|<xref:System.Configuration.Assemblies.AssemblyHash?displayProperty=nameWithType>|<xref:System.Configuration.Assemblies.AssemblyHash> 類別已被取代。|
|<xref:System.Diagnostics.Contracts.Internal.ContractHelper?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。 改為在 System.Runtime.CompilerServices 命名空間中使用 <xref:System.Runtime.CompilerServices.ContractHelper?displayProperty=nameWithType> 類別。|
|<xref:System.Reflection.Emit.UnmanagedMarshal?displayProperty=nameWithType>|有可用的替代 API ：請改為發出 <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> 自訂屬性。|
|<xref:System.Runtime.InteropServices.BIND_OPTS?displayProperty=nameWithType>|請改用 <xref:System.Runtime.InteropServices.ComTypes.BIND_OPTS?displayProperty=nameWithType>。|
|<xref:System.Runtime.InteropServices.BINDPTR?displayProperty=nameWithType>|請改用 <xref:System.Runtime.InteropServices.ComTypes.BINDPTR?displayProperty=nameWithType>。|
|<xref:System.Runtime.InteropServices.CALLCONV?displayProperty=nameWithType>|請改用 <xref:System.Runtime.InteropServices.ComTypes.CALLCONV?displayProperty=nameWithType>。|
|<xref:System.Runtime.InteropServices.CONNECTDATA?displayProperty=nameWithType>|請改用 <xref:System.Runtime.InteropServices.ComTypes.CONNECTDATA?displayProperty=nameWithType>。|
|<xref:System.Runtime.InteropServices.DESCKIND?displayProperty=nameWithType>|請改用 <xref:System.Runtime.InteropServices.ComTypes.DESCKIND?displayProperty=nameWithType>。|
|<xref:System.Runtime.InteropServices.DISPPARAMS?displayProperty=nameWithType>|請改用 <xref:System.Runtime.InteropServices.ComTypes.DISPPARAMS?displayProperty=nameWithType>。|
|<xref:System.Runtime.InteropServices.ELEMDESC?displayProperty=nameWithType>|請改用 <xref:System.Runtime.InteropServices.ComTypes.ELEMDESC?displayProperty=nameWithType>。|
|<xref:System.Runtime.InteropServices.EXCEPINFO?displayProperty=nameWithType>|請改用 <xref:System.Runtime.InteropServices.ComTypes.EXCEPINFO?displayProperty=nameWithType>。|
|<xref:System.Runtime.InteropServices.FILETIME?displayProperty=nameWithType>|請改用 <xref:System.Runtime.InteropServices.ComTypes.FILETIME?displayProperty=nameWithType>。|
|<xref:System.Runtime.InteropServices.FUNCDESC?displayProperty=nameWithType>|請改用 <xref:System.Runtime.InteropServices.ComTypes.FUNCDESC?displayProperty=nameWithType>。|
|<xref:System.Runtime.InteropServices.FUNCFLAGS?displayProperty=nameWithType>|請改用 <xref:System.Runtime.InteropServices.ComTypes.FUNCFLAGS?displayProperty=nameWithType>。|
|<xref:System.Runtime.InteropServices.FUNCKIND?displayProperty=nameWithType>|請改用 <xref:System.Runtime.InteropServices.ComTypes.FUNCKIND?displayProperty=nameWithType>。|
|<xref:System.Runtime.InteropServices.IDispatchImplAttribute?displayProperty=nameWithType>|這個屬性已被取代，將在未來的版本中移除。|
|<xref:System.Runtime.InteropServices.IDispatchImplType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.IDispatchImplAttribute?displayProperty=nameWithType> 已被取代。|
|<xref:System.Runtime.InteropServices.IDLDESC?displayProperty=nameWithType>|請改用 <xref:System.Runtime.InteropServices.ComTypes.IDLDESC?displayProperty=nameWithType>。|
|<xref:System.Runtime.InteropServices.IDLFLAG?displayProperty=nameWithType>|請改用 <xref:System.Runtime.InteropServices.ComTypes.IDLFLAG?displayProperty=nameWithType>。|
|<xref:System.Runtime.InteropServices.IMPLTYPEFLAGS?displayProperty=nameWithType>|請改用 <xref:System.Runtime.InteropServices.ComTypes.IMPLTYPEFLAGS?displayProperty=nameWithType>。|
|<xref:System.Runtime.InteropServices.INVOKEKIND?displayProperty=nameWithType>|請改用 <xref:System.Runtime.InteropServices.ComTypes.INVOKEKIND?displayProperty=nameWithType>。|
|<xref:System.Runtime.InteropServices.LIBFLAGS?displayProperty=nameWithType>|請改用 <xref:System.Runtime.InteropServices.ComTypes.LIBFLAGS?displayProperty=nameWithType>。|
|<xref:System.Runtime.InteropServices.PARAMDESC?displayProperty=nameWithType>|請改用 <xref:System.Runtime.InteropServices.ComTypes.PARAMDESC?displayProperty=nameWithType>。|
|<xref:System.Runtime.InteropServices.PARAMFLAG?displayProperty=nameWithType>|請改用 <xref:System.Runtime.InteropServices.ComTypes.PARAMFLAG?displayProperty=nameWithType>。|
|<xref:System.Runtime.InteropServices.SetWin32ContextInIDispatchAttribute?displayProperty=nameWithType>|這個屬性已被取代。 應用程式定義域不再遵循 IDispatch 呼叫中的啟動內容界限。|
|<xref:System.Runtime.InteropServices.STATSTG?displayProperty=nameWithType>|請改用 <xref:System.Runtime.InteropServices.ComTypes.STATSTG?displayProperty=nameWithType>。|
|<xref:System.Runtime.InteropServices.SYSKIND?displayProperty=nameWithType>|請改用 <xref:System.Runtime.InteropServices.ComTypes.SYSKIND?displayProperty=nameWithType>。|
|<xref:System.Runtime.InteropServices.TYPEATTR?displayProperty=nameWithType>|請改用 <xref:System.Runtime.InteropServices.ComTypes.TYPEATTR?displayProperty=nameWithType>。|
|<xref:System.Runtime.InteropServices.TYPEDESC?displayProperty=nameWithType>|請改用 <xref:System.Runtime.InteropServices.ComTypes.TYPEDESC?displayProperty=nameWithType>。|
|<xref:System.Runtime.InteropServices.TYPEFLAGS?displayProperty=nameWithType>|請改用 <xref:System.Runtime.InteropServices.ComTypes.TYPEFLAGS?displayProperty=nameWithType>。|
|<xref:System.Runtime.InteropServices.TYPEKIND?displayProperty=nameWithType>|請改用 <xref:System.Runtime.InteropServices.ComTypes.TYPEKIND?displayProperty=nameWithType>。|
|<xref:System.Runtime.InteropServices.TYPELIBATTR?displayProperty=nameWithType>|請改用 <xref:System.Runtime.InteropServices.ComTypes.TYPELIBATTR?displayProperty=nameWithType>。|
|<xref:System.Runtime.InteropServices.UCOMIBindCtx?displayProperty=nameWithType>|請改用 <xref:System.Runtime.InteropServices.ComTypes.IBindCtx?displayProperty=nameWithType>。|
|<xref:System.Runtime.InteropServices.UCOMIConnectionPoint?displayProperty=nameWithType>|請改用 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint?displayProperty=nameWithType>。|
|<xref:System.Runtime.InteropServices.UCOMIConnectionPointContainer?displayProperty=nameWithType>|請改用 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer?displayProperty=nameWithType>。|
|<xref:System.Runtime.InteropServices.UCOMIEnumConnectionPoints?displayProperty=nameWithType>|請改用 <xref:System.Runtime.InteropServices.ComTypes.IEnumConnectionPoints?displayProperty=nameWithType>。|
|<xref:System.Runtime.InteropServices.UCOMIEnumConnections?displayProperty=nameWithType>|請改用 <xref:System.Runtime.InteropServices.ComTypes.IEnumConnections?displayProperty=nameWithType>。|
|<xref:System.Runtime.InteropServices.UCOMIEnumMoniker?displayProperty=nameWithType>|請改用 <xref:System.Runtime.InteropServices.ComTypes.IEnumMoniker?displayProperty=nameWithType>。|
|<xref:System.Runtime.InteropServices.UCOMIEnumString?displayProperty=nameWithType>|請改用 <xref:System.Runtime.InteropServices.ComTypes.IEnumString?displayProperty=nameWithType>。|
|<xref:System.Runtime.InteropServices.UCOMIEnumVARIANT?displayProperty=nameWithType>|請改用 <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT?displayProperty=nameWithType>。|
|<xref:System.Runtime.InteropServices.UCOMIMoniker?displayProperty=nameWithType>|請改用 <xref:System.Runtime.InteropServices.ComTypes.IMoniker?displayProperty=nameWithType>。|
|<xref:System.Runtime.InteropServices.UCOMIPersistFile?displayProperty=nameWithType>|請改用 <xref:System.Runtime.InteropServices.ComTypes.IPersistFile?displayProperty=nameWithType>。|
|<xref:System.Runtime.InteropServices.UCOMIRunningObjectTable?displayProperty=nameWithType>|請改用 <xref:System.Runtime.InteropServices.ComTypes.IRunningObjectTable?displayProperty=nameWithType>。|
|<xref:System.Runtime.InteropServices.UCOMIStream?displayProperty=nameWithType>|請改用 <xref:System.Runtime.InteropServices.ComTypes.IStream?displayProperty=nameWithType>。|
|<xref:System.Runtime.InteropServices.UCOMITypeComp?displayProperty=nameWithType>|請改用 <xref:System.Runtime.InteropServices.ComTypes.ITypeComp?displayProperty=nameWithType>。|
|<xref:System.Runtime.InteropServices.UCOMITypeInfo?displayProperty=nameWithType>|請改用 <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo?displayProperty=nameWithType>。|
|<xref:System.Runtime.InteropServices.UCOMITypeLib?displayProperty=nameWithType>|請改用 <xref:System.Runtime.InteropServices.ComTypes.ITypeLib?displayProperty=nameWithType>。|
|<xref:System.Runtime.InteropServices.VARDESC?displayProperty=nameWithType>|請改用 <xref:System.Runtime.InteropServices.ComTypes.VARDESC?displayProperty=nameWithType>。|
|<xref:System.Runtime.InteropServices.VARFLAGS?displayProperty=nameWithType>|請改用 <xref:System.Runtime.InteropServices.ComTypes.VARFLAGS?displayProperty=nameWithType> 。|
|<xref:System.Security.SecurityCriticalScope?displayProperty=nameWithType>|<xref:System.Security.SecurityCriticalScope> 僅用於 .NET 2.0 透明度相容性。|
|<xref:System.Security.SecurityTreatAsSafeAttribute?displayProperty=nameWithType>|<xref:System.Security.SecurityTreatAsSafeAttribute> 僅用於 .NET 2.0 透明度相容性。 請改用 <xref:System.Security.SecuritySafeCriticalAttribute?displayProperty=nameWithType>。|
|<xref:System.Security.Policy.FirstMatchCodeGroup?displayProperty=nameWithType>|這個型別已經過時，將在未來的 .NET Framework 發行版本中移除。|
|<xref:System.Security.Policy.PermissionRequestEvidence?displayProperty=nameWithType>|組件層級宣告式安全性已過期，CLR 預設不再強制使用。|
|<xref:System.Security.Policy.UnionCodeGroup?displayProperty=nameWithType>|這個型別已經過時，將在未來的 .NET Framework 發行版本中移除。|

 [回到頁首](#introduction)

<a name="Core"></a>
### <a name="assembly-systemcoredll"></a>組件︰System.Core.dll

|類型|訊息|
|----------|-------------|
|<xref:System.Runtime.CompilerServices.ExecutionScope?displayProperty=nameWithType>|使用這個型別會產生編譯器錯誤。<br /><br /> 請勿使用這個型別。|

 [回到頁首](#introduction)

<a name="data"></a>
### <a name="assembly-systemdatadll"></a>組件︰System.Data.dll

|類型|訊息|
|----------|-------------|
|<xref:System.Data.DataSysDescriptionAttribute?displayProperty=nameWithType>|<xref:System.Data.DataSysDescriptionAttribute> 已被取代。|
|<xref:System.Data.PropertyAttributes?displayProperty=nameWithType>|<xref:System.Data.PropertyAttributes> 已被取代。|
|<xref:System.Data.TypedDataSetGenerator?displayProperty=nameWithType>|<xref:System.Data.TypedDataSetGenerator> 類別將在未來的發行版本中移除。 請使用 System.Design.dll 中的 <xref:System.Data.Design.TypedDataSetGenerator?displayProperty=nameWithType>。|
|<xref:System.Xml.XmlDataDocument?displayProperty=nameWithType>|<xref:System.Xml.XmlDataDocument> 類別將在未來的發行版本中移除。|

 [回到頁首](#introduction)

<a name="oracleclient"></a>
### <a name="assembly-systemdataoracleclientdll"></a>組件︰System.Data.OracleClient.dll

|類型|訊息|
|----------|-------------|
|<xref:System.Data.OracleClient.OracleClientFactory?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleClientFactory> 已被取代。|
|<xref:System.Data.OracleClient.OracleCommand?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleCommand> 已被取代。|
|<xref:System.Data.OracleClient.OracleCommandBuilder?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleCommandBuilder> 已被取代。|
|<xref:System.Data.OracleClient.OracleConnection?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleConnection> 已被取代。|
|<xref:System.Data.OracleClient.OracleConnectionStringBuilder?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleConnectionStringBuilder> 已被取代。|
|<xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleDataAdapter> 已被取代。|
|<xref:System.Data.OracleClient.OraclePermission?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OraclePermission> 已被取代。|
|<xref:System.Data.OracleClient.OraclePermissionAttribute?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OraclePermissionAttribute?displayProperty=nameWithType> 已被取代。|

 [回到頁首](#introduction)

<a name="design"></a>
### <a name="assembly-systemdesigndll"></a>組件︰System.Design.dll

|類型|訊息|
|----------|-------------|
|<xref:System.ComponentModel.Design.LocalizationExtenderProvider?displayProperty=nameWithType>|這個類別已被取代。 請改用 <xref:System.ComponentModel.Design.Serialization.CodeDomLocalizationProvider?displayProperty=nameWithType>。|
|<xref:System.Web.UI.Design.DataBindingCollectionConverter?displayProperty=nameWithType>|由於資料繫結編輯功能是經由 <xref:System.ComponentModel.Design.DesignerActionList?displayProperty=nameWithType> 而非屬性方格啟動，因此不建議使用這個型別。|
|<xref:System.Web.UI.Design.DataBindingCollectionEditor?displayProperty=nameWithType>|由於資料繫結編輯功能是經由 <xref:System.ComponentModel.Design.DesignerActionList?displayProperty=nameWithType> 而非屬性方格啟動，因此不建議使用這個型別。|
|<xref:System.Web.UI.Design.IControlDesignerBehavior?displayProperty=nameWithType>|建議的替代方案是 <xref:System.Web.UI.Design.IControlDesignerTag?displayProperty=nameWithType> 和 <xref:System.Web.UI.Design.IControlDesignerView?displayProperty=nameWithType>。|
|<xref:System.Web.UI.Design.IHtmlControlDesignerBehavior?displayProperty=nameWithType>|建議的替代方案是 <xref:System.Web.UI.Design.IControlDesignerTag?displayProperty=nameWithType> 和 <xref:System.Web.UI.Design.IControlDesignerView?displayProperty=nameWithType>。|
|<xref:System.Web.UI.Design.ITemplateEditingFrame?displayProperty=nameWithType>|由於範本編輯功能是在 <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType> 中處理，因此不建議使用這個型別。 若要支援範本編輯功能，請公開 <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> 屬性中的範本資料，並且呼叫 <xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A?displayProperty=nameWithType>。|
|<xref:System.Web.UI.Design.IWebFormReferenceManager?displayProperty=nameWithType>|建議的替代做法是 <xref:System.Web.UI.Design.WebFormsReferenceManager?displayProperty=nameWithType>。 <xref:System.Web.UI.Design.WebFormsReferenceManager> 包含其他功能而且允許更大的擴充性。 若要取得 <xref:System.Web.UI.Design.WebFormsReferenceManager>，請從您的 `RootDesigner.ReferenceManager` 使用 <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType> 屬性。|
|<xref:System.Web.UI.Design.IWebFormsDocumentService?displayProperty=nameWithType>|建議的替代做法是 <xref:System.Web.UI.Design.WebFormsRootDesigner?displayProperty=nameWithType>。 <xref:System.Web.UI.Design.WebFormsRootDesigner> 包含其他功能而且允許更大的擴充性。 若要取得 <xref:System.Web.UI.Design.WebFormsRootDesigner>，請從您的 <xref:System.Web.UI.Design.ControlDesigner.RootDesigner%2A> 使用 <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType> 屬性。|
|<xref:System.Web.UI.Design.ITemplateEditingService?displayProperty=nameWithType>|由於範本編輯功能是在 <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType> 中處理，因此不建議使用這個型別。 若要支援範本編輯功能，請公開 <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> 屬性中的範本資料，並且呼叫 <xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A?displayProperty=nameWithType>。|
|<xref:System.Web.UI.Design.ReadWriteControlDesigner?displayProperty=nameWithType>|建議的替代方案是 <xref:System.Web.UI.Design.ContainerControlDesigner?displayProperty=nameWithType>，因為它會使用 <xref:System.Web.UI.Design.EditableDesignerRegion?displayProperty=nameWithType> 來編輯內容。 設計工具區域可讓您有效控制所編輯的內容。|
|<xref:System.Web.UI.Design.TemplateEditingService?displayProperty=nameWithType>|由於範本編輯功能是在 <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType> 中處理，因此不建議使用這個型別。 若要支援範本編輯功能，請公開 <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> 屬性中的範本資料，並且呼叫 <xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A?displayProperty=nameWithType>。|
|<xref:System.Web.UI.Design.TemplateEditingVerb?displayProperty=nameWithType>|由於範本編輯功能是在 <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType> 中處理，因此不建議使用這個型別。 若要支援範本編輯功能，請公開 <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> 屬性中的範本資料，並且呼叫 <xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A?displayProperty=nameWithType>。|
|<xref:System.Web.UI.Design.WebControls.CalendarAutoFormatDialog?displayProperty=nameWithType>|由於 [自動格式設定] 對話方塊是由設計工具主應用程式啟動，因此不建議使用這個型別。 可用的自動格式設定清單會公開在 <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType> 屬性中的 <xref:System.Web.UI.Design.ControlDesigner.AutoFormats%2A?displayProperty=nameWithType> 上。|
|<xref:System.Web.UI.Design.WebControls.PanelDesigner?displayProperty=nameWithType>|建議的替代方案是 <xref:System.Web.UI.Design.WebControls.PanelContainerDesigner?displayProperty=nameWithType>，因為它會使用 <xref:System.Web.UI.Design.EditableDesignerRegion?displayProperty=nameWithType> 來編輯內容。 設計工具區域可讓您有效控制所編輯的內容。|

 [回到頁首](#introduction)

<a name="system"></a>
### <a name="assembly-systemdll"></a>組件︰System.dll

|類型|訊息|
|----------|-------------|
|<xref:System.ComponentModel.IComNativeDescriptorHandler?displayProperty=nameWithType>|這個介面已被取代。 請改為加入 <xref:System.ComponentModel.TypeDescriptionProvider?displayProperty=nameWithType> 來處理 <xref:System.ComponentModel.TypeDescriptor.ComObjectType%2A?displayProperty=nameWithType> 型別。|
|<xref:System.ComponentModel.RecommendedAsConfigurableAttribute?displayProperty=nameWithType>|請改用 <xref:System.ComponentModel.SettingsBindableAttribute?displayProperty=nameWithType> 來處理新的設定模型。|
|<xref:System.ComponentModel.Design.Serialization.RootDesignerSerializerAttribute?displayProperty=nameWithType>|這個屬性已被取代。 請改用 <xref:System.ComponentModel.Design.Serialization.DesignerSerializerAttribute?displayProperty=nameWithType>。|
|<xref:System.Diagnostics.DiagnosticsConfigurationHandler?displayProperty=nameWithType>|這個類別已被取代。|
|<xref:System.Diagnostics.PerformanceCounterManager?displayProperty=nameWithType>|這個類別已被取代。 請改為透過 <xref:System.Diagnostics.PerformanceCounter?displayProperty=nameWithType> 類別使用效能計數器。|
|<xref:System.Net.GlobalProxySelection?displayProperty=nameWithType>|這個類別已被取代。 請改用 <xref:System.Net.WebRequest.DefaultWebProxy%2A?displayProperty=nameWithType> 來存取和設定全域預設 Proxy。 請使用 'null' 而非 <xref:System.Net.GlobalProxySelection.GetEmptyWebProxy%2A?displayProperty=nameWithType>。|
|<xref:System.Net.Sockets.SocketClientAccessPolicyProtocol?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。<br /><br /> 使用這個型別會產生編譯器錯誤。<br /><br /> 這個 API 支援 .NET Framework 基礎結構，並不適合直接從您的程式碼中使用。|

 [回到頁首](#introduction)

<a name="enterpriseservices"></a>
### <a name="assembly-systementerpriseservicesdll"></a>組件︰System.EnterpriseServices.dll

|類型|訊息|
|----------|-------------|
|<xref:System.EnterpriseServices.RegistrationHelperTx?displayProperty=nameWithType>|<xref:System.EnterpriseServices.RegistrationHelperTx> 類別已被取代。|

 [回到頁首](#introduction)

<a name="net"></a>
### <a name="assembly-systemnetdll"></a>組件︰System.Net.dll

|類型|訊息|
|----------|-------------|
|<xref:System.Net.INetworkProgress?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。<br /><br /> 使用這個型別會產生編譯器錯誤。<br /><br /> 這個 API 支援 .NET Framework 基礎結構，並不適合直接從您的程式碼中使用。|
|<xref:System.Net.IUnsafeWebRequestCreate?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。<br /><br /> 使用這個型別會產生編譯器錯誤。<br /><br /> 這個 API 支援 .NET Framework 基礎結構，並不適合直接從您的程式碼中使用。|
|<xref:System.Net.NetworkProgressChangedEventArgs?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。<br /><br /> 使用這個型別會產生編譯器錯誤。<br /><br /> 這個 API 支援 .NET Framework 基礎結構，並不適合直接從您的程式碼中使用。|
|<xref:System.Net.UiSynchronizationContext?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。<br /><br /> 使用這個型別會產生編譯器錯誤。<br /><br /> 這個 API 支援 .NET Framework 基礎結構，並不適合直接從您的程式碼中使用。|
|<xref:System.Net.Sockets.HttpPolicyDownloaderProtocol?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。<br /><br /> 使用這個型別會產生編譯器錯誤。<br /><br /> 這個 API 支援 .NET Framework 基礎結構，並不適合直接從您的程式碼中使用。|
|<xref:System.Net.Sockets.SecurityCriticalAction?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。<br /><br /> 使用這個型別會產生編譯器錯誤。<br /><br /> 這個 API 支援 .NET Framework 基礎結構，並不適合直接從您的程式碼中使用。|
|<xref:System.Net.Sockets.SocketPolicy?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。<br /><br /> 使用這個型別會產生編譯器錯誤。<br /><br /> 這個 API 支援 .NET Framework 基礎結構，並不適合直接從您的程式碼中使用。|
|<xref:System.Net.Sockets.UdpAnySourceMulticastClient?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。<br /><br /> 使用這個型別會產生編譯器錯誤。<br /><br /> 這個 API 支援 .NET Framework 基礎結構，並不適合直接從您的程式碼中使用。|
|<xref:System.Net.Sockets.UdpSingleSourceMulticastClient?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。<br /><br /> 使用這個型別會產生編譯器錯誤。<br /><br /> 這個 API 支援 .NET Framework 基礎結構，並不適合直接從您的程式碼中使用。|

 [回到頁首](#introduction)

<a name="servicemodel"></a>
### <a name="assembly-systemservicemodeldll"></a>組件︰System.ServiceModel.dll

|類型|訊息|
|----------|-------------|
|<xref:System.ServiceModel.NetPeerTcpBinding?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。<br /><br /> 對等通道功能已經過時，未來將會移除。|
|<xref:System.ServiceModel.Channels.HttpCookieContainerBindingElement?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。<br /><br /> 這個型別已經過時。 若要啟用 HTTP <xref:System.Net.CookieContainer>，請使用 Http 繫結或 `AllowCookies` 的 <xref:System.ServiceModel.Channels.HttpTransportBindingElement> 屬性。|
|<xref:System.ServiceModel.Channels.PeerCustomResolverBindingElement?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。<br /><br /> 對等通道功能已經過時，未來將會移除。|
|<xref:System.ServiceModel.Channels.PeerTransportBindingElement?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。<br /><br /> 對等通道功能已經過時，未來將會移除。|
|<xref:System.ServiceModel.Configuration.NetPeerTcpBindingCollectionElement?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。<br /><br /> 對等通道功能已經過時，未來將會移除。|
|<xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。<br /><br /> 對等通道功能已經過時，未來將會移除。|
|<xref:System.ServiceModel.Configuration.PeerTransportElement?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。<br /><br /> 對等通道功能已經過時，未來將會移除。|
|<xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。<br /><br /> 對等通道功能已經過時，未來將會移除。|

 [回到頁首](#introduction)

<a name="web"></a>
### <a name="assembly-systemwebdll"></a>組件︰System.Web.dll

|類型|訊息|
|----------|-------------|
|<xref:System.Web.Configuration.PassportAuthentication?displayProperty=nameWithType>|這個型別已經過時。 已不再支援 Passport 驗證產品，並且以 [Microsoft 帳戶](https://go.microsoft.com/fwlink/?LinkId=733413)取代該產品|
|<xref:System.Web.Mail.MailAttachment?displayProperty=nameWithType>|建議的替代做法是 <xref:System.Net.Mail.Attachment?displayProperty=nameWithType>。|
|<xref:System.Web.Mail.MailEncoding?displayProperty=nameWithType>|建議的替代做法是 <xref:System.Net.Mime.TransferEncoding?displayProperty=nameWithType>。|
|<xref:System.Web.Mail.MailFormat?displayProperty=nameWithType>|建議的替代做法是 <xref:System.Net.Mail.MailMessage.IsBodyHtml%2A?displayProperty=nameWithType>。|
|<xref:System.Web.Mail.MailMessage?displayProperty=nameWithType>|建議的替代做法是 <xref:System.Net.Mail.MailMessage?displayProperty=nameWithType>。|
|<xref:System.Web.Mail.MailPriority?displayProperty=nameWithType>|建議的替代做法是 <xref:System.Net.Mail.MailPriority?displayProperty=nameWithType>。|
|<xref:System.Web.Mail.SmtpMail?displayProperty=nameWithType>|建議的替代做法是 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>。|
|<xref:System.Web.Security.PassportAuthenticationEventArgs?displayProperty=nameWithType>|這個型別已經過時。 已不再支援 Passport 驗證產品，並且以 [Microsoft 帳戶](https://go.microsoft.com/fwlink/?LinkId=733413)取代該產品|
|<xref:System.Web.Security.PassportAuthenticationEventHandler?displayProperty=nameWithType>|這個型別已經過時。 已不再支援 Passport 驗證產品，並且以 [Microsoft 帳戶](https://go.microsoft.com/fwlink/?LinkId=733413)取代該產品|
|<xref:System.Web.Security.PassportAuthenticationModule?displayProperty=nameWithType>|這個型別已經過時。 已不再支援 Passport 驗證產品，並且以 [Microsoft 帳戶](https://go.microsoft.com/fwlink/?LinkId=733413)取代該產品|
|<xref:System.Web.Security.PassportIdentity?displayProperty=nameWithType>|這個型別已經過時。 已不再支援 Passport 驗證產品，並且以 [Microsoft 帳戶](https://go.microsoft.com/fwlink/?LinkId=733413)取代該產品|
|<xref:System.Web.Security.PassportPrincipal?displayProperty=nameWithType>|這個型別已經過時。 已不再支援 Passport 驗證產品，並且以 [Microsoft 帳戶](https://go.microsoft.com/fwlink/?LinkId=733413)取代該產品|
|<xref:System.Web.UI.ObjectConverter?displayProperty=nameWithType>|建議的替代方案是 <xref:System.Convert?displayProperty=nameWithType> 和 <xref:System.String.Format%2A?displayProperty=nameWithType>。|

 [回到頁首](#introduction)

<a name="mobile"></a>
### <a name="assembly-systemwebmobiledll"></a>組件︰System.Web.Mobile.dll

|類型|訊息|
|----------|-------------|
|<xref:System.Web.Mobile.CookielessData?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.Mobile.DeviceFilterElement?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.Mobile.DeviceFilterElementCollection?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.Mobile.DeviceFiltersSection?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.Mobile.ErrorHandlerModule?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.Mobile.MobileCapabilities?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.Mobile.MobileDeviceCapabilitiesSectionHandler?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.Mobile.MobileErrorInfo?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.Mobile.MobileFormsAuthentication?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.Design.MobileControls.IMobileDesigner?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.Design.MobileControls.IMobileWebFormServices?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.Design.MobileControls.MobileResource?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.Design.MobileControls.Converters.DataFieldConverter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.Design.MobileControls.Converters.DataMemberConverter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.AdRotator?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Alignment?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.ArrayListCollectionBase?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.BaseValidator?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.BooleanOption?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Calendar?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Command?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.CommandFormat?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.CompareValidator?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Constants?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.ControlElement?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.ControlElementCollection?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.ControlPager?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.CustomValidator?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.DesignerAdapterAttribute?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.DeviceElement?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.DeviceElementCollection?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.DeviceOverridableAttribute?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.DeviceSpecific?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoice?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoiceCollection?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoiceControlBuilder?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoiceTemplateBuilder?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoiceTemplateContainer?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.DeviceSpecificControlBuilder?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.ErrorFormatterPage?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.FontInfo?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.FontSize?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Form?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.FormControlBuilder?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.FormMethod?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.IControlAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Image?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.IObjectListFieldCollection?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.IPageAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.ItemPager?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.ITemplateable?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Label?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Link?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.List?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.ListCommandEventArgs?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.ListCommandEventHandler?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.ListControlBuilder?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.ListDataBindEventArgs?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.ListDataBindEventHandler?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.ListDecoration?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.ListSelectType?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.LiteralLink?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.LiteralText?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.LiteralTextContainerControlBuilder?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.LiteralTextControlBuilder?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.LoadItemsEventArgs?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.LoadItemsEventHandler?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.MobileControl?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.MobileControlBuilder?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.MobileControlsSection?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.MobileControlsSectionHandler?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.MobileListItem?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.MobileListItemCollection?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.MobileListItemType?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.MobilePage?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.MobileTypeNameConverter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.MobileUserControl?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.ObjectList?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.ObjectListCommand?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.ObjectListCommandCollection?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.ObjectListCommandEventArgs?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.ObjectListCommandEventHandler?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.ObjectListControlBuilder?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.ObjectListDataBindEventArgs?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.ObjectListDataBindEventHandler?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.ObjectListField?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.ObjectListFieldCollection?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.ObjectListItem?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.ObjectListItemCollection?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.ObjectListSelectEventArgs?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.ObjectListSelectEventHandler?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.ObjectListShowCommandsEventArgs?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.ObjectListShowCommandsEventHandler?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.ObjectListTitleAttribute?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.ObjectListViewMode?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.PagedControl?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.PagerStyle?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Panel?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.PanelControlBuilder?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.PersistNameAttribute?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.PhoneCall?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.RangeValidator?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.RegularExpressionValidator?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.RequiredFieldValidator?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.SelectionList?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Style?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.StyleSheet?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.StyleSheetControlBuilder?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.TemplateContainer?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.TextBox?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.TextBoxControlBuilder?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.TextControl?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.TextView?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.TextViewElement?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.ValidationSummary?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Wrapping?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlCalendarAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlCommandAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlFormAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlImageAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlLinkAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlMobileTextWriter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlPageAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlPhoneCallAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlSelectionListAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlTextBoxAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.ControlAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlCalendarAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlCommandAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlControlAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlFormAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlImageAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlLabelAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlLinkAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlListAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlLiteralTextAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlMobileTextWriter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlObjectListAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlPageAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlPanelAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlPhoneCallAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlSelectionListAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlTextBoxAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlTextViewAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlValidationSummaryAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlValidatorAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.MobileTextWriter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.MultiPartWriter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.UpWmlMobileTextWriter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.UpWmlPageAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.WmlCalendarAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.WmlCommandAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.WmlControlAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.WmlFormAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.WmlImageAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.WmlLabelAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.WmlLinkAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.WmlListAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.WmlLiteralTextAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.WmlMobileTextWriter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.WmlObjectListAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.WmlPageAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.WmlPanelAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.WmlPhoneCallAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.WmlPostFieldType?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.WmlSelectionListAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.WmlTextBoxAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.WmlTextViewAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.WmlValidationSummaryAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.WmlValidatorAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.Doctype?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.StyleSheetLocation?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlCalendarAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlCommandAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlControlAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlCssHandler?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlFormAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlImageAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlLabelAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlLinkAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlListAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlLiteralTextAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlMobileTextWriter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlObjectListAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlPageAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlPanelAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlPhoneCallAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlSelectionListAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlTextBoxAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlTextViewAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlValidationSummaryAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlValidatorAdapter?displayProperty=nameWithType>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](https://go.microsoft.com/fwlink/?LinkId=157231)。|

 [回到頁首](#introduction)

<a name="workflow_activities"></a>
### <a name="assembly-systemworkflowactivitiesdll"></a>組件︰System.Workflow.Activities.dll

|類型|訊息|
|----------|-------------|
|<xref:System.Workflow.Activities?displayProperty=nameWithType> 命名空間中的所有型別。|在 .NET Framework 4.5 中首先被取代。<br /><br /> System.Workflow.\* 類型已被取代。 請改用 <xref:System.Activities>.\* 的新類型。|
|<xref:System.Workflow.Activities.Configuration.ActiveDirectoryRoleFactoryConfiguration?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。<br /><br /> System.Workflow.\* 類型已被取代。 請改用 <xref:System.Activities>.\* 的新類型。|
|<xref:System.Workflow.Activities.Rules.RuleActionTrackingEvent?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。<br /><br /> System.Workflow.\* 類型已被取代。 請改用 <xref:System.Activities>.\* 的新類型。|
|<xref:System.Workflow.Activities.Rules.RuleConditionReference?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。<br /><br /> System.Workflow.\* 類型已被取代。 請改用 <xref:System.Activities>.\* 的新類型。|
|<xref:System.Workflow.Activities.Rules.RuleSetReference?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。<br /><br /> System.Workflow.\* 類型已被取代。 請改用 <xref:System.Activities>.\* 的新類型。|

 [回到頁首](#introduction)

<a name="workflow_componentmodel"></a>
### <a name="assembly-systemworkflowcomponentmodeldll"></a>組件︰System.Workflow.ComponentModel.dll

|類型|訊息|
|----------|-------------|
|在 <xref:System.Workflow.ComponentModel> 命名空間中除了 <xref:System.Workflow.ComponentModel.GetValueOverride?displayProperty=nameWithType> 和 <xref:System.Workflow.ComponentModel.SetValueOverride?displayProperty=nameWithType> 之外的所有型別|在 .NET Framework 4.5 中首先被取代。<br /><br /> System.Workflow.\* 類型已被取代。 請改用 <xref:System.Activities>.\* 的新類型。|
|在 <xref:System.Workflow.ComponentModel.Compiler> 命名空間中除了 <xref:System.Workflow.ComponentModel.Compiler.ValidationError?displayProperty=nameWithType> 和 <xref:System.Workflow.ComponentModel.Compiler.ValidationErrorCollection?displayProperty=nameWithType> 之外的所有型別|在 .NET Framework 4.5 中首先被取代。<br /><br /> System.Workflow.\* 類型已被取代。 請改用 <xref:System.Activities>.\* 的新類型。|
|在 <xref:System.Workflow.ComponentModel.Design> 命名空間中除了 <xref:System.Workflow.ComponentModel.Design.ConnectorEventHandler> 之外的所有型別|在 .NET Framework 4.5 中首先被取代。<br /><br /> System.Workflow.\* 類型已被取代。 請改用 <xref:System.Activities>.\* 的新類型。|
|<xref:System.Workflow.ComponentModel.Serialization.ActivityCodeDomSerializationManager?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。<br /><br /> System.Workflow.\* 類型已被取代。 請改用 <xref:System.Activities>.\* 的新類型。|
|<xref:System.Workflow.ComponentModel.Serialization.ActivityCodeDomSerializer?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。<br /><br /> System.Workflow.\* 類型已被取代。 請改用 <xref:System.Activities>.\* 的新類型。|
|<xref:System.Workflow.ComponentModel.Serialization.ActivityMarkupSerializer?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。<br /><br /> System.Workflow.\* 類型已被取代。 請改用 <xref:System.Activities>.\* 的新類型。|
|<xref:System.Workflow.ComponentModel.Serialization.ActivitySurrogateSelector?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。<br /><br /> System.Workflow.\* 類型已被取代。 請改用 <xref:System.Activities>.\* 的新類型。|
|<xref:System.Workflow.ComponentModel.Serialization.ActivityTypeCodeDomSerializer?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。<br /><br /> System.Workflow.\* 類型已被取代。 請改用 <xref:System.Activities>.\* 的新類型。|
|<xref:System.Workflow.ComponentModel.Serialization.CompositeActivityMarkupSerializer?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。<br /><br /> System.Workflow.\* 類型已被取代。 請改用 <xref:System.Activities>.\* 的新類型。|
|<xref:System.Workflow.ComponentModel.Serialization.DependencyObjectCodeDomSerializer?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。<br /><br /> System.Workflow.\* 類型已被取代。 請改用 <xref:System.Activities>.\* 的新類型。|

 [回到頁首](#introduction)

<a name="workflow_runtime"></a>
### <a name="assembly-systemworkflowruntimedll"></a>組件︰System.Workflow.Runtime.dll

|類型|訊息|
|----------|-------------|
|<xref:System.Activities.Statements.Interop?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。<br /><br />Workflow Foundation 3.0 類型已被取代。 請改用 <xref:System.Activities>.\* 的 Workflow 4.0 類型。|
|<xref:System.Activities.Tracking.InteropTrackingRecord?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。<br /><br />Workflow Foundation 3.0 類型已被取代。 請改用 <xref:System.Activities>.\* 的 Workflow 4.0 類型。|
|<xref:System.Workflow.Runtime> 命名空間中的所有型別。|在 .NET Framework 4.5 中首先被取代。<br /><br /> System.Workflow.\* 類型已被取代。 請改用 <xref:System.Activities>.\* 的新類型。|
|<xref:System.Workflow.Runtime.Configuration> 命名空間中的所有型別。|在 .NET Framework 4.5 中首先被取代。<br /><br /> System.Workflow.\* 類型已被取代。 請改用 <xref:System.Activities>.\* 的新類型。|
|在 <xref:System.Workflow.Runtime.DebugEngine> 命名空間中除了 <xref:System.Workflow.Runtime.DebugEngine.DebugEngineCallback> 之外的所有型別|在 .NET Framework 4.5 中首先被取代。<br /><br /> System.Workflow.\* 類型已被取代。 請改用 <xref:System.Activities>.\* 的新類型。|
|在 <xref:System.Workflow.Runtime.Hosting> 命名空間中除了 <xref:System.Workflow.Runtime.Hosting.WorkflowCommitWorkBatchService.CommitWorkBatchCallback> 之外的所有型別|在 .NET Framework 4.5 中首先被取代。<br /><br /> System.Workflow.\* 類型已被取代。 請改用 <xref:System.Activities>.\* 的新類型。|
|<xref:System.Workflow.Runtime.Tracking> 命名空間中的所有型別。|在 .NET Framework 4.5 中首先被取代。<br /><br /> System.Workflow.\* 類型已被取代。 請改用 <xref:System.Activities>.\* 的新類型。|

 [回到頁首](#introduction)

<a name="workflowservices"></a>
### <a name="assembly-systemworkflowservicesdll"></a>組件︰System.WorkflowServices.dll

|類型|訊息|
|----------|-------------|
|<xref:System.ServiceModel.WorkflowServiceHost?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。<br /><br /> WF 3 型別已被取代。 請改用 <xref:System.Activities>.\* 的新 WF 4 類型。|
|<xref:System.ServiceModel.Activation.WorkflowServiceHostFactory?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。<br /><br /> WF 3 型別已被取代。 請改用 <xref:System.Activities>.\* 的新 WF 4 類型。|
|<xref:System.ServiceModel.Activities.Description.WorkflowRuntimeEndpoint?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。<br /><br /> WF 3 型別已被取代。 請改用 <xref:System.Activities>.\* 的新 WF 4 類型。|
|<xref:System.ServiceModel.Configuration.ExtendedWorkflowRuntimeServiceElementCollection?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。<br /><br /> WF 3 型別已被取代。 請改用 <xref:System.Activities>.\* 的新 WF 4 類型。|
|<xref:System.ServiceModel.Configuration.PersistenceProviderElement?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。<br /><br /> WF 3 型別已被取代。 請改用 <xref:System.Activities>.\* 的新 WF 4 類型。|
|<xref:System.ServiceModel.Configuration.WorkflowRuntimeElement?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。<br /><br /> WF 3 型別已被取代。 請改用 <xref:System.Activities>.\* 的新 WF 4 類型。|
|<xref:System.ServiceModel.Description.DurableOperationAttribute?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。<br /><br /> WF 3 型別已被取代。 請改用 <xref:System.Activities>.\* 的新 WF 4 類型。|
|<xref:System.ServiceModel.Description.DurableServiceAttribute?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。<br /><br /> WF 3 型別已被取代。 請改用 <xref:System.Activities>.\* 的新 WF 4 類型。|
|<xref:System.ServiceModel.Description.PersistenceProviderBehavior?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。<br /><br /> WF 3 型別已被取代。 請改用 <xref:System.Activities>.\* 的新 WF 4 類型。|
|<xref:System.ServiceModel.Description.UnknownExceptionAction?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。<br /><br /> WF 3 型別已被取代。 請改用 <xref:System.Activities>.\* 的新 WF 4 類型。|
|<xref:System.ServiceModel.Description.WorkflowRuntimeBehavior?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。<br /><br /> WF 3 型別已被取代。 請改用 <xref:System.Activities>.\* 的新 WF 4 類型。|
|<xref:System.ServiceModel.Dispatcher.DurableOperationContext?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。<br /><br /> WF 3 型別已被取代。 請改用 <xref:System.Activities>.\* 的新 WF 4 類型。|
|<xref:System.ServiceModel.Persistence.InstanceLockException?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。<br /><br /> WF 3 型別已被取代。 請改用 <xref:System.Activities>.\* 的新 WF 4 類型。|
|<xref:System.ServiceModel.Persistence.InstanceNotFoundException?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。<br /><br /> WF 3 型別已被取代。 請改用 <xref:System.Activities>.\* 的新 WF 4 類型。|
|<xref:System.ServiceModel.Persistence.LockingPersistenceProvider?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。<br /><br /> WF 3 型別已被取代。 請改用 <xref:System.Activities>.\* 的新 WF 4 類型。|
|<xref:System.ServiceModel.Persistence.PersistenceException?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。<br /><br /> WF 3 型別已被取代。 請改用 <xref:System.Activities>.\* 的新 WF 4 類型。|
|<xref:System.ServiceModel.Persistence.PersistenceProvider?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。<br /><br /> WF 3 型別已被取代。 請改用 <xref:System.Activities>.\* 的新 WF 4 類型。|
|<xref:System.ServiceModel.Persistence.PersistenceProviderFactory?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。<br /><br /> WF 3 型別已被取代。 請改用 <xref:System.Activities>.\* 的新 WF 4 類型。|
|<xref:System.ServiceModel.Persistence.SqlPersistenceProviderFactory?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。<br /><br /> WF 3 型別已被取代。 請改用 <xref:System.Activities>.\* 的新 WF 4 類型。|
|<xref:System.Workflow.Activities?displayProperty=nameWithType> 命名空間中的所有型別。|在 .NET Framework 4.5 中首先被取代。<br /><br /> WF 3 型別已被取代。 請改用 <xref:System.Activities>.\* 的新 WF 4 類型。|
|<xref:System.Workflow.Runtime.Hosting.ChannelManagerService?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。<br /><br /> WF 3 型別已被取代。 請改用 <xref:System.Activities>.\* 的新 WF 4 類型。|

 [回到頁首](#introduction)

<a name="xaml"></a>
### <a name="assembly-systemxamldll"></a>組件︰System.Xaml.dll

|類型|訊息|
|----------|-------------|
|<xref:System.Windows.Markup.AcceptedMarkupExtensionExpressionTypeAttribute?displayProperty=nameWithType>|XAML 剖析器已不使用這個項目。 請查看 <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute?displayProperty=nameWithType>。|

 [回到頁首](#introduction)

<a name="xml"></a>
### <a name="assembly-systemxmldll"></a>組件︰System.Xml.dll

|類型|訊息|
|----------|-------------|
|<xref:System.Xml.IApplicationResourceStreamResolver?displayProperty=nameWithType>|在 .NET Framework 4.5 中首先被取代。<br /><br /> 使用這個型別會產生編譯器錯誤。<br /><br /> 這個 API 支援 .NET Framework 基礎結構，並不適合直接從您的程式碼中使用。|
|<xref:System.Xml.Schema.XmlSchemaCollection?displayProperty=nameWithType>|請使用 <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType> 進行結構描述編譯和驗證。|
|<xref:System.Xml.XmlValidatingReader?displayProperty=nameWithType>|請改用 <xref:System.Xml.XmlReader?displayProperty=nameWithType> 方法搭配適當的 <xref:System.Xml.XmlReader.Create%2A?displayProperty=nameWithType> 所建立的 <xref:System.Xml.XmlReaderSettings?displayProperty=nameWithType>。|
|<xref:System.Xml.XmlXapResolver?displayProperty=nameWithType>|使用這個型別會產生編譯器錯誤。 這個 API 支援 .NET Framework 基礎結構，並不適合直接從您的程式碼中使用。|
|<xref:System.Xml.Xsl.XslTransform?displayProperty=nameWithType>|這個類別已被取代。 請改用 <xref:System.Xml.Xsl.XslCompiledTransform?displayProperty=nameWithType>。|

 [回到頁首](#introduction)

<a name="WindowsBase"></a>
### <a name="assembly-windowsbasedll"></a>組件︰WindowsBase.dll

|類型|訊息|
|----------|-------------|
|<xref:System.Windows.Markup.IReceiveMarkupExtension?displayProperty=nameWithType>|<xref:System.Windows.Markup.IReceiveMarkupExtension?displayProperty=nameWithType> 已被取代。 這個介面不再使用。|

 [回到頁首](#introduction)

<a name="obsolete_types_in_microsoft_assemblies"></a>
## <a name="obsolete-types-in-microsoft-assemblies"></a>Microsoft 組件中的過時型別
 下列章節將列出 Microsoft 組件中的過時型別。 這些組件是特殊用途的組件，例如以個別語言 (例如 Microsoft.JScript.dll 或 Microsoft.VisualC.dll) 為目標的組件。

<a name="IEHost"></a>
### <a name="assembly-iehostdll-and-ieexecexe"></a>組件︰IEHost.dll 和 IEExec.exe
 IEHost.dll 和 IEExec.exe 組件已經從 .NET Framework 中移除。 其所有型別和成員都已淘汱，並自 .NET Framework 4 起不再支援。 這些組件之前是用來裝載 Windows Form 控制項以及在 Internet Explorer 中執行可執行檔。 建議的替代方案包括 ClickOnce、XAML 瀏覽器應用程式 (XBAP) 和 Microsoft Silverlight。

 [回到頁首](#introduction)

<a name="Engine"></a>
### <a name="assembly-microsoftbuildenginedll"></a>組件︰Microsoft.Build.Engine.dll

|類型|訊息|
|----------|-------------|
|<xref:Microsoft.Build.BuildEngine.Engine?displayProperty=nameWithType>|這個類別已被取代。 請改用 *Microsoft.Build* 組件的 <xref:Microsoft.Build.Evaluation.ProjectCollection?displayProperty=nameWithType>。|
|<xref:Microsoft.Build.BuildEngine.Project?displayProperty=nameWithType>|這個類別已被取代。 請改用 *Microsoft.Build* 組件的 <xref:Microsoft.Build.Evaluation.ProjectCollection?displayProperty=nameWithType>。|

 [回到頁首](#introduction)

<a name="jscript"></a>
### <a name="assembly-microsoftjscriptdll"></a>組件︰Microsoft.JScript.dll

|類型|訊息|
|----------|-------------|
|<xref:Microsoft.JScript.Vsa.BaseVsaEngine?displayProperty=nameWithType>|這個類型在 Visual Studio 2005 中已過時；未來沒有取代項目。 如需詳細資訊，請參閱 <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> 文件。|
|<xref:Microsoft.JScript.Vsa.BaseVsaSite?displayProperty=nameWithType>|這個類型在 Visual Studio 2005 中已過時；未來沒有取代項目。 如需詳細資訊，請參閱 <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> 文件。|
|<xref:Microsoft.JScript.Vsa.BaseVsaStartup?displayProperty=nameWithType>|這個類型在 Visual Studio 2005 中已過時；未來沒有取代項目。 如需詳細資訊，請參閱 <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> 文件。|
|<xref:Microsoft.JScript.Vsa.IJSVsaCodeItem?displayProperty=nameWithType>|這個類型在 Visual Studio 2005 中已過時；未來沒有取代項目。 如需詳細資訊，請參閱 <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> 文件。|
|<xref:Microsoft.JScript.Vsa.IJSVsaEngine?displayProperty=nameWithType>|這個類型在 Visual Studio 2005 中已過時；未來沒有取代項目。 如需詳細資訊，請參閱 <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> 文件。|
|<xref:Microsoft.JScript.Vsa.IJSVsaError?displayProperty=nameWithType>|這個類型在 Visual Studio 2005 中已過時；未來沒有取代項目。 如需詳細資訊，請參閱 <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> 文件。|
|<xref:Microsoft.JScript.Vsa.IJSVsaGlobalItem?displayProperty=nameWithType>|這個類型在 Visual Studio 2005 中已過時；未來沒有取代項目。 如需詳細資訊，請參閱 <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> 文件。|
|<xref:Microsoft.JScript.Vsa.IJSVsaItem?displayProperty=nameWithType>|這個類型在 Visual Studio 2005 中已過時；未來沒有取代項目。 如需詳細資訊，請參閱 <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> 文件。|
|<xref:Microsoft.JScript.Vsa.IJSVsaItems?displayProperty=nameWithType>|這個類型在 Visual Studio 2005 中已過時；未來沒有取代項目。 如需詳細資訊，請參閱 <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> 文件。|
|<xref:Microsoft.JScript.Vsa.IJSVsaPersistSite?displayProperty=nameWithType>|這個類型在 Visual Studio 2005 中已過時；未來沒有取代項目。 如需詳細資訊，請參閱 <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> 文件。|
|<xref:Microsoft.JScript.Vsa.IJSVsaReferenceItem?displayProperty=nameWithType>|這個類型在 Visual Studio 2005 中已過時；未來沒有取代項目。 如需詳細資訊，請參閱 <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> 文件。|
|<xref:Microsoft.JScript.Vsa.IJSVsaSite?displayProperty=nameWithType>|這個類型在 Visual Studio 2005 中已過時；未來沒有取代項目。 如需詳細資訊，請參閱 <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> 文件。|
|<xref:Microsoft.JScript.Vsa.JSVsaError?displayProperty=nameWithType>|這個類型在 Visual Studio 2005 中已過時；未來沒有取代項目。 如需詳細資訊，請參閱 <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> 文件。|
|<xref:Microsoft.JScript.Vsa.JSVsaException?displayProperty=nameWithType>|這個類型在 Visual Studio 2005 中已過時；未來沒有取代項目。 如需詳細資訊，請參閱 <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> 文件。|
|<xref:Microsoft.JScript.Vsa.JSVsaItemFlag?displayProperty=nameWithType>|這個類型在 Visual Studio 2005 中已過時；未來沒有取代項目。 如需詳細資訊，請參閱 <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> 文件。|
|<xref:Microsoft.JScript.Vsa.JSVsaItemType?displayProperty=nameWithType>|這個類型在 Visual Studio 2005 中已過時；未來沒有取代項目。 如需詳細資訊，請參閱 <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> 文件。|
|<xref:Microsoft.JScript.Vsa.ResInfo?displayProperty=nameWithType>|這個類型在 Visual Studio 2005 中已過時；未來沒有取代項目。 如需詳細資訊，請參閱 <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> 文件。|
|<xref:Microsoft.JScript.Vsa.VsaEngine?displayProperty=nameWithType>|這個類型在 Visual Studio 2005 中已過時；未來沒有取代項目。 如需詳細資訊，請參閱 <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> 文件。|

 [回到頁首](#introduction)

<a name="VBCompat"></a>
### <a name="assembly-microsoftvisualbasiccompatibilitydll"></a>組件︰Microsoft.VisualBasic.Compatibility.dll

如需從 Visual Basic 6 移轉的資訊，請參閱 [Visual Basic 6.0 資源中心](https://docs.microsoft.com/previous-versions/visualstudio/visual-basic-6/visual-basic-6.0-documentation)。
  
|類型|訊息|
|----------|-------------|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.BaseControlArray?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.BaseOcxArray?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ButtonArray?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.CheckBoxArray?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.CheckedListBoxArray?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ColorDialogArray?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ComboBoxArray?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DirListBox?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DirListBoxArray?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DriveListBox?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DriveListBoxArray?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FileListBox?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FileListBoxArray?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FixedLengthString?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FontDialogArray?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FormShowConstants?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.GroupBoxArray?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.HScrollBarArray?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ImageListArray?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.LabelArray?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ListBoxArray?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ListBoxItem?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ListViewArray?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.LoadResConstants?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MaskedTextBoxArray?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MenuItemArray?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MouseButtonConstants?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.OpenFileDialogArray?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.PanelArray?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.PictureBoxArray?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.PrintDialogArray?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ProgressBarArray?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.RadioButtonArray?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.RichTextBoxArray?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.SaveFileDialogArray?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ScaleMode?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ShiftConstants?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.StatusBarArray?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.StatusStripArray?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.Support?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.TabControlArray?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.TextBoxArray?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.TimerArray?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ToolBarArray?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ToolStripArray?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ToolStripMenuItemArray?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.TreeViewArray?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.VScrollBarArray?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebBrowserArray?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClass?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassContainingClassNotOptional?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassCouldNotFindEvent?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassNextItemCannotBeCurrentWebItem?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassNextItemRespondNotFound?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassUserWebClassNameNotOptional?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassWebClassFileNameNotOptional?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassWebItemNotValid?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItem?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemAssociatedWebClassNotOptional?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemClosingTagNotFound?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemCouldNotLoadEmbeddedResource?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemCouldNotLoadTemplateFile?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemNameNotOptional?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemNoTemplateSpecified?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemTooManyNestedTags?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemUnexpectedErrorReadingTemplateFile?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ZOrderConstants?displayProperty=nameWithType>|這個成員已過時。|

 [回到頁首](#introduction)

<a name="VBCompatData"></a>
### <a name="assembly-microsoftvisualbasiccompatibilitydatadll"></a>組件︰Microsoft.VisualBasic.Compatibility.Data.dll

|類型|訊息|
|----------|-------------|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.BOFActionEnum?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.EndOfRecordsetDelegate?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.EOFActionEnum?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.ErrorDelegate?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.FetchCompleteDelegate?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.FetchProgressDelegate?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.FieldChangeCompleteDelegate?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.MoveCompleteDelegate?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.OrientationEnum?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.RecordChangeCompleteDelegate?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.RecordsetChangeCompleteDelegate?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.WillChangeFieldDelegate?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.WillChangeRecordDelegate?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.WillChangeRecordsetDelegate?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.WillMoveDelegate?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODCArray?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.BaseDataEnvironment?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.BindingCollectionEnumerator?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.CONNECTDATA?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBBINDING?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBCOLUMNINFO?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBID?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBinding?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBindingCollection?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBKINDENUM?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBPROPIDSET?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IAccessor?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IChapteredRowset?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IColumnsInfo?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IConnectionPoint?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IConnectionPointContainer?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IDataFormat?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IDataFormatDisp?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IEnumConnectionPoints?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IEnumConnections?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowPosition?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowPositionChange?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowset?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowsetChange?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowsetIdentity?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowsetInfo?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowsetNotify?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MBinding?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MBindingCollection?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.SRDescriptionAttribute?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.UGUID?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.UNAME?displayProperty=nameWithType>|這個成員已過時。|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.UpdateMode?displayProperty=nameWithType>|這個成員已過時。|

 [回到頁首](#introduction)

<a name="visualc"></a>
### <a name="assembly-microsoftvisualcdll"></a>組件︰Microsoft.VisualC.dll

|類型|訊息|
|----------|-------------|
|<xref:Microsoft.VisualC.DebugInfoInPDBAttribute?displayProperty=nameWithType>|Microsoft.VisualC.dll 這個組件已經過時，其存在目的只是為了提供回溯相容性。|
|<xref:Microsoft.VisualC.DecoratedNameAttribute?displayProperty=nameWithType>|Microsoft.VisualC.dll 這個組件已經過時，其存在目的只是為了提供回溯相容性。|
|<xref:Microsoft.VisualC.IsConstModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll 這個組件已經過時，其存在目的只是為了提供回溯相容性。|
|<xref:Microsoft.VisualC.IsCXXReferenceModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll 這個組件已經過時，其存在目的只是為了提供回溯相容性。|
|<xref:Microsoft.VisualC.IsLongModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll 這個組件已經過時，其存在目的只是為了提供回溯相容性。|
|<xref:Microsoft.VisualC.IsSignedModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll 這個組件已經過時，其存在目的只是為了提供回溯相容性。|
|<xref:Microsoft.VisualC.IsVolatileModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll 這個組件已經過時，其存在目的只是為了提供回溯相容性。|
|<xref:Microsoft.VisualC.MiscellaneousBitsAttribute?displayProperty=nameWithType>|Microsoft.VisualC.dll 這個組件已經過時，其存在目的只是為了提供回溯相容性。|
|<xref:Microsoft.VisualC.NeedsCopyConstructorModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll 這個組件已經過時，其存在目的只是為了提供回溯相容性。|
|<xref:Microsoft.VisualC.NoSignSpecifiedModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll 這個組件已經過時，其存在目的只是為了提供回溯相容性。|

## <a name="see-also"></a>另請參閱

- [類別庫中已淘汰的功能](whats-obsolete.md)
- [過時的成員](obsolete-members.md)
