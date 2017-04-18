---
title: "如何：顯示 Windows Form ListView 控制項的圖示 | Microsoft Docs"
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
  - "圖示, 為 ListView 控制項顯示"
  - "ImageList 元件 [Windows Form], 使用 ListView 控制項"
  - "清單檢視, 顯示圖示"
  - "清單, 顯示圖示"
  - "ListView 控制項 [Windows Form], 顯示圖示"
ms.assetid: 9d577542-8595-429b-99e5-078770ec9d35
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 如何：顯示 Windows Form ListView 控制項的圖示
Windows Form <xref:System.Windows.Forms.ListView> 控制項可以顯示來自三個影像清單的圖示。  List、Details 以及 SmallIcon 檢視會根據 <xref:System.Windows.Forms.ListView.SmallImageList%2A> 屬性中指定的影像清單來顯示影像。  LargeIcon 檢視根據 <xref:System.Windows.Forms.ListView.LargeImageList%2A> 屬性中指定的影像清單來顯示影像。  清單檢視還可以顯示額外的圖示集，這些圖示在 <xref:System.Windows.Forms.ListView.StateImageList%2A> 屬性中設定，顯示在大圖示或小圖示的旁邊。  如需影像清單的詳細資訊，請參閱 [ImageList 元件](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) 和 [如何：使用 Windows Form ImageList 元件加入或移除影像](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)。  
  
### 如果要在清單檢視顯示影像  
  
1.  將適當的屬性 \(<xref:System.Windows.Forms.ListView.SmallImageList%2A>、<xref:System.Windows.Forms.ListView.LargeImageList%2A> 或 <xref:System.Windows.Forms.ListView.StateImageList%2A>\) 設定為要使用的現有 <xref:System.Windows.Forms.ImageList> 元件。  
  
     這些屬性可使用 \[屬性\] 視窗或程式碼在設計工具中設定。  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#41)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#41)]  
  
2.  設定有相關圖示的各個清單項目的 <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> 或 <xref:System.Windows.Forms.ListViewItem.StateImageIndex%2A> 屬性。  
  
     您可以在程式碼或 \[**ListViewItem 集合編輯器**\] 中設定這些屬性。  若要開啟 \[**ListViewItem 集合編輯器**\]，請按一下 \[**屬性**\] 視窗中 <xref:System.Windows.Forms.ListView.Items%2A> 屬性旁邊的省略按鈕 \(![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\)。  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#42)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#42)]  
  
## 請參閱  
 [ListView 控制項概觀](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)   
 [如何：使用 Windows Form ListView 控制項加入和移除項目](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)   
 [如何：將資料行加入至 Windows Form ListView 控制項](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)   
 [如何：將自訂資訊加入 TreeView 或 ListView 控制項 \(Windows Form\)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)   
 [ImageList 元件](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)