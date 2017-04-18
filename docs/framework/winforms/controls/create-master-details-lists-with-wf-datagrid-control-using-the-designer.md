---
title: "如何：使用設計工具搭配 Windows Form DataGrid 控制項建立主版詳細資料清單 | Microsoft Docs"
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
  - "DataGrid 控制項 [Windows Form], 主從式清單"
  - "主從式清單"
  - "關聯資料表, 在 DataGrid 控制項中顯示"
ms.assetid: 19438ba2-f687-4417-a2fb-ab1cd69d4ded
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：使用設計工具搭配 Windows Form DataGrid 控制項建立主版詳細資料清單
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。  如需詳細資訊，請參閱 [Windows Form DataGridView 和 DataGrid 控制項之間的差異](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。  
  
 如果您的 <xref:System.Data.DataSet> 包含一系列關聯的資料表，您可以使用兩個 <xref:System.Windows.Forms.DataGrid> 控制項，以主版詳細資料格式顯示資料。  一個 <xref:System.Windows.Forms.DataGrid> 指定為主版資料格，第二個則指定為詳細資料資料格。  當您在主要清單中選取項目時，相關的所有子項目都將顯示在詳細資料清單中。  例如，如果 <xref:System.Data.DataSet> 包含 Customers 資料表和關聯的 Orders 資料表，則您會將 Customers 資料表指定為主版資料格，並將 Orders 資料表指定為詳細資料資料格。  在主要資料格中選取客戶時，Orders 資料表中與該客戶相關的所有訂單都會顯示於詳細資料格中。  
  
 下列程序需要 \[**Windows 應用程式**\] 專案。  如需設定這類專案的詳細資訊，請參閱 [How to: Create a Windows Application Project](http://msdn.microsoft.com/zh-tw/b2f93fed-c635-4705-8d0e-cf079a264efa)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要在設計工具中建立主版詳細資料清單  
  
1.  加入兩個 <xref:System.Windows.Forms.DataGrid> 控制項至表單。  如需詳細資訊，請參閱 [如何：將控制項加入至 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。  在 [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)] 中，<xref:System.Windows.Forms.DataGrid> 控制項預設不會在 \[**工具箱**\] 中。  如需詳細資訊，請參閱 [How to: Add Items to the Toolbox](http://msdn.microsoft.com/zh-tw/458e119e-17fe-450b-b889-e31c128bd7e0)。  
  
    > [!NOTE]
    >  下列步驟不適用於 [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)]，其設計階段資料繫結是使用 \[**資料來源**\] 視窗來進行。  如需詳細資訊，請參閱[將控制項繫結至 Visual Studio 中的資料](../Topic/Bind%20controls%20to%20data%20in%20Visual%20Studio.md)和 [如何：在 Windows Form 應用程式中顯示相關的資料](../Topic/How%20to:%20Display%20Related%20Data%20in%20a%20Windows%20Forms%20Application.md)。  
  
2.  從 \[**伺服器總管**\] 中拖放兩個或多個資料表至表單。  
  
3.  從 \[**資料**\] 功能表中，選取 \[**產生資料集**\]。  
  
4.  使用 XML 設計工具設定資料表間的關聯性。  如需詳細資訊，請參閱 MSDN 上的＜HOW TO：在 XML 結構描述和資料集中建立一對多關聯性＞。  
  
5.  從 \[**檔案**\] 功能表選取 \[**全部儲存**\] 來儲存關聯性。  
  
6.  設定您要指定為主版資料格的 <xref:System.Windows.Forms.DataGrid> 控制項，如以下所示：  
  
    1.  從 <xref:System.Windows.Forms.DataGrid.DataSource%2A> 屬性的下拉式清單中，選取 <xref:System.Data.DataSet>。  
  
    2.  從 <xref:System.Windows.Forms.DataGrid.DataMember%2A> 屬性的下拉式清單中，選取主版資料表 \(例如 "Customers"\)。  
  
7.  設定您要指定為詳細資料資料格的 <xref:System.Windows.Forms.DataGrid> 控制項，如以下所示：  
  
    1.  從 <xref:System.Windows.Forms.DataGrid.DataSource%2A> 屬性的下拉式清單中，選取 <xref:System.Data.DataSet>。  
  
    2.  從 <xref:System.Windows.Forms.DataGrid.DataMember%2A> 屬性的下拉式清單中，選取主版和詳細資料資料表之間的關聯性 \(例如 "Customers.CustOrd"\)。  若要檢視關聯性，按一下下拉式清單中主要資料表旁的加號 \(**\+**\) 來展開節點。  
  
## 請參閱  
 [DataGrid 控制項](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)   
 [DataGrid 控制項概觀](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)   
 [如何：將 Windows Form DataGrid 控制項繫結至資料來源](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)   
 [將控制項繫結至 Visual Studio 中的資料](../Topic/Bind%20controls%20to%20data%20in%20Visual%20Studio.md)