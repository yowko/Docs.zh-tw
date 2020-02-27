---
title: 如何：使用設計工具加入或移除 ImageList 影像
ms.date: 03/30/2017
helpviewer_keywords:
- ImageList component [Windows Forms], adding images
- ImageList component [Windows Forms], removing images
- images [Windows Forms], adding to ImageList component
ms.assetid: 5699b244-e37c-4d20-bc35-7441e55c1e3a
ms.openlocfilehash: cdc7b563a0ee4f8779b99b4e9a6786e78f8d500f
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628718"
---
# <a name="how-to-add-or-remove-imagelist-images-with-the-designer"></a><span data-ttu-id="ff074-102">如何：使用設計工具加入或移除 ImageList 影像</span><span class="sxs-lookup"><span data-stu-id="ff074-102">How to: Add or Remove ImageList Images with the Designer</span></span>

<span data-ttu-id="ff074-103">您可以使用幾種不同的方式，將影像新增至 <xref:System.Windows.Forms.ImageList> 元件。</span><span class="sxs-lookup"><span data-stu-id="ff074-103">You can add images to an <xref:System.Windows.Forms.ImageList> component several different ways.</span></span> <span data-ttu-id="ff074-104">您可以使用與 <xref:System.Windows.Forms.ImageList>相關聯的智慧標籤非常快速地新增影像，或者，如果您要在 <xref:System.Windows.Forms.ImageList>上設定數個其他屬性，您可能會發現使用屬性視窗來新增影像會更方便。</span><span class="sxs-lookup"><span data-stu-id="ff074-104">You can add images very quickly by using the smart tag associated with the <xref:System.Windows.Forms.ImageList>, or if you are setting several other properties on the <xref:System.Windows.Forms.ImageList>, you may find it more convenient to add images with the Properties window.</span></span> <span data-ttu-id="ff074-105">您也可以使用程式碼來新增影像。</span><span class="sxs-lookup"><span data-stu-id="ff074-105">You can also add images by using code.</span></span> <span data-ttu-id="ff074-106">如需如何使用程式碼加入影像的詳細資訊，請參閱[如何：使用 Windows Forms ImageList 元件來新增或移除映射](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)。</span><span class="sxs-lookup"><span data-stu-id="ff074-106">For more information about how to add images with code, see [How to: Add or Remove Images with the Windows Forms ImageList Component](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span> <span data-ttu-id="ff074-107">通常，您會先使用影像填入 <xref:System.Windows.Forms.ImageList> 元件，再將其與控制項建立關聯，但這不是必要的。</span><span class="sxs-lookup"><span data-stu-id="ff074-107">Typically you populate the <xref:System.Windows.Forms.ImageList> component with images before it is associated with a control, but this is not required.</span></span>

### <a name="to-add-or-remove-images-by-using-the-properties-window"></a><span data-ttu-id="ff074-108">若要使用屬性視窗來新增或移除映射</span><span class="sxs-lookup"><span data-stu-id="ff074-108">To add or remove images by using the Properties window</span></span>

1. <span data-ttu-id="ff074-109">選取 [<xref:System.Windows.Forms.ImageList>] 元件，或在表單中加入一個。</span><span class="sxs-lookup"><span data-stu-id="ff074-109">Select the <xref:System.Windows.Forms.ImageList> component, or add one to the form.</span></span>

2. <span data-ttu-id="ff074-110">在 [屬性視窗中，按一下 [](./media/visual-studio-ellipsis-button.png)] 屬性旁邊的省略號按鈕（!Visual Studio 的屬性視窗中的省略號按鈕（...）。<xref:System.Windows.Forms.ImageList.Images%2A></span><span class="sxs-lookup"><span data-stu-id="ff074-110">In the Properties window, click the ellipsis button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.ImageList.Images%2A> property.</span></span>

3. <span data-ttu-id="ff074-111">在 [**映射集合編輯器**] 中，按一下 [**新增**] 或 [**移除**]，從清單中新增或移除影像。</span><span class="sxs-lookup"><span data-stu-id="ff074-111">In the **Image Collection Editor**, click **Add** or **Remove** to add or remove images from the list.</span></span>

### <a name="to-add-or-remove-images-using-the-smart-tag"></a><span data-ttu-id="ff074-112">使用智慧標籤新增或移除影像</span><span class="sxs-lookup"><span data-stu-id="ff074-112">To add or remove images using the smart tag</span></span>

1. <span data-ttu-id="ff074-113">選取 [<xref:System.Windows.Forms.ImageList>] 元件，或在表單中加入一個。</span><span class="sxs-lookup"><span data-stu-id="ff074-113">Select the <xref:System.Windows.Forms.ImageList> component, or add one to the form.</span></span>

2. <span data-ttu-id="ff074-114">按一下設計工具動作圖像（</span><span class="sxs-lookup"><span data-stu-id="ff074-114">Click the designer actions glyph (</span></span>![小型黑色箭號](./media/designer-actions-glyph.gif)<span data-ttu-id="ff074-116">)</span><span class="sxs-lookup"><span data-stu-id="ff074-116">)</span></span>

3. <span data-ttu-id="ff074-117">在 [ **ImageList**工作] 對話方塊中，選取 **[選擇影像**]。</span><span class="sxs-lookup"><span data-stu-id="ff074-117">In the **ImageList Tasks** dialog box, select **Choose Images**.</span></span>

4. <span data-ttu-id="ff074-118">在 [ **Images] 集合編輯器**中，按一下 [**新增**] 或 [**移除**]，從清單中新增或移除映射。</span><span class="sxs-lookup"><span data-stu-id="ff074-118">In the **Images Collection Editor** click **Add** or **Remove** to add or remove images from the list.</span></span>

## <a name="see-also"></a><span data-ttu-id="ff074-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ff074-119">See also</span></span>

- [<span data-ttu-id="ff074-120">影像、點陣圖和中繼檔</span><span class="sxs-lookup"><span data-stu-id="ff074-120">Images, Bitmaps, and Metafiles</span></span>](../advanced/images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="ff074-121">逐步解說：使用設計工具動作執行一般工作</span><span class="sxs-lookup"><span data-stu-id="ff074-121">Walkthrough: Perform common tasks using designer actions</span></span>](perform-common-tasks-design-actions.md)
- [<span data-ttu-id="ff074-122">ImageList 元件</span><span class="sxs-lookup"><span data-stu-id="ff074-122">ImageList Component</span></span>](imagelist-component-windows-forms.md)
