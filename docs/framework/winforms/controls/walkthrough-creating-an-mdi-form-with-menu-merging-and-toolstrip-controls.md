---
title: 逐步解說：使用功能表合併和 ToolStrip 控制項建立 MDI 表單
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripPanel control [Windows Forms]
- MDI [Windows Forms], creating forms
- multiple document interface forms
- MDI forms
- ToolStrip control [Windows Forms]
- MDI forms [Windows Forms], creating
- MDI forms [Windows Forms], walkthroughs
ms.assetid: fbab4221-74af-42d0-bbf4-3c97f7b2e544
ms.openlocfilehash: e0343b98cb71521b35418e70550a93e0bfe20fa8
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628783"
---
# <a name="walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a>逐步解說：使用功能表合併和 ToolStrip 控制項建立 MDI 表單

<xref:System.Windows.Forms?displayProperty=nameWithType> 命名空間支援多重文件介面 (MDI) 應用程式，而 <xref:System.Windows.Forms.MenuStrip> 控制項則支援功能表合併。 MDI 表單也可以由 <xref:System.Windows.Forms.ToolStrip> 控制項建立。

本逐步解說示範如何搭配使用 <xref:System.Windows.Forms.ToolStripPanel> 控制項與 MDI 表單。 這個表單也支援子功能表的功能表合併。 本逐步解說將說明下列工作：

- 建立 Windows Forms 專案。

- 建立表單的主功能表。 功能表的實際名稱會有所不同。

- 將 <xref:System.Windows.Forms.ToolStripPanel> 控制項加入至 [**工具箱**]。

- 建立子表單。

- 依迭置順序排列 <xref:System.Windows.Forms.ToolStripPanel> 控制項。

當您完成時，您將會有一個支援功能表合併和可移動 <xref:System.Windows.Forms.ToolStrip> 控制項的 MDI 表單。

若要將本主題中的程式碼複製成單一清單，請參閱[如何：使用功能表合併和 ToolStrip 控制項建立 MDI 表單](how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md)。

## <a name="prerequisites"></a>Prerequisites

您將需要 Visual Studio 才能完成此逐步解說。

## <a name="create-the-project"></a>建立專案

1. 在 Visual Studio 中，建立稱為**system.windows.forms.toolstrip.mdiform**的 Windows 應用程式專案（**檔案 > ** **新增** > **專案** > **Visual C#** 或**Visual Basic** > **傳統桌面** > **Windows Forms 應用程式**）。

2. 在 Windows Form 設計工具中，選取表單。

3. 在 屬性視窗中，將 <xref:System.Windows.Forms.Form.IsMdiContainer%2A> 的值設定為 `true`。

## <a name="create-the-main-menu"></a>建立主功能表

父 MDI 表單包含主功能表。 主功能表有一個名為**Window**的功能表項目。 您可以使用 [**視窗]** 功能表項目來建立子表單。 子表單中的功能表項目會合並到主功能表中。

1. 將 [<xref:System.Windows.Forms.MenuStrip>] 控制項從 [**工具箱**] 拖曳至表單上。

2. 將 <xref:System.Windows.Forms.ToolStripMenuItem> 新增至 [<xref:System.Windows.Forms.MenuStrip>] 控制項，並將其命名為**視窗**。

3. 選取 <xref:System.Windows.Forms.MenuStrip> 控制項。

4. 在 屬性視窗中，將 <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> 屬性的值設定為 `ToolStripMenuItem1`。

5. 將子專案新增至 [**視窗]** 功能表項目，然後將 [子專案] 命名為**New**。

6. 在 屬性視窗中，按一下 **事件**。

7. 按兩下 [<xref:System.Windows.Forms.ToolStripItem.Click>] 事件。

     Windows Form 設計工具會產生 <xref:System.Windows.Forms.ToolStripItem.Click> 事件的事件處理常式。

8. 將下列程式碼插入事件處理常式。

     [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#2)]

## <a name="add-the-toolstrippanel-control-to-the-toolbox"></a>將 ToolStripPanel 控制項新增至工具箱

當您使用具有 MDI 表單的 <xref:System.Windows.Forms.MenuStrip> 控制項時，必須擁有 <xref:System.Windows.Forms.ToolStripPanel> 控制項。 您必須將 <xref:System.Windows.Forms.ToolStripPanel> 控制項加入 [**工具箱**] 中，才能在 Windows Form 設計工具中建立 MDI 表單。

1. 開啟 [**工具箱**]，然後按一下 [**所有 Windows Forms** ] 索引標籤，以顯示可用的 Windows Forms 控制項。

2. 以滑鼠右鍵按一下以開啟快捷方式功能表，然後選取 **[選擇專案**]。

3. 在 [**選擇工具箱專案**] 對話方塊中，在 [**名稱**] 欄中向下拖曳，直到您找到 [ **ToolStripPanel**]。

4. 選取**ToolStripPanel**的核取方塊，然後按一下 **[確定]** 。

     [<xref:System.Windows.Forms.ToolStripPanel>] 控制項會出現在 [**工具箱**] 中。

## <a name="create-a-child-form"></a>建立子表單

在這個程式中，您將定義具有自己的 <xref:System.Windows.Forms.MenuStrip> 控制項的個別子表單類別。 這個表單的功能表項目會與父表單的專案合併。

1. 將名為 `ChildForm` 的新表單新增至專案。

     如需詳細資訊，請參閱[如何：將 Windows Forms 新增至專案](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y2xxdce3(v=vs.100))。

2. 將 [<xref:System.Windows.Forms.MenuStrip>] 控制項從 [**工具箱**] 拖曳至子表單。

3. 按一下 <xref:System.Windows.Forms.MenuStrip> 控制項的設計工具動作圖像（![小型黑色箭號](./media/designer-actions-glyph.gif)），然後選取 [**編輯專案**]。

4. 在 [**專案集合編輯器**] 對話方塊中，將名為**ChildMenuItem**的新 <xref:System.Windows.Forms.ToolStripMenuItem> 新增至子功能表。

     如需詳細資訊，請參閱[ToolStrip 專案集合編輯器](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233643(v=vs.100))。

## <a name="test-the-form"></a>測試表單

1. 按**F5**以編譯並執行您的表單。

2. 按一下 [**視窗]** 功能表項目以開啟功能表，然後按一下 [**新增**]。

     會在表單的 MDI 工作區中建立新的子表單。 子表單的功能表會與主功能表合併。

3. 關閉子表單。

     子表單的功能表會從主功能表中移除。

4. 按一下 [**新增**數次]。

     子表單會自動列在 [**視窗]** 功能表項目底下，因為已指派 <xref:System.Windows.Forms.MenuStrip> 控制項的 <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> 屬性。

## <a name="add-toolstrip-support"></a>新增 ToolStrip 支援

在這個程式中，您會將四個 <xref:System.Windows.Forms.ToolStrip> 控制項加入至 MDI 父表單。 每個 <xref:System.Windows.Forms.ToolStrip> 控制項都會加入 <xref:System.Windows.Forms.ToolStripPanel> 控制項內，並停駐在表單的邊緣。

1. 將 [<xref:System.Windows.Forms.ToolStripPanel>] 控制項從 [**工具箱**] 拖曳至表單上。

2. 選取 <xref:System.Windows.Forms.ToolStripPanel> 控制項，然後按兩下 [**工具箱**] 中的 [<xref:System.Windows.Forms.ToolStrip>] 控制項。

     <xref:System.Windows.Forms.ToolStrip> 控制項會在 <xref:System.Windows.Forms.ToolStripPanel> 控制項中建立。

3. 選取 <xref:System.Windows.Forms.ToolStripPanel> 控制項。

4. 在 屬性視窗中，將控制項的 <xref:System.Windows.Forms.Control.Dock%2A> 屬性值變更為 <xref:System.Windows.Forms.DockStyle.Left>。

     <xref:System.Windows.Forms.ToolStripPanel> 控制項會停駐在主功能表下方的表單左邊。 MDI 工作區會調整大小以符合 <xref:System.Windows.Forms.ToolStripPanel> 控制項。

5. 重複步驟1到4。

     將新的 <xref:System.Windows.Forms.ToolStripPanel> 控制項停駐在表單頂端。

     <xref:System.Windows.Forms.ToolStripPanel> 控制項停駐在主功能表底下，但位於第一個 <xref:System.Windows.Forms.ToolStripPanel> 控制項的右邊。 此步驟說明在正確定位 <xref:System.Windows.Forms.ToolStripPanel> 控制項時，迭置順序的重要性。

6. 針對兩個 <xref:System.Windows.Forms.ToolStripPanel> 控制項重複步驟1到4。

     將新的 <xref:System.Windows.Forms.ToolStripPanel> 控制項停駐在表單的右邊和底部。

## <a name="arrange-toolstrippanel-controls-by-z-order"></a>依迭置順序排列 ToolStripPanel 控制項

停駐的 <xref:System.Windows.Forms.ToolStripPanel> 控制項在 MDI 表單上的位置是由控制項在迭置順序中的位置決定。 您可以輕鬆地在 [檔大綱] 視窗中排列控制項的迭置順序。

1. 在 [ **View** ] 功能表中，按一下 [**其他視窗**]，然後按一下 [**檔大綱**]。

     上一個程式中 <xref:System.Windows.Forms.ToolStripPanel> 控制項的相片順序並不是標準的。 這是因為迭置順序不正確。 使用 [檔大綱] 視窗，即可變更控制項的迭置順序。

2. 在 [檔大綱] 視窗中，選取 [ **ToolStripPanel4**]。

3. 重複按一下向下箭號按鈕，直到**ToolStripPanel4**位於清單的底部。

     **ToolStripPanel4**控制項會停駐在表單底部的其他控制項底下。

4. 選取 [ **ToolStripPanel2**]。

5. 按一下向下箭號按鈕一次，將控制項第三個位置放在清單中。

     **ToolStripPanel2**控制項會停駐在表單的頂端，並放在主功能表下方和其他控制項的上方。

6. 在 [**檔大綱**] 視窗中選取各種控制項，然後將它們移至迭置順序中的不同位置。 請注意，停駐控制項的位置上，迭置順序的效果。 使用 CTRL-Z 或 [**編輯**] 功能表上的 [**復原**] 來復原變更。

## <a name="checkpoint---test-your-form"></a>檢查點-測試您的表單

1. 按**F5**以編譯並執行您的表單。

2. 按一下 <xref:System.Windows.Forms.ToolStrip> 控制項的底框，並將控制項拖曳至表單上的不同位置。

     您可以將 <xref:System.Windows.Forms.ToolStrip> 控制項從一個 <xref:System.Windows.Forms.ToolStripPanel> 控制項拖曳至另一個。

## <a name="next-steps"></a>後續步驟

在本逐步解說中，您已建立具有 <xref:System.Windows.Forms.ToolStrip> 控制項和功能表合併的 MDI 父表單。 您可以將 <xref:System.Windows.Forms.ToolStrip> 系列控制項用於其他許多用途：

- 使用 <xref:System.Windows.Forms.ContextMenuStrip>建立控制項的快捷方式功能表。 如需詳細資訊，請參閱[CoNtextMenu 元件總覽](contextmenu-component-overview-windows-forms.md)。

- 建立具有自動填入標準功能表的表單。 如需詳細資訊，請參閱[逐步解說：提供標準功能表項目給表單](walkthrough-providing-standard-menu-items-to-a-form.md)。

- 為您的 <xref:System.Windows.Forms.ToolStrip> 控制項提供專業的外觀。 如需詳細資訊，請參閱[如何：設定應用程式的 ToolStrip](how-to-set-the-toolstrip-renderer-for-an-application.md)轉譯器。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [操作說明：建立 MDI 父表單](../advanced/how-to-create-mdi-parent-forms.md)
- [操作說明：建立 MDI 子表單](../advanced/how-to-create-mdi-child-forms.md)
- [操作說明：將 MenuStrip 插入至 MDI 下拉式功能表](how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms.md)
- [ToolStrip 控制項](toolstrip-control-windows-forms.md)
