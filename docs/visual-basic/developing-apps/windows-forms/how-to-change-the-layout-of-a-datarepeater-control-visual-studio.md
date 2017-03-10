---
title: "How to: Change the Layout of a DataRepeater Control (Visual Studio) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "DataRepeater, changing layout style"
  - "DataRepeater, changing orientation"
ms.assetid: 33aa8fd5-ac63-4bd0-ba13-8c2ab17e7824
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# How to: Change the Layout of a DataRepeater Control (Visual Studio)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項的顯示可以是縱向 \(垂直捲動項目\) 或橫向 \(水平捲動項目\)。  只要變更 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> 屬性，就能在設計階段或執行階段變更顯示方向。  如果您在執行階段變更 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> 屬性，可能也會想要調整 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> 的大小，以及調整子控制項的位置。  
  
> [!NOTE]
>  如果您在執行階段時在 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> 上調整控制項的位置，則必須於重新定位控制項的程式碼區塊開頭及結尾處呼叫 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A> 和 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A> 方法。  
  
### 若要在設計階段變更配置  
  
1.  在 \[Windows Form 設計工具\] 中，選取 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項。  
  
    > [!NOTE]
    >  您必須選取 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項的外框，方法是按一下該控制項的下方區域，而非上方 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> 區域。  
  
2.  在 \[屬性\] 視窗中，將 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> 屬性設定為 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles> 或 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles>。  
  
### 若要在執行階段變更配置  
  
1.  將下列程式碼加入至按鈕或功能表的 `Click` 事件處理常式：  
  
     [!code-cs[VbPowerPacksDataRepeaterLayout#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/csharp/VbPowerPacksDataRepeaterLayoutCS/VbPowerPacksDataRepeaterLayout.cs#1)]
     [!code-vb[VbPowerPacksDataRepeaterLayout#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/visualbasic/VbPowerPacksDataRepeaterLayout/VbPowerPacksDataRepeaterLayout.vb#1)]  
  
2.  在大部分情況下，您會想要加入與「範例」一節所示類似的程式碼以調整 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> 的大小，並配合新的方向重新整理控制項。  
  
## 範例  
 下列範例顯示如何在事件處理常式中回應 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyleChanged> 事件。  這個範例要求您的表單上必須有一個名為 `DataRepeater1` 的 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項，而且其 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> 包含兩個名為 `TextBox1` 和 `TextBox2` 的 <xref:System.Windows.Forms.TextBox> 控制項。  
  
 [!code-cs[VbPowerPacksDataRepeaterLayout#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/csharp/VbPowerPacksDataRepeaterLayoutCS/VbPowerPacksDataRepeaterLayout.cs#2)]
 [!code-vb[VbPowerPacksDataRepeaterLayout#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/visualbasic/VbPowerPacksDataRepeaterLayout/VbPowerPacksDataRepeaterLayout.vb#2)]  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>   
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>   
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A>   
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A>   
 [Introduction to the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [Troubleshooting the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)   
 [How to: Change the Appearance of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)