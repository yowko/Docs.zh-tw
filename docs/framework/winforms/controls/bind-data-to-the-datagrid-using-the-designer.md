---
title: "如何：使用設計工具將資料繫結至 Windows Form DataGridView 控制項 | Microsoft Docs"
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
  - "資料來源, 繫結至 Windows Form 控制項"
  - "DataGridView 控制項 [Windows Form], 資料繫結"
  - "Windows Form 控制項, 繫結至資料來源。"
ms.assetid: f4f46009-cec2-441b-8668-6b5af057558b
caps.latest.revision: 23
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 23
---
# 如何：使用設計工具將資料繫結至 Windows Form DataGridView 控制項
您可以使用設計工具，將 <xref:System.Windows.Forms.DataGridView> 控制項連接到數個不同類型的資料來源，包括資料庫、商務物件 \(Business Object\) 或 Web 服務。  當您使用設計工具繫結控制項至資料來源時，控制項會自動繫結至表示資料來源的 <xref:System.Windows.Forms.BindingSource> 元件。  此外，會在控制項中自動產生資料行，以符合資料來源提供的結構描述資訊。  
  
 在資料行產生後，您可進行修改以符合需要。  例如，您可以移除或隱藏不想顯示的資料行、重新整理資料行，或修改資料行型別。  如需修改資料行的詳細資訊，請參閱列於＜請參閱＞章節的主題。  
  
 您也可以將多個 <xref:System.Windows.Forms.DataGridView> 控制項繫結至關聯資料表，以建立主從式關聯性。  在這種關聯下，其中一個控制項會顯示父資料表，另一個控制項只會顯示在子資料表中與父資料表中目前資料列相關聯的那些資料列。  如需詳細資訊，請參閱 [如何：在 Windows Form 應用程式中顯示相關的資料](../Topic/How%20to:%20Display%20Related%20Data%20in%20a%20Windows%20Forms%20Application.md)。  
  
 在下列程序中，需要 \[**Windows 應用程式**\] 專案以及含有一個 <xref:System.Windows.Forms.DataGridView> 控制項的表單 \(如果具有主從式關聯性，則需要兩個控制項\)。  如需啟動這類專案的詳細資訊，請參閱 [How to: Create a Windows Application Project](http://msdn.microsoft.com/zh-tw/b2f93fed-c635-4705-8d0e-cf079a264efa)和 [如何：將控制項加入至 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要將控制項繫結至資料來源  
  
1.  按一下 <xref:System.Windows.Forms.DataGridView> 控制項右上角的智慧標籤圖像 \(![智慧標籤圖像](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.png "VS\_WinFormSmtTagGlyph")\)。  
  
2.  按一下 \[**選擇資料來源**\] 選項的下拉式箭號。  
  
3.  如果您的專案尚未擁有資料來源，請按一下 \[**加入專案資料來源**\] 並遵循精靈所指示的步驟。  
  
     如需詳細資訊，請參閱[資料來源組態精靈](../Topic/Data%20Source%20Configuration%20Wizard.md)。  您的新資料來源將出現在 \[**選擇資料來源**\] 下拉式視窗中。  如果新的資料來源只包含一個成員 \(例如，單一資料庫資料表\)，則控制項將會自動繫結至該成員。  否則，請繼續進行下一個步驟。  
  
4.  如果 \[**其他資料來源**\] 和 \[**專案資料來源**\] 節點尚未展開，請將它們展開，然後選取控制項要繫結的資料來源。  
  
5.  如果資料來源包含一個以上的成員 \(例如，如果已建立包含多個資料表的 <xref:System.Data.DataSet?displayProperty=fullName>\)，請展開資料來源，然後選取要繫結的特定成員。  
  
6.  若要建立主從式關聯性，請在第二個 <xref:System.Windows.Forms.DataGridView> 控制項的 \[**選擇資料來源**\] 下拉式視窗中，展開為父資料表建立的 <xref:System.Windows.Forms.BindingSource>，然後從顯示的清單中選取關聯的子資料表。  
  
    > [!NOTE]
    >  如果專案已經有資料來源，您也可以使用 \[**資料來源**\] 視窗建立資料表單。  如需詳細資訊，請參閱[資料來源視窗](../Topic/Data%20Sources%20Window.md)。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.BindingSource>   
 <xref:System.Windows.Forms.DataGridView.DataMember%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=fullName>   
 [如何：連接至資料庫中的資料](../Topic/How%20to:%20Connect%20to%20Data%20in%20a%20Database.md)   
 [如何：使用設計工具在 Windows Form DataGridView 控制項中加入和移除資料行](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)   
 [如何：使用設計工具變更 Windows Form DataGridView 控制項中資料行的順序](../../../../docs/framework/winforms/controls/change-the-order-of-columns-in-the-datagrid-using-the-designer.md)   
 [如何：使用設計工具變更 Windows Form DataGridView 資料行的類型](../../../../docs/framework/winforms/controls/change-the-type-of-a-wf-datagridview-column-using-the-designer.md)   
 [如何：使用設計工具凍結 Windows Form DataGridView 控制項中的資料行](../../../../docs/framework/winforms/controls/freeze-columns-in-the-datagrid-using-the-designer.md)   
 [如何：使用設計工具隱藏 Windows Form DataGridView 控制項中的資料行](../../../../docs/framework/winforms/controls/hide-columns-in-the-datagrid-using-the-designer.md)   
 [如何：使用設計工具將 Windows Form DataGridView 控制項中的資料行設為唯讀](../../../../docs/framework/winforms/controls/make-columns-read-only-in-the-datagrid-using-the-designer.md)   
 [How to: Create a Windows Application Project](http://msdn.microsoft.com/zh-tw/b2f93fed-c635-4705-8d0e-cf079a264efa)   
 [如何：將控制項加入至 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)   
 [資料來源視窗](../Topic/Data%20Sources%20Window.md)   
 [如何：在 Windows Form 應用程式中顯示相關的資料](../Topic/How%20to:%20Display%20Related%20Data%20in%20a%20Windows%20Forms%20Application.md)