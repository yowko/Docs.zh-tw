---
title: "實作 UI 自動化 TableItem 控制項模式 | Microsoft Docs"
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
  - "控制項模式，資料表項目"
  - "UI 自動化中，資料表 Item 控制項模式"
  - "TableItem 控制項模式"
ms.assetid: ac178408-1485-436f-8d3e-eee3bf80cb24
caps.latest.revision: 14
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 14
---
# 實作 UI 自動化 TableItem 控制項模式
> [!NOTE]
>  這份文件適用於.NET Framework 開發人員想要使用 managed[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]中定義的類別<xref:System.Windows.Automation>命名空間。 如需最新資訊[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，請參閱[Windows Automation API: UI 自動化](http://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 本主題介紹的指導方針和慣例實作<xref:System.Windows.Automation.Provider.ITableItemProvider>，包括事件和屬性的相關資訊。 其他參考的連結會在概觀的結尾列出。  
  
 <xref:System.Windows.Automation.TableItemPattern>控制項模式用來支援子控制項的容器實作<xref:System.Windows.Automation.Provider.ITableProvider>。 個別儲存格功能的存取權由必要並行實作<xref:System.Windows.Automation.Provider.IGridItemProvider>。 此控制項模式相當於<xref:System.Windows.Automation.Provider.IGridItemProvider>與任何控制項實作的區別<xref:System.Windows.Automation.Provider.ITableItemProvider>必須以程式設計方式公開其資料列和資料行資訊的個別儲存格之間的關聯性。 如需實作此控制項模式的控制項的範例，請參閱[控制項模式對應 UI 自動化用戶端的](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)。  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>實作方針和慣例  
  
-   相關的格線項目功能，請參閱[實作 UI 自動化 GridItem 控制項模式](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md)。  
  
<a name="Required_Members_for_ITableItemProvider"></a>   
## <a name="required-members-for-itableitemprovider"></a>ITableItemProvider 的必要成員  
  
|必要成員|成員類型|備註|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetColumnHeaderItems%2A>|方法|無|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetRowHeaderItems%2A>|方法|無|  
  
 此控制項模式沒有任何相關聯的屬性或事件。  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>例外狀況  
 此控制項模式沒有任何相關聯的例外狀況。  
  
## <a name="see-also"></a>另請參閱  
 [UI 自動化控制項模式概觀](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)   
 [支援 UI 自動化提供者的控制項模式](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)   
 [用戶端的 UI 自動化控制項模式](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)   
 [實作 UI 自動化 Table 控制項模式](../../../docs/framework/ui-automation/implementing-the-ui-automation-table-control-pattern.md)   
 [實作 UI 自動化 GridItem 控制項模式](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md)   
 [UI 自動化樹狀目錄概觀](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)   
 [使用 UI 自動化中的快取](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)