---
title: "如何：使用設計工具，以 Windows Form 建立多窗格使用者介面 | Microsoft Docs"
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
  - "多窗格使用者介面"
  - "SplitContainer 控制項 [Windows Form], 使用設計工具"
  - "使用者介面, 多窗格"
ms.assetid: c3f9294d-a26c-4198-9242-f237f55f7573
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 如何：使用設計工具，以 Windows Form 建立多窗格使用者介面
在下列程序中，您將建立一個多窗格使用者介面，它和 Microsoft Outlook 中的使用者介面類似，具有 \[**資料夾**\] 清單、\[**訊息**\] 窗格，以及 \[**預覽**\] 窗格。  這個排列主要是透過停駐控制項和表單來達成。  
  
 當停駐控制項時，您決定控制項應該貼近父容器 \(Container\) 的哪一個邊緣。  因此，如果您設定 <xref:System.Windows.Forms.SplitContainer.Dock%2A> 屬性為 <xref:System.Windows.Forms.DockStyle>，則控制項的右邊緣將停駐在其父控制項的右邊緣。  此外，控制項的停駐邊緣會調整大小以符合其容器控制項的邊緣。  如需 <xref:System.Windows.Forms.SplitContainer.Dock%2A> 屬性如何運作的詳細資訊，請參閱 [如何：將控制項停駐在 Windows Form 上](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)。  
  
 這個程序集中焦點於排列 <xref:System.Windows.Forms.SplitContainer> 和其他在表單上的控制項，並非加入功能來讓應用程式模仿 Microsoft Outlook。  
  
 若要建立這個使用者介面，將所有控制項置於 <xref:System.Windows.Forms.SplitContainer> 控制項中 \(包含在左邊面板中的 <xref:System.Windows.Forms.TreeView> 控制項\)。  <xref:System.Windows.Forms.SplitContainer> 控制項的右邊面板包含第二個 <xref:System.Windows.Forms.SplitContainer> 控制項和 <xref:System.Windows.Forms.ListView> 控制項 \(位於 <xref:System.Windows.Forms.RichTextBox> 控制項之上\)。  這些 <xref:System.Windows.Forms.SplitContainer> 控制項可讓您單獨的調整表單上其他控制項的大小。  您可以修改以下程序的方法來建立您自己的自訂使用者介面。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要在設計階段建立 Outlook 樣式的使用者介面  
  
1.  建立新的 \[Windows 應用程式\] 專案。  如需詳細資訊，請參閱 [How to: Create a Windows Application Project](http://msdn.microsoft.com/zh-tw/b2f93fed-c635-4705-8d0e-cf079a264efa)。  
  
2.  將 <xref:System.Windows.Forms.SplitContainer> 控制項從 \[**工具箱**\] 拖曳至表單。  請在 \[**屬性**\] 視窗中，將 <xref:System.Windows.Forms.SplitContainer.Dock%2A> 屬性設定為 <xref:System.Windows.Forms.DockStyle>。  
  
3.  從 \[**工具箱**\] 拖曳 <xref:System.Windows.Forms.TreeView> 控制項至 <xref:System.Windows.Forms.SplitContainer> 控制項左邊的面板。  在 \[**屬性**\] 視窗中，將 <xref:System.Windows.Forms.SplitContainer.Dock%2A> 屬性設定為 <xref:System.Windows.Forms.DockStyle>，方式是在按向下鍵時，在顯示的數值編輯器中按一下左邊窗格。  
  
4.  從 \[**工具箱**\] 拖曳另一個 <xref:System.Windows.Forms.SplitContainer> 控制項；將它放置於您加入至表單的 <xref:System.Windows.Forms.SplitContainer> 控制項的右邊面板中。  請在 \[**屬性**\] 視窗中，將 <xref:System.Windows.Forms.SplitContainer.Dock%2A> 屬性設定為 <xref:System.Windows.Forms.DockStyle>，並將 <xref:System.Windows.Forms.SplitContainer.Orientation%2A> 屬性設定為 <xref:System.Windows.Forms.Orientation>。  
  
5.  從 \[**工具箱**\] 拖曳 <xref:System.Windows.Forms.ListView> 控制項至您第二個加入至表單的 <xref:System.Windows.Forms.SplitContainer> 控制項上方的面板。  將 <xref:System.Windows.Forms.ListView> 控制項的 <xref:System.Windows.Forms.SplitContainer.Dock%2A> 屬性設定為 <xref:System.Windows.Forms.DockStyle>。  
  
6.  從 \[**工具箱**\] 拖曳 <xref:System.Windows.Forms.RichTextBox> 控制項至第二個 <xref:System.Windows.Forms.SplitContainer> 控制項下方的面板。  將 <xref:System.Windows.Forms.RichTextBox> 控制項的 <xref:System.Windows.Forms.SplitContainer.Dock%2A> 屬性設定為 <xref:System.Windows.Forms.DockStyle>。  
  
     針對此點，如果您按 F5 來執行此應用程式，表單會顯示三個部分所組成的使用者介面，與 Microsoft Outlook 的使用者介面類似。  
  
    > [!NOTE]
    >  將滑鼠指標置於 <xref:System.Windows.Forms.SplitContainer> 控制項內任何一個分隔器上方時，就可以調整內部維度的大小。  
  
     就應用程式開發而言，您已經製作出複雜的使用者介面。  下一步是進行應用程式本身的程式開發，或許，藉由連接 <xref:System.Windows.Forms.TreeView> 控制項和 <xref:System.Windows.Forms.ListView> 控制項，至某種資料來源。  如需有關連接控制項至資料的詳細資訊，請參閱[資料繫結和 Windows Form](../../../../docs/framework/winforms/data-binding-and-windows-forms.md)。  
  
## 請參閱  
 <xref:System.Windows.Forms.SplitContainer>   
 [SplitContainer 控制項](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)