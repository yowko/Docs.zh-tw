---
title: 作法：使用設計工具重新調整 Windows Forms DataGridView 控制項的資料行順序
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], column order
- Windows Forms, columns
- columns [Windows Forms], reordering
- data [Windows Forms], displaying
ms.assetid: d82bd69c-6799-4439-a32c-91139c5901d1
ms.openlocfilehash: 3864ce70f058259b597df904311bd4a48218b151
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040352"
---
# <a name="how-to-enable-column-reordering-in-the-windows-forms-datagridview-control-using-the-designer"></a>HOW TO：使用設計工具重新調整 Windows Forms DataGridView 控制項的資料行順序
當您查看 Windows Forms <xref:System.Windows.Forms.DataGridView>控制項中顯示的資料時, 使用者有時會想要比較特定資料行中的值。 如果資料行廣泛地在控制項中區隔, 這可能不方便, 特別是當使用者必須水準來回滾動, 才能查看他們感興趣的所有資料行時。 您可以讓使用者重新排列資料行, 以更輕鬆地比較資料行值。 當您啟用資料行重新調整時, 使用者可以使用滑鼠拖曳資料行標頭, 將資料行移至新位置。

 下列程式需要具有包含<xref:System.Windows.Forms.DataGridView>控制項之表單的**Windows 應用程式**專案。 如需設定這類專案的相關資訊, [請參閱如何:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project) , [以及如何:將控制項新增至](how-to-add-controls-to-windows-forms.md)Windows Forms。

## <a name="to-enable-column-reordering"></a>啟用資料行重新排列

- 按一下控制項右上角的智慧標籤圖像 (![智慧標籤]圖像(./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")), 然後選取 [ <xref:System.Windows.Forms.DataGridView> **啟用資料行重新排列**]。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType>
- [如何：使用設計工具凍結 Windows Forms DataGridView 控制項中的資料行](freeze-columns-in-the-datagrid-using-the-designer.md)
- [如何：建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [如何：將控制項新增至 Windows Forms](how-to-add-controls-to-windows-forms.md)
