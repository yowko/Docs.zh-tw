---
title: "How to: Display Item Headers in a DataRepeater Control (Visual Studio) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "DataRepeater, item headers"
  - "DataRepeater, selection indicators"
ms.assetid: 37321447-0ffa-43e1-bdc9-0480e392b90f
caps.latest.revision: 7
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 7
---
# How to: Display Item Headers in a DataRepeater Control (Visual Studio)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

當選取 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> 時，<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項中的項目標題會提供視覺指示器。  當 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> 屬性是設定為 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles> \(預設值\) 時，項目標題會顯示在每個項目的左方。  當 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> 屬性是設定為 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles> 時，項目標題會顯示在每個項目的上方。  
  
 項目第一次被選取時，項目標題顯示的色彩會由 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> 屬性指定，而且會出現一個白色箭頭圖示。  
  
> [!NOTE]
>  如果將 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> 設定為 <xref:System.Drawing.Color.White%2A>，則項目第一次被選取時並不會顯示選取符號。  
  
 當 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> 中的欄位獲得焦點 \(Focus\) 時，項目標題的色彩會變更為 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> 背景色彩，而且箭頭圖示會變更成黑色。  如果資料已經變更，就會在項目標題顯示鉛筆符號。  
  
 項目標題的預設寬度 \(在 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> 屬性設定為 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles> 時則為預設高度\) 是 15 個像素。  只要設定 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> 屬性即可變更寬度。  
  
> [!NOTE]
>  如果 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> 屬性值是設定為小於 11，則在項目標題中不會顯示指示器符號。  
  
 只要將 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> 屬性設定為 \[**False**\]，就能隱藏項目標題。  當 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> 設定為 \[**False**\] 時，唯一能表示項目是否已選取的標記只有 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> 周圍圍繞的虛線。  
  
> [!NOTE]
>  藉由在 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項的 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> 事件中監視 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> 的 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A> 屬性，您也可以自行提供選取指示器。  如需詳細資訊，請參閱 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>。  
  
### 若要變更項目標題的外觀  
  
1.  在 \[Windows Form 設計工具\] 中，選取 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項的下方區域。  
  
    > [!NOTE]
    >  您必須選取控制項的下方區域。  如果選取項目樣板區段，將會在 \[屬性\] 視窗中顯示不同的屬性集。  
  
2.  在 \[屬性\] 視窗中，使用 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> 屬性變更項目標題的色彩。  
  
    > [!NOTE]
    >  如果將 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> 設定為 <xref:System.Drawing.Color.White%2A>，則項目第一次被選取時並不會顯示選取符號。  
  
3.  使用 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> 屬性變更項目標題的寬度 \(或高度\)。  
  
    > [!NOTE]
    >  如果 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> 屬性值是設定為小於 11，則在項目標題中不會顯示指示器符號。  
  
### 若要隱藏項目標題  
  
1.  在 \[Windows Form 設計工具\] 中，選取 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項的下方區域。  
  
    > [!NOTE]
    >  您必須選取控制項的下方區域。  如果選取項目樣板區段，將會在 \[屬性\] 視窗中顯示不同的屬性集。  
  
2.  在 \[屬性\] 視窗中，將 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> 屬性設定為 \[**False**\]。  
  
     當 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 中的項目被選取時，唯一的指示會是 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> 的周圍有虛線圍繞。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>   
 [Introduction to the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [How to: Change the Appearance of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)   
 [How to: Change the Layout of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)   
 [Troubleshooting the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)