---
title: 作法：使用設計工具防止在 Windows Forms DataGridView 控制項中新增和刪除資料列
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], preventing row addition or deletion
ms.assetid: a17722bd-9400-41e6-8dcc-c9c151f0a749
ms.openlocfilehash: 20f9b85dc48ccd634468d0fed000120723f8ee5c
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69038195"
---
# <a name="how-to-prevent-row-addition-and-deletion-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="0b8e7-102">HOW TO：使用設計工具防止在 Windows Forms DataGridView 控制項中新增和刪除資料列</span><span class="sxs-lookup"><span data-stu-id="0b8e7-102">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="0b8e7-103">有時候您會想要防止使用者在您的 <xref:System.Windows.Forms.DataGridView> 控制項中輸入新的資料列或刪除現有的資料列。</span><span class="sxs-lookup"><span data-stu-id="0b8e7-103">Sometimes you will want to prevent users from entering new rows of data or deleting existing rows in your <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="0b8e7-104">新的資料列會在控制項底部的新記錄的特殊資料列中輸入。</span><span class="sxs-lookup"><span data-stu-id="0b8e7-104">New rows are entered in the special row for new records at the bottom of the control.</span></span> <span data-ttu-id="0b8e7-105">當您停用資料列加入時, 不會顯示新記錄的資料列。</span><span class="sxs-lookup"><span data-stu-id="0b8e7-105">When you disable row addition, the row for new records is not displayed.</span></span> <span data-ttu-id="0b8e7-106">接著, 您可以停用資料列刪除和儲存格編輯, 讓控制項成為完全唯讀的。</span><span class="sxs-lookup"><span data-stu-id="0b8e7-106">You can then make the control entirely read-only by disabling row deletion and cell editing.</span></span>

 <span data-ttu-id="0b8e7-107">下列程式需要具有包含<xref:System.Windows.Forms.DataGridView>控制項之表單的**Windows 應用程式**專案。</span><span class="sxs-lookup"><span data-stu-id="0b8e7-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="0b8e7-108">如需設定這類專案的相關資訊, [請參閱如何:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project) , [以及如何:將控制項新增至](how-to-add-controls-to-windows-forms.md)Windows Forms。</span><span class="sxs-lookup"><span data-stu-id="0b8e7-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-prevent-row-addition-and-deletion"></a><span data-ttu-id="0b8e7-109">防止加入和刪除資料列</span><span class="sxs-lookup"><span data-stu-id="0b8e7-109">To prevent row addition and deletion</span></span>

- <span data-ttu-id="0b8e7-110">按一下<xref:System.Windows.Forms.DataGridView>控制項右上角的智慧標籤圖像 (![智慧標籤]圖像(./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")), 然後清除 [**啟用加入**] 和 [**啟用刪除**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="0b8e7-110">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then clear the **Enable Adding** and **Enable Deleting** check boxes.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="0b8e7-111">若要將控制項設為完全唯讀, 請清除 [**啟用編輯**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="0b8e7-111">To make the control entirely read-only, clear the **Enable Editing** check box as well.</span></span>

## <a name="see-also"></a><span data-ttu-id="0b8e7-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b8e7-112">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>
- [<span data-ttu-id="0b8e7-113">如何：建立 Windows Forms 應用程式專案</span><span class="sxs-lookup"><span data-stu-id="0b8e7-113">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="0b8e7-114">如何：將控制項新增至 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0b8e7-114">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
