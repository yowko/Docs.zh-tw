---
title: HOW TO：將 Windows Forms 上的物件分層
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, layering
- controls [Windows Forms], layering
- z order
- controls [Windows Forms], positioning
- z-order
ms.assetid: 1acc4281-2976-4715-86f4-bda68134baaf
ms.openlocfilehash: 80973e16445079876e01c89f20b5ecbdca602eb8
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039717"
---
# <a name="how-to-layer-objects-on-windows-forms"></a><span data-ttu-id="deea8-102">HOW TO：將 Windows Forms 上的物件分層</span><span class="sxs-lookup"><span data-stu-id="deea8-102">How to: Layer Objects on Windows Forms</span></span>
<span data-ttu-id="deea8-103">當您建立複雜的使用者介面, 或使用多重文件介面 (MDI) 表單時, 您通常會想要將控制項和子表單分層, 以建立更複雜的使用者介面 (UI)。</span><span class="sxs-lookup"><span data-stu-id="deea8-103">When you create a complex user interface, or work with a multiple document interface (MDI) form, you will often want to layer both controls and child forms to create more complex user interfaces (UI).</span></span> <span data-ttu-id="deea8-104">若要移動和追蹤群組內容中的控制項和視窗, 您可以操控其迭置順序。</span><span class="sxs-lookup"><span data-stu-id="deea8-104">To move and keep track of controls and windows within the context of a group, you manipulate their z-order.</span></span> <span data-ttu-id="deea8-105">迭置*順序*是表單上控制項的視覺分層, 沿著表單的 Z 軸 (深度)。</span><span class="sxs-lookup"><span data-stu-id="deea8-105">*Z-order* is the visual layering of controls on a form along the form's z-axis (depth).</span></span> <span data-ttu-id="deea8-106">位於 z 順序頂端的視窗會與所有其他視窗重迭。</span><span class="sxs-lookup"><span data-stu-id="deea8-106">The window at the top of the z-order overlaps all other windows.</span></span> <span data-ttu-id="deea8-107">所有其他視窗會在迭置順序的底部重迭視窗。</span><span class="sxs-lookup"><span data-stu-id="deea8-107">All other windows overlap the window at the bottom of the z-order.</span></span>

## <a name="to-layer-controls-at-design-time"></a><span data-ttu-id="deea8-108">在設計階段圖層控制項</span><span class="sxs-lookup"><span data-stu-id="deea8-108">To layer controls at design time</span></span>

1. <span data-ttu-id="deea8-109">選取您想要階層式控制項。</span><span class="sxs-lookup"><span data-stu-id="deea8-109">Select a control that you want to layer.</span></span>

2. <span data-ttu-id="deea8-110">在 [**格式**] 功能表上, 指向 [**順序**], 然後按一下 [**帶入前端**] 或 [**送回**]。</span><span class="sxs-lookup"><span data-stu-id="deea8-110">On the **Format** menu, point to **Order**, and then click **Bring To Front** or **Send To Back**.</span></span>

## <a name="to-layer-controls-programmatically"></a><span data-ttu-id="deea8-111">以程式設計方式分層控制項</span><span class="sxs-lookup"><span data-stu-id="deea8-111">To layer controls programmatically</span></span>

- <span data-ttu-id="deea8-112"><xref:System.Windows.Forms.Control.BringToFront%2A>使用和<xref:System.Windows.Forms.Control.SendToBack%2A>方法來操作控制項的迭置順序。</span><span class="sxs-lookup"><span data-stu-id="deea8-112">Use the <xref:System.Windows.Forms.Control.BringToFront%2A> and <xref:System.Windows.Forms.Control.SendToBack%2A> methods to manipulate the z-order of the controls.</span></span>

     <span data-ttu-id="deea8-113">例如, 如果<xref:System.Windows.Forms.TextBox> `txtFirstName`控制項位於另一個控制項之下, 而您想要將它放在最上層, 請使用下列程式碼:</span><span class="sxs-lookup"><span data-stu-id="deea8-113">For example, if a <xref:System.Windows.Forms.TextBox> control, `txtFirstName`, is underneath another control and you want to have it on top, use the following code:</span></span>

    ```vb
    txtFirstName.BringToFront()
    ```

    ```csharp
    txtFirstName.BringToFront();
    ```

    ```cpp
    txtFirstName->BringToFront();
    ```

> [!NOTE]
>  <span data-ttu-id="deea8-114">Windows Forms 支援*控制項*內含專案。</span><span class="sxs-lookup"><span data-stu-id="deea8-114">Windows Forms supports *control containment*.</span></span> <span data-ttu-id="deea8-115">控制項內含專案牽涉到將一些控制項放在包含控制項內, 例如<xref:System.Windows.Forms.RadioButton> <xref:System.Windows.Forms.GroupBox>控制項內的一些控制項。</span><span class="sxs-lookup"><span data-stu-id="deea8-115">Control containment involves placing a number of controls within a containing control, such as a number of <xref:System.Windows.Forms.RadioButton> controls within a <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="deea8-116">然後, 您可以在包含控制項內分層控制項。</span><span class="sxs-lookup"><span data-stu-id="deea8-116">You can then layer the controls within the containing control.</span></span> <span data-ttu-id="deea8-117">移動 [群組方塊] 也會移動控制項, 因為它們包含在其中。</span><span class="sxs-lookup"><span data-stu-id="deea8-117">Moving the group box moves the controls as well, because they are contained inside it.</span></span>

## <a name="see-also"></a><span data-ttu-id="deea8-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="deea8-118">See also</span></span>

- [<span data-ttu-id="deea8-119">Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="deea8-119">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="deea8-120">排列 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="deea8-120">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="deea8-121">標記個別 Windows Forms 控制項並提供其捷徑</span><span class="sxs-lookup"><span data-stu-id="deea8-121">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="deea8-122">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="deea8-122">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="deea8-123">依功能區分 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="deea8-123">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
