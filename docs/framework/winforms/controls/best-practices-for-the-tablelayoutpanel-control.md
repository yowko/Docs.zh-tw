---
title: TableLayoutPanel 控制項的最佳作法
ms.date: 03/30/2017
helpviewer_keywords:
- layout [Windows Forms]
- TableLayoutPanel control [Windows Forms], best practices
- forms [Windows Forms], best practices
- AutoSize property [Windows Forms], tableLayoutPanel control
- controls [Windows Forms], sizing
- TableLayoutPanel control [Windows Forms], AutoSize behavior
- layout [Windows Forms], AutoSize
- layout [Windows Forms], best practices
- best practices [Windows Forms], tableLayoutPanel control
- sizing [Windows Forms], automatic
- automatic sizing
ms.assetid: b6706efb-d7a4-45ec-8cf4-08fa993e3afb
ms.openlocfilehash: e46d0fe6913bec61bd56199b7cb56a9b24d15bd0
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211352"
---
# <a name="best-practices-for-the-tablelayoutpanel-control"></a><span data-ttu-id="f754b-102">TableLayoutPanel 控制項的最佳作法</span><span class="sxs-lookup"><span data-stu-id="f754b-102">Best Practices for the TableLayoutPanel Control</span></span>
<span data-ttu-id="f754b-103"><xref:System.Windows.Forms.TableLayoutPanel>控制項提供功能強大的版面配置功能，您應該仔細考慮您的 Windows Forms 上使用之前。</span><span class="sxs-lookup"><span data-stu-id="f754b-103">The <xref:System.Windows.Forms.TableLayoutPanel> control provides powerful layout features that you should consider carefully before using on your Windows Forms.</span></span>

## <a name="recommendations"></a><span data-ttu-id="f754b-104">建議</span><span class="sxs-lookup"><span data-stu-id="f754b-104">Recommendations</span></span>
 <span data-ttu-id="f754b-105">下列建議可協助您使用<xref:System.Windows.Forms.TableLayoutPanel>控制項其最佳的利用。</span><span class="sxs-lookup"><span data-stu-id="f754b-105">The following recommendations will help you use the <xref:System.Windows.Forms.TableLayoutPanel> control to its best advantage.</span></span>

### <a name="targeted-use"></a><span data-ttu-id="f754b-106">目標的使用</span><span class="sxs-lookup"><span data-stu-id="f754b-106">Targeted Use</span></span>
 <span data-ttu-id="f754b-107">使用<xref:System.Windows.Forms.TableLayoutPanel>謹慎控制。</span><span class="sxs-lookup"><span data-stu-id="f754b-107">Use the <xref:System.Windows.Forms.TableLayoutPanel> control sparingly.</span></span> <span data-ttu-id="f754b-108">您不應該使用它在所有情況下，需要可調整大小的版面配置。</span><span class="sxs-lookup"><span data-stu-id="f754b-108">You should not use it in all situations that require a resizable layout.</span></span> <span data-ttu-id="f754b-109">下列清單描述使用的最大的版面配置<xref:System.Windows.Forms.TableLayoutPanel>控制項：</span><span class="sxs-lookup"><span data-stu-id="f754b-109">The following list describes layouts that benefit most from the use of the <xref:System.Windows.Forms.TableLayoutPanel> control:</span></span>

- <span data-ttu-id="f754b-110">在其中有多個部分彼此依比例調整表單的版面配置。</span><span class="sxs-lookup"><span data-stu-id="f754b-110">Layouts in which there are multiple parts of the form that resize proportionally to each other.</span></span>

- <span data-ttu-id="f754b-111">要修改或動態產生在執行階段，如有增加或減少的使用者可自訂欄位的資料輸入表單的配置會根據喜好設定。</span><span class="sxs-lookup"><span data-stu-id="f754b-111">Layouts that will be modified or generated dynamically at run time, such as data entry forms that have user-customizable fields added or subtracted based on preferences.</span></span>

- <span data-ttu-id="f754b-112">應該保持為整體的固定大小的版面配置。</span><span class="sxs-lookup"><span data-stu-id="f754b-112">Layouts that should remain at an overall fixed size.</span></span> <span data-ttu-id="f754b-113">比方說，您可能會有對話方塊，應保持小於 800 x 600 解析度，但您需要支援當地語系化的字串。</span><span class="sxs-lookup"><span data-stu-id="f754b-113">For example, you may have a dialog box that should remain smaller than 800 x 600, but you need to support localized strings.</span></span>

 <span data-ttu-id="f754b-114">下列清單將描述並不能享有大幅使用的版面配置<xref:System.Windows.Forms.TableLayoutPanel>控制項：</span><span class="sxs-lookup"><span data-stu-id="f754b-114">The following list describes layouts that do not benefit greatly from using the <xref:System.Windows.Forms.TableLayoutPanel> control:</span></span>

- <span data-ttu-id="f754b-115">簡單資料輸入表單具有單一資料行的標籤和文字輸入區域的單一資料行。</span><span class="sxs-lookup"><span data-stu-id="f754b-115">Simple data entry forms with a single column of labels and a single column of text-entry areas.</span></span>

- <span data-ttu-id="f754b-116">以單一大型的表單顯示時的調整大小，就會發生應填滿所有可用的空間的區域。</span><span class="sxs-lookup"><span data-stu-id="f754b-116">Forms with a single large display area that should fill all the available space when a resize occurs.</span></span> <span data-ttu-id="f754b-117">這個範例是一個表單來顯示單一<xref:System.Windows.Forms.PropertyGrid>控制項。</span><span class="sxs-lookup"><span data-stu-id="f754b-117">An example of this is a form that displays a single <xref:System.Windows.Forms.PropertyGrid> control.</span></span> <span data-ttu-id="f754b-118">在此情況下，使用錨定，因為重新調整表單大小時，沒有其他項目應該展開。</span><span class="sxs-lookup"><span data-stu-id="f754b-118">In this case, use anchoring, because nothing else should expand when the form is resized.</span></span>

 <span data-ttu-id="f754b-119">請謹慎選擇哪些控制項需要位於<xref:System.Windows.Forms.TableLayoutPanel>控制項。</span><span class="sxs-lookup"><span data-stu-id="f754b-119">Choose carefully which controls need to be in a <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="f754b-120">如果您有您的文字，使用錨定的 30%的成長的空間，請考慮使用<xref:System.Windows.Forms.Control.Anchor%2A>只顯示屬性。</span><span class="sxs-lookup"><span data-stu-id="f754b-120">If you have room for your text to grow by 30% using anchoring, consider using the <xref:System.Windows.Forms.Control.Anchor%2A> property only.</span></span> <span data-ttu-id="f754b-121">如果您可以評估您的版面配置所需的空間，使用<xref:System.Windows.Forms.Control.Dock%2A>並<xref:System.Windows.Forms.Control.Anchor%2A>遠比預估的剩餘空間的詳細資料和<xref:System.Windows.Forms.Control.AutoSize%2A>行為。</span><span class="sxs-lookup"><span data-stu-id="f754b-121">If you can estimate the space required by your layout, use of <xref:System.Windows.Forms.Control.Dock%2A> and <xref:System.Windows.Forms.Control.Anchor%2A> is easier than estimating the details of remaining space and <xref:System.Windows.Forms.Control.AutoSize%2A> behavior.</span></span>

 <span data-ttu-id="f754b-122">一般而言，當設計您的版面配置與<xref:System.Windows.Forms.TableLayoutPanel>控制項，讓設計越簡單越好。</span><span class="sxs-lookup"><span data-stu-id="f754b-122">In general, when designing your layout with the <xref:System.Windows.Forms.TableLayoutPanel> control, keep the design as simple as possible.</span></span>

### <a name="use-the-document-outline-window"></a><span data-ttu-id="f754b-123">使用 [文件大綱] 視窗</span><span class="sxs-lookup"><span data-stu-id="f754b-123">Use the Document Outline Window</span></span>
 <span data-ttu-id="f754b-124">[文件大綱] 視窗可讓您的配置，您可以使用它來操作控制項的疊置順序和父子式關聯性的樹狀檢視。</span><span class="sxs-lookup"><span data-stu-id="f754b-124">The Document Outline window gives you a tree view of your layout, which you can use to manipulate the z-order and parent-child relationships of your controls.</span></span> <span data-ttu-id="f754b-125">從**檢視 功能表**，選取**其他 Windows**，然後選取**文件大綱**。</span><span class="sxs-lookup"><span data-stu-id="f754b-125">From the **View menu**, select **Other Windows**, then select **Document Outline**.</span></span>

### <a name="avoid-nesting"></a><span data-ttu-id="f754b-126">避免巢狀結構</span><span class="sxs-lookup"><span data-stu-id="f754b-126">Avoid Nesting</span></span>
 <span data-ttu-id="f754b-127">避免其他的巢狀<xref:System.Windows.Forms.TableLayoutPanel>控制項內<xref:System.Windows.Forms.TableLayoutPanel>控制項。</span><span class="sxs-lookup"><span data-stu-id="f754b-127">Avoid nesting other <xref:System.Windows.Forms.TableLayoutPanel> controls within a <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="f754b-128">偵錯巢狀版面配置可能很困難。</span><span class="sxs-lookup"><span data-stu-id="f754b-128">Debugging nested layouts can be difficult.</span></span>

### <a name="avoid-visual-inheritance"></a><span data-ttu-id="f754b-129">避免視覺繼承</span><span class="sxs-lookup"><span data-stu-id="f754b-129">Avoid Visual Inheritance</span></span>
 <span data-ttu-id="f754b-130"><xref:System.Windows.Forms.TableLayoutPanel>控制項不支援在 Windows Form 設計工具，在 Visual Studio 中的視覺化繼承。</span><span class="sxs-lookup"><span data-stu-id="f754b-130">The <xref:System.Windows.Forms.TableLayoutPanel> control does not support visual inheritance in the Windows Forms Designer in Visual Studio.</span></span> <span data-ttu-id="f754b-131">A <xref:System.Windows.Forms.TableLayoutPanel> 「 已鎖定 」 在設計階段，會出現在衍生類別中的控制項。</span><span class="sxs-lookup"><span data-stu-id="f754b-131">A <xref:System.Windows.Forms.TableLayoutPanel> control in a derived class appears as "locked" at design time.</span></span>

## <a name="see-also"></a><span data-ttu-id="f754b-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f754b-132">See also</span></span>

- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
