---
title: "Implementing the UI Automation Value Control Pattern | Microsoft Docs"
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
  - "control patterns, Value"
  - "UI Automation, Value control pattern"
  - "Value control pattern"
ms.assetid: b0fcdd87-3add-4345-bca9-e891205e02ba
caps.latest.revision: 25
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 24
---
# Implementing the UI Automation Value Control Pattern
> [!NOTE]
>  這份文件適用於想要使用 `true` 命名空間中定義之 Managed <xref:System.Windows.Automation.Provider.IValueProvider> 類別的 .NET Framework 開發人員。 如需 <xref:System.Windows.Automation.Provider.IValueProvider> 的最新資訊，請參閱 Windows Automation API：使用者介面自動化<xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty>`false``true`。  
  
 本主題將介紹實作 <xref:System.Windows.Automation.Provider.IValueProvider> 的方針和慣例，包括事件和屬性的相關資訊。 其他參考的連結列於主題的結尾。  
  
 <xref:System.Windows.Automation.Provider.IValueProvider> 控制項模式用來支援不跨越某個範圍的內建值且可以表示為字串的控制項。 這個字串可以是可編輯的，視控制項及其設定而定。 如需實作此模式的控制項範例，請參閱 <xref:System.Windows.Automation.Provider.IValueProvider>。  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## 實作方針和慣例  
 實作值控制項模式時，請注意下列方針和慣例：  
  
-   如果任何項目的值是可編輯的，則例如 <xref:System.Windows.Automation.Provider.IValueProvider> 和 `true` 等控制項必須支援 <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty>，而不論控制項目前的編輯模式為何。 如果子項目是可編輯的，父控制項也必須支援 <xref:System.Windows.Automation.Provider.IValueProvider>。  
  
 ![可編輯的清單項目。](../../../docs/framework/ui-automation/media/uia-valuepattern-editable-listitem.PNG "UIA\_ValuePattern\_Editable\_ListItem")  
可編輯的清單項目範例  
  
-   單行編輯控制項支援藉由實作 <xref:System.Windows.Automation.Provider.IValueProvider>，以程式設計方式存取其內容。 不過，多行編輯控制項不會實作 <xref:System.Windows.Automation.Provider.IValueProvider>；它們是改為藉由實作 `true` 來提供其內容的存取。  
  
-   若要擷取多行編輯控制項的文字內容，控制項必須實作 <xref:System.Windows.Automation.Provider.IValueProvider>。 不過，<xref:System.Windows.Automation.Provider.IValueProvider> 不支援設定控制項的值。  
  
-   <xref:System.Windows.Automation.Provider.IValueProvider> 不支援擷取格式設定資訊或子字串值。 在這些案例中請實作 <xref:System.Windows.Automation.Provider.IValueProvider>。  
  
-   <xref:System.Windows.Automation.Provider.IValueProvider> 必須由例如來自 <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> 的色彩選擇器`true`選擇控制項等控制項實作 \(下面詳述\)，它可支援色彩值 \(例如「黃色」\) 和對等內部 `false` 結構之間的字串對應。  
  
 ![已反白顯示黃色的色彩選擇器](../../../docs/framework/ui-automation/media/uia-valuepattern-colorpicker.png "UIA\_ValuePattern\_ColorPicker")  
色樣字串對應範例  
  
-   控制項的 <xref:System.Windows.Automation.Provider.IValueProvider> 應該設為 `true`，<xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> 應該設為 `false`，才能允許呼叫 <xref:System.Windows.Automation.Provider.IValueProvider.SetValue%2A>。  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## IValueProvider 的必要成員  
 以下是實作 <xref:System.Windows.Automation.Provider.IValueProvider> 的必要屬性和方法。  
  
|必要成員|成員類型|備註|  
|----------|----------|--------|  
|<xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty>|屬性|無|  
|<xref:System.Windows.Automation.ValuePattern.ValueProperty>|屬性|無|  
|<xref:System.Windows.Automation.ValuePattern.SetValue%2A>|方法|無|  
  
<a name="Exceptions"></a>   
## 例外狀況  
 提供者必須擲回下列例外狀況。  
  
|例外狀況類型|條件|  
|------------|--------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> -   如果地區設定特有的資訊以不正確的格式傳遞至控制項，例如日期格式不正確。|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> -   如果新的值不能從字串轉換成控制項可辨識的格式。|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> -   嘗試對未啟用的控制項進行操作。|  
  
## 請參閱  
 [UI Automation Control Patterns Overview](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)   
 [Support Control Patterns in a UI Automation Provider](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)   
 [UI Automation Control Patterns for Clients](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)   
 [TextPattern Insert Text Sample](http://msdn.microsoft.com/zh-tw/67353f93-7ee2-42f2-ab76-5c078cf6ca16)   
 [UI Automation Tree Overview](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)   
 [Use Caching in UI Automation](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)