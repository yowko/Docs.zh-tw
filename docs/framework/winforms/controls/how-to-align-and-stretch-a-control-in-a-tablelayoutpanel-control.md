---
title: HOW TO：在 TableLayoutPanel 控制項中對齊和縮放控制項
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor.TLP.AlignStretchCtrl
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms], stretching controls
- controls [Windows Forms], stretching
- controls [Windows Forms], aligning
ms.assetid: 7dc1a157-6fee-4995-8ebc-b65bdc0909a8
ms.openlocfilehash: c0bcf91d358d233b5b1d2e300d63112303e87a09
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59095396"
---
# <a name="how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control"></a>HOW TO：在 TableLayoutPanel 控制項中對齊和縮放控制項
您可以對齊和縮放控制項<xref:System.Windows.Forms.TableLayoutPanel>具有<xref:System.Windows.Forms.Control.Anchor%2A>和<xref:System.Windows.Forms.Control.Dock%2A>屬性。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-align-and-stretch-a-control"></a>若要對齊和縮放控制項  
  
1.  從 [工具箱] <xref:System.Windows.Forms.TableLayoutPanel>**將** 控制項拖曳至表單。  
  
2.  拖曳<xref:System.Windows.Forms.Button>控制項從**工具箱**的左上方儲存格中<xref:System.Windows.Forms.TableLayoutPanel>控制項。 <xref:System.Windows.Forms.Button>控制項在儲存格中置中對齊。  
  
3.  設定的值<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Anchor%2A>屬性設`Left,Right`。 <xref:System.Windows.Forms.Button>控制兩端之間自動縮放以符合儲存格的寬度。  
  
4.  設定的值<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Anchor%2A>屬性設`Top,Bottom`。 <xref:System.Windows.Forms.Button>控制兩端之間自動縮放以符合資料格的高度。  
  
5.  設定的值<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Dock%2A>屬性設<xref:System.Windows.Forms.DockStyle.Fill>。 <xref:System.Windows.Forms.Button>展開以填滿儲存格的控制項。  
  
6.  設定的值<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Dock%2A>屬性設<xref:System.Windows.Forms.DockStyle.None>。 <xref:System.Windows.Forms.Button>控制項傳回至其原始大小，並將移至儲存格的左上角。 **Windows Form 設計工具**已設定<xref:System.Windows.Forms.Control.Anchor%2A>屬性設`Top, Left`。  
  
7.  設定的值<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Anchor%2A>屬性設`Bottom,Right`。 <xref:System.Windows.Forms.Button>控制項移到儲存格右下角。  
  
8.  設定的值<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Anchor%2A>屬性設<xref:System.Windows.Forms.AnchorStyles.None>。 <xref:System.Windows.Forms.Button>控制項移到儲存格的中央。  
  
## <a name="see-also"></a>另請參閱

- [TableLayoutPanel 控制項](tablelayoutpanel-control-windows-forms.md)
