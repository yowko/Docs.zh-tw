---
title: "實作 UI 自動化 ScrollItem 控制項模式 | Microsoft Docs"
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
  - "控制項模式，捲軸項目"
  - "UI 自動化 Scroll Item 控制項模式"
  - "Scroll Item 控制項模式"
ms.assetid: 903bab5c-80c1-44d7-bdc2-0a418893b987
caps.latest.revision: 16
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 16
---
# 實作 UI 自動化 ScrollItem 控制項模式
> [!NOTE]
>  這份文件適用於.NET Framework 開發人員想要使用 managed[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]中定義的類別<xref:System.Windows.Automation>命名空間。 如需最新資訊[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，請參閱[Windows Automation API: UI 自動化](http://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 本主題介紹的指導方針和慣例實作<xref:System.Windows.Automation.Provider.IScrollItemProvider>，包括屬性、 方法和事件的相關資訊。 其他參考的連結列於主題的結尾。  
  
 <xref:System.Windows.Automation.ScrollItemPattern>控制項模式用來支援個別的子控制項的容器實作<xref:System.Windows.Automation.Provider.IScrollProvider>。 此控制項模式會擔任子控制項及其容器之間的通訊通道，以確保容器可變更其顯示子控制項的檢視區內目前可見內容 (或區域)。 如需實作此控制項模式的控制項的範例，請參閱[控制項模式對應 UI 自動化用戶端的](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)。  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>實作方針和慣例  
 實作捲軸項目控制項模式時，請注意下列方針和慣例：  
  
-   視窗或畫布控制項內含的項目不必實作 IScrollItemProvider 介面。 另外，不過，它們必須公開 （expose) 的有效位置<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>。 這可讓 UI 自動化用戶端應用程式使用<xref:System.Windows.Automation.ScrollPattern>控制模式以顯示子系項目容器上的方法。  
  
<a name="Required_Members_for_IScrollItemProvider"></a>   
## <a name="required-members-for-iscrollitemprovider"></a>IScrollItemProvider 的必要成員  
 實作 IScrollProvider 介面需要下列方法。  
  
|必要成員|成員類型|備註|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider.ScrollIntoView%2A>|方法|無|  
  
 此控制項模式沒有任何相關聯的屬性或事件。  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>例外狀況  
 提供者必須擲回下列例外狀況。  
  
|例外狀況類型|條件|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|如果無法將項目捲動到檢視中：<br /><br /> -   <xref:System.Windows.Automation.ScrollItemPattern.ScrollIntoView%2A>|  
  
## <a name="see-also"></a>另請參閱  
 [UI 自動化控制項模式概觀](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)   
 [支援 UI 自動化提供者的控制項模式](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)   
 [用戶端的 UI 自動化控制項模式](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)   
 [UI 自動化樹狀目錄概觀](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)   
 [使用 UI 自動化中的快取](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)