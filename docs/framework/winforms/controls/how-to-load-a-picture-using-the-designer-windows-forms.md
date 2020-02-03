---
title: 如何：使用設計工具載入圖片
ms.date: 03/30/2017
helpviewer_keywords:
- picture formats
- images [Windows Forms], displaying on Windows Forms
- pictures [Windows Forms], displaying
- forms [Windows Forms], displaying images
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 4dc7b973-afb1-4276-8322-20825af96655
ms.openlocfilehash: 12b90d561a18fcffaafb9c45b7fa6be6dd060215
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736323"
---
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a><span data-ttu-id="0edad-102">如何：使用設計工具載入圖片 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="0edad-102">How to: Load a Picture Using the Designer (Windows Forms)</span></span>

<span data-ttu-id="0edad-103">您可以使用 Windows Forms <xref:System.Windows.Forms.PictureBox> 控制項，將 <xref:System.Windows.Forms.PictureBox.Image%2A> 屬性設為有效的圖片，在設計階段將圖片載入並顯示在表單上。</span><span class="sxs-lookup"><span data-stu-id="0edad-103">With the Windows Forms <xref:System.Windows.Forms.PictureBox> control, you can load and display a picture on a form at design time by setting the <xref:System.Windows.Forms.PictureBox.Image%2A> property to a valid picture.</span></span> <span data-ttu-id="0edad-104">下表顯示可接受的檔案類型。</span><span class="sxs-lookup"><span data-stu-id="0edad-104">The following table shows the acceptable file types.</span></span>

|<span data-ttu-id="0edad-105">類型</span><span class="sxs-lookup"><span data-stu-id="0edad-105">Type</span></span>|<span data-ttu-id="0edad-106">副檔名</span><span class="sxs-lookup"><span data-stu-id="0edad-106">File name extension</span></span>|
|---|---|
|<span data-ttu-id="0edad-107">點陣圖</span><span class="sxs-lookup"><span data-stu-id="0edad-107">Bitmap</span></span>|<span data-ttu-id="0edad-108">.bmp</span><span class="sxs-lookup"><span data-stu-id="0edad-108">.bmp</span></span>|
|<span data-ttu-id="0edad-109">圖示</span><span class="sxs-lookup"><span data-stu-id="0edad-109">Icon</span></span>|<span data-ttu-id="0edad-110">.ico</span><span class="sxs-lookup"><span data-stu-id="0edad-110">.ico</span></span>|
|<span data-ttu-id="0edad-111">GIF</span><span class="sxs-lookup"><span data-stu-id="0edad-111">GIF</span></span>|<span data-ttu-id="0edad-112">.gif</span><span class="sxs-lookup"><span data-stu-id="0edad-112">.gif</span></span>|
|<span data-ttu-id="0edad-113">中繼檔</span><span class="sxs-lookup"><span data-stu-id="0edad-113">Metafile</span></span>|<span data-ttu-id="0edad-114">.wmf</span><span class="sxs-lookup"><span data-stu-id="0edad-114">.wmf</span></span>|
|<span data-ttu-id="0edad-115">JPEG</span><span class="sxs-lookup"><span data-stu-id="0edad-115">JPEG</span></span>|<span data-ttu-id="0edad-116">.jpg</span><span class="sxs-lookup"><span data-stu-id="0edad-116">.jpg</span></span>|

## <a name="to-display-a-picture-at-design-time"></a><span data-ttu-id="0edad-117">在設計階段顯示圖片</span><span class="sxs-lookup"><span data-stu-id="0edad-117">To display a picture at design time</span></span>

1. <span data-ttu-id="0edad-118">在表單上繪製 <xref:System.Windows.Forms.PictureBox> 控制項。</span><span class="sxs-lookup"><span data-stu-id="0edad-118">Draw a <xref:System.Windows.Forms.PictureBox> control on a form.</span></span>

2. <span data-ttu-id="0edad-119">在 [**屬性**] 視窗中，選取 [<xref:System.Windows.Forms.PictureBox.Image%2A>] 屬性，然後選取省略號按鈕以顯示 [**開啟**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0edad-119">In the **Properties** window, select the <xref:System.Windows.Forms.PictureBox.Image%2A> property, then select the ellipsis button to display the **Open** dialog box.</span></span>

3. <span data-ttu-id="0edad-120">如果您要尋找特定的檔案類型（例如 .gif 檔案），請在 [**檔案類型**] 方塊中選取它。</span><span class="sxs-lookup"><span data-stu-id="0edad-120">If you're looking for a specific file type (for example, .gif files), select it in the **Files of type** box.</span></span>

4. <span data-ttu-id="0edad-121">選取您要顯示的檔案。</span><span class="sxs-lookup"><span data-stu-id="0edad-121">Select the file you want to display.</span></span>

## <a name="to-clear-the-picture-at-design-time"></a><span data-ttu-id="0edad-122">若要在設計階段清除圖片</span><span class="sxs-lookup"><span data-stu-id="0edad-122">To clear the picture at design time</span></span>

1. <span data-ttu-id="0edad-123">在 [**屬性**] 視窗中，選取 [<xref:System.Windows.Forms.PictureBox.Image%2A>] 屬性。</span><span class="sxs-lookup"><span data-stu-id="0edad-123">In the **Properties** window, select the <xref:System.Windows.Forms.PictureBox.Image%2A> property.</span></span> <span data-ttu-id="0edad-124">以滑鼠右鍵按一下影像物件名稱左側的小型縮圖影像，然後選擇 [**重設**]。</span><span class="sxs-lookup"><span data-stu-id="0edad-124">Right-click the small thumbnail image that appears to the left of the name of the image object, and then choose **Reset**.</span></span>

## <a name="see-also"></a><span data-ttu-id="0edad-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0edad-125">See also</span></span>

- <xref:System.Windows.Forms.PictureBox>
- [<span data-ttu-id="0edad-126">PictureBox 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="0edad-126">PictureBox Control Overview</span></span>](picturebox-control-overview-windows-forms.md)
- [<span data-ttu-id="0edad-127">操作說明：於執行階段修改圖片的大小或位置</span><span class="sxs-lookup"><span data-stu-id="0edad-127">How to: Modify the Size or Placement of a Picture at Run Time</span></span>](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [<span data-ttu-id="0edad-128">操作說明：在執行階段設定圖案</span><span class="sxs-lookup"><span data-stu-id="0edad-128">How to: Set Pictures at Run Time</span></span>](how-to-set-pictures-at-run-time-windows-forms.md)
- [<span data-ttu-id="0edad-129">PictureBox 控制項</span><span class="sxs-lookup"><span data-stu-id="0edad-129">PictureBox Control</span></span>](picturebox-control-windows-forms.md)
