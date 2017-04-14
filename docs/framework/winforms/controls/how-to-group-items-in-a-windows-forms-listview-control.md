---
title: "如何：在 Windows Form ListView 控制項中群組項目 | Microsoft Docs"
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
  - "群組"
  - "群組"
  - "群組, Windows Form 控制項"
  - "清單檢視, 群組項目"
  - "清單, 群組項目"
  - "ListView 控制項 [Windows Form], 群組項目"
ms.assetid: 610416a1-8da4-436c-af19-5f19e654769b
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# 如何：在 Windows Form ListView 控制項中群組項目
您可以使用 <xref:System.Windows.Forms.ListView> 控制項的群組功能，以群組方式顯示相關的項目。  在畫面上，這些群組是以含有群組標題的水平群組標頭加以區隔。  您可以使用 <xref:System.Windows.Forms.ListView> 群組將項目按照字母順序、按照日期或任何其他邏輯來分組，讓大型清單的巡覽更加容易。  下圖顯示的是一些群組的項目。  
  
 ![ListView 群組](../../../../docs/framework/winforms/controls/media/listviewgroups.gif "ListViewGroups")  
ListView 群組項目  
  
 若要啟用群組，您必須在設計工具中或是以程式設計方式，先建立一或多個群組。  定義群組之後，就可以將 <xref:System.Windows.Forms.ListView> 項目指派給群組。  您也可以用程式的方式，將項目從一個群組移動至另一個。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ListView> 群組只能在 [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] 上使用，您的應用程式會呼叫 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=fullName> 方法。  在早期的作業系統上，任何與群組相關的程式碼都沒有作用，而且不會出現群組。  如需詳細資訊，請參閱 <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=fullName>。  
  
### 若要加入群組  
  
1.  請使用 <xref:System.Windows.Forms.ListView.Groups%2A> 集合的 <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> 方法。  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#21)]  
  
### 若要移除群組  
  
1.  請使用 <xref:System.Windows.Forms.ListView.Groups%2A> 集合的 <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> 或 <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> 方法。  
  
     <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> 方法只會移除單一群組，而 <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> 方法則會移除清單中的所有群組。  
  
    > [!NOTE]
    >  移除群組不會移除群組中的項目。  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#22)]  
  
### 若要指派項目給群組或在群組之間移動項目  
  
1.  請設定個別項目的 <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=fullName> 屬性。  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#23)]  
  
## 請參閱  
 <xref:System.Windows.Forms.ListView>   
 <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.ListViewGroup>   
 [ListView 控制項](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)   
 [ListView 控制項概觀](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)   
 [Windows XP Features and Windows Forms Controls](http://msdn.microsoft.com/zh-tw/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)   
 [如何：使用 Windows Form ListView 控制項加入和移除項目](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)