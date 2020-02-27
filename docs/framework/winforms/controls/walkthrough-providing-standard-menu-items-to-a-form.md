---
title: 逐步解說：對表單提供標準功能表項目
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
ms.openlocfilehash: ee80aad445c00bb4b98b49c80495fa512150bcef
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628770"
---
# <a name="walkthrough-providing-standard-menu-items-to-a-form"></a>逐步解說：對表單提供標準功能表項目

您可以使用 <xref:System.Windows.Forms.MenuStrip> 控制項來為您的表單提供標準功能表。

本逐步解說示範如何使用 <xref:System.Windows.Forms.MenuStrip> 控制項來建立標準功能表。 當使用者選取功能表項目時，表單會也會回應。 本逐步解說將說明下列工作：

- 建立 Windows Forms 專案。

- 建立標準功能表。

- 建立 <xref:System.Windows.Forms.StatusStrip> 控制項。

- 處理功能表項目選取專案。

當您完成時，您將會有一個具有標準功能表的表單，以顯示 <xref:System.Windows.Forms.StatusStrip> 控制項中的功能表項目選取專案。

若要將本主題中的程式碼複製成單一清單，請參閱[如何：將標準功能表項目提供給表單](how-to-provide-standard-menu-items-to-a-form.md)。

## <a name="prerequisites"></a>Prerequisites

您將需要 Visual Studio 才能完成此逐步解說。

## <a name="create-the-project"></a>建立專案

1. 在 Visual Studio 中，建立稱為**StandardMenuForm**的 Windows 應用程式專案（**檔案 > ** **新增** > **專案** > **Visual C#** 或**Visual Basic** > **傳統桌面** > **Windows Forms 應用程式**）。

2. 在 Windows Form 設計工具中，選取表單。

## <a name="create-a-standard-menu"></a>建立標準功能表

Windows Form 設計工具可以使用標準功能表項目，自動填入 <xref:System.Windows.Forms.MenuStrip> 控制項。

1. 從 [**工具箱**] 將 [<xref:System.Windows.Forms.MenuStrip>] 控制項拖曳至表單上。

2. 按一下 <xref:System.Windows.Forms.MenuStrip> 控制項的設計工具動作圖像（![小型黑色箭號](./media/designer-actions-glyph.gif)），然後選取 [**插入標準專案**]。

     [<xref:System.Windows.Forms.MenuStrip>] 控制項會以標準功能表項目填入。

3. 按一下 [檔案] 功能表**項，以**查看其預設功能表項目和對應的圖示。

## <a name="create-a-statusstrip-control"></a>建立 StatusStrip 控制項

使用 [<xref:System.Windows.Forms.StatusStrip>] 控制項來顯示 Windows Forms 應用程式的狀態。 在目前的範例中，使用者選取的功能表項目會顯示在 <xref:System.Windows.Forms.StatusStrip> 控制項中。

1. 從 [**工具箱**] 將 [<xref:System.Windows.Forms.StatusStrip>] 控制項拖曳至表單上。

     <xref:System.Windows.Forms.StatusStrip> 控制項會自動停駐在表單底部。

2. 按一下 [<xref:System.Windows.Forms.StatusStrip>] 控制項的下拉式按鈕，然後選取 [ **StatusLabel** ] 將 <xref:System.Windows.Forms.ToolStripStatusLabel> 控制項加入至 [<xref:System.Windows.Forms.StatusStrip>] 控制項。

## <a name="handle-item-selection"></a>處理專案選取

處理當使用者選取功能表項目時所要回應的 <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> 事件。

1. 按一下您在建立標準功能表一節中建立**的 [檔案**] 功能表項目。

2. 在 [屬性] 視窗中按一下 [事件]。

3. 按兩下 [<xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked>] 事件。

     Windows Form 設計工具會產生 <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> 事件的事件處理常式。

4. 將下列程式碼插入事件處理常式。

     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#3)]

5. 將 `UpdateStatus` 公用程式方法定義插入表單中。

     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#2)]

## <a name="checkpoint--test-your-form"></a>檢查點-測試您的表單

1. 按**F5**以編譯並執行您的表單。

2. 按一下 [檔案 **] 功能表項目**以開啟功能表。

3. **在 [檔案] 功能表上**，按一下其中一個專案來選取它。

     <xref:System.Windows.Forms.StatusStrip> 控制項會顯示選取的專案。

## <a name="next-steps"></a>後續步驟

在此逐步解說中，您已建立具有標準功能表的表單。 您可以將 <xref:System.Windows.Forms.ToolStrip> 系列控制項用於其他許多用途：

- 使用 <xref:System.Windows.Forms.ContextMenuStrip>建立控制項的快捷方式功能表。 如需詳細資訊，請參閱[CoNtextMenu 元件總覽](contextmenu-component-overview-windows-forms.md)。

- 建立具有固定 <xref:System.Windows.Forms.ToolStrip> 控制項的多重文件介面（MDI）表單。 如需詳細資訊，請參閱[逐步解說：使用功能表合併和 ToolStrip 控制項建立 MDI 表單](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md)。

- 為您的 <xref:System.Windows.Forms.ToolStrip> 控制項提供專業的外觀。 如需詳細資訊，請參閱[如何：設定應用程式的 ToolStrip](how-to-set-the-toolstrip-renderer-for-an-application.md)轉譯器。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [MenuStrip 控制項](menustrip-control-windows-forms.md)
