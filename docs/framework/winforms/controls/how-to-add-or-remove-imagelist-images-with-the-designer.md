---
title: HOW TO：使用設計工具新增或移除 ImageList 影像
ms.date: 03/30/2017
helpviewer_keywords:
- ImageList component [Windows Forms], adding images
- ImageList component [Windows Forms], removing images
- images [Windows Forms], adding to ImageList component
ms.assetid: 5699b244-e37c-4d20-bc35-7441e55c1e3a
ms.openlocfilehash: b85b4d39235d49966b5f3c108986c8dd04bed5fe
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59161521"
---
# <a name="how-to-add-or-remove-imagelist-images-with-the-designer"></a><span data-ttu-id="4bfd3-102">HOW TO：使用設計工具新增或移除 ImageList 影像</span><span class="sxs-lookup"><span data-stu-id="4bfd3-102">How to: Add or Remove ImageList Images with the Designer</span></span>
<span data-ttu-id="4bfd3-103">您可以新增映像發佈至<xref:System.Windows.Forms.ImageList>元件數個不同的方式。</span><span class="sxs-lookup"><span data-stu-id="4bfd3-103">You can add images to an <xref:System.Windows.Forms.ImageList> component several different ways.</span></span> <span data-ttu-id="4bfd3-104">您可以使用相關聯的智慧標籤，非常快速地將影像<xref:System.Windows.Forms.ImageList>，或如果您要設定幾個其他屬性上<xref:System.Windows.Forms.ImageList>，您可能會發現它更方便地新增 [屬性] 視窗的影像。</span><span class="sxs-lookup"><span data-stu-id="4bfd3-104">You can add images very quickly by using the smart tag associated with the <xref:System.Windows.Forms.ImageList>, or if you are setting several other properties on the <xref:System.Windows.Forms.ImageList>, you may find it more convenient to add images with the Properties window.</span></span> <span data-ttu-id="4bfd3-105">您也可以使用程式碼，以新增映像。</span><span class="sxs-lookup"><span data-stu-id="4bfd3-105">You can also add images by using code.</span></span> <span data-ttu-id="4bfd3-106">如需有關新增程式碼使用的映像的詳細資訊，請參閱[How to:新增或移除映像的 Windows Form ImageList 元件](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)。</span><span class="sxs-lookup"><span data-stu-id="4bfd3-106">For more information about how to add images with code, see [How to: Add or Remove Images with the Windows Forms ImageList Component](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span> <span data-ttu-id="4bfd3-107">通常您填入<xref:System.Windows.Forms.ImageList>映像之前表單與控制項相關聯，但這不是必要元件。</span><span class="sxs-lookup"><span data-stu-id="4bfd3-107">Typically you populate the <xref:System.Windows.Forms.ImageList> component with images before it is associated with a control, but this is not required.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4bfd3-108">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="4bfd3-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="4bfd3-109">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="4bfd3-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="4bfd3-110">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="4bfd3-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-add-or-remove-images-by-using-the-properties-window"></a><span data-ttu-id="4bfd3-111">若要新增或移除映像，使用 [屬性] 視窗</span><span class="sxs-lookup"><span data-stu-id="4bfd3-111">To add or remove images by using the Properties window</span></span>  
  
1.  <span data-ttu-id="4bfd3-112">選取<xref:System.Windows.Forms.ImageList>元件，或新增至表單。</span><span class="sxs-lookup"><span data-stu-id="4bfd3-112">Select the <xref:System.Windows.Forms.ImageList> component, or add one to the form.</span></span>  
  
2.  <span data-ttu-id="4bfd3-113">在 [屬性] 視窗中，按一下 省略符號按鈕 (![VisualStudioEllipsesButton 螢幕擷取畫面](../media/vbellipsesbutton.png "vbEllipsesButton")) 旁邊<xref:System.Windows.Forms.ImageList.Images%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="4bfd3-113">In the Properties window, click the ellipsis button (![VisualStudioEllipsesButton screenshot](../media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.ImageList.Images%2A> property.</span></span>  
  
3.  <span data-ttu-id="4bfd3-114">在**影像集合編輯器**，按一下 **新增**或**移除**新增或移除清單中的映像。</span><span class="sxs-lookup"><span data-stu-id="4bfd3-114">In the **Image Collection Editor**, click **Add** or **Remove** to add or remove images from the list.</span></span>  
  
### <a name="to-add-or-remove-images-using-the-smart-tag"></a><span data-ttu-id="4bfd3-115">若要加入或移除使用智慧標籤的影像</span><span class="sxs-lookup"><span data-stu-id="4bfd3-115">To add or remove images using the smart tag</span></span>  
  
1.  <span data-ttu-id="4bfd3-116">選取<xref:System.Windows.Forms.ImageList>元件，或新增至表單。</span><span class="sxs-lookup"><span data-stu-id="4bfd3-116">Select the <xref:System.Windows.Forms.ImageList> component, or add one to the form.</span></span>  
  
2.  <span data-ttu-id="4bfd3-117">按一下智慧標籤圖像 (![智慧標籤圖像](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))</span><span class="sxs-lookup"><span data-stu-id="4bfd3-117">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))</span></span>  
  
3.  <span data-ttu-id="4bfd3-118">在  **ImageList 工作**對話方塊中，選取**選擇映像**。</span><span class="sxs-lookup"><span data-stu-id="4bfd3-118">In the **ImageList Tasks** dialog box, select **Choose Images**.</span></span>  
  
4.  <span data-ttu-id="4bfd3-119">在  **Editor Kolekce Images**按一下 **新增**或**移除**新增或移除清單中的映像。</span><span class="sxs-lookup"><span data-stu-id="4bfd3-119">In the **Images Collection Editor** click **Add** or **Remove** to add or remove images from the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bfd3-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4bfd3-120">See also</span></span>

- [<span data-ttu-id="4bfd3-121">影像、點陣圖和中繼檔</span><span class="sxs-lookup"><span data-stu-id="4bfd3-121">Images, Bitmaps, and Metafiles</span></span>](../advanced/images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="4bfd3-122">逐步解說：使用 Windows Forms 控制項的智慧標籤執行一般工作</span><span class="sxs-lookup"><span data-stu-id="4bfd3-122">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>](performing-common-tasks-using-smart-tags-on-wf-controls.md)
- [<span data-ttu-id="4bfd3-123">ImageList 元件</span><span class="sxs-lookup"><span data-stu-id="4bfd3-123">ImageList Component</span></span>](imagelist-component-windows-forms.md)
