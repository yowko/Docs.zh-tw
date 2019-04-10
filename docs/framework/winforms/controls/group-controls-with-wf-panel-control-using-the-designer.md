---
title: HOW TO：使用設計工具以 Windows Forms Panel 控制項分組控制項
ms.date: 03/30/2017
helpviewer_keywords:
- Panel control [Windows Forms], grouping controls
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
ms.assetid: 7e1cd708-fdb1-49d8-9ca2-5640b276bf2e
ms.openlocfilehash: 1a3fcac56df1328c12d7a5dcb542138afdb486f5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59214828"
---
# <a name="how-to-group-controls-with-the-windows-forms-panel-control-using-the-designer"></a>HOW TO：使用設計工具以 Windows Forms Panel 控制項分組控制項
Windows Form<xref:System.Windows.Forms.Panel>控制項用來分組其他控制項。 有三個群組控制項的原因。 其中一個是視覺化群組相關的表單項目，清楚的使用者介面;另一個是以程式設計方式分組，選項按鈕： 例如，最後一個適用於在設計階段將控制項移動做為一個單位。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-create-a-group-of-controls"></a>若要建立的控制項群組  
  
1.  拖曳<xref:System.Windows.Forms.Panel>控制項從**Windows Forms**  索引標籤的 工具箱 拖曳至表單。  
  
2.  將其他控制項加入窗格中，每個面板內繪製。  
  
     如果您有現有的控制項，您想要包圍的面板中，您可以選取所有的控制項，它們剪到 剪貼簿上，選取<xref:System.Windows.Forms.Panel>控制項，然後再將它們貼到 面板 中。 您也可以將它們拖曳至面板。  
  
3.  （選擇性）如果您想要將框線加入至面板，設定其<xref:System.Windows.Forms.BorderStyle>屬性。 有三種選擇： <xref:System.Windows.Forms.BorderStyle.Fixed3D>， <xref:System.Windows.Forms.BorderStyle.FixedSingle>，和<xref:System.Windows.Forms.BorderStyle.None>。  
  
## <a name="see-also"></a>另請參閱

- [Panel 控制項](panel-control-windows-forms.md)
- [Panel 控制項概觀](panel-control-overview-windows-forms.md)
- [HOW TO：設定面板背景](how-to-set-the-background-of-a-windows-forms-panel.md)
