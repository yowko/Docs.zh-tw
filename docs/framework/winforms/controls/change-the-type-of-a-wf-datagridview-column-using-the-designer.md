---
title: HOW TO：使用設計工具的 Windows Forms DataGridView 資料行的類型變更
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], types
- DataGridView control [Windows Forms], changing column type
- data [Windows Forms], displaying
ms.assetid: 7f994d45-600d-4190-a187-35803214b40c
ms.openlocfilehash: 189dd6d3e7eae7f4d9305bed97711da150198335
ms.sourcegitcommit: 0069cb3de8eed4e92b2195d29e5769a76111acdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/16/2019
ms.locfileid: "56333036"
---
# <a name="how-to-change-the-type-of-a-windows-forms-datagridview-column-using-the-designer"></a><span data-ttu-id="34999-102">HOW TO：使用設計工具的 Windows Forms DataGridView 資料行的類型變更</span><span class="sxs-lookup"><span data-stu-id="34999-102">How to: Change the Type of a Windows Forms DataGridView Column Using the Designer</span></span>
<span data-ttu-id="34999-103">有時候您會想要變更已新增至 Windows Forms 資料行的類型<xref:System.Windows.Forms.DataGridView>控制項。</span><span class="sxs-lookup"><span data-stu-id="34999-103">Sometimes you will want to change the type of a column that has already been added to a Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="34999-104">比方說，您可能想要修改的某些資料行時將控制項繫結至資料來源自動產生的類型。</span><span class="sxs-lookup"><span data-stu-id="34999-104">For example, you may want to modify the types of some of the columns that are generated automatically when you bind the control to a data source.</span></span> <span data-ttu-id="34999-105">當您顯示的資料表有包含相關資料表中的資料列的外部索引鍵資料行時，這非常有用。</span><span class="sxs-lookup"><span data-stu-id="34999-105">This is useful when the table you display has columns containing foreign keys to rows in a related table.</span></span> <span data-ttu-id="34999-106">在此情況下，您可能要取代的文字 方塊中資料行顯示下拉式方塊資料行顯示更有意義的值，從相關資料表中的這些外部索引鍵。</span><span class="sxs-lookup"><span data-stu-id="34999-106">In this case, you may want to replace the text box columns that display these foreign keys with combo box columns that display more meaningful values from the related table.</span></span>  
  
 <span data-ttu-id="34999-107">下列程序需要**Windows 應用程式**表單，其中包含專案<xref:System.Windows.Forms.DataGridView>控制項。</span><span class="sxs-lookup"><span data-stu-id="34999-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="34999-108">如需這類專案的設定資訊，請參閱[How to:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)和[How to:將控制項新增至 Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="34999-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="34999-109">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="34999-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="34999-110">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="34999-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="34999-111">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="34999-111">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-change-the-type-of-a-column-using-the-designer"></a><span data-ttu-id="34999-112">若要變更使用設計工具的資料行的類型</span><span class="sxs-lookup"><span data-stu-id="34999-112">To change the type of a column using the designer</span></span>  
  
1.  <span data-ttu-id="34999-113">按一下智慧標籤圖像 (![智慧標籤圖像](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) 的右上角<xref:System.Windows.Forms.DataGridView>控制項，然後再選取**編輯資料行**。</span><span class="sxs-lookup"><span data-stu-id="34999-113">Click the smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>  
  
2.  <span data-ttu-id="34999-114">選取的資料行**選取的資料行**清單。</span><span class="sxs-lookup"><span data-stu-id="34999-114">Select a column from the **Selected Columns** list.</span></span>  
  
3.  <span data-ttu-id="34999-115">在 **資料行屬性**方格中，設定`ColumnType`到新的資料行類型的屬性。</span><span class="sxs-lookup"><span data-stu-id="34999-115">In the **Column Properties** grid, set the `ColumnType` property to the new column type.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="34999-116">`ColumnType`屬性是只有設計階段屬性，指出代表資料行類型的類別。</span><span class="sxs-lookup"><span data-stu-id="34999-116">The `ColumnType` property is a design-time-only property that indicates the class representing the column type.</span></span> <span data-ttu-id="34999-117">它不是資料行類別中定義的實際屬性。</span><span class="sxs-lookup"><span data-stu-id="34999-117">It is not an actual property defined in a column class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34999-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34999-118">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- [<span data-ttu-id="34999-119">如何：建立 Windows Forms 應用程式專案</span><span class="sxs-lookup"><span data-stu-id="34999-119">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="34999-120">如何：將控制項新增至 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="34999-120">How to: Add Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
