---
title: 實作 UI 自動化 GridItem 控制項模式
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, GridItem
- UI Automation GridItem control pattern
- GridItem control pattern
ms.assetid: bffbae08-fe2a-42fd-ab84-f37187518916
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: bfe2e62e98dd206d85e87d8885a1c58786a420fc
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43855461"
---
# <a name="implementing-the-ui-automation-griditem-control-pattern"></a>實作 UI 自動化 GridItem 控制項模式
> [!NOTE]
>  這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。 如需最新資訊[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，請參閱 < [Windows Automation API： 使用者介面自動化](https://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 本主題將介紹的實作方針和慣例<xref:System.Windows.Automation.Provider.IGridItemProvider>，包括內容的相關資訊。 其他參考的連結會在概觀的結尾列出。  
  
 <xref:System.Windows.Automation.GridItemPattern>控制項模式用以支援實作容器的個別子控制項<xref:System.Windows.Automation.Provider.IGridProvider>。 如需實作此控制項模式的控制項範例，請參閱 [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)。  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>實作方針和慣例  
 當實作<xref:System.Windows.Automation.Provider.IGridProvider>，請注意下列方針和慣例：  
  
-   方格座標是以零起始，左上資料格座標為 (0, 0)。  
  
-   合併的資料格將會報告它們<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>和<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>屬性根據其基礎的錨定儲存格所定義的使用者介面自動化提供者。 通常，它會是最上層或最左邊的資料列或資料行。  
  
-   <xref:System.Windows.Automation.Provider.IGridItemProvider> 不提供例如合併或分割資料格方格的主動操作。  
  
-   控制實作<xref:System.Windows.Automation.Provider.IGridItemProvider>通常可周遊 （也就是使用者介面自動化用戶端可以移至相鄰的控制項） 使用鍵盤。  
  
<a name="Required_Members_for_IGridItemProvider"></a>   
## <a name="required-members-for-igriditemprovider"></a>IGridItemProvider 的必要成員  
 以下是實作 <xref:System.Windows.Automation.Provider.IGridItemProvider> 的必要屬性和方法。  
  
|必要成員|成員類型|注意|  
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
 [在 UI 自動化中使用快取](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
