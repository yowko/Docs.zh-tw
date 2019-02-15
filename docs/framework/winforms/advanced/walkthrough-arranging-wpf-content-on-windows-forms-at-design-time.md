---
title: 逐步解說：在設計階段排列 Windows Form 的 WPF 內容
ms.date: 03/30/2017
helpviewer_keywords:
- WPF user control [Windows Forms], hosting in a layout panel
- WPF content [Windows Forms], arranging at design time
- Windows Forms, arranging WPF content at design time
- WPF content [Windows Forms], hosting in Windows Forms
- Windows Forms, anchoring and docking WPF content
- interoperability [WPF]
ms.assetid: 5efb1c53-1484-43d6-aa8a-f4861b99bb8a
ms.openlocfilehash: 543546de4f9b93deb5fa70c98608246e9c06e4f7
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/15/2019
ms.locfileid: "56304553"
---
# <a name="walkthrough-arranging-wpf-content-on-windows-forms-at-design-time"></a>逐步解說：在設計階段排列 Windows Form 的 WPF 內容
本逐步解說示範如何使用 Windows Form 的配置功能 (例如錨定和對齊線)，來排列 Windows Presentation Foundation (WPF) 控制項。

 在這個逐步解說中，您將執行下列工作：

-   建立專案。

-   建立 WPF 控制項。

-   將 WPF 控制項裝載到配置面板中。

-   使用對齊線來對齊 WPF 控制項。

-   錨定和停駐 WPF 控制項。

> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   Visual Studio 2012.  
  
## <a name="creating-the-project"></a>建立專案  
 第一個步驟是建立 Windows Form 專案。  
  
> [!NOTE]
>  裝載 WPF 內容時，只支援 C# 和 Visual Basic 專案。  
  
#### <a name="to-create-the-project"></a>若要建立專案  
  
-   建立新的 Windows Forms 應用程式專案在 Visual Basic 或 Visual C# 中名為`ArrangeElementHost`。  
  
## <a name="creating-the-wpf-control"></a>建立 WPF 控制項  
 在將 WPF 控制項加入專案後，即可在表單上予以排列。  
  
#### <a name="to-create-wpf-controls"></a>建立 WPF 控制項  
  
1.  將新的 WPF <xref:System.Windows.Controls.UserControl> 加入專案。 使用控制項類型的預設名稱 `UserControl1.xaml`。 如需詳細資訊，請參閱[逐步解說：在設計階段建立 Windows Form 上的新 WPF 內容](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)。  
  
2.  在 [設計] 檢視中，確定已選取 `UserControl1`。 如需詳細資訊，請參閱[如何：選取並移動設計介面上的項目](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100))。  
  
3.  在 **屬性**視窗中，設定的值<xref:System.Windows.FrameworkElement.Width%2A>並<xref:System.Windows.FrameworkElement.Height%2A>屬性，以`200`。  
  
4.  將 <xref:System.Windows.Controls.Control.Background%2A> 屬性值設定為 `Blue`。  
  
5.  建置專案。  
  
## <a name="hosting-wpf-controls-in-a-layout-panel"></a>將 WPF 控制項裝載到配置面板中  
 您可以使用與其他 Windows Form 控制項相同的方式，在配置面板中使用 WPF 控制項。  
  
#### <a name="to-host-wpf-controls-in-a-layout-panel"></a>將 WPF 控制項裝載到配置面板中  
  
1.  在 Windows Form 設計工具中開啟 `Form1`。  
  
2.  在 **工具箱**，拖曳<xref:System.Windows.Forms.TableLayoutPanel>控制項拖曳至表單。  
  
3.  在 <xref:System.Windows.Forms.TableLayoutPanel>控制項的智慧標籤面板中，選取**移除最後一個資料列**。  
  
4.  將 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的大小調整為更寬且更高的大小。  
  
5.  在 **工具箱**，按兩下`UserControl1`若要建立的執行個體`UserControl1`的第一個資料格中<xref:System.Windows.Forms.TableLayoutPanel>控制項。  
  
     
  `UserControl1` 的執行個體會裝載到名為 `elementHost1` 的新 <xref:System.Windows.Forms.Integration.ElementHost> 控制項中。  
  
6.  在**工具箱**，按兩下`UserControl1`建立另一個執行個體中的第二個儲存格<xref:System.Windows.Forms.TableLayoutPanel>控制項。  
  
7.  在 **文件大綱**視窗中，選取`tableLayoutPanel1`。 如需詳細資訊，請參閱 <<c0> [ 文件大綱 視窗](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/46xf4h0w(v=vs.100)#using-the-document-outline-window-for-silverlight-and-wpf)。  
  
8.  在 **屬性**視窗中，設定的值<xref:System.Windows.Forms.Control.Padding%2A>屬性設`10, 10, 10, 10`。  
  
     兩個 <xref:System.Windows.Forms.Integration.ElementHost> 控制項的大小會調整以配合新的配置。  
  
## <a name="using-snaplines-to-align-wpf-controls"></a>使用對齊線來對齊 WPF 控制項  
 對齊線可讓您輕鬆對齊表單上的控制項。 您也可以使用對齊線來對齊 WPF 控制項。 如需詳細資訊，請參閱[逐步解說：排列控制項，在 Windows Form 使用對齊線](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)。  
  
#### <a name="to-use-snaplines-to-align-wpf-controls"></a>使用對齊線來對齊 WPF 控制項  
  
1.  從**工具箱**，將拖曳的執行個體`UserControl1`拖曳至表單並將它放在下方的空間<xref:System.Windows.Forms.TableLayoutPanel>控制項。  
  
     
  `UserControl1` 的執行個體會裝載到名為 `elementHost3` 的新 <xref:System.Windows.Forms.Integration.ElementHost> 控制項中。  
  
2.  使用對齊線，將 `elementHost3` 的左邊緣與 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的左邊緣對齊。  
  
3.  使用對齊線，將 `elementHost3` 的大小調整成與 <xref:System.Windows.Forms.TableLayoutPanel> 控制項同寬。  
  
4.  將 `elementHost3` 往 <xref:System.Windows.Forms.TableLayoutPanel> 控制項方向移動，直到中央對齊線出現在兩個控制項之間為止。  
  
5.  在 **屬性**視窗中，將 Margin 屬性的值`20, 20, 20, 20`。  
  
6.  將 `elementHost3` 往 <xref:System.Windows.Forms.TableLayoutPanel> 控制項反方向移動，直到中央對齊線再度出現為止。 中央對齊線現在表示邊界 20。  
  
7.  將 `elementHost3` 向右移，直到其左邊緣與 `elementHost1` 的左邊緣對齊為止。  
  
8.  變更 `elementHost3` 的寬度，直到其右邊緣與 `elementHost2` 的右邊緣對齊為止。  
  
## <a name="anchoring-and-docking-wpf-controls"></a>錨定和停駐 WPF 控制項  
 裝載於表單上之 WPF 控制項的錨定和停駐行為，與其他 Windows Form 控制項相同。  
  
#### <a name="to-anchor-and-dock-wpf-controls"></a>錨定和停駐 WPF 控制項  
  
1.  選取 `elementHost1`。  
  
2.  在 **屬性**視窗中，將<xref:System.Windows.Forms.Control.Anchor%2A>屬性設**上、 下、 Left、 Right**。  
  
3.  將 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的大小調整為更大的大小。  
  
     `elementHost1` 控制項會調整大小以填滿儲存格。  
  
4.  選取 `elementHost2`。  
  
5.  在 **屬性**視窗中，設定的值<xref:System.Windows.Forms.Control.Dock%2A>屬性設<xref:System.Windows.Forms.DockStyle.Fill>。  
  
     
  `elementHost2` 控制項會調整大小以填滿儲存格。  
  
6.  選取 <xref:System.Windows.Forms.TableLayoutPanel> 控制項。  
  
7.  將其 <xref:System.Windows.Forms.Control.Dock%2A> 屬性的值設定為 <xref:System.Windows.Forms.DockStyle.Top>。  
  
8.  選取 `elementHost3`。  
  
9. 將其 <xref:System.Windows.Forms.Control.Dock%2A> 屬性的值設定為 <xref:System.Windows.Forms.DockStyle.Fill>。  
  
     `elementHost3` 控制項會調整大小以填滿表單上的剩餘空間。  
  
10. 調整表單的大小。  
  
     這三個 <xref:System.Windows.Forms.Integration.ElementHost> 控制項都會適當地調整大小。  
  
     如需詳細資訊，請參閱[如何：錨定和停駐 TableLayoutPanel 控制項中的子控制項](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [如何：錨定和停駐 TableLayoutPanel 控制項中的子控制項](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [如何：將控制項和表單邊緣對齊在設計階段](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)
- [逐步解說：使用對齊線的 Windows Form 上排列控制項](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [移轉和互通性](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)
- [使用 WPF 控制項](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)
- [在 Visual Studio 中設計 XAML](/visualstudio/designers/designing-xaml-in-visual-studio)
