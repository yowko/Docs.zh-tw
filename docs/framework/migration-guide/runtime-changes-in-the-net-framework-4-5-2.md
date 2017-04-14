---
title: ".NET Framework 4.5.2 中的執行階段變更 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 94ac01ea-8b12-44d2-b12b-5220a5d14d87
caps.latest.revision: 5
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 5
---
# .NET Framework 4.5.2 中的執行階段變更
在某些罕見的情況下，執行階段變更可能會影響以舊版 .NET Framework 為目標但在 .NET Framework 4.5.2 執行階段上執行的現有應用程式， 其中包含下列區域的變更：  
  
-   [ASP.NET](#ASP_NET)  
  
-   [Entity Framework](#EF)  
  
<a name="ASP_NET"></a>   
## ASP.NET 執行階段變更  
  
|功能|變更|影響|範圍|  
|--------|--------|--------|--------|  
|[頁面項目](http://msdn.microsoft.com/zh-tw/4123bb66-3fe4-4d62-b70e-33758656b458)的 `enableViewStateMac` 屬性|ASP.NET 不再允許開發人員指定：<br /><br /> `<pages enableViewStateMac="false" />`<br /><br /> 或：<br /><br /> `<@Page EnableViewStateMac="false" %>`|檢視狀態訊息驗證碼 \(MAC\) 現在會強制所有要求內嵌檢視狀態。 只會影響將 <xref:System.Web.UI.Page.EnableViewStateMac%2A> 屬性明確設為 `false` 的應用程式。<br /><br /> 如需詳細資訊，請參閱[解決檢視狀態訊息驗證碼 \(MAC\) 錯誤](http://support.microsoft.com/kb/2915218)。|主要|  
  
<a name="EF"></a>   
## Entity Framework 執行階段變更  
  
|功能|變更|影響|範圍|  
|--------|--------|--------|--------|  
|QueryView 的關聯性|當應用程式執行與 QueryView \(巡覽屬性為 0..1\) 相關的查詢，嘗試在查詢中包含相關的項目時 \(例如藉由呼叫 <xref:System.StackOverflowException>\)，Entity Framework 不再擲回 `.Include(e=>e.RelatedNavProp)` 例外狀況。|這項變更只會影響使用 QueryViews \(關聯性為 1\-0..1\) 執行呼叫 `.Include` 之查詢的程式碼。 這項功能可提高可靠性，對於幾乎所有應用程式應該都是透明的。 不過，如果這項功能造成未預期的行為，您可以在應用程式組態檔的 `<appSettings>` 區段中加入下列項目，來停用這項功能：<br /><br /> `<add key="EntityFramework_SimplifyUserSpecifiedViews"  value="false" />`|邊緣|  
  
## 請參閱  
 [重定目標變更](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-5-2.md)   
 [4.5 中的應用程式相容性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5.md)   
 [4.5.1 中的應用程式相容性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5-1.md)