---
title: 逐步解說：向表單提供標準的功能表項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- menu items [Windows Forms], standard
- toolbars [Windows Forms], walkthroughs
- StatusStrip control [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: dac37d98-589e-4d6d-9673-6437e8943122
ms.openlocfilehash: ebfacadfee3ea069359a72ea0402751e9e6280d7
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211509"
---
# <a name="walkthrough-providing-standard-menu-items-to-a-form"></a>逐步解說：向表單提供標準的功能表項目

您可以使用 <xref:System.Windows.Forms.MenuStrip> 控制項來為您的表單提供標準功能表。

本逐步解說示範如何使用<xref:System.Windows.Forms.MenuStrip>控制項來建立標準功能表。 當使用者選取功能表項目，也會回應格式。 本逐步解說會說明下列工作：

- 建立 Windows Forms 專案。

- 建立標準功能表。

- 建立<xref:System.Windows.Forms.StatusStrip>控制項。

- 處理功能表項目選取項目。

當您完成時，您必須具有標準功能表會顯示功能表項目中的選取項目表單<xref:System.Windows.Forms.StatusStrip>控制項。

若要將此主題中的程式碼複製為單一清單，請參閱[如何：對表單提供標準功能表項目](how-to-provide-standard-menu-items-to-a-form.md)。

## <a name="prerequisites"></a>必要條件

您將需要 Visual Studio 來完成此逐步解說。

## <a name="create-the-project"></a>建立專案

1. 在 Visual Studio 中建立名為 Windows 應用程式專案**StandardMenuForm** (**檔案** > **新增** > **專案**  > **視覺化C#** 或是**Visual Basic** > **傳統桌面** >  **Windows Forms 應用程式**)。

2. 在 Windows Form 設計工具中，選取的表單。

## <a name="create-a-standard-menu"></a>建立標準功能表

Windows Form 設計工具可以自動填入<xref:System.Windows.Forms.MenuStrip>具有標準功能表項目控制項。

1. 從**工具箱**，拖曳<xref:System.Windows.Forms.MenuStrip>控制項拖曳至表單。

2. 按一下 <xref:System.Windows.Forms.MenuStrip>控制項的智慧標籤圖像 （glyph) (![智慧標籤圖像](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))，然後選取**插入標準項目**。

     <xref:System.Windows.Forms.MenuStrip>控制項填入標準功能表項目。

3. 按一下 **檔案**功能表項目，以查看其預設功能表項目和對應的圖示。

## <a name="create-a-statusstrip-control"></a>建立 StatusStrip 控制項

使用<xref:System.Windows.Forms.StatusStrip>控制項來顯示 Windows Forms 應用程式的狀態。 在目前的範例中，使用者所選取的功能表項目會顯示在<xref:System.Windows.Forms.StatusStrip>控制項。

1. 從**工具箱**，拖曳<xref:System.Windows.Forms.StatusStrip>控制項拖曳至表單。

     <xref:System.Windows.Forms.StatusStrip>控制項自動停駐於表單底部。

2. 按一下 <xref:System.Windows.Forms.StatusStrip>控制項的下拉式按鈕，然後選取**statuslabel 設**以新增<xref:System.Windows.Forms.ToolStripStatusLabel>若要控制<xref:System.Windows.Forms.StatusStrip>控制項。

## <a name="handle-item-selection"></a>處理項目選取

處理<xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked>事件以回應使用者選取功能表項目時。

1. 按一下 **檔案**功能表項目，您在 「 建立中建立標準功能表一節。

2. 在 [屬性] 視窗中按一下 [事件]。

3. 按兩下<xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked>事件。

     Windows Form 設計工具產生的事件處理常式<xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked>事件。

4. 事件處理常式中插入下列程式碼。

     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#3)]

5. 插入`UpdateStatus`在表單的公用程式方法定義。

     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#2)]

## <a name="checkpoint--test-your-form"></a>檢查點-測試您的表單

1. 按下**F5**編譯及執行您的表單。

2. 按一下 **檔案**以開啟功能表的功能表項目。

3. 在 [**檔案**] 功能表中，按一下其中一個項目，即可選取它。

     <xref:System.Windows.Forms.StatusStrip>控制項會顯示選取的項目。

## <a name="next-steps"></a>後續步驟

在本逐步解說中，您已建立具有標準功能表的表單。 您可以使用<xref:System.Windows.Forms.ToolStrip>用於許多其他用途的控制項系列：

- 建立您的控制項使用的快顯功能表<xref:System.Windows.Forms.ContextMenuStrip>。 如需詳細資訊，請參閱 < [ContextMenu 元件概觀](contextmenu-component-overview-windows-forms.md)。

- 建立多個文件介面 (MDI) 表單使用停駐<xref:System.Windows.Forms.ToolStrip>控制項。 如需詳細資訊，請參閱[逐步解說：使用功能表合併和 ToolStrip 控制項建立 MDI 表單](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md)。

- 提供您<xref:System.Windows.Forms.ToolStrip>控制項專業外觀。 如需詳細資訊，請參閱[如何：設定應用程式的 ToolStrip 產生器](how-to-set-the-toolstrip-renderer-for-an-application.md)。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [MenuStrip 控制項](menustrip-control-windows-forms.md)
