---
title: "ListView 控制項概觀 (Windows Form) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ListView"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "清單檢視"
  - "清單"
  - "ListView 控制項 [Windows Form], 關於 ListView 控制項"
ms.assetid: c9ef56c1-3bb1-4101-9f4e-e95e720f2756
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# ListView 控制項概觀 (Windows Form)
Windows Form <xref:System.Windows.Forms.ListView> 控制項顯示具有圖示的項目清單。  您可以使用清單檢視來建立如 Windows 檔案總管右窗格的使用者介面。  控制項有四種檢視模式：LargeIcon、SmallIcon、List 和 Details。  
  
## ListView 控制項可以做到的功能  
  
> [!NOTE]
>  「並排」是額外的檢視模式，只適用於 Windows XP 和 Windows Server 2003 作業系統。  如需詳細資訊，請參閱 [如何：在 Windows Form ListView 控制項中啟用並排顯示](../../../../docs/framework/winforms/controls/how-to-enable-tile-view-in-a-windows-forms-listview-control.md)。  
  
 LargeIcon 模式在項目文字旁顯示大圖示；如果控制項夠大，項目會以多行顯示。  SmallIcon 模式除了顯示的是小圖示之外，其餘與 LargeIcon 都相同。  List 模式顯示小圖示，但一定是單行。  Details 模式以多行顯示項目。  如需詳細資訊，請參閱 [如何：將資料行加入至 Windows Form ListView 控制項](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)。  檢視模式由 <xref:System.Windows.Forms.ListView.View%2A> 屬性決定。  所有的檢視模式可以顯示來自影像清單 \(Image List\) 的影像。  如需詳細資訊，請參閱 [如何：顯示 Windows Form ListView 控制項的圖示](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)。  
  
 下表列出一些 <xref:System.Windows.Forms.ListView> 的成員，以及檢視中有效的成員。  
  
|ListView 成員|檢視|  
|-----------------|--------|  
|<xref:System.Windows.Forms.ListView.Alignment%2A> 屬性|<xref:System.Windows.Forms.View> 或 <xref:System.Windows.Forms.View>|  
|<xref:System.Windows.Forms.ListView.AutoArrange%2A> 屬性|<xref:System.Windows.Forms.View> 或 <xref:System.Windows.Forms.View>|  
|<xref:System.Windows.Forms.ListView.AutoResizeColumn%2A> 方法|<xref:System.Windows.Forms.View>|  
|<xref:System.Windows.Forms.ListView.Columns%2A> 屬性|<xref:System.Windows.Forms.View> 或 <xref:System.Windows.Forms.View>|  
|<xref:System.Windows.Forms.ListView.DrawSubItem> 事件|<xref:System.Windows.Forms.View>|  
|<xref:System.Windows.Forms.ListView.FindItemWithText%2A> 方法|<xref:System.Windows.Forms.View>、<xref:System.Windows.Forms.View> 或 <xref:System.Windows.Forms.View>|  
|<xref:System.Windows.Forms.ListView.FindNearestItem%2A> 方法|<xref:System.Windows.Forms.View> 或 <xref:System.Windows.Forms.View>|  
|<xref:System.Windows.Forms.ListView.GetItemAt%2A> 方法|<xref:System.Windows.Forms.View> 或 <xref:System.Windows.Forms.View>|  
|<xref:System.Windows.Forms.ListView.Groups%2A> 屬性|所有檢視，除了 <xref:System.Windows.Forms.View>|  
|<xref:System.Windows.Forms.ListView.HeaderStyle%2A> 屬性|<xref:System.Windows.Forms.View>.|  
|<xref:System.Windows.Forms.ListView.InsertionMark%2A> 屬性|<xref:System.Windows.Forms.View>、<xref:System.Windows.Forms.View> 或 <xref:System.Windows.Forms.View>|  
  
 <xref:System.Windows.Forms.ListView> 控制項的主要屬性是 <xref:System.Windows.Forms.ListView.Items%2A>，其中包含控制項顯示的項目。  <xref:System.Windows.Forms.ListView.SelectedItems%2A> 屬性包含控制項中目前選取的項目集合。  使用者可以選取多重項目，例如在 <xref:System.Windows.Forms.ListView.MultiSelect%2A> 屬性設定為 `true` 時，一次拖放數個項目到另一個控制項中。  如果 <xref:System.Windows.Forms.ListView.CheckBoxes%2A> 屬性設定為 `true`，則 <xref:System.Windows.Forms.ListView> 控制項可以在項目旁邊顯示核取方塊。  
  
 <xref:System.Windows.Forms.ListView.Activation%2A> 屬性決定使用者必須採取哪種類型的動作，才能啟動清單中的項目：選項有 <xref:System.Windows.Forms.ItemActivation>、<xref:System.Windows.Forms.ItemActivation> 和 <xref:System.Windows.Forms.ItemActivation>。  <xref:System.Windows.Forms.ItemActivation> 啟動需要按一下來啟動項目。  <xref:System.Windows.Forms.ItemActivation> 啟動需要使用者按兩下來啟動項目；按一下則會變更項目文字的顏色。  <xref:System.Windows.Forms.ItemActivation> 啟動需要使用者按兩下來啟動項目，但是項目的外觀不會改變。  
  
 <xref:System.Windows.Forms.ListView> 控制項也支援 Windows XP 平台所提供的視覺化樣式和其他功能，包括群組、並排顯示和插入標記。  如需詳細資訊，請參閱 [Windows XP Features and Windows Forms Controls](http://msdn.microsoft.com/zh-tw/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)。  
  
## 請參閱  
 <xref:System.Windows.Forms.ListView>   
 [ListView 控制項](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)   
 [如何：使用 Windows Form ListView 控制項加入和移除項目](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)   
 [如何：將資料行加入至 Windows Form ListView 控制項](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)   
 [如何：顯示 Windows Form ListView 控制項的圖示](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)   
 [如何：使用 Windows Form ListView 控制項以資料行顯示子項目](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)   
 [如何：選取 Windows Form ListView 控制項中的項目](../../../../docs/framework/winforms/controls/how-to-select-an-item-in-the-windows-forms-listview-control.md)   
 [如何：在 Windows Form ListView 控制項中群組項目](../../../../docs/framework/winforms/controls/how-to-group-items-in-a-windows-forms-listview-control.md)   
 [如何：在 Windows Form ListView 控制項中顯示插入標記](../../../../docs/framework/winforms/controls/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control.md)   
 [如何：將搜尋能力加入至 ListView 控制項](../../../../docs/framework/winforms/controls/how-to-add-search-capabilities-to-a-listview-control.md)   
 [如何：將自訂資訊加入 TreeView 或 ListView 控制項 \(Windows Form\)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)   
 [逐步解說：利用 Windows Form 建立多窗格使用者介面](../../../../docs/framework/winforms/controls/how-to-create-a-multipane-user-interface-with-windows-forms.md)