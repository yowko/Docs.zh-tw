---
title: "實作 UI 自動化 GridItem 控制項模式 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GridItem 控制項模式"
  - "UI 自動化 GridItem 控制項模式"
  - "GridItem 控制項模式"
ms.assetid: bffbae08-fe2a-42fd-ab84-f37187518916
caps.latest.revision: 15
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 15
---
# 實作 UI 自動化 GridItem 控制項模式
> [!NOTE]
>  這份文件適用於.NET Framework 開發人員想要使用 managed[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]中定義的類別<xref:System.Windows.Automation>命名空間。 如需最新資訊[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，請參閱[Windows Automation API: UI 自動化](http://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 本主題介紹的指導方針和慣例實作<xref:System.Windows.Automation.Provider.IGridItemProvider>，包括屬性的相關資訊。 其他參考的連結會在概觀的結尾列出。  
  
 <xref:System.Windows.Automation.GridItemPattern>控制項模式用來支援個別的子控制項的容器實作<xref:System.Windows.Automation.Provider.IGridProvider>。 如需實作此控制項模式的控制項的範例，請參閱[控制項模式對應 UI 自動化用戶端的](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)。  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>實作方針和慣例  
 當實作<xref:System.Windows.Automation.Provider.IGridProvider>，請注意下列指導方針和慣例︰  
  
-   方格座標是以零起始，左上資料格座標為 (0, 0)。  
  
-   合併資料格將會回報其<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>和<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>屬性根據其基礎錨點的儲存格所定義的 UI 自動化提供者。 通常，它會是最上層或最左邊的資料列或資料行。  
  
-   <xref:System.Windows.Automation.Provider.IGridItemProvider>不提供例如合併或分割資料格方格的作用中操作。  
  
-   控制實作<xref:System.Windows.Automation.Provider.IGridItemProvider>可通常貫穿 （也就是 UI 自動化用戶端可以移動至相鄰的控制項） 使用鍵盤。  
  
<a name="Required_Members_for_IGridItemProvider"></a>   
## <a name="required-members-for-igriditemprovider"></a>IGridItemProvider 的必要成員  
 下列屬性和方法所需的實作<xref:System.Windows.Automation.Provider.IGridItemProvider>。  
  
|必要成員|成員類型|備註|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>|屬性|無|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>|屬性|無|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.RowSpan%2A>|屬性|無|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ColumnSpan%2A>|屬性|無|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A>|屬性|無|  
  
 此控制項模式沒有任何相關聯的方法或事件。  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>例外狀況  
 此控制項模式沒有任何相關聯的例外狀況。  
  
## <a name="see-also"></a>另請參閱  
 [UI 自動化控制項模式概觀](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)   
 [支援 UI 自動化提供者的控制項模式](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)   
 [用戶端的 UI 自動化控制項模式](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)   
 [實作 UI 自動化 Grid 控制項模式](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md)   
 [UI 自動化樹狀目錄概觀](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)   
 [使用 UI 自動化中的快取](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)