---
title: "如何：使用設計工具將 Windows Form DataGrid 控制項繫結至資料來源 | Microsoft Docs"
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
  - "繫結控制項"
  - "繫結控制項, DataGrid 控制項"
  - "資料繫結, DataGrid 控制項"
  - "資料繫結控制項, DataGrid"
  - "DataGrid 控制項 [Windows Form], 資料繫結"
  - "資料集 [Windows Form], 繫結至 DataGrid 控制項"
  - "Windows Form 控制項, 資料繫結"
ms.assetid: 4e96e3d0-b1cc-4de1-8774-bc9970ec4554
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 如何：使用設計工具將 Windows Form DataGrid 控制項繫結至資料來源
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。  如需詳細資訊，請參閱 [Windows Form DataGridView 和 DataGrid 控制項之間的差異](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。  
  
 Windows Form <xref:System.Windows.Forms.DataGrid> 控制項是特別設計來顯示資料來源的資訊。  您可以在設計階段設定 <xref:System.Windows.Forms.DataGrid.DataSource%2A> 和 <xref:System.Windows.Forms.DataGrid.DataMember%2A> 屬性，或是在執行階段呼叫 <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> 方法來繫結控制項。  雖然您可顯示來自各種不同資料來源的資料，但最常見的來源是資料集和資料檢視。  
  
 如果在設計階段可使用資料來源 \(例如，如果表單包含資料集或資料檢視的執行個體\)，您可在設計階段將方格繫結至資料來源。  接著您可預覽方格中如何顯示資料。  
  
 您也可在執行階段時以程式設計的方式來繫結方格。  當您要依據在執行階段取得的資料來設定資料來源時，這種做法就相當有用。  例如，應用程式可能讓使用者指定所要檢視之資料表的名稱。  當資料來源在設計階段不存在時，這麼做也是必要的。  這些資料來源包括陣列、集合、不具型別資料集和資料讀取器 \(Reader\)。  
  
 下列程序需要 **Windows 應用程式**專案，且專案具有包含 <xref:System.Windows.Forms.DataGrid> 控制項的表單。  如需設定這類專案的詳細資訊，請參閱 [How to: Create a Windows Application Project](http://msdn.microsoft.com/zh-tw/b2f93fed-c635-4705-8d0e-cf079a264efa) 和 [如何：將控制項加入至 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。  在 [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)] 中，<xref:System.Windows.Forms.DataGrid> 控制項預設不會在 \[**工具箱**\] 中。  如需將它加入 \[工具箱\] 的詳細資訊，請參閱 [How to: Add Items to the Toolbox](http://msdn.microsoft.com/zh-tw/458e119e-17fe-450b-b889-e31c128bd7e0)。  此外，在 [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)] 中，您可以使用 \[**資料來源**\] 視窗來進行設計階段資料繫結。  如需詳細資訊，請參閱[將控制項繫結至 Visual Studio 中的資料](../Topic/Bind%20controls%20to%20data%20in%20Visual%20Studio.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要在設計工具中將 DataGrid 控制項資料繫結至單一資料表  
  
1.  將控制項的 <xref:System.Windows.Forms.DataGrid.DataSource%2A> 屬性設定為含有您要繫結的資料項目的物件。  
  
2.  如果資料來源是資料集，請將 <xref:System.Windows.Forms.DataGrid.DataMember%2A> 屬性設定為要繫結的資料表名稱  
  
3.  如果資料來源是資料集或以資料集資料表為基礎的資料檢視，請將程式碼加入表單來填滿資料集。  
  
     您實際上使用的程式碼要視資料集從何處取得資料而定。  如果資料集是直接從資料庫填入，您通常會呼叫資料配接器 \(Adapter\) 的 `Fill` 方法，如下列程式碼所示，其中會填入名為 `DsCategories1` 的資料集：  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
4.  \(選擇性\) 將適當的資料表樣式和資料行樣式加入至資料格。  
  
     如果沒有資料表樣式，您將看到資料表，但只能看到最少的格式和所有的資料行。  
  
### 若要在設計工具中將 DataGrid 控制項資料繫結至資料集中的多個資料表  
  
1.  將控制項的 <xref:System.Windows.Forms.DataGrid.DataSource%2A> 屬性設定為含有您要繫結的資料項目的物件。  
  
2.  如果資料集包含關聯資料表 \(也就是如果它包含關聯物件\)，請將 <xref:System.Windows.Forms.DataGrid.DataMember%2A> 屬性設定為父資料表的名稱。  
  
3.  撰寫程式碼以填滿資料集。  
  
## 請參閱  
 [DataGrid 控制項概觀](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)   
 [如何：將資料表和資料行加入至 Windows Form DataGrid 控制項](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)   
 [DataGrid 控制項](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)   
 [Windows Form 資料繫結](../../../../docs/framework/winforms/windows-forms-data-binding.md)   
 [存取 Visual Studio 中的資料](../Topic/Accessing%20data%20in%20Visual%20Studio.md)