---
title: "如何：使用設計工具將 Windows Form 控制項繫結至類型 | Microsoft Docs"
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
  - "BindingSource 元件 [Windows Form], 繫結至類型"
  - "控制項 [Windows Form], 繫結至類型"
  - "類型 [Windows Form], 將控制項繫結至"
ms.assetid: 5ab984b5-c2d0-4638-a572-1c84013e8746
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：使用設計工具將 Windows Form 控制項繫結至類型
當您在建置與資料互動的控制項時，有些時候會發現必須將控制項繫結至型別，而不是物件。  通常您會需要在設計階段將控制項繫結至型別，因為資料可能還無法使用，但是您仍然要讓資料繫結控制項從型別的公用介面顯示資料。  下列程序將示範如何建立與型別繫結的新 <xref:System.Windows.Forms.BindingSource>，接著示範如何將型別的其中一個屬性繫結至 <xref:System.Windows.Forms.TextBox> 的 <xref:System.Windows.Forms.TextBox.Text%2A> 屬性。  
  
### 若要將 BindingSource 繫結至型別  
  
1.  建立一個 Windows Form 專案。  
  
     如需詳細資訊，請參閱 [How to: Create a Windows Application Project](http://msdn.microsoft.com/zh-tw/b2f93fed-c635-4705-8d0e-cf079a264efa)。  
  
2.  在 \[**設計**\] 檢視中，將一個 <xref:System.Windows.Forms.BindingSource> 元件拖曳到表單上。  
  
3.  在 \[**屬性**\] 視窗中，按一下 <xref:System.Windows.Forms.BindingSource.DataSource%2A> 屬性旁邊的箭頭。  
  
4.  在 \[**資料來源 UI 型別編輯器**\] 中，按一下 \[**加入專案資料來源**\]。  
  
5.  在 \[**選擇資料來源類型**\] 頁面上，選取 \[**物件**\]，再按一下 \[**下一步**\]。  
  
6.  選取要繫結的型別：  
  
    -   如果您要繫結的型別位於目前的專案中，或已將包含該型別的組件加入做為參考，請展開節點以找出您要的型別，然後選取該型別。  
  
         \-或\-  
  
    -   如果您要繫結的型別位於另一個目前不在參考清單上的組件中，請按一下 \[**加入參考**\]，然後按一下 \[**專案**\] 索引標籤。  選取其中包含您要的商務物件之專案，然後按一下 \[**確定**\]。  這個專案隨即出現在組件清單中，接著您就可以展開節點以找出所要的型別，然後選取該型別。  
  
        > [!NOTE]
        >  如果您要繫結至一個在架構或 Microsoft 組件中的型別，請清除 \[**隱藏以 Microsoft 或 System 開頭的組件**\] 核取方塊。  
  
7.  按 \[**下一步**\]，再按一下 \[**完成**\]。  
  
### 若要將控制項繫結至 BindingSource  
  
1.  將 <xref:System.Windows.Forms.TextBox> 加入表單中。  
  
2.  在 \[**屬性**\] 視窗中展開 **\(DataBindings\)** 節點。  
  
3.  按一下 <xref:System.Windows.Forms.TextBox.Text%2A> 屬性旁的箭號。  
  
4.  在 \[**資料來源 UI 型別編輯器**\] 中，展開先前加入的 <xref:System.Windows.Forms.BindingSource> 之節點，然後選取您要的屬性，以將其繫結至 <xref:System.Windows.Forms.TextBox> 的 <xref:System.Windows.Forms.TextBox.Text%2A> 屬性。  
  
## 請參閱  
 [BindingSource 元件](../../../../docs/framework/winforms/controls/bindingsource-component.md)   
 [如何：將 Windows Form 控制項繫結至類型](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)   
 [將控制項繫結至 Visual Studio 中的資料](../Topic/Bind%20controls%20to%20data%20in%20Visual%20Studio.md)