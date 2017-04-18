---
title: "如何：在 MenuStrip 中顯示選項按鈕 (Windows Form) | Microsoft Docs"
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
  - "顯示選項按鈕, 控制項 [Windows Form]"
  - "控制項 [Windows Form], 顯示選項按鈕"
  - "選項按鈕 [Windows Form], 在 MenuStrip 中顯示"
ms.assetid: 8b596af2-9ff8-4f7b-93d7-cba830e167f4
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：在 MenuStrip 中顯示選項按鈕 (Windows Form)
選項按鈕與核取方塊類似，唯一的不同是使用者一次只能選取一個選項。  雖然根據預設，<xref:System.Windows.Forms.ToolStripMenuItem> 類別未提供選項按鈕行為，但是此類別提供核取方塊行為，讓您可以進行自訂，以便在 <xref:System.Windows.Forms.MenuStrip> 控制項中實作功能表項目的選項按鈕行為。  
  
 當功能表項目的 <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> 屬性為 `true` 時，使用者可以按一下該項目，以切換核取記號的顯示。  <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> 屬性會指示目前項目的狀態。  若要實作基本的選項按鈕行為，您必須確認當某一個項目被選取時，將前一個所選取之項目的 <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> 屬性設定為 `false`。  
  
 下列程序將說明如何在繼承 <xref:System.Windows.Forms.ToolStripMenuItem> 類別的類別中，實作此功能和其他功能。  `ToolStripRadioButtonMenuItem` 類別將覆寫 <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> 和 <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> 等成員，以提供選項按鈕的選取行為和外觀。  此外，這個類別將覆寫 <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> 屬性，除非選取父項目，否則會停用子功能表上的選項。  
  
### 若要實作選項按鈕的選取行為  
  
1.  將 <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> 屬性初始化為 `true`，以啟用項目選取。  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#110)]
     [!code-vb[ToolStripRadioButtonMenuItem#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#110)]  
  
2.  覆寫 <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> 方法，以便選取新項目時，清除先前所選取之項目的選取。  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#120)]
     [!code-vb[ToolStripRadioButtonMenuItem#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#120)]  
  
3.  覆寫 <xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A> 方法，以確保按一下已經被選取的項目將不會清除選取。  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#130](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#130)]
     [!code-vb[ToolStripRadioButtonMenuItem#130](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#130)]  
  
### 若要修改選項按鈕項目的外觀  
  
1.  覆寫 <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A>方法，使用 <xref:System.Windows.Forms.RadioButtonRenderer> 類別以選項按鈕取代預設的核取記號。  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#140](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#140)]
     [!code-vb[ToolStripRadioButtonMenuItem#140](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#140)]  
  
2.  覆寫 <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>、<xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>、<xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A> 和 <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A> 方法，以追蹤滑鼠的狀態並確保 <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> 方法繪製正確的選項按鈕狀態。  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#150](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#150)]
     [!code-vb[ToolStripRadioButtonMenuItem#150](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#150)]  
  
### 若要在未選取父項目時，停用子功能表上的選項  
  
1.  覆寫 <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> 屬性，當其父項目的 <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> 值為 `true` 而且 <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> 值為 `false` 時，便會停用該項目。  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#160](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#160)]
     [!code-vb[ToolStripRadioButtonMenuItem#160](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#160)]  
  
2.  覆寫 <xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A> 方法，以訂閱父項目的 <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> 事件。  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#170](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#170)]
     [!code-vb[ToolStripRadioButtonMenuItem#170](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#170)]  
  
3.  在父項目之 <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> 事件的處理常式中，使項目失效，以使用新的啟用狀態來更新顯示。  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#180](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#180)]
     [!code-vb[ToolStripRadioButtonMenuItem#180](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#180)]  
  
## 範例  
 下列程式碼範例將提供完整的 `ToolStripRadioButtonMenuItem` 類別、<xref:System.Windows.Forms.Form> 類別和 `Program` 類別，以示範選項按鈕行為。  
  
 [!code-csharp[ToolStripRadioButtonMenuItem#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#000)]
 [!code-vb[ToolStripRadioButtonMenuItem#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#000)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   System、System.Drawing 和 System.Windows.Forms 組件的參考。  
  
## 請參閱  
 <xref:System.Windows.Forms.MenuStrip>   
 <xref:System.Windows.Forms.ToolStripMenuItem>   
 <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.RadioButtonRenderer>   
 [MenuStrip 控制項](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)   
 [如何：實作自訂的 ToolStripRenderer](../../../../docs/framework/winforms/controls/how-to-implement-a-custom-toolstriprenderer.md)