---
title: TableLayoutPanel 控制項 (Windows Form)
ms.date: 03/30/2017
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms]
- layout [Windows Forms]
- controls [Windows Forms], sizing
- sizing [Windows Forms], automatic
- layout [Windows Forms], TableLayoutPanel control
- automatic sizing
ms.assetid: f55175c6-424e-4782-a86e-3f79c1550235
ms.openlocfilehash: 6d0a693feeb241b5772f2e1049e7876ed1c0da20
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703135"
---
# <a name="tablelayoutpanel-control-windows-forms"></a><span data-ttu-id="ddba2-102">TableLayoutPanel 控制項 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="ddba2-102">TableLayoutPanel Control (Windows Forms)</span></span>
<span data-ttu-id="ddba2-103"><xref:System.Windows.Forms.TableLayoutPanel> 控制項會在格線中排列其內容。</span><span class="sxs-lookup"><span data-stu-id="ddba2-103">The <xref:System.Windows.Forms.TableLayoutPanel> control arranges its contents in a grid.</span></span> <span data-ttu-id="ddba2-104">由於配置會在設計階段和執行階段執行，因此當應用程式環境變更時，配置也會隨著動態變更。</span><span class="sxs-lookup"><span data-stu-id="ddba2-104">Because the layout is performed both at design time and run time, it can change dynamically as the application environment changes.</span></span> <span data-ttu-id="ddba2-105">這可讓面板中的控制項按比例調整大小，以便回應變更 (例如，由於當地語系化所造成的父控制項調整大小或文字長度變更)。</span><span class="sxs-lookup"><span data-stu-id="ddba2-105">This gives the controls in the panel the ability to proportionally resize, so it can respond to changes such as the parent control resizing or text length changing due to localization.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ddba2-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="ddba2-106">In This Section</span></span>  
 [<span data-ttu-id="ddba2-107">TableLayoutPanel 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="ddba2-107">TableLayoutPanel Control Overview</span></span>](tablelayoutpanel-control-overview.md)  
 <span data-ttu-id="ddba2-108">介紹 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的一般概念，這個控制項可讓您建立具有資料列和資料行的配置。</span><span class="sxs-lookup"><span data-stu-id="ddba2-108">Introduces the general concepts of the <xref:System.Windows.Forms.TableLayoutPanel> control, which allows you to create a layout with rows and columns.</span></span>  
  
 [<span data-ttu-id="ddba2-109">TableLayoutPanel 控制項的最佳作法</span><span class="sxs-lookup"><span data-stu-id="ddba2-109">Best Practices for the TableLayoutPanel Control</span></span>](best-practices-for-the-tablelayoutpanel-control.md)  
 <span data-ttu-id="ddba2-110">概述建議可幫助您獲得最佳的 <xref:System.Windows.Forms.TableLayoutPanel> 控制項版面配置功能。</span><span class="sxs-lookup"><span data-stu-id="ddba2-110">Outlines recommendations to help you get the most out of the layout features of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
 [<span data-ttu-id="ddba2-111">AutoSize 在 TableLayoutPanel 控制項中的行為</span><span class="sxs-lookup"><span data-stu-id="ddba2-111">AutoSize Behavior in the TableLayoutPanel Control</span></span>](autosize-behavior-in-the-tablelayoutpanel-control.md)  
 <span data-ttu-id="ddba2-112">說明 <xref:System.Windows.Forms.TableLayoutPanel> 控制項支援自動調整大小行為的方式。</span><span class="sxs-lookup"><span data-stu-id="ddba2-112">Explains the ways in which the <xref:System.Windows.Forms.TableLayoutPanel> control supports automatic sizing behavior.</span></span>  
  
 [<span data-ttu-id="ddba2-113">如何：錨定和停駐 TableLayoutPanel 控制項中的子控制項</span><span class="sxs-lookup"><span data-stu-id="ddba2-113">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 <span data-ttu-id="ddba2-114">示範如何錨定和停駐 <xref:System.Windows.Forms.TableLayoutPanel> 控制項中的子控制項。</span><span class="sxs-lookup"><span data-stu-id="ddba2-114">Shows how to anchor and dock child controls in a <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
 [<span data-ttu-id="ddba2-115">如何：設計可適當回應當地語系化的 Windows Forms 配置</span><span class="sxs-lookup"><span data-stu-id="ddba2-115">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>](how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)  
 <span data-ttu-id="ddba2-116">示範如何使用 <xref:System.Windows.Forms.TableLayoutPanel> 控制項來建立適當回應當地語系化的表單。</span><span class="sxs-lookup"><span data-stu-id="ddba2-116">Demonstrates using a <xref:System.Windows.Forms.TableLayoutPanel> control to build a form that responds well to localization.</span></span>  
  
 [<span data-ttu-id="ddba2-117">如何：建立適用於資料輸入且可調整大小的 Windows Form</span><span class="sxs-lookup"><span data-stu-id="ddba2-117">How to: Create a Resizable Windows Form for Data Entry</span></span>](how-to-create-a-resizable-windows-form-for-data-entry.md)  
 <span data-ttu-id="ddba2-118">示範如何使用 <xref:System.Windows.Forms.TableLayoutPanel> 控制項來建立可適當回應調整大小的表單。</span><span class="sxs-lookup"><span data-stu-id="ddba2-118">Demonstrates using a <xref:System.Windows.Forms.TableLayoutPanel> control to build a form that responds well to resizing.</span></span>  
  
1.  [<span data-ttu-id="ddba2-119">如何：對齊和縮放 TableLayoutPanel 控制項中的控制項</span><span class="sxs-lookup"><span data-stu-id="ddba2-119">How to: Align and Stretch a Control in a TableLayoutPanel Control</span></span>](how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control.md)  
  
2.  [<span data-ttu-id="ddba2-120">如何：合併資料列和 TableLayoutPanel 控制項中的資料行</span><span class="sxs-lookup"><span data-stu-id="ddba2-120">How to: Span Rows and Columns in a TableLayoutPanel Control</span></span>](how-to-span-rows-and-columns-in-a-tablelayoutpanel-control.md)  
  
3.  [<span data-ttu-id="ddba2-121">如何：編輯資料行和 TableLayoutPanel 控制項中的資料列</span><span class="sxs-lookup"><span data-stu-id="ddba2-121">How to: Edit Columns and Rows in a TableLayoutPanel Control</span></span>](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)  
  
4.  [<span data-ttu-id="ddba2-122">逐步解說：排列 Windows Form 使用 TableLayoutPanel 控制項</span><span class="sxs-lookup"><span data-stu-id="ddba2-122">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
  
## <a name="reference"></a><span data-ttu-id="ddba2-123">參考資料</span><span class="sxs-lookup"><span data-stu-id="ddba2-123">Reference</span></span>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 <span data-ttu-id="ddba2-124">提供 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的參考文件。</span><span class="sxs-lookup"><span data-stu-id="ddba2-124">Provides reference documentation for the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
 <xref:System.Windows.Forms.TableLayoutSettings>  
 <span data-ttu-id="ddba2-125">提供 <xref:System.Windows.Forms.TableLayoutSettings> 類型的參考文件。</span><span class="sxs-lookup"><span data-stu-id="ddba2-125">Provides reference documentation for the <xref:System.Windows.Forms.TableLayoutSettings> type.</span></span>  
  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <span data-ttu-id="ddba2-126">提供 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項的參考文件。</span><span class="sxs-lookup"><span data-stu-id="ddba2-126">Provides reference documentation for the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ddba2-127">相關章節</span><span class="sxs-lookup"><span data-stu-id="ddba2-127">Related Sections</span></span>  
 [<span data-ttu-id="ddba2-128">當地語系化</span><span class="sxs-lookup"><span data-stu-id="ddba2-128">Localization</span></span>](../../../standard/globalization-localization/localization.md)  
 <span data-ttu-id="ddba2-129">提供當地語系化相關主題的概觀。</span><span class="sxs-lookup"><span data-stu-id="ddba2-129">Provides an overview of topics relating to localization.</span></span>  
  
 <span data-ttu-id="ddba2-130">另請參閱[Localizing Applications](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/z68135h5(v=vs.120))。</span><span class="sxs-lookup"><span data-stu-id="ddba2-130">Also see [Localizing Applications](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/z68135h5(v=vs.120)).</span></span>
