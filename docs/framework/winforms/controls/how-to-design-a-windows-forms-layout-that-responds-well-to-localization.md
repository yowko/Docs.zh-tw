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
ms.openlocfilehash: c1aa62413e1c9cc29507b7b0ed5cbf1c5fcea26a
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928560"
---
# <a name="how-to-design-a-windows-forms-layout-that-responds-well-to-localization"></a>HOW TO：設計可適當回應當地語系化的 Windows Forms 配置
建立準備好當地語系化的表單，將會大幅加速開發國際市場。 您可以使用 <xref:System.Windows.Forms.TableLayoutPanel> 控制項來實作版面配置，當控制項因 <xref:System.Windows.Forms.Control.Text%2A> 屬性值變更而調整大小時，它會依正常程序回應。  
  
## <a name="example"></a>範例  
 在您翻譯顯示字串值為其他語言時，此表單會示範如何建立可按比例調整的版面配置。 這個翻譯的過程稱為「當地語系化」(localization)。 如需詳細資訊，請參閱[當地語系化](../../../standard/globalization-localization/localization.md)。  
  
 在 Visual Studio 中對於本工作有更詳盡的支援。  另請參閱逐步解說： [建立可調整比例以進行當地語系化](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100))的版面配置。  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/CS/localizableform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/VB/localizableform.vb#1)]  
  
## <a name="additional-resources"></a>其他資源

1. [如何：在 TableLayoutPanel 控制項中對齊和延展控制項](how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control.md)  
  
2. [逐步解說：使用 FlowLayoutPanel 排列 Windows Forms 上的控制項](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  

3. [如何：跨越 TableLayoutPanel 控制項中的資料列和資料行](how-to-span-rows-and-columns-in-a-tablelayoutpanel-control.md)  
  
4. [如何：編輯 TableLayoutPanel 控制項中的資料行和資料列](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)  
  
5. [逐步解說：在 Windows Forms 控制項上使用智慧標籤執行一般工作](performing-common-tasks-using-smart-tags-on-wf-controls.md)  
  
6. [逐步解說：使用 TableLayoutPanel 排列 Windows Forms 上的控制項](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  

7. [逐步解說：配置具有填補、邊界和 AutoSize 屬性的 Windows Forms 控制項](windows-forms-controls-padding-autosize.md)  
  
8. [如何：支援使用 AutoSize 和 TableLayoutPanel 控制項對 Windows Forms 進行當地語系化](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/1zkt8b33(v=vs.100))  
  
9. [逐步解說：建立可調整大小的 Windows Form 以進行資料輸入](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
- System、System.Data、System.Drawing 和 System.Windows.Forms 組件的參考。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
- [當地語系化](../../../standard/globalization-localization/localization.md)
