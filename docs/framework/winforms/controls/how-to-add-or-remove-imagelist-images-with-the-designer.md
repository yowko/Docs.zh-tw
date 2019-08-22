---
title: 作法：使用設計工具新增或移除 ImageList 影像
ms.date: 03/30/2017
helpviewer_keywords:
- ImageList component [Windows Forms], adding images
- ImageList component [Windows Forms], removing images
- images [Windows Forms], adding to ImageList component
ms.assetid: 5699b244-e37c-4d20-bc35-7441e55c1e3a
ms.openlocfilehash: be17d5e6a12824c1c9edc867c99e77a6a1437a36
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658588"
---
# <a name="how-to-add-or-remove-imagelist-images-with-the-designer"></a><span data-ttu-id="ecabb-102">作法：使用設計工具新增或移除 ImageList 影像</span><span class="sxs-lookup"><span data-stu-id="ecabb-102">How to: Add or Remove ImageList Images with the Designer</span></span>

<span data-ttu-id="ecabb-103">您可以使用幾種不同<xref:System.Windows.Forms.ImageList>的方式將影像新增至元件。</span><span class="sxs-lookup"><span data-stu-id="ecabb-103">You can add images to an <xref:System.Windows.Forms.ImageList> component several different ways.</span></span> <span data-ttu-id="ecabb-104">您可以使用與<xref:System.Windows.Forms.ImageList>相關聯的智慧標籤非常快速地新增影像, 或者<xref:System.Windows.Forms.ImageList>, 如果您要在上設定數個其他屬性, 您可能會發現使用屬性視窗新增影像會比較方便。</span><span class="sxs-lookup"><span data-stu-id="ecabb-104">You can add images very quickly by using the smart tag associated with the <xref:System.Windows.Forms.ImageList>, or if you are setting several other properties on the <xref:System.Windows.Forms.ImageList>, you may find it more convenient to add images with the Properties window.</span></span> <span data-ttu-id="ecabb-105">您也可以使用程式碼來新增影像。</span><span class="sxs-lookup"><span data-stu-id="ecabb-105">You can also add images by using code.</span></span> <span data-ttu-id="ecabb-106">如需如何使用程式碼加入影像的詳細資訊, [請參閱如何:使用 Windows Forms ImageList 元件](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)來新增或移除映射。</span><span class="sxs-lookup"><span data-stu-id="ecabb-106">For more information about how to add images with code, see [How to: Add or Remove Images with the Windows Forms ImageList Component](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span> <span data-ttu-id="ecabb-107">通常, 您會<xref:System.Windows.Forms.ImageList>在元件與控制項建立關聯之前, 先將影像填入其中, 但這不是必要的。</span><span class="sxs-lookup"><span data-stu-id="ecabb-107">Typically you populate the <xref:System.Windows.Forms.ImageList> component with images before it is associated with a control, but this is not required.</span></span>

### <a name="to-add-or-remove-images-by-using-the-properties-window"></a><span data-ttu-id="ecabb-108">若要使用屬性視窗來新增或移除映射</span><span class="sxs-lookup"><span data-stu-id="ecabb-108">To add or remove images by using the Properties window</span></span>

1. <span data-ttu-id="ecabb-109"><xref:System.Windows.Forms.ImageList>選取元件, 或將它新增至表單。</span><span class="sxs-lookup"><span data-stu-id="ecabb-109">Select the <xref:System.Windows.Forms.ImageList> component, or add one to the form.</span></span>

2. <span data-ttu-id="ecabb-110">在 屬性視窗中, 按一下![ <xref:System.Windows.Forms.ImageList.Images%2A>屬性旁邊的省略號按鈕 ([](./media/visual-studio-ellipsis-button.png)Visual Studio 的屬性視窗中的省略號按鈕 (...))。</span><span class="sxs-lookup"><span data-stu-id="ecabb-110">In the Properties window, click the ellipsis button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.ImageList.Images%2A> property.</span></span>

3. <span data-ttu-id="ecabb-111">在**影像集合編輯器**，按一下 **新增**或**移除**新增或移除清單中的映像。</span><span class="sxs-lookup"><span data-stu-id="ecabb-111">In the **Image Collection Editor**, click **Add** or **Remove** to add or remove images from the list.</span></span>

### <a name="to-add-or-remove-images-using-the-smart-tag"></a><span data-ttu-id="ecabb-112">使用智慧標籤新增或移除影像</span><span class="sxs-lookup"><span data-stu-id="ecabb-112">To add or remove images using the smart tag</span></span>

1. <span data-ttu-id="ecabb-113"><xref:System.Windows.Forms.ImageList>選取元件, 或將它新增至表單。</span><span class="sxs-lookup"><span data-stu-id="ecabb-113">Select the <xref:System.Windows.Forms.ImageList> component, or add one to the form.</span></span>

2. <span data-ttu-id="ecabb-114">按一下智慧標籤圖像 (![智慧標籤]圖像(./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))</span><span class="sxs-lookup"><span data-stu-id="ecabb-114">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))</span></span>

3. <span data-ttu-id="ecabb-115">在 [ **ImageList**工作] 對話方塊中, 選取 **[選擇影像**]。</span><span class="sxs-lookup"><span data-stu-id="ecabb-115">In the **ImageList Tasks** dialog box, select **Choose Images**.</span></span>

4. <span data-ttu-id="ecabb-116">在 [ **Images] 集合編輯器**中, 按一下 [**新增**] 或 [**移除**], 從清單中新增或移除映射。</span><span class="sxs-lookup"><span data-stu-id="ecabb-116">In the **Images Collection Editor** click **Add** or **Remove** to add or remove images from the list.</span></span>

## <a name="see-also"></a><span data-ttu-id="ecabb-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ecabb-117">See also</span></span>

- [<span data-ttu-id="ecabb-118">影像、點陣圖和中繼檔</span><span class="sxs-lookup"><span data-stu-id="ecabb-118">Images, Bitmaps, and Metafiles</span></span>](../advanced/images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="ecabb-119">逐步解說：在 Windows Forms 控制項上使用智慧標籤執行一般工作</span><span class="sxs-lookup"><span data-stu-id="ecabb-119">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>](performing-common-tasks-using-smart-tags-on-wf-controls.md)
- [<span data-ttu-id="ecabb-120">ImageList 元件</span><span class="sxs-lookup"><span data-stu-id="ecabb-120">ImageList Component</span></span>](imagelist-component-windows-forms.md)
