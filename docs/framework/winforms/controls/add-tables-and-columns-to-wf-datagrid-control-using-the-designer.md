---
title: "如何：使用設計工具在 Windows Form DataGrid 控制項中加入表格和資料行 | Microsoft Docs"
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
  - "資料行 [Windows Form], 加入至 DataGrid 控制項"
  - "DataGrid 控制項 [Windows Form], 加入資料表和資料行"
  - "資料表 [Windows Form], 加入至 DataGrid 控制項"
ms.assetid: 4a6d1b34-b696-476b-bf8a-57c6230aa9e1
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：使用設計工具在 Windows Form DataGrid 控制項中加入表格和資料行
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。  如需詳細資訊，請參閱 [Windows Form DataGridView 和 DataGrid 控制項之間的差異](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。  
  
 您可以建立 <xref:System.Windows.Forms.DataGridTableStyle> 物件並將這些物件加入至 <xref:System.Windows.Forms.GridTableStylesCollection> 物件 \(透過 <xref:System.Windows.Forms.DataGrid> 控制項的 <xref:System.Windows.Forms.DataGrid.TableStyles%2A> 屬性存取\)，以資料表和資料行顯示 Windows Form <xref:System.Windows.Forms.DataGrid> 控制項中的資料。  每一個資料表樣式都顯示 <xref:System.Windows.Forms.DataGridTableStyle> 的 <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> 屬性中指定的資料表的內容。  依照預設，沒有指定資料行樣式的資料表樣式，將會把所有的資料行顯示於該資料表內。  您可以將 <xref:System.Windows.Forms.DataGridColumnStyle> 物件加入至 <xref:System.Windows.Forms.GridColumnStylesCollection>，再透過各個 <xref:System.Windows.Forms.DataGridTableStyle> 的 <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> 屬性來存取，即可限制要從資料表顯示哪些資料行。  
  
 下列程序需要 **Windows 應用程式**專案，且專案具有包含 <xref:System.Windows.Forms.DataGrid> 控制項的表單。  如需設定這類專案的詳細資訊，請參閱 [How to: Create a Windows Application Project](http://msdn.microsoft.com/zh-tw/b2f93fed-c635-4705-8d0e-cf079a264efa)和 [如何：將控制項加入至 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。  依照預設，在 [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)] 中，<xref:System.Windows.Forms.DataGrid> 控制項不會在 \[**工具箱**\] 中。  如需將它加入 \[工具箱\] 的詳細資訊，請參閱 [How to: Add Items to the Toolbox](http://msdn.microsoft.com/zh-tw/458e119e-17fe-450b-b889-e31c128bd7e0)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要在設計工具中將資料表加入至 DataGrid 控制項  
  
1.  為了顯示資料表中的資料，您必須先將 <xref:System.Windows.Forms.DataGrid> 控制項繫結至資料集。  如需詳細資訊，請參閱 [如何：使用設計工具將 Windows Form DataGrid 控制項繫結至資料來源](../../../../docs/framework/winforms/controls/bind-wf-datagrid-control-to-a-data-source-using-the-designer.md)。  
  
2.  在 \[屬性\] 視窗中選取 <xref:System.Windows.Forms.DataGrid> 控制項的 <xref:System.Windows.Forms.DataGrid.TableStyles%2A> 屬性，再按一下屬性旁邊的省略符號 \(![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) 按鈕，以便顯示 \[**DataGridTableStyle 集合編輯器**\]。  
  
3.  在集合編輯器中，按一下 \[**加入**\] 以插入資料表樣式。  
  
4.  按一下 \[**確定**\] 關閉集合編輯器，再按一下 <xref:System.Windows.Forms.DataGrid.TableStyles%2A> 屬性旁邊的省略符號按鈕以重新開啟集合編輯器。  
  
     當您重新開啟集合編輯器時，所有繫結至控制項的資料表都將出現在資料表樣式 <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> 屬性的下拉式清單中。  
  
5.  在集合編輯器的 \[**成員**\] 方塊中，按一下資料表樣式。  
  
6.  在集合編輯器的 \[**屬性**\] 方塊中，選取要顯示的資料表之 <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> 值。  
  
### 若要在設計工具中將資料行加入至 DataGrid 控制項  
  
1.  在 \[**DataGridTableStyle 集合編輯器**\] 的 \[**成員**\] 方塊中，選取適當的表格樣式。  在集合編輯器的 \[**屬性**\] 方塊中，選取 <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> 集合，再按一下屬性旁邊的省略符號 \(![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) 按鈕，以便顯示 \[**DataGridColumnStyle 集合編輯器**\]。  
  
2.  在集合編輯器中，按一下 \[**加入**\] 來插入資料行樣式，或按一下 \[**加入**\] 旁邊的向下鍵來指定資料行型別。  
  
     在下拉式清單中，您可以選取 <xref:System.Windows.Forms.DataGridTextBoxColumn> 或 <xref:System.Windows.Forms.DataGridBoolColumn> 型別。  
  
3.  按一下 \[確定\] 關閉 \[**DataGridColumnStyle 集合編輯器**\]，再按一下 <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> 屬性旁邊的省略符號按鈕以重新開啟集合編輯器。  
  
     當您重新開啟集合編輯器時，繫結資料表中的所有資料行都將出現在資料行樣式 <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> 屬性的下拉式清單中。  
  
4.  在集合編輯器的 \[**成員**\] 方塊中，按一下資料行樣式。  
  
5.  在集合編輯器的 \[**屬性**\] 方塊中，選取要顯示的資料行之 <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> 值。  
  
## 請參閱  
 [DataGrid 控制項](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)   
 [如何：刪除或隱藏 Windows Form DataGrid 控制項中的資料行](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)