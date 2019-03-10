---
title: HOW TO：合併資料列和 TableLayoutPanel 控制項中的資料行
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor.TLP.SpanRowsColumns
helpviewer_keywords:
- columns [Windows Forms], spanning
- merging cells
- TableLayoutPanel control [Windows Forms], spanning rows and columns
- rows [Windows Forms], spanning
- cells [Windows Forms], merging
ms.assetid: a8a2fdd3-a848-48b0-a4cd-4e85ebded87e
ms.openlocfilehash: e4fc00c3966d44ba36a0c59b37ae2fa1cd431014
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703032"
---
# <a name="how-to-span-rows-and-columns-in-a-tablelayoutpanel-control"></a>HOW TO：合併資料列和 TableLayoutPanel 控制項中的資料行
中的控制項<xref:System.Windows.Forms.TableLayoutPanel>控制項可以跨越相鄰的資料列和資料行。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-span-columns-and-rows"></a>若要擴展資料行和資料列  
  
1.  從 [工具箱] <xref:System.Windows.Forms.TableLayoutPanel>**將** 控制項拖曳至表單。  
  
2.  拖曳<xref:System.Windows.Forms.Button>控制項從**工具箱**的左上方儲存格中<xref:System.Windows.Forms.TableLayoutPanel>控制項。  
  
3.  設定<xref:System.Windows.Forms.Button>控制項的**ColumnSpan**屬性設**2**。 請注意，<xref:System.Windows.Forms.Button>控制項跨越的第一個和第二個資料行。  
  
4.  設定<xref:System.Windows.Forms.Button>控制項的**RowSpan**屬性設**2**。 請注意，<xref:System.Windows.Forms.Button>控制項跨越的第一個和第二個資料列。  
  
5.  設定<xref:System.Windows.Forms.Button>控制項的**ColumnSpan**屬性設**1**。 請注意，<xref:System.Windows.Forms.Button>控制項將移至第一個資料行，而且跨越的第一個和第二個資料列。  
  
## <a name="see-also"></a>另請參閱
- [TableLayoutPanel 控制項](tablelayoutpanel-control-windows-forms.md)
