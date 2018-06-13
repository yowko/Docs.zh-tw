---
title: 如何：在 TableLayoutPanel 控制項中對齊和縮放控制項
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor.TLP.AlignStretchCtrl
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms], stretching controls
- controls [Windows Forms], stretching
- controls [Windows Forms], aligning
ms.assetid: 7dc1a157-6fee-4995-8ebc-b65bdc0909a8
ms.openlocfilehash: 5abe233a240e74e41d4defad060383aec155ea71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529272"
---
# <a name="how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control"></a>如何：在 TableLayoutPanel 控制項中對齊和縮放控制項
您可以對齊和縮放控制項<xref:System.Windows.Forms.TableLayoutPanel>與<xref:System.Windows.Forms.Control.Anchor%2A>和<xref:System.Windows.Forms.Control.Dock%2A>屬性。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
### <a name="to-align-and-stretch-a-control"></a>若要對齊和縮放控制項  
  
1.  拖曳<xref:System.Windows.Forms.TableLayoutPanel>控制項從**工具箱**拖曳至表單。  
  
2.  拖曳<xref:System.Windows.Forms.Button>控制項從**工具箱**左上方儲存格的<xref:System.Windows.Forms.TableLayoutPanel>控制項。 <xref:System.Windows.Forms.Button>控制項置中於資料格。  
  
3.  值設定<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Anchor%2A>屬性`Left,Right`。 <xref:System.Windows.Forms.Button>控制兩端之間自動縮放以符合儲存格的寬度。  
  
4.  值設定<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Anchor%2A>屬性`Top,Bottom`。 <xref:System.Windows.Forms.Button>控制兩端之間自動縮放以符合資料格的高度。  
  
5.  值設定<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Dock%2A>屬性<xref:System.Windows.Forms.DockStyle.Fill>。 <xref:System.Windows.Forms.Button>控制展開並填滿資料格。  
  
6.  值設定<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Dock%2A>屬性<xref:System.Windows.Forms.DockStyle.None>。 <xref:System.Windows.Forms.Button>控制項傳回至其原始大小，並將移至儲存格的左上角。 **Windows Form 設計工具**已設定<xref:System.Windows.Forms.Control.Anchor%2A>屬性`Top, Left`。  
  
7.  值設定<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Anchor%2A>屬性`Bottom,Right`。 <xref:System.Windows.Forms.Button>控制項移到儲存格右下角。  
  
8.  值設定<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Anchor%2A>屬性<xref:System.Windows.Forms.AnchorStyles.None>。 <xref:System.Windows.Forms.Button>控制項移到儲存格中央。  
  
## <a name="see-also"></a>另請參閱  
 [TableLayoutPanel 控制項](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)
