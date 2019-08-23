---
title: HOW TO：使用設計工具變更 Windows Forms DataGridView 資料行的類型
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], types
- DataGridView control [Windows Forms], changing column type
- data [Windows Forms], displaying
ms.assetid: 7f994d45-600d-4190-a187-35803214b40c
ms.openlocfilehash: e0b0b01a3c6da0680a3ec5fcd591344e04658a37
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917613"
---
# <a name="how-to-change-the-type-of-a-windows-forms-datagridview-column-using-the-designer"></a><span data-ttu-id="8a17b-102">HOW TO：使用設計工具變更 Windows Forms DataGridView 資料行的類型</span><span class="sxs-lookup"><span data-stu-id="8a17b-102">How to: Change the Type of a Windows Forms DataGridView Column Using the Designer</span></span>
<span data-ttu-id="8a17b-103">有時候您會想要變更已經加入至 Windows Forms <xref:System.Windows.Forms.DataGridView>控制項的資料行類型。</span><span class="sxs-lookup"><span data-stu-id="8a17b-103">Sometimes you will want to change the type of a column that has already been added to a Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="8a17b-104">例如, 當您將控制項系結至資料來源時, 您可能會想要修改自動產生之部分資料行的類型。</span><span class="sxs-lookup"><span data-stu-id="8a17b-104">For example, you may want to modify the types of some of the columns that are generated automatically when you bind the control to a data source.</span></span> <span data-ttu-id="8a17b-105">當您顯示的資料表中有資料行包含相關資料表中之資料列的外鍵時, 這會很有用。</span><span class="sxs-lookup"><span data-stu-id="8a17b-105">This is useful when the table you display has columns containing foreign keys to rows in a related table.</span></span> <span data-ttu-id="8a17b-106">在此情況下, 您可能會想要將顯示這些外鍵的文字方塊資料行, 取代為在相關資料表中顯示更有意義之值的下拉式方塊資料行。</span><span class="sxs-lookup"><span data-stu-id="8a17b-106">In this case, you may want to replace the text box columns that display these foreign keys with combo box columns that display more meaningful values from the related table.</span></span>

 <span data-ttu-id="8a17b-107">下列程式需要具有包含<xref:System.Windows.Forms.DataGridView>控制項之表單的**Windows 應用程式**專案。</span><span class="sxs-lookup"><span data-stu-id="8a17b-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="8a17b-108">如需設定這類專案的相關資訊, [請參閱如何:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project) , [以及如何:將控制項新增至](how-to-add-controls-to-windows-forms.md)Windows Forms。</span><span class="sxs-lookup"><span data-stu-id="8a17b-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

### <a name="to-change-the-type-of-a-column-using-the-designer"></a><span data-ttu-id="8a17b-109">若要使用設計工具變更資料行的類型</span><span class="sxs-lookup"><span data-stu-id="8a17b-109">To change the type of a column using the designer</span></span>

1. <span data-ttu-id="8a17b-110">按一下<xref:System.Windows.Forms.DataGridView>控制項右上角的智慧標籤圖像 (![智慧標籤]圖像(./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")), 然後選取 [編輯資料**行**]。</span><span class="sxs-lookup"><span data-stu-id="8a17b-110">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>

2. <span data-ttu-id="8a17b-111">從 [選取的資料**行**] 清單中選取資料行。</span><span class="sxs-lookup"><span data-stu-id="8a17b-111">Select a column from the **Selected Columns** list.</span></span>

3. <span data-ttu-id="8a17b-112">在 [資料**行屬性**] 方格中`ColumnType` , 將屬性設定為新的資料行類型。</span><span class="sxs-lookup"><span data-stu-id="8a17b-112">In the **Column Properties** grid, set the `ColumnType` property to the new column type.</span></span>

    > [!NOTE]
    > <span data-ttu-id="8a17b-113">`ColumnType`屬性是僅限設計階段的屬性, 表示代表資料行類型的類別。</span><span class="sxs-lookup"><span data-stu-id="8a17b-113">The `ColumnType` property is a design-time-only property that indicates the class representing the column type.</span></span> <span data-ttu-id="8a17b-114">它不是在資料行類別中定義的實際屬性。</span><span class="sxs-lookup"><span data-stu-id="8a17b-114">It is not an actual property defined in a column class.</span></span>

## <a name="see-also"></a><span data-ttu-id="8a17b-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a17b-115">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- [<span data-ttu-id="8a17b-116">如何：建立 Windows Forms 應用程式專案</span><span class="sxs-lookup"><span data-stu-id="8a17b-116">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="8a17b-117">如何：將控制項新增至 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8a17b-117">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
