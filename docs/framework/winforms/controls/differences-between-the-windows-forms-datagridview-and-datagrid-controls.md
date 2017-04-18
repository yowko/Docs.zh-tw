---
title: "Windows Form DataGridView 和 DataGrid 控制項之間的差異 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "資料格"
  - "DataGrid 控制項 [Windows Form], 比較的 DataGridView 控制項"
  - "DataGridView 控制項 [Windows Form], 比較的 DataGrid 控制項"
ms.assetid: d412c786-140e-4210-8a56-a68467530a55
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Windows Form DataGridView 和 DataGrid 控制項之間的差異
<xref:System.Windows.Forms.DataGridView> 控制項是取代 <xref:System.Windows.Forms.DataGrid> 控制項的新控制項。  <xref:System.Windows.Forms.DataGridView> 控制項提供許多在 <xref:System.Windows.Forms.DataGrid> 控制項中所沒有的基本及進階的功能。  此外，<xref:System.Windows.Forms.DataGridView> 控制項的架構會讓它比 <xref:System.Windows.Forms.DataGrid> 控制項更容易擴充和自訂。  
  
 下表說明在 <xref:System.Windows.Forms.DataGridView> 控制項中可以使用的數種主要功能，這些功能是 <xref:System.Windows.Forms.DataGrid> 控制項中所沒有的。  
  
|DataGridView 控制項功能|描述|  
|------------------------|--------|  
|多重資料行型別|<xref:System.Windows.Forms.DataGridView> 控制項會提供比 <xref:System.Windows.Forms.DataGrid> 控制項還多的內建資料行型別。  這些資料行型別符合大部分常見案例的需求，但也比 <xref:System.Windows.Forms.DataGrid> 控制項中的資料行型別更容易擴充或取代。  如需詳細資訊，請參閱 [Windows Form DataGridView 控制項中的資料行類型](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)。|  
|顯示資料的多種方式|<xref:System.Windows.Forms.DataGrid> 控制項是限制於顯示外部資料來源的資料。  然而，<xref:System.Windows.Forms.DataGridView> 控制項能顯示儲存於控制項的未繫結資料、得自繫結資料來源的資料，或繫結與未繫結資料兩者。  您也可以在 <xref:System.Windows.Forms.DataGridView> 控制項中實作虛擬模式，以提供自訂資料管理。  如需詳細資訊，請參閱 [Windows Form DataGridView 控制項的資料顯示模式](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)。|  
|自訂顯示資料的多種方式|<xref:System.Windows.Forms.DataGridView> 控制項提供許多屬性和事件，可讓您指定資料格式化與顯示的方式。  例如，您可以依據包含的資料來變更儲存格、資料列和資料行的外觀，或是以別種資料型別的對等資料取代某種資料型別的資料。  如需詳細資訊，請參閱 [Windows Form DataGridView 控制項中的資料格式](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md)。|  
|變更儲存格、資料列、資料行和行首外觀與行為的多種選項|<xref:System.Windows.Forms.DataGridView> 控制項可讓您使用許多方式來運作個別的方格元件。  例如，您可以凍結資料列和資料行以防止發生捲動；隱藏資料列、資料行和行首；變更資料列、資料行和行首調整大小的方式；變更使用者選取的方式；提供工具提示和捷徑功能表給個別的儲存格、資料列和資料行。|  
  
 <xref:System.Windows.Forms.DataGrid> 控制項是針對回溯相容性以及特殊需求而保留。  <xref:System.Windows.Forms.DataGridView> 控制項則幾乎可以用於所有用途。  在 <xref:System.Windows.Forms.DataGrid> 控制項中唯一可以使用的功能 \(在 <xref:System.Windows.Forms.DataGridView> 控制項中無法使用\)，便是階層式顯示單一控制項中兩個相關表格的資訊。  您必須使用兩個 <xref:System.Windows.Forms.DataGridView> 控制項來顯示兩個具主從式 \(Master\/Detail\) 關聯性之表格的相關資訊。  
  
## 升級至 DataGridView 控制項  
 如果您擁有在單一資料繫結案例中使用 <xref:System.Windows.Forms.DataGrid> 控制項的現有應用程式，只要以新控制項取代舊控制項即可。  兩個控制項都使用標準 Windows Form 資料繫結架構，所以 <xref:System.Windows.Forms.DataGridView> 控制項會顯示您的繫結資料，不需進行額外的設定。  不過，您可能會想利用資料繫結改良的優點，方法是將資料繫結至 <xref:System.Windows.Forms.BindingSource> 元件，然後可將元件繫結至 <xref:System.Windows.Forms.DataGridView> 控制項。  如需詳細資訊，請參閱 [BindingSource 元件](../../../../docs/framework/winforms/controls/bindingsource-component.md)。  
  
 因為 <xref:System.Windows.Forms.DataGridView> 控制項具有全新的架構，所以沒有直截了當的轉換路徑，可讓您使用 <xref:System.Windows.Forms.DataGrid> 自訂和 <xref:System.Windows.Forms.DataGridView> 控制項。  然而，因為在新控制項中可以使用內建功能，所以 <xref:System.Windows.Forms.DataGridView> 控制項的許多 <xref:System.Windows.Forms.DataGrid> 自訂是不必要的。  如果您已經建立 <xref:System.Windows.Forms.DataGrid> 控制項的自訂資料行型別，想和 <xref:System.Windows.Forms.DataGridView> 控制項搭配使用，就需要使用新架構再實作一次。  如需詳細資訊，請參閱[自訂 Windows Form DataGridView 控制項](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGrid>   
 <xref:System.Windows.Forms.BindingSource>   
 [DataGridView 控制項](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)   
 [DataGrid 控制項](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)   
 [BindingSource 元件](../../../../docs/framework/winforms/controls/bindingsource-component.md)   
 [Windows Form DataGridView 控制項中的資料行類型](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)   
 [Windows Form DataGridView 控制項中的儲存格樣式](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)   
 [Windows Form DataGridView 控制項的資料顯示模式](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)   
 [Windows Form DataGridView 控制項中的資料格式](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md)   
 [Windows Form DataGridView 控制項中的調整大小選項](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md)   
 [Windows Form DataGridView 控制項中的資料行排序模式](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)   
 [Windows Form DataGridView 控制項中的選取模式](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md)   
 [自訂 Windows Form DataGridView 控制項](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)