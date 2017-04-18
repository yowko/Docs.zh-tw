---
title: "Windows Form 資料繫結 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "繫結控制項, Windows Form"
  - "資料 [Windows Form]"
  - "資料 [Windows Form], 架構"
  - "Windows Form 控制項, 資料繫結"
  - "Windows Form, 資料繫結"
ms.assetid: c3826d8e-ea25-4ad4-a669-45bfb19192aa
caps.latest.revision: 25
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 25
---
# Windows Form 資料繫結
在 Windows Form 中的資料繫結會提供方法，讓您在表單上的控制項顯示及變更來自資料來源的資訊。  您不只可以繫結至傳統的資料來源，也能繫結至幾乎任何包含資料的結構。  
  
## 在本節中  
 [資料繫結和 Windows Form](../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 提供在 Windows Form 中的資料繫結概觀。  
  
 [Windows Form 支援的資料來源](../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md)  
 描述可以搭配 Windows Form 使用的資料來源。  
  
 [與資料繫結相關的介面](../../../docs/framework/winforms/interfaces-related-to-data-binding.md)  
 描述數個與 Windows Form 資料繫結搭配使用的介面。  
  
 [如何：巡覽 Windows Form 中的資料](../../../docs/framework/winforms/how-to-navigate-data-in-windows-forms.md)  
 示範如何瀏覽資料來源中的項目。  
  
 [Windows Form 資料繫結中的變更告知](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 說明不同類型的 Windows Form 資料繫結變更通知。  
  
 [如何：實作 INotifyPropertyChanged 介面](../../../docs/framework/winforms/how-to-implement-the-inotifypropertychanged-interface.md)  
 示範如何實作 <xref:System.ComponentModel.INotifyPropertyChanged> 介面。  介面會與繫結的控制項溝通商務物件的屬性變更  
  
 [如何：套用 PropertyNameChanged 模式](../../../docs/framework/winforms/how-to-apply-the-propertynamechanged-pattern.md)  
 示範如何將 *PropertyNameChanged* 模式套用到 Windows Form 使用者控制項。  
  
 [如何：實作 ITypedList 介面](../../../docs/framework/winforms/how-to-implement-the-itypedlist-interface.md)  
 示範如何藉由實作 <xref:System.ComponentModel.ITypedList> 介面，讓您探索可繫結清單的結構描述。  
  
 [如何：實作 IListSource 介面](../../../docs/framework/winforms/how-to-implement-the-ilistsource-interface.md)  
 示範如何實作 <xref:System.ComponentModel.IListSource> 介面來建立可繫結的類別，它不會實作 <xref:System.Collections.IList>，而是從另一個位置提供清單。  
  
 [如何：確保繫結至相同資料來源的多個控制項都能保持同步](../../../docs/framework/winforms/multiple-controls-bound-to-data-source-synchronized.md)  
 示範如何處理 <xref:System.Windows.Forms.BindingSource.BindingComplete> 事件以確保繫結至資料來源的所有控制項都能保持同步。  
  
 [如何：確認子資料表中選取的資料列保持在正確位置](../../../docs/framework/winforms/ensure-the-selected-row-in-a-child-table-correct.md)  
 示範在變更父資料表的欄位時，如何確定子資料表的所選取資料列不會變更。  
  
 另請參閱[與資料繫結相關的介面](http://msdn.microsoft.com/library/41e17s4b\(v=vs.110\))、[如何：巡覽 Windows Form 中的資料](http://msdn.microsoft.com/library/b63ha24w\(v=vs.110\))、[如何：在 Windows Form 上建立簡單繫結控制項](http://msdn.microsoft.com/library/sw223a62\(v=vs.110\))。  
  
## 參考  
 <xref:System.Windows.Forms.Binding?displayProperty=fullName>  
 描述代表可繫結元件和資料來源之間繫結的類別。  
  
 <xref:System.Windows.Forms.BindingSource?displayProperty=fullName>  
 描述封裝資料來源以便繫結至控制項的類別。  
  
## 相關章節  
 [BindingSource 元件](../../../docs/framework/winforms/controls/bindingsource-component.md)  
 包含主題的清單，這些主題會示範如何使用 <xref:System.Windows.Forms.BindingSource> 元件。  
  
 [DataGridView 控制項](../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 提供主題的清單，這些主題會示範如何使用可繫結 datagrid 控制項。  
  
 另請參閱[存取 Visual Studio 中的資料](http://msdn.microsoft.com/library/wzabh8c4%20\(v=vs.110\))或[存取 Visual Studio 中的資料](http://msdn.microsoft.com/library/wzabh8c4%20\(v=vs.110\))。