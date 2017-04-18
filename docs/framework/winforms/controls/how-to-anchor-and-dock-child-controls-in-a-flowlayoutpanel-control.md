---
title: "如何：錨定和停駐 FlowLayoutPanel 控制項中的子控制項 | Microsoft Docs"
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
  - "子控制項, 錨定和停駐"
  - "控制項 [Windows Form], 子項"
  - "FlowLayoutPanel 控制項 [Windows Form], 子控制項"
  - "版面配置 [Windows Form], 子控制項"
ms.assetid: a2bcdfca-9b63-45e6-9c0e-3411015cba98
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 如何：錨定和停駐 FlowLayoutPanel 控制項中的子控制項
<xref:System.Windows.Forms.FlowLayoutPanel> 控制項在其子控制項中支援 <xref:System.Windows.Forms.Control.Anchor%2A> 和 <xref:System.Windows.Forms.Control.Dock%2A> 屬性。  
  
### 錨定和停駐 FlowLayoutPanel 控制項中的子控制項  
  
1.  請在表單上建立 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項。  
  
2.  設定 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項的 <xref:System.Windows.Forms.Control.Width%2A> 為 300，並將其 <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> 設定為 <xref:System.Windows.Forms.FlowDirection>。  
  
3.  建立兩個 <xref:System.Windows.Forms.Button> 控制項，並置入 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項。  
  
4.  設定第一個按鈕的 <xref:System.Windows.Forms.Control.Width%2A> 為 200。  
  
5.  將第二個按鈕的 <xref:System.Windows.Forms.Control.Dock%2A> 屬性設為 <xref:System.Windows.Forms.DockStyle>。  
  
    > [!NOTE]
    >  第二個按鈕會假設與第一個按鈕的寬度相同。  它不會自動縮放 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項的寬度。  
  
6.  將第二個按鈕的 <xref:System.Windows.Forms.Control.Dock%2A> 屬性設為 `None`。  這會使按鈕假設為原始的寬度。  
  
7.  將第二個按鈕的 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性設為 `Left、 Right`。  
  
    > [!IMPORTANT]
    >  第二個按鈕會假設與第一個按鈕的寬度相同。  它不會自動縮放 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項的寬度。  這是在 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項錨定和停駐的一般規則：對於垂直流動方向，<xref:System.Windows.Forms.FlowLayoutPanel> 控制項會計算資料行中最寬子控制項的隱含資料行寬度。  此資料行中具有 <xref:System.Windows.Forms.Control.Anchor%2A> 或 <xref:System.Windows.Forms.Control.Dock%2A> 屬性的所有其他控制項會配合隱含資料行對齊或自動縮放。  此行為的運作方式類似水平流動方向。  <xref:System.Windows.Forms.FlowLayoutPanel> 控制項由此資料列中最高子控制項的高度計算隱含資料列的高度，在此資料列中所有停駐或錨定的子控制項會配合隱含資料列對齊或調整大小。  
  
## 範例  
 下圖顯示四個按鈕，相對於藍色按鈕錨定和停駐在 <xref:System.Windows.Forms.FlowLayoutPanel>。  <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> 為 <xref:System.Windows.Forms.FlowDirection>。  
  
 ![FlowLayoutPanel 錨定](../../../../docs/framework/winforms/controls/media/net-flpanchorexp.png "NET\_FLPanchorExp")  
  
 下圖顯示四個按鈕，相對於藍色按鈕錨定和停駐在 <xref:System.Windows.Forms.FlowLayoutPanel>。  <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> 為 <xref:System.Windows.Forms.FlowDirection>。  
  
 ![FlowLayoutPanel 錨定](../../../../docs/framework/winforms/controls/media/vs-flpanchor2.png "VS\_FLPanchor2")  
  
 下列程式碼範例示範 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項中的 <xref:System.Windows.Forms.Button> 控制項之不同的 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性值。  
  
 [!code-csharp[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/CS/FlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/VB/FlpAnchorExampleForm.vb#1)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   System、System.Data、System.Drawing 和 System.Windows.Forms 組件的參考。  
  
 如需從 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 或 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 的命令列建置這個範例的相關資訊，請參閱[從命令列建置](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) 或[使用 csc.exe 建置命令列](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。  您也可以透過將程式碼貼入新的專案，在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。  另請參閱[如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。  
  
## 請參閱  
 <xref:System.Windows.Forms.FlowLayoutPanel>   
 [FlowLayoutPanel 控制項概觀](../../../../docs/framework/winforms/controls/flowlayoutpanel-control-overview.md)