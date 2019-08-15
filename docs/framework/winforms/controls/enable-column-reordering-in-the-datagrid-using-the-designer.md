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
# <a name="how-to-enable-column-reordering-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="10395-102">HOW TO：使用設計工具重新調整 Windows Forms DataGridView 控制項的資料行順序</span><span class="sxs-lookup"><span data-stu-id="10395-102">How to: Enable Column Reordering in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="10395-103">當您查看 Windows Forms <xref:System.Windows.Forms.DataGridView>控制項中顯示的資料時, 使用者有時會想要比較特定資料行中的值。</span><span class="sxs-lookup"><span data-stu-id="10395-103">When viewing data displayed in a Windows Forms <xref:System.Windows.Forms.DataGridView> control, users sometimes want to compare the values in specific columns.</span></span> <span data-ttu-id="10395-104">如果資料行廣泛地在控制項中區隔, 這可能不方便, 特別是當使用者必須水準來回滾動, 才能查看他們感興趣的所有資料行時。</span><span class="sxs-lookup"><span data-stu-id="10395-104">This can be inconvenient if the columns are widely separated in the control, especially if users must scroll back and forth horizontally in order to see all the columns they are interested in.</span></span> <span data-ttu-id="10395-105">您可以讓使用者重新排列資料行, 以更輕鬆地比較資料行值。</span><span class="sxs-lookup"><span data-stu-id="10395-105">You can make the task of comparing column values easier by enabling your users to reorder the columns.</span></span> <span data-ttu-id="10395-106">當您啟用資料行重新調整時, 使用者可以使用滑鼠拖曳資料行標頭, 將資料行移至新位置。</span><span class="sxs-lookup"><span data-stu-id="10395-106">When you enable column reordering, users can move a column to a new position by dragging the column header with the mouse.</span></span>

 <span data-ttu-id="10395-107">下列程式需要具有包含<xref:System.Windows.Forms.DataGridView>控制項之表單的**Windows 應用程式**專案。</span><span class="sxs-lookup"><span data-stu-id="10395-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="10395-108">如需設定這類專案的相關資訊, [請參閱如何:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project) , [以及如何:將控制項新增至](how-to-add-controls-to-windows-forms.md)Windows Forms。</span><span class="sxs-lookup"><span data-stu-id="10395-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-enable-column-reordering"></a><span data-ttu-id="10395-109">啟用資料行重新排列</span><span class="sxs-lookup"><span data-stu-id="10395-109">To enable column reordering</span></span>

- <span data-ttu-id="10395-110">按一下控制項右上角的智慧標籤圖像 (![智慧標籤]圖像(./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")), 然後選取 [ <xref:System.Windows.Forms.DataGridView> **啟用資料行重新排列**]。</span><span class="sxs-lookup"><span data-stu-id="10395-110">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Enable Column Reordering**.</span></span>

## <a name="see-also"></a><span data-ttu-id="10395-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10395-111">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType>
- [<span data-ttu-id="10395-112">如何：使用設計工具凍結 Windows Forms DataGridView 控制項中的資料行</span><span class="sxs-lookup"><span data-stu-id="10395-112">How to: Freeze Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](freeze-columns-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="10395-113">如何：建立 Windows Forms 應用程式專案</span><span class="sxs-lookup"><span data-stu-id="10395-113">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="10395-114">如何：將控制項新增至 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="10395-114">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
