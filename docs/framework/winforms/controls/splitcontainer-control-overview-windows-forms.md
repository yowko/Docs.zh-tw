---
title: "SplitContainer 控制項概觀 (Windows Form)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SplitContainer
helpviewer_keywords: SplitContainer control [Windows Forms], about SplitContainer control
ms.assetid: 6de5a5f7-97a5-402d-be6d-7e2785483db5
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7d2e538241cca8288158628df777895fae9aa756
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="splitcontainer-control-overview-windows-forms"></a>SplitContainer 控制項概觀 (Windows Form)
Windows Form <xref:System.Windows.Forms.SplitContainer> 控制項可視為一個複合控制項，其中包含兩個可移動的分隔列所分隔的面板。 將滑鼠指標移到分隔列上時，指標會變更形狀，以顯示分隔列是可移動的。  
  
> [!IMPORTANT]
>  在**工具箱**，<xref:System.Windows.Forms.SplitContainer>控制項取代<xref:System.Windows.Forms.Splitter>控制了在舊版的[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]。 <xref:System.Windows.Forms.SplitContainer> 控制項會比 <xref:System.Windows.Forms.Splitter> 控制項合用。 <xref:System.Windows.Forms.Splitter>類別仍然包含在[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]相容性與現有的應用程式，但強烈建議您將<xref:System.Windows.Forms.SplitContainer>新專案的控制項。  
  
 與<xref:System.Windows.Forms.SplitContainer>控制項，您可以建立複雜的使用者介面; 通常，一個面板中的選擇會決定其他面板中所顯示的物件。 這種排列方式可有效地顯示及瀏覽資訊。 擁有兩個面板可讓您彙總資訊區域中，並提升列或 「 分隔器 」 可讓輕鬆調整面板的大小的使用者。  
  
 多個<xref:System.Windows.Forms.SplitContainer>控制項也可以巢狀，第二個<xref:System.Windows.Forms.SplitContainer>控制項的水平導向建立上方和下方的面板。  
  
 請注意，<xref:System.Windows.Forms.SplitContainer>鍵盤存取預設控制項; 使用者可以按下方向鍵，如果移動分隔器<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A>屬性設定為`false`。  
  
 <xref:System.Windows.Forms.SplitContainer.Orientation%2A>屬性<xref:System.Windows.Forms.SplitContainer>控制項會決定分隔器，而不是控制項本身的方向。 因此，當這個屬性設定為<xref:System.Windows.Forms.Orientation.Vertical>，分隔器執行由上往下，建立左、 右面板。  
  
 此外，請注意，值<xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A>屬性的值而有所不同<xref:System.Windows.Forms.SplitContainer.Orientation%2A>屬性。 如需詳細資訊，請參閱<xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A>屬性。  
  
 您也可以限制的大小和移動<xref:System.Windows.Forms.SplitContainer>控制項。 <xref:System.Windows.Forms.SplitContainer.FixedPanel%2A>屬性會決定哪個面板會維持相同大小之後<xref:System.Windows.Forms.SplitContainer>調整控制項大小，而<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A>屬性會決定分隔器是否可移動的鍵盤或滑鼠。  
  
> [!NOTE]
>  即使<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A>屬性設定為`true`，分隔器可能仍然以程式設計的方式，例如使用移動<xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A>屬性。  
  
 最後，每個面板<xref:System.Windows.Forms.SplitContainer>控制項具有屬性，以決定其個別的大小。  
  
## <a name="commonly-used-properties-methods-and-events"></a>常用屬性、方法和事件  
  
|名稱|描述|  
|----------|-----------------|  
|<xref:System.Windows.Forms.SplitContainer.FixedPanel%2A> 屬性|決定哪個面板維持相同大小之後<xref:System.Windows.Forms.SplitContainer>調整控制項大小。|  
|<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> 屬性|決定分隔器是否可移動的鍵盤或滑鼠。|  
|<xref:System.Windows.Forms.SplitContainer.Orientation%2A> 屬性|決定分隔器是否垂直或水平排列。|  
|<xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> 屬性|決定從左方或上方的邊緣可移動的分隔列以像素為單位的距離。|  
|<xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> 屬性|決定最小距離，單位為像素，使用者可以移動分隔器。|  
|<xref:System.Windows.Forms.SplitContainer.SplitterWidth%2A> 屬性|決定的厚度，以像素的分隔器。|  
|<xref:System.Windows.Forms.SplitContainer.SplitterMoving>事件|發生於分隔器移動。|  
|<xref:System.Windows.Forms.SplitContainer.SplitterMoved>事件|發生於分隔器移動。|  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Forms.SplitContainer>  
 [SplitContainer 控制項](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)  
 [SplitContainer 控制項範例](http://msdn.microsoft.com/library/9015fad0-7108-4d85-a83a-a72d038c4f65)
