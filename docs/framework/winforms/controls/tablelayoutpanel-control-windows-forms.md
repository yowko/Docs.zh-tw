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
ms.openlocfilehash: b51d3bd8e9d8816dfae6c10fc752adb0b3cea59c
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59337782"
---
# <a name="tablelayoutpanel-control-windows-forms"></a><span data-ttu-id="93ae8-102">TableLayoutPanel 控制項 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="93ae8-102">TableLayoutPanel Control (Windows Forms)</span></span>
<span data-ttu-id="93ae8-103"><xref:System.Windows.Forms.TableLayoutPanel> 控制項會在格線中排列其內容。</span><span class="sxs-lookup"><span data-stu-id="93ae8-103">The <xref:System.Windows.Forms.TableLayoutPanel> control arranges its contents in a grid.</span></span> <span data-ttu-id="93ae8-104">由於配置會在設計階段和執行階段執行，因此當應用程式環境變更時，配置也會隨著動態變更。</span><span class="sxs-lookup"><span data-stu-id="93ae8-104">Because the layout is performed both at design time and run time, it can change dynamically as the application environment changes.</span></span> <span data-ttu-id="93ae8-105">這可讓面板中的控制項按比例調整大小，以便回應變更 (例如，由於當地語系化所造成的父控制項調整大小或文字長度變更)。</span><span class="sxs-lookup"><span data-stu-id="93ae8-105">This gives the controls in the panel the ability to proportionally resize, so it can respond to changes such as the parent control resizing or text length changing due to localization.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="93ae8-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="93ae8-106">In This Section</span></span>  
 [<span data-ttu-id="93ae8-107">TableLayoutPanel 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="93ae8-107">TableLayoutPanel Control Overview</span></span>](tablelayoutpanel-control-overview.md)  
 <span data-ttu-id="93ae8-108">介紹 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的一般概念，這個控制項可讓您建立具有資料列和資料行的配置。</span><span class="sxs-lookup"><span data-stu-id="93ae8-108">Introduces the general concepts of the <xref:System.Windows.Forms.TableLayoutPanel> control, which allows you to create a layout with rows and columns.</span></span>  
  
 [<span data-ttu-id="93ae8-109">TableLayoutPanel 控制項的最佳作法</span><span class="sxs-lookup"><span data-stu-id="93ae8-109">Best Practices for the TableLayoutPanel Control</span></span>](best-practices-for-the-tablelayoutpanel-control.md)  
 <span data-ttu-id="93ae8-110">概述建議可幫助您獲得最佳的 <xref:System.Windows.Forms.TableLayoutPanel> 控制項版面配置功能。</span><span class="sxs-lookup"><span data-stu-id="93ae8-110">Outlines recommendations to help you get the most out of the layout features of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
 [<span data-ttu-id="93ae8-111">AutoSize 在 TableLayoutPanel 控制項中的行為</span><span class="sxs-lookup"><span data-stu-id="93ae8-111">AutoSize Behavior in the TableLayoutPanel Control</span></span>](autosize-behavior-in-the-tablelayoutpanel-control.md)  
 <span data-ttu-id="93ae8-112">說明 <xref:System.Windows.Forms.TableLayoutPanel> 控制項支援自動調整大小行為的方式。</span><span class="sxs-lookup"><span data-stu-id="93ae8-112">Explains the ways in which the <xref:System.Windows.Forms.TableLayoutPanel> control supports automatic sizing behavior.</span></span>  
  
 [<span data-ttu-id="93ae8-113">HOW TO：錨定和停駐 TableLayoutPanel 控制項中的子控制項</span><span class="sxs-lookup"><span data-stu-id="93ae8-113">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 <span data-ttu-id="93ae8-114">示範如何錨定和停駐 <xref:System.Windows.Forms.TableLayoutPanel> 控制項中的子控制項。</span><span class="sxs-lookup"><span data-stu-id="93ae8-114">Shows how to anchor and dock child controls in a <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
 [<span data-ttu-id="93ae8-115">HOW TO：設計可適當回應當地語系化的 Windows Forms 配置</span><span class="sxs-lookup"><span data-stu-id="93ae8-115">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>](how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)  
 <span data-ttu-id="93ae8-116">示範如何使用 <xref:System.Windows.Forms.TableLayoutPanel> 控制項來建立適當回應當地語系化的表單。</span><span class="sxs-lookup"><span data-stu-id="93ae8-116">Demonstrates using a <xref:System.Windows.Forms.TableLayoutPanel> control to build a form that responds well to localization.</span></span>  
  
 [<span data-ttu-id="93ae8-117">HOW TO：建立適用於資料輸入且可調整大小的 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="93ae8-117">How to: Create a Resizable Windows Form for Data Entry</span></span>](how-to-create-a-resizable-windows-form-for-data-entry.md)  
 <span data-ttu-id="93ae8-118">示範如何使用 <xref:System.Windows.Forms.TableLayoutPanel> 控制項來建立可適當回應調整大小的表單。</span><span class="sxs-lookup"><span data-stu-id="93ae8-118">Demonstrates using a <xref:System.Windows.Forms.TableLayoutPanel> control to build a form that responds well to resizing.</span></span>  
  
1. [<span data-ttu-id="93ae8-119">HOW TO：在 TableLayoutPanel 控制項中對齊和縮放控制項</span><span class="sxs-lookup"><span data-stu-id="93ae8-119">How to: Align and Stretch a Control in a TableLayoutPanel Control</span></span>](how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control.md)  
  
2. [<span data-ttu-id="93ae8-120">HOW TO：擴展 TableLayoutPanel 控制項中的資料列和資料行</span><span class="sxs-lookup"><span data-stu-id="93ae8-120">How to: Span Rows and Columns in a TableLayoutPanel Control</span></span>](how-to-span-rows-and-columns-in-a-tablelayoutpanel-control.md)  
  
3. [<span data-ttu-id="93ae8-121">HOW TO：編輯 TableLayoutPanel 控制項中的資料行和資料列</span><span class="sxs-lookup"><span data-stu-id="93ae8-121">How to: Edit Columns and Rows in a TableLayoutPanel Control</span></span>](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)  
  
4. [<span data-ttu-id="93ae8-122">逐步解說：使用 TableLayoutPanel 排列 Windows Forms 的控制項</span><span class="sxs-lookup"><span data-stu-id="93ae8-122">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
  
## <a name="reference"></a><span data-ttu-id="93ae8-123">參考資料</span><span class="sxs-lookup"><span data-stu-id="93ae8-123">Reference</span></span>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 <span data-ttu-id="93ae8-124">提供 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的參考文件。</span><span class="sxs-lookup"><span data-stu-id="93ae8-124">Provides reference documentation for the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
 <xref:System.Windows.Forms.TableLayoutSettings>  
 <span data-ttu-id="93ae8-125">提供 <xref:System.Windows.Forms.TableLayoutSettings> 類型的參考文件。</span><span class="sxs-lookup"><span data-stu-id="93ae8-125">Provides reference documentation for the <xref:System.Windows.Forms.TableLayoutSettings> type.</span></span>  
  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <span data-ttu-id="93ae8-126">提供 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項的參考文件。</span><span class="sxs-lookup"><span data-stu-id="93ae8-126">Provides reference documentation for the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="93ae8-127">相關章節</span><span class="sxs-lookup"><span data-stu-id="93ae8-127">Related Sections</span></span>  
 [<span data-ttu-id="93ae8-128">當地語系化</span><span class="sxs-lookup"><span data-stu-id="93ae8-128">Localization</span></span>](../../../standard/globalization-localization/localization.md)  
 <span data-ttu-id="93ae8-129">提供當地語系化相關主題的概觀。</span><span class="sxs-lookup"><span data-stu-id="93ae8-129">Provides an overview of topics relating to localization.</span></span>  
  
 <span data-ttu-id="93ae8-130">另請參閱[Localizing Applications](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/z68135h5(v=vs.120))。</span><span class="sxs-lookup"><span data-stu-id="93ae8-130">Also see [Localizing Applications](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/z68135h5(v=vs.120)).</span></span>
