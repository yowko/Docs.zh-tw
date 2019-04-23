---
title: HOW TO：設計可適當回應當地語系化的 Windows Forms 配置
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms]
- application design [Windows Forms], localization
- Windows Forms, localization
- localization [Windows Forms], Windows Forms layout
ms.assetid: d13eff2d-701c-4b6e-8838-3885cbfb7223
ms.openlocfilehash: 131dc688d2a742fa7a0d99ec7858d4e280c9882f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59310755"
---
# <a name="how-to-design-a-windows-forms-layout-that-responds-well-to-localization"></a>HOW TO：設計可適當回應當地語系化的 Windows Forms 配置
建立準備好當地語系化的表單，將會大幅加速開發國際市場。 您可以使用 <xref:System.Windows.Forms.TableLayoutPanel> 控制項來實作版面配置，當控制項因 <xref:System.Windows.Forms.Control.Text%2A> 屬性值變更而調整大小時，它會依正常程序回應。  
  
## <a name="example"></a>範例  
 在您翻譯顯示字串值為其他語言時，此表單會示範如何建立可按比例調整的版面配置。 這個翻譯的過程稱為「當地語系化」(localization)。 如需詳細資訊，請參閱[當地語系化](../../../standard/globalization-localization/localization.md)。  
  
 在 Visual Studio 中對於本工作有更詳盡的支援。  另請參閱[逐步解說：建立版面配置調整比例以配合當地語系化](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100))。  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/CS/localizableform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/VB/localizableform.vb#1)]  
  
## <a name="additional-resources"></a>其他資源
1. [如何：對齊和縮放 TableLayoutPanel 控制項中的控制項](how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control.md)  
  
2. [逐步解說：排列 Windows Form 使用 FlowLayoutPanel 控制項](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  

3. [如何：合併資料列和 TableLayoutPanel 控制項中的資料行](how-to-span-rows-and-columns-in-a-tablelayoutpanel-control.md)  
  
4. [如何：編輯資料行和 TableLayoutPanel 控制項中的資料列](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)  
  
5. [逐步解說：一般工作，使用智慧標籤執行 Windows Form 控制項](performing-common-tasks-using-smart-tags-on-wf-controls.md)  
  
6. [逐步解說：排列 Windows Form 使用 TableLayoutPanel 控制項](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  

7. [逐步解說：配置 Windows Form 控制項和邊框距離、 邊界和 AutoSize 屬性](windows-forms-controls-padding-autosize.md)  
  
8. [如何：支援使用 AutoSize 和 TableLayoutPanel 控制項的 Windows Form 的當地語系化](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/1zkt8b33(v=vs.100))  
  
9. [逐步解說：建立適用於資料輸入且可調整大小的 Windows Form](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   System、System.Data、System.Drawing 和 System.Windows.Forms 組件的參考。  
  
 Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。 您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
- [當地語系化](../../../standard/globalization-localization/localization.md)
