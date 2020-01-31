---
title: DataGridView 控制項中的選取模式
ms.date: 03/30/2017
helpviewer_keywords:
- selection [Windows Forms], modes in DataGridView control
- DataGridView control [Windows Forms], selection mode
ms.assetid: a3ebfd3d-0525-479d-9d96-d9e017289b36
ms.openlocfilehash: e20bf6307d77bf189b698e847c6b855c249dc3c1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743035"
---
# <a name="selection-modes-in-the-windows-forms-datagridview-control"></a>Windows Form DataGridView 控制項中的選取模式

有時候您會想要讓應用程式根據 <xref:System.Windows.Forms.DataGridView> 控制項內的使用者選取專案來執行動作。 視動作而定，您可能會想要限制可能的選擇種類。 例如，假設您的應用程式可以列印目前所選記錄的報表。 在此情況下，您可能會想要設定 <xref:System.Windows.Forms.DataGridView> 控制項，讓按一下資料列內的任何位置一律會選取整個資料列，而且一次只能選取一個資料列。

您可以將 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> 屬性設定為下列其中一個 <xref:System.Windows.Forms.DataGridViewSelectionMode> 列舉值，以指定允許的選取專案。

|DataGridViewSelectionMode 值|描述|
|-------------------------------------|-----------------|
|<xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>|按一下資料格即可選取它。 資料列和資料行標頭不能用來選取。|
|<xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>|按一下資料格即可選取它。 按一下資料行標頭，即可選取整個資料行。 資料行標題不能用於排序。|
|<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>|按一下儲存格或資料行標頭，即可選取整個資料行。 資料行標題不能用於排序。|
|<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>|按一下儲存格或資料列標頭就會選取整個資料列。|
|<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>|預設選取模式。 按一下資料格即可選取它。 按一下資料列標頭就會選取整個資料列。|

> [!NOTE]
> 在執行時間變更選取模式，會自動清除目前的選取範圍。

根據預設，使用者可以選取多個資料列、資料行或資料格，方法是在選取以擴充或修改選取專案時，按 CTRL 或 SHIFT 鍵，或按一下左上方的頁首儲存格，以選取控制項中的所有儲存格。 若要避免此行為，請將 <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> 屬性設為 `false`。

<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> 和 <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> 模式可讓使用者藉由選取資料列並按下 DELETE 鍵來加以刪除。 只有當目前的儲存格不是編輯模式、<xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A> 屬性設定為 [`true`]，而且基礎資料來源支援使用者驅動資料列刪除時，使用者才可以刪除資料列。 請注意，這些設定不會防止以程式設計方式刪除資料列。

## <a name="programmatic-selection"></a>以程式設計方式選取

目前的選取範圍模式會限制以程式設計方式選取的行為，以及使用者選擇。 您可以藉由設定 <xref:System.Windows.Forms.DataGridView> 控制項中任何資料格、資料列或資料行的 [`Selected`] 屬性，以程式設計方式變更目前的選取範圍。 您也可以透過 [<xref:System.Windows.Forms.DataGridView.SelectAll%2A>] 方法選取控制項中的所有資料格，視選取模式而定。 若要清除選取專案，請使用 <xref:System.Windows.Forms.DataGridView.ClearSelection%2A> 方法。

如果 <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> 屬性設定為 `true`，您可以藉由變更元素的 `Selected` 屬性，在選取範圍中加入或移除 <xref:System.Windows.Forms.DataGridView> 元素。 否則，將 `Selected` 屬性設定為某個元素的 `true` 會自動從選取專案中移除其他元素。

請注意，變更 <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> 屬性的值並不會改變目前的選取範圍。

您可以透過 <xref:System.Windows.Forms.DataGridView> 控制項的 <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>、<xref:System.Windows.Forms.DataGridView.SelectedRows%2A>和 <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> 屬性，抓取目前選取的儲存格、資料列或資料行的集合。 當選取控制項中的每個資料格時，存取這些屬性會沒有效率。 為了避免這種情況下的效能降低，請先使用 <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> 方法。 此外，存取這些集合以判斷所選資料格、資料列或資料行的數目可能沒有效率。 相反地，您應該使用 <xref:System.Windows.Forms.DataGridView.GetCellCount%2A>、<xref:System.Windows.Forms.DataGridViewRowCollection.GetRowCount%2A>或 <xref:System.Windows.Forms.DataGridViewColumnCollection.GetColumnCount%2A> 方法，傳入 <xref:System.Windows.Forms.DataGridViewElementStates.Selected> 值。

> [!TIP]
> 您可以在 <xref:System.Windows.Forms.DataGridView> 類別總覽中找到示範如何以程式設計方式使用所選儲存格的範例程式碼。

## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.MultiSelect%2A>
- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>
- <xref:System.Windows.Forms.DataGridViewSelectionMode>
- [選取範圍和剪貼簿與 Windows Forms DataGridView 控制項搭配使用](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
- [操作說明：設定 Windows Forms DataGridView 控制項的選取模式](how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control.md)
