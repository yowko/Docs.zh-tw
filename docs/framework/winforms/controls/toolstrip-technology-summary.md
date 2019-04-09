---
title: ToolStrip 技術摘要
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], technology summary
- status bars [Windows Forms], technology summary
- toolbars [Windows Forms], technology summary
- menus [Windows Forms], technology summary
ms.assetid: e8d61973-7af9-429f-9df5-05a899c15a7b
ms.openlocfilehash: b6537faa3be7ee28a934927fc95100a34a64e176
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59120950"
---
# <a name="toolstrip-technology-summary"></a>ToolStrip 技術摘要
本主題提供有關 `ToolStrip` 控制項及支援這些控制項之類別的摘要資訊。  
  
 `ToolStrip` 控制項以及與其相關聯的類別提供了完整的解決方案，可用於建立工具列、 狀態列和功能表。  
  
## <a name="namespaces"></a>命名空間  
 <xref:System.Windows.Forms?displayProperty=nameWithType>  
  
## <a name="background"></a>背景  
 有了 `ToolStrip` 控制項以及與其相關聯的類別，您可以建立具有一致且專業的外觀和行為的進階工具列功能。 `ToolStrip` 控制項和類別透過先前的控制項提供下列改良功能：  
  
-   更一致的事件模型。  
  
-   更一致的設計階段行為，其中包含工作清單和項目集合編輯器。  
  
-   使用 `ToolStripManager` 和 `ToolStripRenderer` 來自訂轉譯。  
  
-   以 `ToolStripContainer` 和 `ToolStripPanel` 來進行內建浮動定位 (共用停駐時工具區域內的水平或垂直空間)。  
  
-   設計階段和執行階段具有 <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> 屬性的項目重新排列。  
  
-   項目重新配置到具有 <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> 屬性的溢位功能表。  
  
-   具有 `ToolStripContainer` 、 `ToolStripPanel` 與 `ToolStripContentPanel` 的完全可設定之控制位置。  
  
-   傳統的 `ToolStrip` 之裝載，或使用 `ToolStripControlHost` 的自訂控制項。  
  
-   合併使用 `ToolStripPanel` 的 `ToolStrip` 控制項。  
  
 `ToolStrip` 是可延伸的基底類別，如`MenuStrip`， `ContextMenuStrip`，和`StatusStrip`。 這些控制項是 <xref:System.Windows.Forms.ToolStripItem> 容器，它們繼承了一般行為和事件處理、擴充以便讓每個實作處理適合它的行為。 衍生自 <xref:System.Windows.Forms.ToolStripItem> 的控制項如下表所示。 基底 `ToolStrip` 類別處理繪製、 使用者輸入，以及這些控制項的拖放事件。  
  
 `ToolStrip` 、 `MenuStrip` 、 `ContextMenuStrip` 和 `StatusStrip` 控制項取代先前的工具列、 功能表、捷徑功能表和狀態列控制項，雖然這些控制項是被保留來確保回溯相容性。  
  
## <a name="toolstrip-classes-at-a-glance"></a>ToolStrip 類別簡介  
 下表顯示依技術領域分組的 ToolStrip 類別。  
  
|技術範圍|類別|  
|---------------------|-----------|  
|工具列、 狀態和功能表容器|<xref:System.Windows.Forms.ToolStrip><br /><br /> <xref:System.Windows.Forms.MenuStrip><br /><br /> <xref:System.Windows.Forms.ContextMenuStrip><br /><br /> <xref:System.Windows.Forms.StatusStrip><br /><br /> <xref:System.Windows.Forms.ToolStripDropDownMenu>|  
|ToolStrip 項目|<xref:System.Windows.Forms.ToolStripLabel><br /><br /> <xref:System.Windows.Forms.ToolStripDropDownItem><br /><br /> <xref:System.Windows.Forms.ToolStripMenuItem><br /><br /> <xref:System.Windows.Forms.ToolStripButton><br /><br /> <xref:System.Windows.Forms.ToolStripStatusLabel><br /><br /> <xref:System.Windows.Forms.ToolStripSeparator><br /><br /> <xref:System.Windows.Forms.ToolStripControlHost><br /><br /> <xref:System.Windows.Forms.ToolStripComboBox><br /><br /> <xref:System.Windows.Forms.ToolStripTextBox><br /><br /> <xref:System.Windows.Forms.ToolStripProgressBar><br /><br /> <xref:System.Windows.Forms.ToolStripDropDownButton><br /><br /> <xref:System.Windows.Forms.ToolStripSplitButton>|  
|位置|<xref:System.Windows.Forms.ToolStripContainer><br /><br /> <xref:System.Windows.Forms.ToolStripContentPanel><br /><br /> <xref:System.Windows.Forms.ToolStripPanel>|  
|展示和轉譯|<xref:System.Windows.Forms.ToolStripManager><br /><br /> <xref:System.Windows.Forms.ToolStripRenderer><br /><br /> <xref:System.Windows.Forms.ToolStripProfessionalRenderer><br /><br /> <xref:System.Windows.Forms.ToolStripRenderMode><br /><br /> <xref:System.Windows.Forms.ToolStripManagerRenderMode>|  
  
## <a name="toolstrip-design-time-features"></a>ToolStrip 設計階段功能  
 <xref:System.Windows.Forms.ToolStrip> 家族控制項提供一組豐富的工具和範本，它能夠就地編輯和定義使用者介面的基礎，讓您可以快速建立實用的應用程式。  
  
### <a name="task-dialog-boxes"></a>工作對話方塊  
 在 Visual Studio 中，按一下設計工具中控制項上的智慧標籤會顯示工作清單中，以便存取許多常用的命令。  
  
-   [MenuStrip 工作對話方塊](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233645(v=vs.100))  
  
-   [ToolStrip 工作對話方塊](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233648(v=vs.100))  
  
-   [ContextMenuStrip 工作對話方塊](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233646(v=vs.100))  
  
-   [StatusStrip 工作對話方塊](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233642(v=vs.100))  
  
-   [ToolStripContainer 工作對話方塊](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233647(v=vs.100))  
  
### <a name="items-collection-editors"></a>項目集合編輯器  
 在 Visual Studio 中，當您按一下 **編輯項目**工作清單，或以滑鼠右鍵按一下控制項，然後選取**編輯項目**在快顯功能表中，控制項的集合編輯器隨即出現。 集合編輯器可讓您新增、 移除和重新排列控制項包含的項目。 您也可以檢視和變更控制項與控制項項目的屬性。  
  
-   [MenuStrip 項目集合編輯器](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233625(v=vs.100))  
  
-   [StatusStrip 項目集合編輯器](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233631(v=vs.100))  
  
-   [ContextMenuStrip 項目集合編輯器](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233641(v=vs.100))  
  
-   [ToolStrip 項目集合編輯器](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233643(v=vs.100))  
  
## <a name="hosting-controls"></a>裝載控制項  
 <xref:System.Windows.Forms.ToolStripControlHost> 類別會提供內建的包裝函式給 <xref:System.Windows.Forms.ToolStripComboBox> 、 <xref:System.Windows.Forms.ToolStripTextBox> 和 <xref:System.Windows.Forms.ToolStripProgressBar> 控制項。 您也可以裝載任何其他現有或者 <xref:System.Windows.Forms.ToolStripControlHost> 中的 COM 控制項。  
  
 如需控制項裝載的範例，請參閱[How to:使用 ToolStripControlHost 為 Windows Form 控制項](how-to-wrap-a-windows-forms-control-with-toolstripcontrolhost.md)。  
  
## <a name="rendering"></a>正在轉譯  
 <xref:System.Windows.Forms.ToolStrip> 類別會實作明顯不同於其他的 Windows Form 控制項的轉譯配置。 透過這種配置，您可以輕鬆地套用樣式和主題。  
  
 要套用樣式到 <xref:System.Windows.Forms.ToolStrip> 和它所包含的所有 <xref:System.Windows.Forms.ToolStripItem> 物件，您不必針對每個項目處理 <xref:System.Windows.Forms.ToolStripItem.Paint> 事件。 相反地，您可以把 <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> 屬性設定為 <xref:System.Windows.Forms.ToolStripRenderMode.Custom> 以外任何一個 <xref:System.Windows.Forms.ToolStripRenderMode> 的值。 或者，您可以把 <xref:System.Windows.Forms.ToolStrip.Renderer%2A> 直接設定成繼承自 <xref:System.Windows.Forms.ToolStripRenderer> 類別的任何類別。 設定這個屬性會自動設定 <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>。  
  
 您可以將相同的樣式套用至多個相同的應用程式中的 <xref:System.Windows.Forms.ToolStrip> 物件，這可以藉由把 <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> 設定為 <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>以及分別把 <xref:System.Windows.Forms.ToolStripManager.RenderMode%2A> 或 <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> 屬性設定為您想要的 <xref:System.Windows.Forms.ToolStripManagerRenderMode> 或 <xref:System.Windows.Forms.ToolStripRenderer> 值。  
  
 例如轉譯的詳細資訊，請參閱[How to:建立並設定自訂轉譯器，Windows 中的 ToolStrip 控制項 form](create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)。  
  
## <a name="styles-and-themes"></a>樣式和主題  
 <xref:System.Windows.Forms.ToolStrip> 和相關聯的類別提供簡單的方法，來支援視覺化樣式，而且不需要覆寫的自訂外觀<xref:System.Windows.Forms.ToolStripItem.OnPaint%2A>每個項目的方法。 使用 <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>、<xref:System.Windows.Forms.ToolStrip.RenderMode%2A> 和 <xref:System.Windows.Forms.ToolStrip.Renderer%2A> 屬性。  
  
## <a name="rafting-and-docking"></a>浮動定位和停駐  
 您可以浮動定位、停駐或絕對定位 <xref:System.Windows.Forms.ToolStrip> 控制項。 <xref:System.Windows.Forms.ToolStrip> 項目會由配置<xref:System.Windows.Forms.ToolStrip.LayoutEngine%2A>的容器。  
  
 *浮動定位*乃是工具列共用水平或垂直空間。 Windows Form 的 <xref:System.Windows.Forms.ToolStripContainer> 可以反過來有個面板，它可以在表單的左邊、 右邊、 上方和下方，並且用來定位和浮動定位 <xref:System.Windows.Forms.ToolStrip> 、 <xref:System.Windows.Forms.MenuStrip> 和 <xref:System.Windows.Forms.StatusStrip> 控制項。 如果您將多個 <xref:System.Windows.Forms.ToolStrip> 控制項放在左邊或右邊 <xref:System.Windows.Forms.ToolStripContainer>，它們會垂直堆疊。 如果您將它們放在頂端或底端 <xref:System.Windows.Forms.ToolStripContainer>，它們會水平堆疊。 您可以使用 <xref:System.Windows.Forms.ToolStripContainer> 的中央 <xref:System.Windows.Forms.ToolStripContentPanel>來定位在表單上的傳統控制項。  
  
 任何或所有 <xref:System.Windows.Forms.ToolStripContainer> 控制項可直接在設計階段選取，而且可以刪除。 <xref:System.Windows.Forms.ToolStripContainer> 可展開及摺疊，並且可以使用它所包含的控制項調整大小。  
  
 *停駐*會指定表單的左邊、 右邊、 上方或下方的控制項的簡單位置。  
  
 透過停駐來浮動定位的優點在於 <xref:System.Windows.Forms.ToolStrip> 、 <xref:System.Windows.Forms.MenuStrip> 和 <xref:System.Windows.Forms.StatusStrip> 控制項可以與其他控制項共用水平或垂直空間。  
  
 大部分的 <xref:System.Windows.Forms.ToolStrip> 控制項能夠如同其他控制項被定位到表單，而不使用浮動定位。 您也可以藉由將 <xref:System.Windows.Forms.ToolStrip> 控制項從它的 <xref:System.Windows.Forms.ToolStripContainer> 移出並且將 `Dock` 屬性設定為 `None`， 來指定它放置在表單的任意位置上，或者藉由個別設定 <xref:System.Windows.Forms.Control.Location%2A> 屬性來指定它的絕對位置。 請參閱[如何：將移出 toolstripcontainer 並移到表單上 ToolStrip](how-to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form.md)。  
  
 使用一或多個 <xref:System.Windows.Forms.ToolStripPanel> 控制項來獲得更大的彈性，特別是針對多重文件介面 (MDI) 應用程式，或如果您不需要 <xref:System.Windows.Forms.ToolStripContainer>。 <xref:System.Windows.Forms.ToolStripPanel> 提供一個可停駐空間來定位及浮動定位除了傳統控制項的 <xref:System.Windows.Forms.ToolStrip> 控制項。 根據預設，<xref:System.Windows.Forms.ToolStripPanel>未出現在設計工具**工具箱**，但您可以用滑鼠右鍵按一下，讓它那里**工具箱**，然後按一下**選擇項目**。 您也以程式設計方式存取與 <xref:System.Windows.Forms.ToolStripPanel> 相似的任何其他類別。  
  
 <xref:System.Windows.Forms.ToolStrip> 、 <xref:System.Windows.Forms.MenuStrip> 和 <xref:System.Windows.Forms.StatusStrip> 讓項目溢位。 這與在 Microsoft Office 工具列上那些項目的使用方式類似。  
  
## <a name="see-also"></a>另請參閱

- [ToolStrip 控制項概觀](toolstrip-control-overview-windows-forms.md)
- [ToolStrip 控制項架構](toolstrip-control-architecture.md)
