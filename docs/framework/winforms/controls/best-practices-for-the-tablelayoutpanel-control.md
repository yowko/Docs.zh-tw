---
title: "TableLayoutPanel 控制項的最佳作法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8f2c5a16ea1f07f7688c9df14bdb6b29350f3acf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="best-practices-for-the-tablelayoutpanel-control"></a><span data-ttu-id="34311-102">TableLayoutPanel 控制項的最佳作法</span><span class="sxs-lookup"><span data-stu-id="34311-102">Best Practices for the TableLayoutPanel Control</span></span>
<span data-ttu-id="34311-103"><xref:System.Windows.Forms.TableLayoutPanel>控制項提供功能強大的配置功能，您應該先在 Windows Form 上使用仔細考慮。</span><span class="sxs-lookup"><span data-stu-id="34311-103">The <xref:System.Windows.Forms.TableLayoutPanel> control provides powerful layout features that you should consider carefully before using on your Windows Forms.</span></span>  
  
## <a name="recommendations"></a><span data-ttu-id="34311-104">建議</span><span class="sxs-lookup"><span data-stu-id="34311-104">Recommendations</span></span>  
 <span data-ttu-id="34311-105">下列建議將協助您使用<xref:System.Windows.Forms.TableLayoutPanel>控制項的最佳優勢。</span><span class="sxs-lookup"><span data-stu-id="34311-105">The following recommendations will help you use the <xref:System.Windows.Forms.TableLayoutPanel> control to its best advantage.</span></span>  
  
### <a name="targeted-use"></a><span data-ttu-id="34311-106">目標的使用</span><span class="sxs-lookup"><span data-stu-id="34311-106">Targeted Use</span></span>  
 <span data-ttu-id="34311-107">使用<xref:System.Windows.Forms.TableLayoutPanel>謹慎控制。</span><span class="sxs-lookup"><span data-stu-id="34311-107">Use the <xref:System.Windows.Forms.TableLayoutPanel> control sparingly.</span></span> <span data-ttu-id="34311-108">您不應該使用所有的情況下，需要可調整大小的配置。</span><span class="sxs-lookup"><span data-stu-id="34311-108">You should not use it in all situations that require a resizable layout.</span></span> <span data-ttu-id="34311-109">下列清單描述獲益最多使用的版面配置<xref:System.Windows.Forms.TableLayoutPanel>控制項：</span><span class="sxs-lookup"><span data-stu-id="34311-109">The following list describes layouts that benefit most from the use of the <xref:System.Windows.Forms.TableLayoutPanel> control:</span></span>  
  
-   <span data-ttu-id="34311-110">有多個部分彼此依比例調整表單的配置。</span><span class="sxs-lookup"><span data-stu-id="34311-110">Layouts in which there are multiple parts of the form that resize proportionally to each other.</span></span>  
  
-   <span data-ttu-id="34311-111">要修改或動態產生在執行階段，例如有加上或扣除的使用者可自訂欄位的資料輸入表單的配置會根據喜好設定。</span><span class="sxs-lookup"><span data-stu-id="34311-111">Layouts that will be modified or generated dynamically at run time, such as data entry forms that have user-customizable fields added or subtracted based on preferences.</span></span>  
  
-   <span data-ttu-id="34311-112">應該保持為整體的固定大小的配置。</span><span class="sxs-lookup"><span data-stu-id="34311-112">Layouts that should remain at an overall fixed size.</span></span> <span data-ttu-id="34311-113">例如，您可能應保持小於 800 x 600，對話方塊中，但是您需要支援當地語系化的字串。</span><span class="sxs-lookup"><span data-stu-id="34311-113">For example, you may have a dialog box that should remain smaller than 800 x 600, but you need to support localized strings.</span></span>  
  
 <span data-ttu-id="34311-114">下列清單描述不使用大大受益的版面配置<xref:System.Windows.Forms.TableLayoutPanel>控制項：</span><span class="sxs-lookup"><span data-stu-id="34311-114">The following list describes layouts that do not benefit greatly from using the <xref:System.Windows.Forms.TableLayoutPanel> control:</span></span>  
  
-   <span data-ttu-id="34311-115">簡單資料項目表單的單一資料行的標籤和單一資料行的文字輸入區域。</span><span class="sxs-lookup"><span data-stu-id="34311-115">Simple data entry forms with a single column of labels and a single column of text-entry areas.</span></span>  
  
-   <span data-ttu-id="34311-116">以單一大型的表單顯示時調整大小，就會發生應該填滿所有可用空間的區域。</span><span class="sxs-lookup"><span data-stu-id="34311-116">Forms with a single large display area that should fill all the available space when a resize occurs.</span></span> <span data-ttu-id="34311-117">舉例來說，這是一個表單來顯示單一<xref:System.Windows.Forms.PropertyGrid>控制項。</span><span class="sxs-lookup"><span data-stu-id="34311-117">An example of this is a form that displays a single <xref:System.Windows.Forms.PropertyGrid> control.</span></span> <span data-ttu-id="34311-118">在此情況下，使用錨點，因為重新調整表單大小時，都應該展開。</span><span class="sxs-lookup"><span data-stu-id="34311-118">In this case, use anchoring, because nothing else should expand when the form is resized.</span></span>  
  
 <span data-ttu-id="34311-119">請小心選擇哪些控制項需要位於<xref:System.Windows.Forms.TableLayoutPanel>控制項。</span><span class="sxs-lookup"><span data-stu-id="34311-119">Choose carefully which controls need to be in a <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="34311-120">如果您有文字，以擴大使用錨定的 30%的空間，請考慮使用<xref:System.Windows.Forms.Control.Anchor%2A>只屬性。</span><span class="sxs-lookup"><span data-stu-id="34311-120">If you have room for your text to grow by 30% using anchoring, consider using the <xref:System.Windows.Forms.Control.Anchor%2A> property only.</span></span> <span data-ttu-id="34311-121">如果您可以評估您的配置所需的空間，使用<xref:System.Windows.Forms.Control.Dock%2A>和<xref:System.Windows.Forms.Control.Anchor%2A>比預估的剩餘空間的詳細資料更容易及<xref:System.Windows.Forms.Control.AutoSize%2A>行為。</span><span class="sxs-lookup"><span data-stu-id="34311-121">If you can estimate the space required by your layout, use of <xref:System.Windows.Forms.Control.Dock%2A> and <xref:System.Windows.Forms.Control.Anchor%2A> is easier than estimating the details of remaining space and <xref:System.Windows.Forms.Control.AutoSize%2A> behavior.</span></span>  
  
 <span data-ttu-id="34311-122">一般而言，當設計具有配置<xref:System.Windows.Forms.TableLayoutPanel>控制項，讓設計越簡單越好。</span><span class="sxs-lookup"><span data-stu-id="34311-122">In general, when designing your layout with the <xref:System.Windows.Forms.TableLayoutPanel> control, keep the design as simple as possible.</span></span>  
  
### <a name="use-the-document-outline-window"></a><span data-ttu-id="34311-123">使用文件大綱 視窗</span><span class="sxs-lookup"><span data-stu-id="34311-123">Use the Document Outline Window</span></span>  
 <span data-ttu-id="34311-124">[文件大綱] 視窗可讓您的配置，您可以使用來操作控制項的疊置順序與父子式關聯性的樹狀檢視。</span><span class="sxs-lookup"><span data-stu-id="34311-124">The Document Outline window gives you a tree view of your layout, which you can use to manipulate the z-order and parent-child relationships of your controls.</span></span> <span data-ttu-id="34311-125">從**檢視 功能表**，選取**其他視窗**，然後選取**文件大綱**。</span><span class="sxs-lookup"><span data-stu-id="34311-125">From the **View menu**, select **Other Windows**, then select **Document Outline**.</span></span>  
  
### <a name="avoid-nesting"></a><span data-ttu-id="34311-126">避免巢狀結構</span><span class="sxs-lookup"><span data-stu-id="34311-126">Avoid Nesting</span></span>  
 <span data-ttu-id="34311-127">避免其他的巢狀<xref:System.Windows.Forms.TableLayoutPanel>內控制<xref:System.Windows.Forms.TableLayoutPanel>控制項。</span><span class="sxs-lookup"><span data-stu-id="34311-127">Avoid nesting other <xref:System.Windows.Forms.TableLayoutPanel> controls within a <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="34311-128">偵錯巢狀的配置可能相當困難。</span><span class="sxs-lookup"><span data-stu-id="34311-128">Debugging nested layouts can be difficult.</span></span>  
  
### <a name="avoid-visual-inheritance"></a><span data-ttu-id="34311-129">避免視覺化繼承</span><span class="sxs-lookup"><span data-stu-id="34311-129">Avoid Visual Inheritance</span></span>  
 <span data-ttu-id="34311-130"><xref:System.Windows.Forms.TableLayoutPanel>控制項不支援在 Windows Form 設計工具的視覺化繼承。</span><span class="sxs-lookup"><span data-stu-id="34311-130">The <xref:System.Windows.Forms.TableLayoutPanel> control does not support visual inheritance in the Windows Forms Designer.</span></span> <span data-ttu-id="34311-131">A <xref:System.Windows.Forms.TableLayoutPanel> 「 已鎖定 」 在設計階段，會出現在衍生類別中的控制項。</span><span class="sxs-lookup"><span data-stu-id="34311-131">A <xref:System.Windows.Forms.TableLayoutPanel> control in a derived class appears as "locked" at design time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34311-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="34311-132">See Also</span></span>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 <xref:System.Windows.Forms.FlowLayoutPanel>
