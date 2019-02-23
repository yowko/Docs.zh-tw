---
title: SplitContainer 控制項概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- SplitContainer
helpviewer_keywords:
- SplitContainer control [Windows Forms], about SplitContainer control
ms.assetid: 6de5a5f7-97a5-402d-be6d-7e2785483db5
ms.openlocfilehash: d96f754c9e28455b6494c17d4d295837c008f535
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2019
ms.locfileid: "56747219"
---
# <a name="splitcontainer-control-overview-windows-forms"></a>SplitContainer 控制項概觀 (Windows Form)
Windows Form <xref:System.Windows.Forms.SplitContainer> 控制項可視為一個複合控制項，其中包含兩個可移動的分隔列所分隔的面板。 將滑鼠指標移到分隔列上時，指標會變更形狀，以顯示分隔列是可移動的。  
  
> [!IMPORTANT]
>  在 **工具箱**，<xref:System.Windows.Forms.SplitContainer>控制項取代了<xref:System.Windows.Forms.Splitter>是否有舊版的 Visual Studio 中的控制項。 
  <xref:System.Windows.Forms.SplitContainer> 控制項會比 <xref:System.Windows.Forms.Splitter> 控制項合用。 <xref:System.Windows.Forms.Splitter>類別仍然包含在[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]相容性與現有的應用程式，但強烈建議您將<xref:System.Windows.Forms.SplitContainer>針對新專案的控制項。  
  
 使用<xref:System.Windows.Forms.SplitContainer>控制項，您可以建立複雜的使用者介面; 通常，一個面板中的選取範圍會決定在其他窗格中所顯示的物件。 這種排列方式可有效地顯示及瀏覽資訊。 有兩個面板可讓您彙總資訊方面的情況下，，和列中或 「 分隔器 」 可以方便使用者調整面板的大小。  
  
 多個<xref:System.Windows.Forms.SplitContainer>控制項可以也巢狀，第二個<xref:System.Windows.Forms.SplitContainer>控制水平，導向建立上方和下方的面板。  
  
 請注意，<xref:System.Windows.Forms.SplitContainer>控制項是鍵盤直接存取預設情況下，使用者可以按下方向鍵來移動分隔器，如果<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A>屬性設定為`false`。  
  
 <xref:System.Windows.Forms.SplitContainer.Orientation%2A>屬性<xref:System.Windows.Forms.SplitContainer>控制項會決定起的分隔器，而不是控制項本身的方向。 因此，當這個屬性設定為<xref:System.Windows.Forms.Orientation.Vertical>，分隔器執行由上而下、 左和右面板的建立。  
  
 此外，請注意，值<xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A>屬性的值而異<xref:System.Windows.Forms.SplitContainer.Orientation%2A>屬性。 如需詳細資訊，請參閱<xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A>屬性。  
  
 您也可以限制的大小和移動<xref:System.Windows.Forms.SplitContainer>控制項。 <xref:System.Windows.Forms.SplitContainer.FixedPanel%2A>屬性會決定哪一個面板會保持相同的大小之後<xref:System.Windows.Forms.SplitContainer>調整控制項大小，而<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A>屬性會決定是否可移動的鍵盤或滑鼠分隔器。  
  
> [!NOTE]
>  即使<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A>屬性設定為`true`，分隔器可能還是以程式設計的方式，例如使用移動<xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A>屬性。  
  
 最後，每個面板<xref:System.Windows.Forms.SplitContainer>控制項有屬性，以決定其個別的大小。  
  
## <a name="commonly-used-properties-methods-and-events"></a>常用屬性、方法和事件  
  
|名稱|描述|  
|----------|-----------------|  
|<xref:System.Windows.Forms.SplitContainer.FixedPanel%2A> 屬性|決定哪個面板會保持相同大小之後<xref:System.Windows.Forms.SplitContainer>調整控制項大小。|  
|<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> 屬性|判斷分隔器是否可以使用鍵盤或滑鼠來移動。|  
|<xref:System.Windows.Forms.SplitContainer.Orientation%2A> 屬性|決定是否垂直或水平排列分隔器。|  
|<xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> 屬性|決定在可移動的分隔器列的像素的左邊緣或上邊緣的距離。|  
|<xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> 屬性|決定的最短距離，單位為像素，使用者可以移動分隔器。|  
|<xref:System.Windows.Forms.SplitContainer.SplitterWidth%2A> 屬性|判斷粗細，單位為像素的分隔器。|  
|<xref:System.Windows.Forms.SplitContainer.SplitterMoving> 事件|發生於分隔器移動。|  
|<xref:System.Windows.Forms.SplitContainer.SplitterMoved> 事件|發生於分隔器移動。|  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.SplitContainer>
- [SplitContainer 控制項](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)
- [SplitContainer 控制項範例](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/0ffz7d1b(v=vs.90))
