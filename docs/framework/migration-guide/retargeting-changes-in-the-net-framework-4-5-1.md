---
title: ".NET Framework 4.5.1 中的重定目標變更 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8087326d-77e9-4804-ba33-ff1bb1bec2b8
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 15
---
# .NET Framework 4.5.1 中的重定目標變更
在某些罕見的情況下，重定目標變更可能會影響以 [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] 為目標來重新編譯的應用程式。 這些變更不會影響以舊版 .NET Framework 為目標但在 4.5.1 版下執行的二進位檔。[!INCLUDE[net_v451](../../../includes/net-v451-md.md)] 包含下列區域的重定目標變更：  
  
-   [核心](#Core)  
  
-   [ADO.NET](#ADO)  
  
-   [MSBuild](#MSBuild)  
  
 下表中的 \[範圍\] 一欄指定每項變更的重要性：  
  
-   主要。 影響大量應用程式或需要大幅修改程式碼的重大變更。 請注意，重定目標變更不屬於此分類。  
  
-   次要。 影響少量應用程式或需要稍微修改程式碼的變更。  
  
-   邊緣。 在非常特定 \(罕見\) 的情況下影響應用程式的變更。  
  
-   透明。 此變更對應用程式的開發人員或使用者的影響不明顯。 發生此變更的應用程式應該不需要修改。  
  
<a name="Core"></a>   
## 核心重定目標變更  
  
|功能|變更|影響|範圍|  
|--------|--------|--------|--------|  
|<xref:System.ObsoleteAttribute?displayProperty=fullName> 屬性|當您建立 Windows 中繼資料庫 \(.winmd 檔案\) 時，<xref:System.ObsoleteAttribute> 屬性會匯出為 <xref:System.ObsoleteAttribute> 和 [Windows.Foundation.DeprecatedAttribute](http://msdn.microsoft.com/library/windows/apps/windows.foundation.metadata.deprecatedattribute.aspx)。|重新編譯使用 <xref:System.ObsoleteAttribute> 屬性的現有原始程式碼，可能會在從 C\+\+\/CX 或 JavaScript 使用該程式碼時產生警告。<br /><br /> 我們不建議您同時套用 <xref:System.ObsoleteAttribute> 和 [Windows.Foundation.DeprecatedAttribute](http://msdn.microsoft.com/library/windows/apps/windows.foundation.metadata.deprecatedattribute.aspx) 至 Managed 組件中的程式碼；這可能會導致建置警告。<br /><br /> 如需詳細資訊，請參閱 <xref:System.ObsoleteAttribute> 參考主題。|邊緣|  
  
<a name="ADO"></a>   
## ADO.NET 重定目標變更  
  
|功能|變更|影響|範圍|  
|--------|--------|--------|--------|  
|<xref:System.Data.Common.DbParameter?displayProperty=fullName> 類別|<xref:System.Data.Common.DbParameter.Precision%2A?displayProperty=fullName> 和 <xref:System.Data.Common.DbParameter.Scale%2A?displayProperty=fullName> 會當做公用虛擬屬性來實作。 這些屬性取代對應的明確介面實作 <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Precision%2A?displayProperty=fullName> 和 <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Scale%2A?displayProperty=fullName>。|這項變更只會影響建置 ADO.NET 資料庫提供者的開發人員。|邊緣|  
  
<a name="MSBuild"></a>   
## MSBuild 重定目標變更  
  
|功能|變更|影響|範圍|  
|--------|--------|--------|--------|  
|`ResolveAssemblyReference` 工作|這項工作會發出警告 MSB3270，指出某個參考或參考的任何一個相依性不符合應用程式的架構。 例如，如果使用 `anycpu` 選項編譯的應用程式包含 x86 參考，則會發生此情況。 這類情況會導致應用程式在執行階段失敗 \(在本範例中，如果應用程式部署為 x64 處理序\)。|影響可分為下列兩方面：<br /><br /> -   重新編譯會產生在舊版 MSBuild 下編譯應用程式時未顯示的警告。 不過，由於此警告識別執行階段失敗的可能來源，因此應該加以調查和解決。<br />-   如果將警告視為錯誤，應用程式將無法編譯。|次要|  
  
## 請參閱  
 [執行階段變更](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-5-1.md)   
 [4.5 中的應用程式相容性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5.md)   
 [4.5.2 中的應用程式相容性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5-2.md)