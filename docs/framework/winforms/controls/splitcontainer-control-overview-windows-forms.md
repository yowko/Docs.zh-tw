---
title: SplitContainer 控制項概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- SplitContainer
helpviewer_keywords:
- SplitContainer control [Windows Forms], about SplitContainer control
ms.assetid: 6de5a5f7-97a5-402d-be6d-7e2785483db5
ms.openlocfilehash: 76299d9bbd2b3eac4e765dfacf579c9979721fff
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963216"
---
# <a name="splitcontainer-control-overview-windows-forms"></a>SplitContainer 控制項概觀 (Windows Form)
Windows Form <xref:System.Windows.Forms.SplitContainer> 控制項可視為一個複合控制項，其中包含兩個可移動的分隔列所分隔的面板。 將滑鼠指標移到分隔列上時，指標會變更形狀，以顯示分隔列是可移動的。  
  
> [!IMPORTANT]
> 在 [**工具箱**] <xref:System.Windows.Forms.SplitContainer>中, 控制項<xref:System.Windows.Forms.Splitter>取代了舊版 Visual Studio 中的控制項。 <xref:System.Windows.Forms.SplitContainer> 控制項會比 <xref:System.Windows.Forms.Splitter> 控制項合用。 .NET Framework 中仍會包含 <xref:System.Windows.Forms.Splitter> 類別，以與現有的應用程式相容，但強烈建議您在新專案中使用 <xref:System.Windows.Forms.SplitContainer> 控制項。  
  
 <xref:System.Windows.Forms.SplitContainer>使用控制項, 您可以建立複雜的使用者介面; 通常, 一個面板中的選取專案會決定要在另一個面板中顯示的物件。 這種排列方式可有效地顯示及瀏覽資訊。 有兩個面板可讓您匯總區域中的資訊, 而橫條或「分割器」則可讓使用者輕鬆調整面板大小。  
  
 一個<xref:System.Windows.Forms.SplitContainer>以上的控制項也可以嵌套, 而第二<xref:System.Windows.Forms.SplitContainer>個控制項水準導向, 以建立頂端和底部的面板。  
  
 請注意, <xref:System.Windows.Forms.SplitContainer>控制項預設為鍵盤可供存取; <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A>如果屬性設定為`false`, 則使用者可以按方向鍵來移動分隔器。  
  
 <xref:System.Windows.Forms.SplitContainer>控制項<xref:System.Windows.Forms.SplitContainer.Orientation%2A>的屬性會決定分隔器的方向, 而不是控制項本身。 因此, 當這個屬性設定為<xref:System.Windows.Forms.Orientation.Vertical>時, 分隔器會從上到下執行, 並建立左窗格和右面板。  
  
 此外, 請注意<xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A>屬性的值會根據<xref:System.Windows.Forms.SplitContainer.Orientation%2A>屬性的值而有所不同。 如需詳細資訊, <xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A>請參閱屬性。  
  
 您也可以限制<xref:System.Windows.Forms.SplitContainer>控制項的大小和移動。 屬性會決定<xref:System.Windows.Forms.SplitContainer>控制項調整大小時, 哪一個面板會保持相同的大小, <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A>而屬性會決定是否要由鍵盤或滑鼠移動分隔器。 <xref:System.Windows.Forms.SplitContainer.FixedPanel%2A>  
  
> [!NOTE]
> 即使屬性設定為`true`, 仍然可能以程式設計方式移動分隔器; 例如, 藉由使用<xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A>屬性。 <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A>  
  
 最後, <xref:System.Windows.Forms.SplitContainer>控制項的每個面板都有屬性可決定其個別大小。  
  
## <a name="commonly-used-properties-methods-and-events"></a>常用屬性、方法和事件  
  
|名稱|說明|  
|----------|-----------------|  
|<xref:System.Windows.Forms.SplitContainer.FixedPanel%2A> 屬性|決定<xref:System.Windows.Forms.SplitContainer>控制項調整大小時, 哪個面板會保持相同的大小。|  
|<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> 屬性|決定是否可以使用鍵盤或滑鼠移動分隔器。|  
|<xref:System.Windows.Forms.SplitContainer.Orientation%2A> 屬性|決定分隔器是以垂直或水準方式排列。|  
|<xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> 屬性|決定從左邊或上邊緣到可移動分隔線列之間的距離 (以圖元為單位)。|  
|<xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> 屬性|決定使用者可以移動分隔器的最小距離 (以圖元為單位)。|  
|<xref:System.Windows.Forms.SplitContainer.SplitterWidth%2A> 屬性|決定分隔器的粗細 (以圖元為單位)。|  
|<xref:System.Windows.Forms.SplitContainer.SplitterMoving> 事件|當分隔器移動時發生。|  
|<xref:System.Windows.Forms.SplitContainer.SplitterMoved> 事件|發生于分隔器移動時。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.SplitContainer>
- [SplitContainer 控制項](splitcontainer-control-windows-forms.md)
- [SplitContainer 控制項範例](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/0ffz7d1b(v=vs.90))
