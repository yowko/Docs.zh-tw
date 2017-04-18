---
title: "SplitContainer 控制項概觀 (Windows Form) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SplitContainer"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "SplitContainer 控制項 [Windows Form], 關於 SplitContainer 控制項"
ms.assetid: 6de5a5f7-97a5-402d-be6d-7e2785483db5
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# SplitContainer 控制項概觀 (Windows Form)
Windows Form <xref:System.Windows.Forms.SplitContainer> 控制項可視為一個複合控制項；它有兩個由可移動的分隔列所分隔的面板。  當滑鼠指標移到此分隔列上，指標會變更其外觀，顯示此分隔列是可移動的。  
  
> [!IMPORTANT]
>  在 \[**工具箱**\] 中，<xref:System.Windows.Forms.SplitContainer> 控制項取代了在之前 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 版本的 <xref:System.Windows.Forms.Splitter> 控制項。  <xref:System.Windows.Forms.SplitContainer> 控制項會比 <xref:System.Windows.Forms.Splitter> 控制項合用。  [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 中仍然包含 <xref:System.Windows.Forms.Splitter> 類別，以保障與現有應用程式間的相容性，但我們強烈建議您在新的專案使用 <xref:System.Windows.Forms.SplitContainer> 控制項。  
  
 使用 <xref:System.Windows.Forms.SplitContainer> 控制項，您可以建立複雜的使用者介面；通常，在面板的選擇會決定另一個面板中物件呈現的方式。  對於顯示和瀏覽資訊而言，這個安排非常的有效率。  在區域內，兩個面板可以讓您彙總 \(Aggregate\) 區域內的資訊，而分隔列，或是說「分隔器」\(Splitter\) 可以讓使用者更容易調整面板的大小。  
  
 一個以上的 <xref:System.Windows.Forms.SplitContainer> 控制項也可以是巢狀的，而第二個 <xref:System.Windows.Forms.SplitContainer> 控制項是水平導向，以建立上方和下方的面板。  
  
 請注意，<xref:System.Windows.Forms.SplitContainer> 控制項預設是可以以鍵盤進行存取；如果 <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> 屬性是設定為 `false`，使用者也可以按方向鍵來移動分隔器。  
  
 <xref:System.Windows.Forms.SplitContainer> 控制項的 <xref:System.Windows.Forms.SplitContainer.Orientation%2A> 屬性會決定分隔器的方向，而不是控制項本身的方向。  因此，當這個屬性設定為 <xref:System.Windows.Forms.Orientation> 時，分隔器會從上至下執行，建立左邊和右邊的面板。  
  
 此外，請注意 <xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A> 屬性的值視 <xref:System.Windows.Forms.SplitContainer.Orientation%2A> 屬性的值而有不同。  如需詳細資訊，請參閱 <xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A> 屬性。  
  
 您也可以限制 <xref:System.Windows.Forms.SplitContainer> 控制項的大小及動作。  <xref:System.Windows.Forms.SplitContainer.FixedPanel%2A> 屬性決定哪一個面板會在 <xref:System.Windows.Forms.SplitContainer> 控制項調整大小後保持相同大小，而 <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> 屬性則是決定分隔器是否可由鍵盤或滑鼠來移動。  
  
> [!NOTE]
>  即使 <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> 屬性設定為 `true`，分隔器仍舊可以以程式方式移動；例如，使用 <xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> 屬性。  
  
 最後，每個 <xref:System.Windows.Forms.SplitContainer> 控制項的面板都有可決定自己大小的屬性。  
  
## 常用的屬性、方法和事件  
  
|名稱|描述|  
|--------|--------|  
|<xref:System.Windows.Forms.SplitContainer.FixedPanel%2A> 屬性|決定哪一個面板在 <xref:System.Windows.Forms.SplitContainer> 控制項已變更大小後，保持相同大小。|  
|<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> 屬性|決定分隔器是否可隨鍵盤或滑鼠移動。|  
|<xref:System.Windows.Forms.SplitContainer.Orientation%2A> 屬性|決定分隔器要呈垂直或水平排列。|  
|<xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> 屬性|決定從左方或上方邊緣至可移動的分隔列間的距離 \(以像素計算\)。|  
|<xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> 屬性|決定使用者可移動分隔器之最短距離 \(以像素計算\)。|  
|<xref:System.Windows.Forms.SplitContainer.SplitterWidth%2A> 屬性|決定分隔器的厚度 \(以像素計算\)。|  
|<xref:System.Windows.Forms.SplitContainer.SplitterMoving> 事件|當分隔器移動時發生。|  
|<xref:System.Windows.Forms.SplitContainer.SplitterMoved> 事件|當分隔器移動後發生。|  
  
## 請參閱  
 <xref:System.Windows.Forms.SplitContainer>   
 [SplitContainer 控制項](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)   
 [SplitContainer Control Sample](http://msdn.microsoft.com/zh-tw/9015fad0-7108-4d85-a83a-a72d038c4f65)