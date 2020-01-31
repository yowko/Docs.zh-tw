---
title: SplitContainer 控制項概觀
ms.date: 03/30/2017
f1_keywords:
- SplitContainer
helpviewer_keywords:
- SplitContainer control [Windows Forms], about SplitContainer control
ms.assetid: 6de5a5f7-97a5-402d-be6d-7e2785483db5
ms.openlocfilehash: 5cb5240ed4ebe3e27c20844681068711c222e9a9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742917"
---
# <a name="splitcontainer-control-overview-windows-forms"></a>SplitContainer 控制項概觀 (Windows Form)
Windows Form <xref:System.Windows.Forms.SplitContainer> 控制項可視為一個複合控制項，其中包含兩個可移動的分隔列所分隔的面板。 將滑鼠指標移到分隔列上時，指標會變更形狀，以顯示分隔列是可移動的。  
  
> [!IMPORTANT]
> 在 [**工具箱**] 中，<xref:System.Windows.Forms.SplitContainer> 控制項取代了舊版 Visual Studio 中的 <xref:System.Windows.Forms.Splitter> 控制項。 <xref:System.Windows.Forms.SplitContainer> 控制項會比 <xref:System.Windows.Forms.Splitter> 控制項合用。 .NET Framework 中仍會包含 <xref:System.Windows.Forms.Splitter> 類別，以與現有的應用程式相容，但強烈建議您在新專案中使用 <xref:System.Windows.Forms.SplitContainer> 控制項。  
  
 有了 <xref:System.Windows.Forms.SplitContainer> 控制項，您就可以建立複雜的使用者介面;通常，一個面板中的選取專案會決定要在另一個面板中顯示的物件。 這種排列方式可有效地顯示及瀏覽資訊。 有兩個面板可讓您匯總區域中的資訊，而橫條或「分割器」則可讓使用者輕鬆調整面板大小。  
  
 您也可以將一個以上的 <xref:System.Windows.Forms.SplitContainer> 控制項加以嵌套，第二個 <xref:System.Windows.Forms.SplitContainer> 控制項水準導向，以建立頂端和底部的面板。  
  
 請注意，<xref:System.Windows.Forms.SplitContainer> 控制項預設為鍵盤可供存取;如果 [<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A>] 屬性設定為 [`false`]，使用者就可以按方向鍵來移動分隔器。  
  
 <xref:System.Windows.Forms.SplitContainer> 控制項的 <xref:System.Windows.Forms.SplitContainer.Orientation%2A> 屬性會決定分隔器的方向，而不是控制項本身。 因此，當這個屬性設定為 <xref:System.Windows.Forms.Orientation.Vertical>時，分隔器會從上到下執行，並建立左窗格和右面板。  
  
 此外，請注意，<xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A> 屬性的值會根據 <xref:System.Windows.Forms.SplitContainer.Orientation%2A> 屬性的值而有所不同。 如需詳細資訊，請參閱 <xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A> 屬性。  
  
 您也可以限制 <xref:System.Windows.Forms.SplitContainer> 控制項的大小和移動。 [<xref:System.Windows.Forms.SplitContainer.FixedPanel%2A>] 屬性會決定在調整 <xref:System.Windows.Forms.SplitContainer> 控制項的大小時，哪個面板會保持相同的大小，而 [<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A>] 屬性會決定是否要由鍵盤或滑鼠移動分隔器。  
  
> [!NOTE]
> 即使 <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> 屬性設為 `true`，仍然可能以程式設計方式移動分隔器;例如，藉由使用 <xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> 屬性。  
  
 最後，<xref:System.Windows.Forms.SplitContainer> 控制項的每個面板都有屬性，可決定其個別大小。  
  
## <a name="commonly-used-properties-methods-and-events"></a>常用屬性、方法和事件  
  
|Name|描述|  
|----------|-----------------|  
|<xref:System.Windows.Forms.SplitContainer.FixedPanel%2A> 屬性|決定 <xref:System.Windows.Forms.SplitContainer> 控制項調整大小時，哪一個面板會保持相同的大小。|  
|<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> 屬性|決定是否可以使用鍵盤或滑鼠移動分隔器。|  
|<xref:System.Windows.Forms.SplitContainer.Orientation%2A> 屬性|決定分隔器是以垂直或水準方式排列。|  
|<xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> 屬性|決定從左邊或上邊緣到可移動分隔線列之間的距離（以圖元為單位）。|  
|<xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> 屬性|決定使用者可以移動分隔器的最小距離（以圖元為單位）。|  
|<xref:System.Windows.Forms.SplitContainer.SplitterWidth%2A> 屬性|決定分隔器的粗細（以圖元為單位）。|  
|<xref:System.Windows.Forms.SplitContainer.SplitterMoving> 事件|當分隔器移動時發生。|  
|<xref:System.Windows.Forms.SplitContainer.SplitterMoved> 事件|發生于分隔器移動時。|  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.SplitContainer>
- [SplitContainer 控制項](splitcontainer-control-windows-forms.md)
- [SplitContainer 控制項範例](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/0ffz7d1b(v=vs.90))
