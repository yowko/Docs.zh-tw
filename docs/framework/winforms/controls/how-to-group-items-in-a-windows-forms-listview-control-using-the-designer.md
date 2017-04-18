---
title: "如何：使用設計工具群組 Windows Form ListView 控制項中的項目 | Microsoft Docs"
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
  - "群組, Windows Form 控制項"
  - "ListView 控制項 [Windows Form], 群組項目"
ms.assetid: 8b615000-69d9-4c64-acaf-b54fa09b69e3
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：使用設計工具群組 Windows Form ListView 控制項中的項目
<xref:System.Windows.Forms.ListView> 控制項的群組功能可以讓您將相關的項目集以群組顯示。  在畫面上，這些群組是以含有群組標題的水平群組標頭加以區隔。  您可以使用 <xref:System.Windows.Forms.ListView> 群組將項目按照字母順序、按照日期或任何其他邏輯來分組，讓大型清單的巡覽更加容易。  下圖顯示的是一些群組的項目。  
  
 ![ListView 群組](../../../../docs/framework/winforms/controls/media/listviewgroups.gif "ListViewGroups")  
  
 下列程序需要 **Windows 應用程式**專案，且專案具有包含 <xref:System.Windows.Forms.ListView> 控制項的表單。  如需設定這類專案的詳細資訊，請參閱 [How to: Create a Windows Application Project](http://msdn.microsoft.com/zh-tw/b2f93fed-c635-4705-8d0e-cf079a264efa) 和 [如何：將控制項加入至 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。  
  
 若要啟用群組，您必須在設計工具中或以程式方式，先建立一或多個 <xref:System.Windows.Forms.ListViewGroup> 物件。  賦予群組定義之後，您就可以將項目指派到其中。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ListView> 群組只能在 [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] 上使用，您的應用程式會呼叫 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=fullName> 方法。  在早期的作業系統上，任何與群組相關的程式碼都沒有作用，而且不會出現群組。  如需詳細資訊，請參閱 <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=fullName>。  
>   
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要在設計工具中加入或移除群組  
  
1.  在 \[**屬性**\] 視窗中，按一下 <xref:System.Windows.Forms.ListView.Groups%2A> 屬性旁邊的**省略符號** \(![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) 按鈕。  
  
     \[**ListViewGroup 集合編輯器**\] 隨即出現。  
  
2.  如果要加入群組，請按一下 \[**加入**\] 按鈕。  然後您可以設定新群組的屬性，例如 <xref:System.Windows.Forms.ListViewGroup.Header%2A> 和 <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A> 屬性。  若要移除群組，請選取群組然後按一下 \[**移除**\] 按鈕。  
  
### 若要在設計工具中將項目指派給群組  
  
1.  在 \[**屬性**\] 視窗中，按一下 <xref:System.Windows.Forms.ListView.Items%2A> 屬性旁邊的**省略符號** \(![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) 按鈕。  
  
     \[**ListViewItem 集合編輯器**\] 隨即出現。  
  
2.  若要加入新項目，請按一下 \[**加入**\] 按鈕。  然後您可以設定新項目的屬性，例如 <xref:System.Windows.Forms.ListViewItem.Text%2A> 和 <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> 屬性。  
  
3.  選取 <xref:System.Windows.Forms.ListViewItem.Group%2A> 屬性，並從下拉式清單中選擇群組。  
  
## 請參閱  
 <xref:System.Windows.Forms.ListView>   
 <xref:System.Windows.Forms.ListView.Groups%2A>   
 <xref:System.Windows.Forms.ListViewGroup>   
 [ListView 控制項](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)   
 [ListView 控制項概觀](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)   
 [Windows XP Features and Windows Forms Controls](http://msdn.microsoft.com/zh-tw/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)   
 [如何：使用 Windows Form ListView 控制項加入和移除項目](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)