---
title: HOW TO：重新指派至不同的父代的現有控制項
ms.date: 03/30/2017
helpviewer_keywords:
- container controls [Windows Forms], Windows Forms
- layout [Windows Forms], resizing
- layout [Windows Forms], child controls
ms.assetid: 5a5723ff-34e0-4b6f-a57b-be4ebe35cb34
ms.openlocfilehash: 650d10fd681a55dfb17425111ef9d81726551da9
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720182"
---
# <a name="how-to-reassign-existing-controls-to-a-different-parent"></a>HOW TO：重新指派至不同的父代的現有控制項
您可以將表單上現有的控制項指派給新的容器控制項。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-reassign-existing-controls-to-a-different-parent"></a>將現有控制項重新指派至不同的父代  
  
1.  從 [工具箱] <xref:System.Windows.Forms.Button>**將三個** 控制項拖曳至表單。  
  
     將它們放在相鄰的位置，但不要對齊。  
  
2.  按一下 [工具箱] 的 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項圖示。  
  
     請勿將圖示拖曳到表單上。  
  
3.  將滑鼠指標靠近三個 <xref:System.Windows.Forms.Button> 控制項。  
  
     指標會變成十字形狀並附有 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項圖示。  
  
4.  按住滑鼠按鈕。  
  
5.  拖曳滑鼠指標以繪製 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項的外框。  
  
6.  繪製三個 <xref:System.Windows.Forms.Button> 控制項的外框。  
  
7.  放開滑鼠按鈕。  
  
     三個 <xref:System.Windows.Forms.Button> 控制項現在都已插入 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項中。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [排列 Windows Forms 上的控制項](arranging-controls-on-windows-forms.md)
- [逐步解說：排列 Windows Form 使用 TableLayoutPanel 控制項](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [逐步解說：使用對齊線的 Windows Form 上排列控制項](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
