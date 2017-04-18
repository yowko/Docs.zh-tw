---
title: "如何：使用設計工具在 Windows Form ListView 控制項中啟用 Tile 檢視 | Microsoft Docs"
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
  - "ListView 控制項 [Windows Form], 並排顯示"
  - "並排顯示功能"
  - "並排, Windows Form, 控制項"
ms.assetid: 12f0816a-52b8-41ee-a6d9-ded3a8a5817a
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 如何：使用設計工具在 Windows Form ListView 控制項中啟用 Tile 檢視
<xref:System.Windows.Forms.ListView> 控制項的並排顯示功能，讓您在圖形和文字資訊之間取得視覺上的平衡。  在並排顯示中顯示的項目文字資訊，和詳細檢視定義的資料行資訊相同。  並排顯示和 <xref:System.Windows.Forms.ListView> 控制項的群組或插入標記功能一起運作。  
  
 並排顯示是使用 32 x 32 的圖示以及數行文字，如下圖所示。  
  
 ![在 ListView 控制項中並排顯示](../../../../docs/framework/winforms/controls/media/listviewtile.gif "ListViewTile")  
  
 並排顯示屬性和方法讓您指定每個項目要顯示的資料行欄位，並集體控制並排顯示視窗中所有項目的大小和外觀。  為了清楚起見，並排的第一行文字永遠是項目名稱且無法變更。  
  
 下列程序需要 **Windows 應用程式**專案，且專案具有包含 <xref:System.Windows.Forms.ListView> 控制項的表單。  如需設定這類專案的詳細資訊，請參閱 [How to: Create a Windows Application Project](http://msdn.microsoft.com/zh-tw/b2f93fed-c635-4705-8d0e-cf079a264efa) 和 [如何：將控制項加入至 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。  
  
> [!NOTE]
>  並排顯示只有在應用程式呼叫 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=fullName> 方法時，才能在 [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] 上使用。  在早期的作業系統上，任何與並排顯示相關的程式碼都沒有作用，而且 <xref:System.Windows.Forms.ListView> 控制項會顯示在大圖示檢視中。  如需詳細資訊，請參閱 <xref:System.Windows.Forms.ListView.View%2A?displayProperty=fullName>。  
>   
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要在設計工具中設定並排顯示  
  
1.  選取表單上的 <xref:System.Windows.Forms.ListView> 控制項。  
  
2.  在 \[**屬性**\] 視窗中，選取 <xref:System.Windows.Forms.ListView.View%2A> 屬性並選擇 \[**並排顯示**\]。  
  
## 請參閱  
 <xref:System.Windows.Forms.ListView.TileSize%2A>   
 [Windows XP Features and Windows Forms Controls](http://msdn.microsoft.com/zh-tw/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)   
 [ListView 控制項概觀](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)