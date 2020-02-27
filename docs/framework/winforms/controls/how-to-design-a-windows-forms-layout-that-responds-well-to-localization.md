---
title: 設計容易當地語系化的版面配置
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
ms.openlocfilehash: 9556c03699713b7d14f81a6eacc8e4ab337e869b
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628627"
---
# <a name="how-to-design-a-windows-forms-layout-that-responds-well-to-localization"></a>如何：設計可適當回應當地語系化的 Windows Form 配置
建立準備好當地語系化的表單，將會大幅加速開發國際市場。 您可以使用 <xref:System.Windows.Forms.TableLayoutPanel> 控制項來實作版面配置，當控制項因 <xref:System.Windows.Forms.Control.Text%2A> 屬性值變更而調整大小時，它會依正常程序回應。

## <a name="example"></a>範例
 在您翻譯顯示字串值為其他語言時，此表單會示範如何建立可按比例調整的版面配置。 這個翻譯的過程稱為「當地語系化」(localization)。 如需詳細資訊，請參閱[當地語系化](../../../standard/globalization-localization/localization.md)。

 在 Visual Studio 中對於本工作有更詳盡的支援。  另請參閱[逐步解說：建立可調整比例以配合當地語系化的配置](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100))。

 [!code-csharp[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/CS/localizableform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/VB/localizableform.vb#1)]

## <a name="additional-resources"></a>其他資源

1. [如何：在 TableLayoutPanel 控制項中對齊和縮放控制項](how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control.md)

2. [逐步解說：使用 FlowLayoutPanel 排列 Windows Forms上的控制項](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)

3. [操作說明：擴展 TableLayoutPanel 控制項中的資料列和資料行](how-to-span-rows-and-columns-in-a-tablelayoutpanel-control.md)

4. [操作說明：編輯 TableLayoutPanel 控制項中的資料行和資料列](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)

5. [逐步解說：使用設計工具動作執行一般工作](perform-common-tasks-design-actions.md)

6. [逐步解說：使用 TableLayoutPanel 排列 Windows Forms 上的控制項](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)

7. [逐步解說：使用邊框距離、邊界和 AutoSize 屬性配置 Windows Forms 控制項](windows-forms-controls-padding-autosize.md)

8. [如何‎：使用 AutoSize 和 TableLayoutPanel 控制項支援 Windows Forms 的當地語系化](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/1zkt8b33(v=vs.100))

9. [逐步解說：建立適用於資料輸入且可調整大小的 Windows Form](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))

## <a name="compiling-the-code"></a>編譯程式碼
 這個範例需要：

- System、System.Data、System.Drawing 和 System.Windows.Forms 組件的參考。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
- [當地語系化](../../../standard/globalization-localization/localization.md)
