---
title: ".NET Framework 中過時的類型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework 4.5, obsolete types
- types, obsolete in .NET Framework 4.5
- obsolete types [.NET Framework]
ms.assetid: e636d024-0fac-45eb-b721-25a8c0ceca8f
caps.latest.revision: 41
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 15ab48dedaef24ea209c38939ee87a0321da55cf
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="obsolete-types-in-the-net-framework"></a>.NET Framework 中過時的類型
<a name="introduction"></a> 本文中的表格列出 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 和 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 中過時的類型，並依組件分組。 使用下列連結查看每個組件中過時的型別和建議的替代方案。 因為這些型別已經過時，其所有成員也已經過時。 如需 .NET Framework 類別庫中其他過時成員的清單，請參閱[過時的成員](../../../docs/framework/whats-new/obsolete-members.md)。  
  
-   [系統組件中的過時類型](#obsolete_types_in_system_assemblies)  
  
    -   [mscorlib.dll](#mscorlib)  
  
    -   [System.Core.dll](#Core)  
  
    -   [System.Data.dll](#data)  
  
    -   [System.Data.OracleClient.dll](#oracleclient)  
  
    -   [System.Design.dll](#design)  
  
    -   [System.dll](#system)  
  
    -   [System.EnterpriseServices.dll](#enterpriseservices)  
  
    -   [System.Net.dll](#net)  
  
    -   [System.ServiceModel.dll](#servicemodel)  
  
    -   [System.Web.dll](#web)  
  
    -   [System.Web.Mobile.dll](#mobile)  
  
    -   [System.Workflow.Activities.dll](#workflow_activities)  
  
    -   [System.Workflow.ComponentModel.dll](#workflow_componentmodel)  
  
    -   [System.Workflow.Runtime.dll](#workflow_runtime)  
  
    -   [System.WorkflowServices.dll](#workflowservices)  
  
    -   [System.Xaml.dll](#xaml)  
  
    -   [System.Xml.dll](#xml)  
  
    -   [WindowsBase.dll](#WindowsBase)  
  
-   [Microsoft 組件中的過時類型](#obsolete_types_in_microsoft_assemblies)  
  
    -   [IEHost.dll 和 IEExec.exe](#IEHost)  
  
    -   [Microsoft.Build.Engine.dll](#Engine)  
  
    -   [Microsoft.JScript.dll](#jscript)  
  
    -   [Microsoft.VisualBasic.Compatibility.dll](#VBCompat)  
  
    -   [Microsoft.VisualBasic.Compatibility.Data.dll](#VBCompatData)  
  
    -   [Microsoft.VisualC.dll](#visualc)  
  
<a name="obsolete_types_in_system_assemblies"></a>   
## <a name="obsolete-types-in-system-assemblies"></a>系統組件中的過時型別  
 下列表格將列出已經在系統組件中宣告為過時的型別。 這些組件是用於以 .NET Framework 為目標的一般用途應用程式開發。  
  
<a name="mscorlib"></a>   
### <a name="assembly-mscorlibdll"></a>組件：mscorlib.dll  
  
|類型|訊息|  
|----------|-------------|  
|<xref:System.ExecutionEngineException?displayProperty=fullName>|這個型別先前會在執行階段中指出未指定的嚴重錯誤。 執行階段已不再引發這個例外狀況，因此這個型別已過時。|  
|<xref:System.Collections.CaseInsensitiveHashCodeProvider?displayProperty=fullName>|請改用 <xref:System.StringComparer?displayProperty=fullName>。|  
|<xref:System.Collections.IHashCodeProvider?displayProperty=fullName>|請改用 <xref:System.Collections.IEqualityComparer?displayProperty=fullName>。|  
|<xref:System.Configuration.Assemblies.AssemblyHash?displayProperty=fullName>|<xref:System.Configuration.Assemblies.AssemblyHash> 類別已被取代。|  
|<xref:System.Diagnostics.Contracts.Internal.ContractHelper?displayProperty=fullName>|在 .NET Framework 4.5 中首先被取代。 請改用 System.Runtime.CompilerServices 命名空間中的 <xref:System.Runtime.CompilerServices.ContractHelper?displayProperty=fullName> 類別。|  
|<xref:System.Reflection.Emit.UnmanagedMarshal?displayProperty=fullName>|有替代的 API 可用：請改為發出 <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> 自訂屬性。|  
|<xref:System.Runtime.InteropServices.BIND_OPTS?displayProperty=fullName>|請改用 <xref:System.Runtime.InteropServices.ComTypes.BIND_OPTS?displayProperty=fullName>。|  
|<xref:System.Runtime.InteropServices.BINDPTR?displayProperty=fullName>|請改用 <xref:System.Runtime.InteropServices.ComTypes.BINDPTR?displayProperty=fullName>。|  
|<xref:System.Runtime.InteropServices.CALLCONV?displayProperty=fullName>|請改用 <xref:System.Runtime.InteropServices.ComTypes.CALLCONV?displayProperty=fullName>。|  
|<xref:System.Runtime.InteropServices.CONNECTDATA?displayProperty=fullName>|請改用 <xref:System.Runtime.InteropServices.ComTypes.CONNECTDATA?displayProperty=fullName>。|  
|<xref:System.Runtime.InteropServices.DESCKIND?displayProperty=fullName>|請改用 <xref:System.Runtime.InteropServices.ComTypes.DESCKIND?displayProperty=fullName>。|  
|<xref:System.Runtime.InteropServices.DISPPARAMS?displayProperty=fullName>|請改用 <xref:System.Runtime.InteropServices.ComTypes.DISPPARAMS?displayProperty=fullName>。|  
|<xref:System.Runtime.InteropServices.ELEMDESC?displayProperty=fullName>|請改用 <xref:System.Runtime.InteropServices.ComTypes.ELEMDESC?displayProperty=fullName>。|  
|<xref:System.Runtime.InteropServices.EXCEPINFO?displayProperty=fullName>|請改用 <xref:System.Runtime.InteropServices.ComTypes.EXCEPINFO?displayProperty=fullName>。|  
|<xref:System.Runtime.InteropServices.FILETIME?displayProperty=fullName>|請改用 <xref:System.Runtime.InteropServices.ComTypes.FILETIME?displayProperty=fullName>。|  
|<xref:System.Runtime.InteropServices.FUNCDESC?displayProperty=fullName>|請改用 <xref:System.Runtime.InteropServices.ComTypes.FUNCDESC?displayProperty=fullName>。|  
|<xref:System.Runtime.InteropServices.FUNCFLAGS?displayProperty=fullName>|請改用 <xref:System.Runtime.InteropServices.ComTypes.FUNCFLAGS?displayProperty=fullName>。|  
|<xref:System.Runtime.InteropServices.FUNCKIND?displayProperty=fullName>|請改用 <xref:System.Runtime.InteropServices.ComTypes.FUNCKIND?displayProperty=fullName>。|  
|<xref:System.Runtime.InteropServices.IDispatchImplAttribute?displayProperty=fullName>|這個屬性已被取代，將在未來的版本中移除。|  
|<xref:System.Runtime.InteropServices.IDispatchImplType?displayProperty=fullName>|<xref:System.Runtime.InteropServices.IDispatchImplAttribute?displayProperty=fullName> 已被取代。|  
|<xref:System.Runtime.InteropServices.IDLDESC?displayProperty=fullName>|請改用 <xref:System.Runtime.InteropServices.ComTypes.IDLDESC?displayProperty=fullName>。|  
|<xref:System.Runtime.InteropServices.IDLFLAG?displayProperty=fullName>|請改用 <xref:System.Runtime.InteropServices.ComTypes.IDLFLAG?displayProperty=fullName>。|  
|<xref:System.Runtime.InteropServices.IMPLTYPEFLAGS?displayProperty=fullName>|請改用 <xref:System.Runtime.InteropServices.ComTypes.IMPLTYPEFLAGS?displayProperty=fullName>。|  
|<xref:System.Runtime.InteropServices.INVOKEKIND?displayProperty=fullName>|請改用 <xref:System.Runtime.InteropServices.ComTypes.INVOKEKIND?displayProperty=fullName>。|  
|<xref:System.Runtime.InteropServices.LIBFLAGS?displayProperty=fullName>|請改用 <xref:System.Runtime.InteropServices.ComTypes.LIBFLAGS?displayProperty=fullName>。|  
|<xref:System.Runtime.InteropServices.PARAMDESC?displayProperty=fullName>|請改用 <xref:System.Runtime.InteropServices.ComTypes.PARAMDESC?displayProperty=fullName>。|  
|<xref:System.Runtime.InteropServices.PARAMFLAG?displayProperty=fullName>|請改用 <xref:System.Runtime.InteropServices.ComTypes.PARAMFLAG?displayProperty=fullName>。|  
|<xref:System.Runtime.InteropServices.SetWin32ContextInIDispatchAttribute?displayProperty=fullName>|這個屬性已被取代。 應用程式定義域不再遵循 IDispatch 呼叫中的啟動內容界限。|  
|<xref:System.Runtime.InteropServices.STATSTG?displayProperty=fullName>|請改用 <xref:System.Runtime.InteropServices.ComTypes.STATSTG?displayProperty=fullName>。|  
|<xref:System.Runtime.InteropServices.SYSKIND?displayProperty=fullName>|請改用 <xref:System.Runtime.InteropServices.ComTypes.SYSKIND?displayProperty=fullName>。|  
|<xref:System.Runtime.InteropServices.TYPEATTR?displayProperty=fullName>|請改用 <xref:System.Runtime.InteropServices.ComTypes.TYPEATTR?displayProperty=fullName>。|  
|<xref:System.Runtime.InteropServices.TYPEDESC?displayProperty=fullName>|請改用 <xref:System.Runtime.InteropServices.ComTypes.TYPEDESC?displayProperty=fullName>。|  
|<xref:System.Runtime.InteropServices.TYPEFLAGS?displayProperty=fullName>|請改用 <xref:System.Runtime.InteropServices.ComTypes.TYPEFLAGS?displayProperty=fullName>。|  
|<xref:System.Runtime.InteropServices.TYPEKIND?displayProperty=fullName>|請改用 <xref:System.Runtime.InteropServices.ComTypes.TYPEKIND?displayProperty=fullName>。|  
|<xref:System.Runtime.InteropServices.TYPELIBATTR?displayProperty=fullName>|請改用 <xref:System.Runtime.InteropServices.ComTypes.TYPELIBATTR?displayProperty=fullName>。|  
|<xref:System.Runtime.InteropServices.UCOMIBindCtx?displayProperty=fullName>|請改用 <xref:System.Runtime.InteropServices.ComTypes.IBindCtx?displayProperty=fullName>。|  
|<xref:System.Runtime.InteropServices.UCOMIConnectionPoint?displayProperty=fullName>|請改用 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint?displayProperty=fullName>。|  
|<xref:System.Runtime.InteropServices.UCOMIConnectionPointContainer?displayProperty=fullName>|請改用 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer?displayProperty=fullName>。|  
|<xref:System.Runtime.InteropServices.UCOMIEnumConnectionPoints?displayProperty=fullName>|請改用 <xref:System.Runtime.InteropServices.ComTypes.IEnumConnectionPoints?displayProperty=fullName>。|  
|<xref:System.Runtime.InteropServices.UCOMIEnumConnections?displayProperty=fullName>|請改用 <xref:System.Runtime.InteropServices.ComTypes.IEnumConnections?displayProperty=fullName>。|  
|<xref:System.Runtime.InteropServices.UCOMIEnumMoniker?displayProperty=fullName>|請改用 <xref:System.Runtime.InteropServices.ComTypes.IEnumMoniker?displayProperty=fullName>。|  
|<xref:System.Runtime.InteropServices.UCOMIEnumString?displayProperty=fullName>|請改用 <xref:System.Runtime.InteropServices.ComTypes.IEnumString?displayProperty=fullName>。|  
|<xref:System.Runtime.InteropServices.UCOMIEnumVARIANT?displayProperty=fullName>|請改用 <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT?displayProperty=fullName>。|  
|<xref:System.Runtime.InteropServices.UCOMIMoniker?displayProperty=fullName>|請改用 <xref:System.Runtime.InteropServices.ComTypes.IMoniker?displayProperty=fullName>。|  
|<xref:System.Runtime.InteropServices.UCOMIPersistFile?displayProperty=fullName>|請改用 <xref:System.Runtime.InteropServices.ComTypes.IPersistFile?displayProperty=fullName>。|  
|<xref:System.Runtime.InteropServices.UCOMIRunningObjectTable?displayProperty=fullName>|請改用 <xref:System.Runtime.InteropServices.ComTypes.IRunningObjectTable?displayProperty=fullName>。|  
|<xref:System.Runtime.InteropServices.UCOMIStream?displayProperty=fullName>|請改用 <xref:System.Runtime.InteropServices.ComTypes.IStream?displayProperty=fullName>。|  
|<xref:System.Runtime.InteropServices.UCOMITypeComp?displayProperty=fullName>|請改用 <xref:System.Runtime.InteropServices.ComTypes.ITypeComp?displayProperty=fullName>。|  
|<xref:System.Runtime.InteropServices.UCOMITypeInfo?displayProperty=fullName>|請改用 <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo?displayProperty=fullName>。|  
|<xref:System.Runtime.InteropServices.UCOMITypeLib?displayProperty=fullName>|請改用 <xref:System.Runtime.InteropServices.ComTypes.ITypeLib?displayProperty=fullName>。|  
|<xref:System.Runtime.InteropServices.VARDESC?displayProperty=fullName>|請改用 <xref:System.Runtime.InteropServices.ComTypes.VARDESC?displayProperty=fullName>。|  
|<xref:System.Runtime.InteropServices.VARFLAGS?displayProperty=fullName>|請改用 <xref:System.Runtime.InteropServices.ComTypes.VARFLAGS?displayProperty=fullName>。|  
|<xref:System.Security.SecurityCriticalScope?displayProperty=fullName>|<xref:System.Security.SecurityCriticalScope> 僅用於 .NET 2.0 透明度相容性。|  
|<xref:System.Security.SecurityTreatAsSafeAttribute?displayProperty=fullName>|<xref:System.Security.SecurityTreatAsSafeAttribute> 僅用於 .NET 2.0 透明度相容性。 請改用 <xref:System.Security.SecuritySafeCriticalAttribute?displayProperty=fullName>。|  
|<xref:System.Security.Policy.FirstMatchCodeGroup?displayProperty=fullName>|這個型別已經過時，將在未來的 .NET Framework 發行版本中移除。|  
|<xref:System.Security.Policy.PermissionRequestEvidence?displayProperty=fullName>|組件層級宣告式安全性已過期，CLR 預設不再強制使用。|  
|<xref:System.Security.Policy.UnionCodeGroup?displayProperty=fullName>|這個型別已經過時，將在未來的 .NET Framework 發行版本中移除。|  
  
 [回到頁首](#introduction)  
  
<a name="Core"></a>   
### <a name="assembly-systemcoredll"></a>組件：System.Core.dll  
  
|類型|訊息|  
|----------|-------------|  
|<xref:System.Runtime.CompilerServices.ExecutionScope?displayProperty=fullName>|使用這個型別會產生編譯器錯誤。<br /><br /> 請勿使用這個型別。|  
  
 [回到頁首](#introduction)  
  
<a name="data"></a>   
### <a name="assembly-systemdatadll"></a>組件：System.Data.dll  
  
|類型|訊息|  
|----------|-------------|  
|<xref:System.Data.DataSysDescriptionAttribute?displayProperty=fullName>|<xref:System.Data.DataSysDescriptionAttribute> 已被取代。|  
|<xref:System.Data.PropertyAttributes?displayProperty=fullName>|<xref:System.Data.PropertyAttributes> 已被取代。|  
|<xref:System.Data.TypedDataSetGenerator?displayProperty=fullName>|<xref:System.Data.TypedDataSetGenerator> 類別將在未來的版本中移除。 請使用 System.Design.dll 中的 <xref:System.Data.Design.TypedDataSetGenerator?displayProperty=fullName>。|  
|<xref:System.Xml.XmlDataDocument?displayProperty=fullName>|<xref:System.Xml.XmlDataDocument> 類別將在未來的版本中移除。|  
  
 [回到頁首](#introduction)  
  
<a name="oracleclient"></a>   
### <a name="assembly-systemdataoracleclientdll"></a>組件：System.Data.OracleClient.dll  
  
|類型|訊息|  
|----------|-------------|  
|<xref:System.Data.OracleClient.OracleClientFactory?displayProperty=fullName>|<xref:System.Data.OracleClient.OracleClientFactory> 已被取代。|  
|<xref:System.Data.OracleClient.OracleCommand?displayProperty=fullName>|<xref:System.Data.OracleClient.OracleCommand> 已被取代。|  
|<xref:System.Data.OracleClient.OracleCommandBuilder?displayProperty=fullName>|<xref:System.Data.OracleClient.OracleCommandBuilder> 已被取代。|  
|<xref:System.Data.OracleClient.OracleConnection?displayProperty=fullName>|<xref:System.Data.OracleClient.OracleConnection> 已被取代。|  
|<xref:System.Data.OracleClient.OracleConnectionStringBuilder?displayProperty=fullName>|<xref:System.Data.OracleClient.OracleConnectionStringBuilder> 已被取代。|  
|<xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=fullName>|<xref:System.Data.OracleClient.OracleDataAdapter> 已被取代。|  
|<xref:System.Data.OracleClient.OraclePermission?displayProperty=fullName>|<xref:System.Data.OracleClient.OraclePermission> 已被取代。|  
|<xref:System.Data.OracleClient.OraclePermissionAttribute?displayProperty=fullName>|<xref:System.Data.OracleClient.OraclePermissionAttribute?displayProperty=fullName> 已被取代。|  
  
 [回到頁首](#introduction)  
  
<a name="design"></a>   
### <a name="assembly-systemdesigndll"></a>組件：System.Design.dll  
  
|類型|訊息|  
|----------|-------------|  
|<xref:System.ComponentModel.Design.LocalizationExtenderProvider?displayProperty=fullName>|這個類別已被取代。 請改用 <xref:System.ComponentModel.Design.Serialization.CodeDomLocalizationProvider?displayProperty=fullName>。|  
|<xref:System.Web.UI.Design.DataBindingCollectionConverter?displayProperty=fullName>|由於資料繫結編輯功能是經由 <xref:System.ComponentModel.Design.DesignerActionList?displayProperty=fullName> 而非屬性方格啟動，因此不建議使用這個類型。|  
|<xref:System.Web.UI.Design.DataBindingCollectionEditor?displayProperty=fullName>|由於資料繫結編輯功能是經由 <xref:System.ComponentModel.Design.DesignerActionList?displayProperty=fullName> 而非屬性方格啟動，因此不建議使用這個類型。|  
|<xref:System.Web.UI.Design.IControlDesignerBehavior?displayProperty=fullName>|建議的替代做法是 <xref:System.Web.UI.Design.IControlDesignerTag?displayProperty=fullName> 和 <xref:System.Web.UI.Design.IControlDesignerView?displayProperty=fullName>。|  
|<xref:System.Web.UI.Design.IHtmlControlDesignerBehavior?displayProperty=fullName>|建議的替代做法是 <xref:System.Web.UI.Design.IControlDesignerTag?displayProperty=fullName> 和 <xref:System.Web.UI.Design.IControlDesignerView?displayProperty=fullName>。|  
|<xref:System.Web.UI.Design.ITemplateEditingFrame?displayProperty=fullName>|由於範本編輯功能是在 <xref:System.Web.UI.Design.ControlDesigner?displayProperty=fullName> 中處理，因此不建議使用這個類型。 若要支援範本編輯功能，請公開 <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=fullName> 屬性中的範本資料，並且呼叫 <xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A?displayProperty=fullName>。|  
|<xref:System.Web.UI.Design.IWebFormReferenceManager?displayProperty=fullName>|建議的替代做法是 <xref:System.Web.UI.Design.WebFormsReferenceManager?displayProperty=fullName>。 <xref:System.Web.UI.Design.WebFormsReferenceManager> 包含其他功能而且允許更大的擴充性。 若要取得 <xref:System.Web.UI.Design.WebFormsReferenceManager>，請從您的 <xref:System.Web.UI.Design.ControlDesigner?displayProperty=fullName> 使用 `RootDesigner.ReferenceManager` 屬性。|  
|<xref:System.Web.UI.Design.IWebFormsDocumentService?displayProperty=fullName>|建議的替代做法是 <xref:System.Web.UI.Design.WebFormsRootDesigner?displayProperty=fullName>。 <xref:System.Web.UI.Design.WebFormsRootDesigner> 包含其他功能而且允許更大的擴充性。 若要取得 <xref:System.Web.UI.Design.WebFormsRootDesigner>，請從您的 <xref:System.Web.UI.Design.ControlDesigner?displayProperty=fullName> 使用 <xref:System.Web.UI.Design.ControlDesigner.RootDesigner%2A> 屬性。|  
|<xref:System.Web.UI.Design.ITemplateEditingService?displayProperty=fullName>|由於範本編輯功能是在 <xref:System.Web.UI.Design.ControlDesigner?displayProperty=fullName> 中處理，因此不建議使用這個類型。 若要支援範本編輯功能，請公開 <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=fullName> 屬性中的範本資料，並且呼叫 <xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A?displayProperty=fullName>。|  
|<xref:System.Web.UI.Design.ReadWriteControlDesigner?displayProperty=fullName>|建議的替代做法是 <xref:System.Web.UI.Design.ContainerControlDesigner?displayProperty=fullName>，因為它會使用 <xref:System.Web.UI.Design.EditableDesignerRegion?displayProperty=fullName> 來編輯內容。 設計工具區域可讓您有效控制所編輯的內容。|  
|<xref:System.Web.UI.Design.TemplateEditingService?displayProperty=fullName>|由於範本編輯功能是在 <xref:System.Web.UI.Design.ControlDesigner?displayProperty=fullName> 中處理，因此不建議使用這個類型。 若要支援範本編輯功能，請公開 <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=fullName> 屬性中的範本資料，並且呼叫 <xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A?displayProperty=fullName>。|  
|<xref:System.Web.UI.Design.TemplateEditingVerb?displayProperty=fullName>|由於範本編輯功能是在 <xref:System.Web.UI.Design.ControlDesigner?displayProperty=fullName> 中處理，因此不建議使用這個類型。 若要支援範本編輯功能，請公開 <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=fullName> 屬性中的範本資料，並且呼叫 <xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A?displayProperty=fullName>。|  
|<xref:System.Web.UI.Design.WebControls.CalendarAutoFormatDialog?displayProperty=fullName>|由於 [自動格式設定] 對話方塊是由設計工具主應用程式啟動，因此不建議使用這個型別。 可用的自動格式設定清單會公開在 <xref:System.Web.UI.Design.ControlDesigner.AutoFormats%2A?displayProperty=fullName> 屬性中的 <xref:System.Web.UI.Design.ControlDesigner?displayProperty=fullName> 上。|  
|<xref:System.Web.UI.Design.WebControls.PanelDesigner?displayProperty=fullName>|建議的替代做法是 <xref:System.Web.UI.Design.WebControls.PanelContainerDesigner?displayProperty=fullName>，因為它會使用 <xref:System.Web.UI.Design.EditableDesignerRegion?displayProperty=fullName> 來編輯內容。 設計工具區域可讓您有效控制所編輯的內容。|  
  
 [回到頁首](#introduction)  
  
<a name="system"></a>   
### <a name="assembly-systemdll"></a>組件：System.dll  
  
|類型|訊息|  
|----------|-------------|  
|<xref:System.ComponentModel.IComNativeDescriptorHandler?displayProperty=fullName>|這個介面已被取代。 請改為新增 <xref:System.ComponentModel.TypeDescriptionProvider?displayProperty=fullName> 來處理 <xref:System.ComponentModel.TypeDescriptor.ComObjectType%2A?displayProperty=fullName> 類型。|  
|<xref:System.ComponentModel.RecommendedAsConfigurableAttribute?displayProperty=fullName>|請改用 <xref:System.ComponentModel.SettingsBindableAttribute?displayProperty=fullName> 來處理新的設定模型。|  
|<xref:System.ComponentModel.Design.Serialization.RootDesignerSerializerAttribute?displayProperty=fullName>|這個屬性已被取代。 請改用 <xref:System.ComponentModel.Design.Serialization.DesignerSerializerAttribute?displayProperty=fullName>。 例如，若要指定 CodeDom 的根設計工具，請使用 `DesignerSerializerAttribute\(...,typeof\(TypeCodeDomSerializer\)\)`。|  
|<xref:System.Diagnostics.DiagnosticsConfigurationHandler?displayProperty=fullName>|這個類別已被取代。|  
|<xref:System.Diagnostics.PerformanceCounterManager?displayProperty=fullName>|這個類別已被取代。 請改為透過 <xref:System.Diagnostics.PerformanceCounter?displayProperty=fullName> 類別使用效能計數器。|  
|<xref:System.Net.GlobalProxySelection?displayProperty=fullName>|這個類別已被取代。 請改用 <xref:System.Net.WebRequest.DefaultWebProxy%2A?displayProperty=fullName> 來存取和設定全域預設 Proxy。 請使用 'null' 而非 <xref:System.Net.GlobalProxySelection.GetEmptyWebProxy%2A?displayProperty=fullName>。|  
|<xref:System.Net.Sockets.SocketClientAccessPolicyProtocol?displayProperty=fullName>|在 .NET Framework 4.5 中首先被取代。<br /><br /> 使用這個型別會產生編譯器錯誤。<br /><br /> 這個 API 支援 .NET Framework 基礎結構，並不適合直接從您的程式碼中使用。|  
  
 [回到頁首](#introduction)  
  
<a name="enterpriseservices"></a>   
### <a name="assembly-systementerpriseservicesdll"></a>組件：System.EnterpriseServices.dll  
  
|類型|訊息|  
|----------|-------------|  
|<xref:System.EnterpriseServices.RegistrationHelperTx?displayProperty=fullName>|<xref:System.EnterpriseServices.RegistrationHelperTx> 類別已被取代。|  
  
 [回到頁首](#introduction)  
  
<a name="net"></a>   
### <a name="assembly-systemnetdll"></a>組件：System.Net.dll  
  
|類型|訊息|  
|----------|-------------|  
|<xref:System.Net.INetworkProgress?displayProperty=fullName>|在 .NET Framework 4.5 中首先被取代。<br /><br /> 使用這個型別會產生編譯器錯誤。<br /><br /> 這個 API 支援 .NET Framework 基礎結構，並不適合直接從您的程式碼中使用。|  
|<xref:System.Net.IUnsafeWebRequestCreate?displayProperty=fullName>|在 .NET Framework 4.5 中首先被取代。<br /><br /> 使用這個型別會產生編譯器錯誤。<br /><br /> 這個 API 支援 .NET Framework 基礎結構，並不適合直接從您的程式碼中使用。|  
|<xref:System.Net.NetworkProgressChangedEventArgs?displayProperty=fullName>|在 .NET Framework 4.5 中首先被取代。<br /><br /> 使用這個型別會產生編譯器錯誤。<br /><br /> 這個 API 支援 .NET Framework 基礎結構，並不適合直接從您的程式碼中使用。|  
|<xref:System.Net.UiSynchronizationContext?displayProperty=fullName>|在 .NET Framework 4.5 中首先被取代。<br /><br /> 使用這個型別會產生編譯器錯誤。<br /><br /> 這個 API 支援 .NET Framework 基礎結構，並不適合直接從您的程式碼中使用。|  
|<xref:System.Net.Sockets.HttpPolicyDownloaderProtocol?displayProperty=fullName>|在 .NET Framework 4.5 中首先被取代。<br /><br /> 使用這個型別會產生編譯器錯誤。<br /><br /> 這個 API 支援 .NET Framework 基礎結構，並不適合直接從您的程式碼中使用。|  
|<xref:System.Net.Sockets.SecurityCriticalAction?displayProperty=fullName>|在 .NET Framework 4.5 中首先被取代。<br /><br /> 使用這個型別會產生編譯器錯誤。<br /><br /> 這個 API 支援 .NET Framework 基礎結構，並不適合直接從您的程式碼中使用。|  
|<xref:System.Net.Sockets.SocketPolicy?displayProperty=fullName>|在 .NET Framework 4.5 中首先被取代。<br /><br /> 使用這個型別會產生編譯器錯誤。<br /><br /> 這個 API 支援 .NET Framework 基礎結構，並不適合直接從您的程式碼中使用。|  
|<xref:System.Net.Sockets.UdpAnySourceMulticastClient?displayProperty=fullName>|在 .NET Framework 4.5 中首先被取代。<br /><br /> 使用這個型別會產生編譯器錯誤。<br /><br /> 這個 API 支援 .NET Framework 基礎結構，並不適合直接從您的程式碼中使用。|  
|<xref:System.Net.Sockets.UdpSingleSourceMulticastClient?displayProperty=fullName>|在 .NET Framework 4.5 中首先被取代。<br /><br /> 使用這個型別會產生編譯器錯誤。<br /><br /> 這個 API 支援 .NET Framework 基礎結構，並不適合直接從您的程式碼中使用。|  
  
 [回到頁首](#introduction)  
  
<a name="servicemodel"></a>   
### <a name="assembly-systemservicemodeldll"></a>組件：System.ServiceModel.dll  
  
|類型|訊息|  
|----------|-------------|  
|<xref:System.ServiceModel.NetPeerTcpBinding?displayProperty=fullName>|在 .NET Framework 4.5 中首先被取代。<br /><br /> 對等通道功能已經過時，未來將會移除。|  
|<xref:System.ServiceModel.Channels.HttpCookieContainerBindingElement?displayProperty=fullName>|在 .NET Framework 4.5 中首先被取代。<br /><br /> 這個型別已經過時。 若要啟用 HTTP <xref:System.Net.CookieContainer>，請使用 HTTP 繫結或 <xref:System.ServiceModel.Channels.HttpTransportBindingElement> 上的 `AllowCookies` 屬性。|  
|<xref:System.ServiceModel.Channels.PeerCustomResolverBindingElement?displayProperty=fullName>|在 .NET Framework 4.5 中首先被取代。<br /><br /> 對等通道功能已經過時，未來將會移除。|  
|<xref:System.ServiceModel.Channels.PeerTransportBindingElement?displayProperty=fullName>|在 .NET Framework 4.5 中首先被取代。<br /><br /> 對等通道功能已經過時，未來將會移除。|  
|<xref:System.ServiceModel.Configuration.NetPeerTcpBindingCollectionElement?displayProperty=fullName>|在 .NET Framework 4.5 中首先被取代。<br /><br /> 對等通道功能已經過時，未來將會移除。|  
|<xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement?displayProperty=fullName>|在 .NET Framework 4.5 中首先被取代。<br /><br /> 對等通道功能已經過時，未來將會移除。|  
|<xref:System.ServiceModel.Configuration.PeerTransportElement?displayProperty=fullName>|在 .NET Framework 4.5 中首先被取代。<br /><br /> 對等通道功能已經過時，未來將會移除。|  
|<xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService?displayProperty=fullName>|在 .NET Framework 4.5 中首先被取代。<br /><br /> 對等通道功能已經過時，未來將會移除。|  
  
 [回到頁首](#introduction)  
  
<a name="web"></a>   
### <a name="assembly-systemwebdll"></a>組件：System.Web.dll  
  
|類型|訊息|  
|----------|-------------|  
|<xref:System.Web.Configuration.PassportAuthentication?displayProperty=fullName>|這個型別已經過時。 已不再支援 Passport 驗證產品，並且以 [Microsoft 帳戶](http://go.microsoft.com/fwlink/?LinkId=733413)取代該產品|  
|<xref:System.Web.Mail.MailAttachment?displayProperty=fullName>|建議的替代做法是 <xref:System.Net.Mail.Attachment?displayProperty=fullName>。|  
|<xref:System.Web.Mail.MailEncoding?displayProperty=fullName>|建議的替代做法是 <xref:System.Net.Mime.TransferEncoding?displayProperty=fullName>。|  
|<xref:System.Web.Mail.MailFormat?displayProperty=fullName>|建議的替代做法是 <xref:System.Net.Mail.MailMessage.IsBodyHtml%2A?displayProperty=fullName>。|  
|<xref:System.Web.Mail.MailMessage?displayProperty=fullName>|建議的替代做法是 <xref:System.Net.Mail.MailMessage?displayProperty=fullName>。|  
|<xref:System.Web.Mail.MailPriority?displayProperty=fullName>|建議的替代做法是 <xref:System.Net.Mail.MailPriority?displayProperty=fullName>。|  
|<xref:System.Web.Mail.SmtpMail?displayProperty=fullName>|建議的替代做法是 <xref:System.Net.Mail.SmtpClient?displayProperty=fullName>。|  
|<xref:System.Web.Security.PassportAuthenticationEventArgs?displayProperty=fullName>|這個型別已經過時。 已不再支援 Passport 驗證產品，並且以 [Microsoft 帳戶](http://go.microsoft.com/fwlink/?LinkId=733413)取代該產品|  
|<xref:System.Web.Security.PassportAuthenticationEventHandler?displayProperty=fullName>|這個型別已經過時。 已不再支援 Passport 驗證產品，並且以 [Microsoft 帳戶](http://go.microsoft.com/fwlink/?LinkId=733413)取代該產品|  
|<xref:System.Web.Security.PassportAuthenticationModule?displayProperty=fullName>|這個型別已經過時。 已不再支援 Passport 驗證產品，並且以 [Microsoft 帳戶](http://go.microsoft.com/fwlink/?LinkId=733413)取代該產品|  
|<xref:System.Web.Security.PassportIdentity?displayProperty=fullName>|這個型別已經過時。 已不再支援 Passport 驗證產品，並且以 [Microsoft 帳戶](http://go.microsoft.com/fwlink/?LinkId=733413)取代該產品|  
|<xref:System.Web.Security.PassportPrincipal?displayProperty=fullName>|這個型別已經過時。 已不再支援 Passport 驗證產品，並且以 [Microsoft 帳戶](http://go.microsoft.com/fwlink/?LinkId=733413)取代該產品|  
|<xref:System.Web.UI.ObjectConverter?displayProperty=fullName>|建議的替代做法是 <xref:System.Convert?displayProperty=fullName> 和 <xref:System.String.Format%2A?displayProperty=fullName>。|  
  
 [回到頁首](#introduction)  
  
<a name="mobile"></a>   
### <a name="assembly-systemwebmobiledll"></a>組件：System.Web.Mobile.dll  
  
|類型|訊息|  
|----------|-------------|  
|<xref:System.Web.Mobile.CookielessData?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.Mobile.DeviceFilterElement?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.Mobile.DeviceFilterElementCollection?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.Mobile.DeviceFiltersSection?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.Mobile.ErrorHandlerModule?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.Mobile.MobileCapabilities?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.Mobile.MobileDeviceCapabilitiesSectionHandler?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.Mobile.MobileErrorInfo?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.Mobile.MobileFormsAuthentication?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.Design.MobileControls.IMobileDesigner?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.Design.MobileControls.IMobileWebFormServices?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.Design.MobileControls.MobileResource?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.Design.MobileControls.Converters.DataFieldConverter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.Design.MobileControls.Converters.DataMemberConverter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.AdRotator?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Alignment?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.ArrayListCollectionBase?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.BaseValidator?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.BooleanOption?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Calendar?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Command?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.CommandFormat?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.CompareValidator?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Constants?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.ControlElement?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.ControlElementCollection?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.ControlPager?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.CustomValidator?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.DesignerAdapterAttribute?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.DeviceElement?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.DeviceElementCollection?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.DeviceOverridableAttribute?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.DeviceSpecific?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoice?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoiceCollection?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoiceControlBuilder?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoiceTemplateBuilder?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoiceTemplateContainer?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.DeviceSpecificControlBuilder?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.ErrorFormatterPage?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.FontInfo?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.FontSize?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Form?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.FormControlBuilder?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.FormMethod?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.IControlAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Image?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.IObjectListFieldCollection?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.IPageAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.ItemPager?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.ITemplateable?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Label?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Link?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.List?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.ListCommandEventArgs?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.ListCommandEventHandler?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.ListControlBuilder?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.ListDataBindEventArgs?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.ListDataBindEventHandler?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.ListDecoration?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.ListSelectType?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.LiteralLink?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.LiteralText?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.LiteralTextContainerControlBuilder?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.LiteralTextControlBuilder?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.LoadItemsEventArgs?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.LoadItemsEventHandler?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.MobileControl?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.MobileControlBuilder?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.MobileControlsSection?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.MobileControlsSectionHandler?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.MobileListItem?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.MobileListItemCollection?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.MobileListItemType?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.MobilePage?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.MobileTypeNameConverter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.MobileUserControl?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.ObjectList?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.ObjectListCommand?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.ObjectListCommandCollection?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.ObjectListCommandEventArgs?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.ObjectListCommandEventHandler?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.ObjectListControlBuilder?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.ObjectListDataBindEventArgs?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.ObjectListDataBindEventHandler?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.ObjectListField?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.ObjectListFieldCollection?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.ObjectListItem?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.ObjectListItemCollection?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.ObjectListSelectEventArgs?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.ObjectListSelectEventHandler?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.ObjectListShowCommandsEventArgs?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.ObjectListShowCommandsEventHandler?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.ObjectListTitleAttribute?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.ObjectListViewMode?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.PagedControl?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.PagerStyle?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Panel?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.PanelControlBuilder?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.PersistNameAttribute?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.PhoneCall?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.RangeValidator?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.RegularExpressionValidator?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.RequiredFieldValidator?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.SelectionList?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Style?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.StyleSheet?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.StyleSheetControlBuilder?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.TemplateContainer?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.TextBox?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.TextBoxControlBuilder?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.TextControl?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.TextView?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.TextViewElement?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.ValidationSummary?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Wrapping?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlCalendarAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlCommandAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlFormAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlImageAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlLinkAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlMobileTextWriter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlPageAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlPhoneCallAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlSelectionListAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlTextBoxAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.ControlAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlCalendarAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlCommandAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlControlAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlFormAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlImageAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlLabelAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlLinkAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlListAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlLiteralTextAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlMobileTextWriter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlObjectListAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlPageAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlPanelAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlPhoneCallAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlSelectionListAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlTextBoxAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlTextViewAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlValidationSummaryAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlValidatorAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.MobileTextWriter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.MultiPartWriter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.UpWmlMobileTextWriter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.UpWmlPageAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlCalendarAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlCommandAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlControlAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlFormAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlImageAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlLabelAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlLinkAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlListAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlLiteralTextAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlMobileTextWriter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlObjectListAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlPageAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlPanelAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlPhoneCallAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlPostFieldType?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlSelectionListAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlTextBoxAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlTextViewAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlValidationSummaryAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlValidatorAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.Doctype?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.StyleSheetLocation?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlCalendarAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlCommandAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlControlAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlCssHandler?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlFormAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlImageAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlLabelAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlLinkAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlListAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlLiteralTextAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlMobileTextWriter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlObjectListAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlPageAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlPanelAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlPhoneCallAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlSelectionListAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlTextBoxAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlTextViewAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlValidationSummaryAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlValidatorAdapter?displayProperty=fullName>|System.Web.Mobile.dll 組件已被取代，不應該再使用。 如需如何開發 ASP.NET 行動應用程式的資訊，請參閱[行動裝置的 ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231)。|  
  
 [回到頁首](#introduction)  
  
<a name="workflow_activities"></a>   
### <a name="assembly-systemworkflowactivitiesdll"></a>組件：System.Workflow.Activities.dll  
  
|類型|訊息|  
|----------|-------------|  
|<xref:System.Workflow.Activities?displayProperty=fullName> 命名空間中的所有類型|在 .NET Framework 4.5 中首先被取代。<br /><br /> System.Workflow.\* 類型已被取代。 請改用 <xref:System.Activities>.\* 的新類型。|  
|<xref:System.Workflow.Activities.Configuration.ActiveDirectoryRoleFactoryConfiguration?displayProperty=fullName>|在 .NET Framework 4.5 中首先被取代。<br /><br /> System.Workflow.\* 類型已被取代。 請改用 <xref:System.Activities>.\* 的新類型。|  
|<xref:System.Workflow.Activities.Rules.RuleActionTrackingEvent?displayProperty=fullName>|在 .NET Framework 4.5 中首先被取代。<br /><br /> System.Workflow.\* 類型已被取代。 請改用 <xref:System.Activities>.\* 的新類型。|  
|<xref:System.Workflow.Activities.Rules.RuleConditionReference?displayProperty=fullName>|在 .NET Framework 4.5 中首先被取代。<br /><br /> System.Workflow.\* 類型已被取代。 請改用 <xref:System.Activities>.\* 的新類型。|  
|<xref:System.Workflow.Activities.Rules.RuleSetReference?displayProperty=fullName>|在 .NET Framework 4.5 中首先被取代。<br /><br /> System.Workflow.\* 類型已被取代。 請改用 <xref:System.Activities>.\* 的新類型。|  
  
 [回到頁首](#introduction)  
  
<a name="workflow_componentmodel"></a>   
### <a name="assembly-systemworkflowcomponentmodeldll"></a>組件：System.Workflow.ComponentModel.dll  
  
|類型|訊息|  
|----------|-------------|  
|<xref:System.Workflow.ComponentModel> 命名空間中除了 <xref:System.Workflow.ComponentModel.GetValueOverride?displayProperty=fullName> 和 <xref:System.Workflow.ComponentModel.SetValueOverride?displayProperty=fullName> 之外的所有類型|在 .NET Framework 4.5 中首先被取代。<br /><br /> System.Workflow.\* 類型已被取代。 請改用 <xref:System.Activities>.\* 的新類型。|  
|<xref:System.Workflow.ComponentModel.Compiler> 命名空間中除了 <xref:System.Workflow.ComponentModel.Compiler.ValidationError?displayProperty=fullName> 和 <xref:System.Workflow.ComponentModel.Compiler.ValidationErrorCollection?displayProperty=fullName> 之外的所有類型|在 .NET Framework 4.5 中首先被取代。<br /><br /> System.Workflow.\* 類型已被取代。 請改用 <xref:System.Activities>.\* 的新類型。|  
|<xref:System.Workflow.ComponentModel.Design> 命名空間中除了 <xref:System.Workflow.ComponentModel.Design.ConnectorEventHandler> 之外的所有類型|在 .NET Framework 4.5 中首先被取代。<br /><br /> System.Workflow.\* 類型已被取代。 請改用 <xref:System.Activities>.\* 的新類型。|  
|<xref:System.Workflow.ComponentModel.Serialization.ActivityCodeDomSerializationManager?displayProperty=fullName>|在 .NET Framework 4.5 中首先被取代。<br /><br /> System.Workflow.\* 類型已被取代。 請改用 <xref:System.Activities>.\* 的新類型。|  
|<xref:System.Workflow.ComponentModel.Serialization.ActivityCodeDomSerializer?displayProperty=fullName>|在 .NET Framework 4.5 中首先被取代。<br /><br /> System.Workflow.\* 類型已被取代。 請改用 <xref:System.Activities>.\* 的新類型。|  
|<xref:System.Workflow.ComponentModel.Serialization.ActivityMarkupSerializer?displayProperty=fullName>|在 .NET Framework 4.5 中首先被取代。<br /><br /> System.Workflow.\* 類型已被取代。 請改用 <xref:System.Activities>.\* 的新類型。|  
|<xref:System.Workflow.ComponentModel.Serialization.ActivitySurrogateSelector?displayProperty=fullName>|在 .NET Framework 4.5 中首先被取代。<br /><br /> System.Workflow.\* 類型已被取代。 請改用 <xref:System.Activities>.\* 的新類型。|  
|<xref:System.Workflow.ComponentModel.Serialization.ActivityTypeCodeDomSerializer?displayProperty=fullName>|在 .NET Framework 4.5 中首先被取代。<br /><br /> System.Workflow.\* 類型已被取代。 請改用 <xref:System.Activities>.\* 的新類型。|  
|<xref:System.Workflow.ComponentModel.Serialization.CompositeActivityMarkupSerializer?displayProperty=fullName>|在 .NET Framework 4.5 中首先被取代。<br /><br /> System.Workflow.\* 類型已被取代。 請改用 <xref:System.Activities>.\* 的新類型。|  
|<xref:System.Workflow.ComponentModel.Serialization.DependencyObjectCodeDomSerializer?displayProperty=fullName>|在 .NET Framework 4.5 中首先被取代。<br /><br /> System.Workflow.\* 類型已被取代。 請改用 <xref:System.Activities>.\* 的新類型。|  
  
 [回到頁首](#introduction)  
  
<a name="workflow_runtime"></a>   
### <a name="assembly-systemworkflowruntimedll"></a>組件：System.Workflow.Runtime.dll  
  
|類型|訊息|  
|----------|-------------| 
|System.Activities.Statements.Interop](assetId:///T:System.Activities.Statements.Interop)|在 .NET Framework 4.5 中首先被取代。<br /><br />Workflow Foundation 3.0 類型已被取代。 請改用 <xref:System.Activities>.\* 的 Workflow 4.0 類型。|  
|<xref:System.Activities.Tracking.InteropTrackingRecord>|在 .NET Framework 4.5 中首先被取代。<br /><br />Workflow Foundation 3.0 類型已被取代。 請改用 <xref:System.Activities>.\* 的 Workflow 4.0 類型。|   
|<xref:System.Workflow.Runtime> 命名空間中的所有類型|在 .NET Framework 4.5 中首先被取代。<br /><br /> System.Workflow.\* 類型已被取代。 請改用 <xref:System.Activities>.\* 的新類型。|  
|<xref:System.Workflow.Runtime.Configuration> 命名空間中的所有類型|在 .NET Framework 4.5 中首先被取代。<br /><br /> System.Workflow.\* 類型已被取代。 請改用 <xref:System.Activities>.\* 的新類型。|  
|<xref:System.Workflow.Runtime.DebugEngine> 命名空間中除了 <xref:System.Workflow.Runtime.DebugEngine.DebugEngineCallback> 之外的所有類型|在 .NET Framework 4.5 中首先被取代。<br /><br /> System.Workflow.\* 類型已被取代。 請改用 <xref:System.Activities>.\* 的新類型。|  
|<xref:System.Workflow.Runtime.Hosting> 命名空間中除了 <xref:System.Workflow.Runtime.Hosting.WorkflowCommitWorkBatchService.CommitWorkBatchCallback> 之外的所有類型|在 .NET Framework 4.5 中首先被取代。<br /><br /> System.Workflow.\* 類型已被取代。 請改用 <xref:System.Activities>.\* 的新類型。|  
|<xref:System.Workflow.Runtime.Tracking> 命名空間中的所有類型|在 .NET Framework 4.5 中首先被取代。<br /><br /> System.Workflow.\* 類型已被取代。 請改用 <xref:System.Activities>.\* 的新類型。|  
  
 [回到頁首](#introduction)  
  
<a name="workflowservices"></a>   
### <a name="assembly-systemworkflowservicesdll"></a>組件：System.WorkflowServices.dll  
  
|類型|訊息|  
|----------|-------------|  
|<xref:System.ServiceModel.WorkflowServiceHost?displayProperty=fullName>|在 .NET Framework 4.5 中首先被取代。<br /><br /> WF 3 型別已被取代。 請改用 <xref:System.Activities>.\* 的新 WF 4 類型。|  
|<xref:System.ServiceModel.Activation.WorkflowServiceHostFactory?displayProperty=fullName>|在 .NET Framework 4.5 中首先被取代。<br /><br /> WF 3 型別已被取代。 請改用 <xref:System.Activities>.\* 的新 WF 4 類型。|  
|<xref:System.ServiceModel.Activities.Description.WorkflowRuntimeEndpoint?displayProperty=fullName>|在 .NET Framework 4.5 中首先被取代。<br /><br /> WF 3 型別已被取代。 請改用 <xref:System.Activities>.\* 的新 WF 4 類型。|  
|<xref:System.ServiceModel.Configuration.ExtendedWorkflowRuntimeServiceElementCollection?displayProperty=fullName>|在 .NET Framework 4.5 中首先被取代。<br /><br /> WF 3 型別已被取代。 請改用 <xref:System.Activities>.\* 的新 WF 4 類型。|  
|<xref:System.ServiceModel.Configuration.PersistenceProviderElement?displayProperty=fullName>|在 .NET Framework 4.5 中首先被取代。<br /><br /> WF 3 型別已被取代。 請改用 <xref:System.Activities>.\* 的新 WF 4 類型。|  
|<xref:System.ServiceModel.Configuration.WorkflowRuntimeElement?displayProperty=fullName>|在 .NET Framework 4.5 中首先被取代。<br /><br /> WF 3 型別已被取代。 請改用 <xref:System.Activities>.\* 的新 WF 4 類型。|  
|<xref:System.ServiceModel.Description.DurableOperationAttribute?displayProperty=fullName>|在 .NET Framework 4.5 中首先被取代。<br /><br /> WF 3 型別已被取代。 請改用 <xref:System.Activities>.\* 的新 WF 4 類型。|  
|<xref:System.ServiceModel.Description.DurableServiceAttribute?displayProperty=fullName>|在 .NET Framework 4.5 中首先被取代。<br /><br /> WF 3 型別已被取代。 請改用 <xref:System.Activities>.\* 的新 WF 4 類型。|  
|<xref:System.ServiceModel.Description.PersistenceProviderBehavior?displayProperty=fullName>|在 .NET Framework 4.5 中首先被取代。<br /><br /> WF 3 型別已被取代。 請改用 <xref:System.Activities>.\* 的新 WF 4 類型。|  
|<xref:System.ServiceModel.Description.UnknownExceptionAction?displayProperty=fullName>|在 .NET Framework 4.5 中首先被取代。<br /><br /> WF 3 型別已被取代。 請改用 <xref:System.Activities>.\* 的新 WF 4 類型。|  
|<xref:System.ServiceModel.Description.WorkflowRuntimeBehavior?displayProperty=fullName>|在 .NET Framework 4.5 中首先被取代。<br /><br /> WF 3 型別已被取代。 請改用 <xref:System.Activities>.\* 的新 WF 4 類型。|  
|<xref:System.ServiceModel.Dispatcher.DurableOperationContext?displayProperty=fullName>|在 .NET Framework 4.5 中首先被取代。<br /><br /> WF 3 型別已被取代。 請改用 <xref:System.Activities>.\* 的新 WF 4 類型。|  
|<xref:System.ServiceModel.Persistence.InstanceLockException?displayProperty=fullName>|在 .NET Framework 4.5 中首先被取代。<br /><br /> WF 3 型別已被取代。 請改用 <xref:System.Activities>.\* 的新 WF 4 類型。|  
|<xref:System.ServiceModel.Persistence.InstanceNotFoundException?displayProperty=fullName>|在 .NET Framework 4.5 中首先被取代。<br /><br /> WF 3 型別已被取代。 請改用 <xref:System.Activities>.\* 的新 WF 4 類型。|  
|<xref:System.ServiceModel.Persistence.LockingPersistenceProvider?displayProperty=fullName>|在 .NET Framework 4.5 中首先被取代。<br /><br /> WF 3 型別已被取代。 請改用 <xref:System.Activities>.\* 的新 WF 4 類型。|  
|<xref:System.ServiceModel.Persistence.PersistenceException?displayProperty=fullName>|在 .NET Framework 4.5 中首先被取代。<br /><br /> WF 3 型別已被取代。 請改用 <xref:System.Activities>.\* 的新 WF 4 類型。|  
|<xref:System.ServiceModel.Persistence.PersistenceProvider?displayProperty=fullName>|在 .NET Framework 4.5 中首先被取代。<br /><br /> WF 3 型別已被取代。 請改用 <xref:System.Activities>.\* 的新 WF 4 類型。|  
|<xref:System.ServiceModel.Persistence.PersistenceProviderFactory?displayProperty=fullName>|在 .NET Framework 4.5 中首先被取代。<br /><br /> WF 3 型別已被取代。 請改用 <xref:System.Activities>.\* 的新 WF 4 類型。|  
|<xref:System.ServiceModel.Persistence.SqlPersistenceProviderFactory?displayProperty=fullName>|在 .NET Framework 4.5 中首先被取代。<br /><br /> WF 3 型別已被取代。 請改用 <xref:System.Activities>.\* 的新 WF 4 類型。|  
|<xref:System.Workflow.Activities?displayProperty=fullName> 命名空間中的所有類型|在 .NET Framework 4.5 中首先被取代。<br /><br /> WF 3 型別已被取代。 請改用 <xref:System.Activities>.\* 的新 WF 4 類型。|  
|<xref:System.Workflow.Runtime.Hosting.ChannelManagerService?displayProperty=fullName>|在 .NET Framework 4.5 中首先被取代。<br /><br /> WF 3 型別已被取代。 請改用 <xref:System.Activities>.\* 的新 WF 4 類型。|  
  
 [回到頁首](#introduction)  
  
<a name="xaml"></a>   
### <a name="assembly-systemxamldll"></a>組件：System.Xaml.dll  
  
|類型|訊息|  
|----------|-------------|  
|<xref:System.Windows.Markup.AcceptedMarkupExtensionExpressionTypeAttribute?displayProperty=fullName>|XAML 剖析器已不使用這個項目。 請查看 <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute?displayProperty=fullName>。|  
  
 [回到頁首](#introduction)  
  
<a name="xml"></a>   
### <a name="assembly-systemxmldll"></a>組件：System.Xml.dll  
  
|類型|訊息|  
|----------|-------------|  
|<xref:System.Xml.IApplicationResourceStreamResolver?displayProperty=fullName>|在 .NET Framework 4.5 中首先被取代。<br /><br /> 使用這個型別會產生編譯器錯誤。<br /><br /> 這個 API 支援 .NET Framework 基礎結構，並不適合直接從您的程式碼中使用。|  
|<xref:System.Xml.Schema.XmlSchemaCollection?displayProperty=fullName>|請使用 <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=fullName> 進行結構描述編譯和驗證。|  
|<xref:System.Xml.XmlValidatingReader?displayProperty=fullName>|請改用 <xref:System.Xml.XmlReader.Create%2A?displayProperty=fullName> 方法搭配適當的 <xref:System.Xml.XmlReaderSettings?displayProperty=fullName> 所建立的 <xref:System.Xml.XmlReader?displayProperty=fullName>。|  
|<xref:System.Xml.XmlXapResolver?displayProperty=fullName>|使用這個型別會產生編譯器錯誤。 這個 API 支援 .NET Framework 基礎結構，並不適合直接從您的程式碼中使用。|  
|<xref:System.Xml.Xsl.XslTransform?displayProperty=fullName>|這個類別已被取代。 請改用 <xref:System.Xml.Xsl.XslCompiledTransform?displayProperty=fullName>。|  
  
 [回到頁首](#introduction)  
  
<a name="WindowsBase"></a>   
### <a name="assembly-windowsbasedll"></a>組件：WindowsBase.dll  
  
|類型|訊息|  
|----------|-------------|  
|<xref:System.Windows.Markup.IReceiveMarkupExtension?displayProperty=fullName>|<xref:System.Windows.Markup.IReceiveMarkupExtension?displayProperty=fullName> 已被取代。 這個介面不再使用。|  
  
 [回到頁首](#introduction)  
  
<a name="obsolete_types_in_microsoft_assemblies"></a>   
## <a name="obsolete-types-in-microsoft-assemblies"></a>Microsoft 組件中的過時型別  
 下列章節將列出 Microsoft 組件中的過時型別。 這些組件是特殊用途的組件，例如以個別語言 (例如 Microsoft.JScript.dll 或 Microsoft.VisualC.dll) 為目標的組件。  
  
<a name="IEHost"></a>   
### <a name="assembly-iehostdll-and-ieexecexe"></a>組件：IEHost.dll 和 IEExec.exe  
 IEHost.dll 和 IEExec.exe 組件已經從 .NET Framework 中移除。 其所有型別和成員都已經過時，而且 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 中不再支援。 這些組件之前是用來裝載 Windows Form 控制項以及在 Internet Explorer 中執行可執行檔。 建議的替代方案包括 ClickOnce、XAML 瀏覽器應用程式 (XBAP) 和 Microsoft Silverlight。  
  
 [回到頁首](#introduction)  
  
<a name="Engine"></a>   
### <a name="assembly-microsoftbuildenginedll"></a>組件：Microsoft.Build.Engine.dll  
  
|類型|訊息|  
|----------|-------------|  
|<xref:Microsoft.Build.BuildEngine.Engine?displayProperty=fullName>|這個類別已被取代。 請改用 <!--zz <xref:Microsoft.Build?displayProperty=fullName> -->``Microsoft.Build` 組件中的 <xref:Microsoft.Build.Evaluation.ProjectCollection?displayProperty=fullName>。|  
|<xref:Microsoft.Build.BuildEngine.Project?displayProperty=fullName>|這個類別已被取代。 請改用 <xref:Microsoft.Build?displayProperty=fullName> 組件中的 <xref:Microsoft.Build.Evaluation.ProjectCollection?displayProperty=fullName>。|  
  
 [回到頁首](#introduction)  
  
<a name="jscript"></a>   
### <a name="assembly-microsoftjscriptdll"></a>組件：Microsoft.JScript.dll  
  
|類型|訊息|  
|----------|-------------|  
|<xref:Microsoft.JScript.Vsa.BaseVsaEngine?displayProperty=fullName>|這個型別在 Visual Studio 2005 中已不適用，因此不建議使用這個型別。目前沒有取代這項功能的項目。 如需其他說明，請參閱 <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> 文件。|  
|<xref:Microsoft.JScript.Vsa.BaseVsaSite?displayProperty=fullName>|這個型別在 Visual Studio 2005 中已不適用，因此不建議使用這個型別。目前沒有取代這項功能的項目。 如需其他說明，請參閱 <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> 文件。|  
|<xref:Microsoft.JScript.Vsa.BaseVsaStartup?displayProperty=fullName>|這個型別在 Visual Studio 2005 中已不適用，因此不建議使用這個型別。目前沒有取代這項功能的項目。 如需其他說明，請參閱 <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> 文件。|  
|<xref:Microsoft.JScript.Vsa.IJSVsaCodeItem?displayProperty=fullName>|這個型別在 Visual Studio 2005 中已不適用，因此不建議使用這個型別。目前沒有取代這項功能的項目。 如需其他說明，請參閱 <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> 文件。|  
|<xref:Microsoft.JScript.Vsa.IJSVsaEngine?displayProperty=fullName>|這個型別在 Visual Studio 2005 中已不適用，因此不建議使用這個型別。目前沒有取代這項功能的項目。 如需其他說明，請參閱 <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> 文件。|  
|<xref:Microsoft.JScript.Vsa.IJSVsaError?displayProperty=fullName>|這個型別在 Visual Studio 2005 中已不適用，因此不建議使用這個型別。目前沒有取代這項功能的項目。 如需其他說明，請參閱 <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> 文件。|  
|<xref:Microsoft.JScript.Vsa.IJSVsaGlobalItem?displayProperty=fullName>|這個型別在 Visual Studio 2005 中已不適用，因此不建議使用這個型別。目前沒有取代這項功能的項目。 如需其他說明，請參閱 <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> 文件。|  
|<xref:Microsoft.JScript.Vsa.IJSVsaItem?displayProperty=fullName>|這個型別在 Visual Studio 2005 中已不適用，因此不建議使用這個型別。目前沒有取代這項功能的項目。 如需其他說明，請參閱 <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> 文件。|  
|<xref:Microsoft.JScript.Vsa.IJSVsaItems?displayProperty=fullName>|這個型別在 Visual Studio 2005 中已不適用，因此不建議使用這個型別。目前沒有取代這項功能的項目。 如需其他說明，請參閱 <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> 文件。|  
|<xref:Microsoft.JScript.Vsa.IJSVsaPersistSite?displayProperty=fullName>|這個型別在 Visual Studio 2005 中已不適用，因此不建議使用這個型別。目前沒有取代這項功能的項目。 如需其他說明，請參閱 <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> 文件。|  
|<xref:Microsoft.JScript.Vsa.IJSVsaReferenceItem?displayProperty=fullName>|這個型別在 Visual Studio 2005 中已不適用，因此不建議使用這個型別。目前沒有取代這項功能的項目。 如需其他說明，請參閱 <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> 文件。|  
|<xref:Microsoft.JScript.Vsa.IJSVsaSite?displayProperty=fullName>|這個型別在 Visual Studio 2005 中已不適用，因此不建議使用這個型別。目前沒有取代這項功能的項目。 如需其他說明，請參閱 <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> 文件。|  
|<xref:Microsoft.JScript.Vsa.JSVsaError?displayProperty=fullName>|這個型別在 Visual Studio 2005 中已不適用，因此不建議使用這個型別。目前沒有取代這項功能的項目。 如需其他說明，請參閱 <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> 文件。|  
|<xref:Microsoft.JScript.Vsa.JSVsaException?displayProperty=fullName>|這個型別在 Visual Studio 2005 中已不適用，因此不建議使用這個型別。目前沒有取代這項功能的項目。 如需其他說明，請參閱 <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> 文件。|  
|<xref:Microsoft.JScript.Vsa.JSVsaItemFlag?displayProperty=fullName>|這個型別在 Visual Studio 2005 中已不適用，因此不建議使用這個型別。目前沒有取代這項功能的項目。 如需其他說明，請參閱 <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> 文件。|  
|<xref:Microsoft.JScript.Vsa.JSVsaItemType?displayProperty=fullName>|這個型別在 Visual Studio 2005 中已不適用，因此不建議使用這個型別。目前沒有取代這項功能的項目。 如需其他說明，請參閱 <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> 文件。|  
|<xref:Microsoft.JScript.Vsa.ResInfo?displayProperty=fullName>|這個型別在 Visual Studio 2005 中已不適用，因此不建議使用這個型別。目前沒有取代這項功能的項目。 如需其他說明，請參閱 <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> 文件。|  
|<xref:Microsoft.JScript.Vsa.VsaEngine?displayProperty=fullName>|這個型別在 Visual Studio 2005 中已不適用，因此不建議使用這個型別。目前沒有取代這項功能的項目。 如需其他說明，請參閱 <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> 文件。|  
  
 [回到頁首](#introduction)  
  
<a name="VBCompat"></a>   
### <a name="assembly-microsoftvisualbasiccompatibilitydll"></a>組件：Microsoft.VisualBasic.Compatibility.dll  
  
|類型|訊息|  
|----------|-------------|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.BaseControlArray?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.BaseOcxArray?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ButtonArray?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.CheckBoxArray?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.CheckedListBoxArray?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ColorDialogArray?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ComboBoxArray?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DirListBox?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DirListBoxArray?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DriveListBox?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DriveListBoxArray?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FileListBox?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FileListBoxArray?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FixedLengthString?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FontDialogArray?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FormShowConstants?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.GroupBoxArray?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.HScrollBarArray?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ImageListArray?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.LabelArray?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ListBoxArray?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ListBoxItem?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ListViewArray?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.LoadResConstants?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MaskedTextBoxArray?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MenuItemArray?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MouseButtonConstants?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.OpenFileDialogArray?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.PanelArray?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.PictureBoxArray?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.PrintDialogArray?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ProgressBarArray?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.RadioButtonArray?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.RichTextBoxArray?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.SaveFileDialogArray?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ScaleMode?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ShiftConstants?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.StatusBarArray?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.StatusStripArray?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.Support?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.TabControlArray?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.TextBoxArray?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.TimerArray?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ToolBarArray?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ToolStripArray?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ToolStripMenuItemArray?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.TreeViewArray?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.VScrollBarArray?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebBrowserArray?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClass?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassContainingClassNotOptional?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassCouldNotFindEvent?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassNextItemCannotBeCurrentWebItem?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassNextItemRespondNotFound?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassUserWebClassNameNotOptional?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassWebClassFileNameNotOptional?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassWebItemNotValid?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItem?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemAssociatedWebClassNotOptional?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemClosingTagNotFound?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemCouldNotLoadEmbeddedResource?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemCouldNotLoadTemplateFile?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemNameNotOptional?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemNoTemplateSpecified?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemTooManyNestedTags?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemUnexpectedErrorReadingTemplateFile?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ZOrderConstants?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
  
 [回到頁首](#introduction)  
  
<a name="VBCompatData"></a>   
### <a name="assembly-microsoftvisualbasiccompatibilitydatadll"></a>組件：Microsoft.VisualBasic.Compatibility.Data.dll  
  
|類型|訊息|  
|----------|-------------|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.BOFActionEnum?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.EndOfRecordsetDelegate?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.EOFActionEnum?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.ErrorDelegate?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.FetchCompleteDelegate?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.FetchProgressDelegate?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.FieldChangeCompleteDelegate?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.MoveCompleteDelegate?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.OrientationEnum?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.RecordChangeCompleteDelegate?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.RecordsetChangeCompleteDelegate?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.WillChangeFieldDelegate?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.WillChangeRecordDelegate?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.WillChangeRecordsetDelegate?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.WillMoveDelegate?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODCArray?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.BaseDataEnvironment?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.BindingCollectionEnumerator?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.CONNECTDATA?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBBINDING?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBCOLUMNINFO?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBID?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBinding?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBindingCollection?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBKINDENUM?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBPROPIDSET?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IAccessor?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IChapteredRowset?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IColumnsInfo?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IConnectionPoint?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IConnectionPointContainer?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IDataFormat?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IDataFormatDisp?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IEnumConnectionPoints?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IEnumConnections?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowPosition?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowPositionChange?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowset?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowsetChange?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowsetIdentity?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowsetInfo?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowsetNotify?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MBinding?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MBindingCollection?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.SRDescriptionAttribute?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.UGUID?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.UNAME?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.UpdateMode?displayProperty=fullName>|請參閱 [Microsoft.VisualBasic.Compatibility.VB6.\<member> 已過時，僅受 32 位元處理序支援](https://msdn.microsoft.com/library/ee839621.aspx)。|  
  
 [回到頁首](#introduction)  
  
<a name="visualc"></a>   
### <a name="assembly-microsoftvisualcdll"></a>組件：Microsoft.VisualC.dll  
  
|類型|訊息|  
|----------|-------------|  
|<xref:Microsoft.VisualC.DebugInfoInPDBAttribute?displayProperty=fullName>|Microsoft.VisualC.dll 這個組件已經過時，其存在目的只是為了提供回溯相容性。|  
|<xref:Microsoft.VisualC.DecoratedNameAttribute?displayProperty=fullName>|Microsoft.VisualC.dll 這個組件已經過時，其存在目的只是為了提供回溯相容性。|  
|<xref:Microsoft.VisualC.IsConstModifier?displayProperty=fullName>|Microsoft.VisualC.dll 這個組件已經過時，其存在目的只是為了提供回溯相容性。|  
|<xref:Microsoft.VisualC.IsCXXReferenceModifier?displayProperty=fullName>|Microsoft.VisualC.dll 這個組件已經過時，其存在目的只是為了提供回溯相容性。|  
|<xref:Microsoft.VisualC.IsLongModifier?displayProperty=fullName>|Microsoft.VisualC.dll 這個組件已經過時，其存在目的只是為了提供回溯相容性。|  
|<xref:Microsoft.VisualC.IsSignedModifier?displayProperty=fullName>|Microsoft.VisualC.dll 這個組件已經過時，其存在目的只是為了提供回溯相容性。|  
|<xref:Microsoft.VisualC.IsVolatileModifier?displayProperty=fullName>|Microsoft.VisualC.dll 這個組件已經過時，其存在目的只是為了提供回溯相容性。|  
|<xref:Microsoft.VisualC.MiscellaneousBitsAttribute?displayProperty=fullName>|Microsoft.VisualC.dll 這個組件已經過時，其存在目的只是為了提供回溯相容性。|  
|<xref:Microsoft.VisualC.NeedsCopyConstructorModifier?displayProperty=fullName>|Microsoft.VisualC.dll 這個組件已經過時，其存在目的只是為了提供回溯相容性。|  
|<xref:Microsoft.VisualC.NoSignSpecifiedModifier?displayProperty=fullName>|Microsoft.VisualC.dll 這個組件已經過時，其存在目的只是為了提供回溯相容性。|  
  
## <a name="see-also"></a>另請參閱  
 [類別庫中的過時功能](../../../docs/framework/whats-new/whats-obsolete.md)   
 [過時的成員](../../../docs/framework/whats-new/obsolete-members.md)
