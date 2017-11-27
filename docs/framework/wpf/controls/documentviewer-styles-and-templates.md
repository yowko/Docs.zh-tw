---
title: "DocumentViewer 樣式和範本"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- templates [WPF], DocumentViewer
- DocumentViewer [WPF], styles and templates
- states [WPF], DocumentViewer
- ControlTemplate [WPF], DocumentViewer
- parts [WPF], DocumentViewer
- styles [WPF], DocumentViewer
ms.assetid: 6bd4ff8f-ea6a-4084-ac58-e7a67446ce1c
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7027fbee6a35b9219e65c9964db9a038e942f14e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="documentviewer-styles-and-templates"></a><span data-ttu-id="45852-102">DocumentViewer 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="45852-102">DocumentViewer Styles and Templates</span></span>
<span data-ttu-id="45852-103">本主題描述樣式和範本<xref:System.Windows.Controls.DocumentViewer>控制項。</span><span class="sxs-lookup"><span data-stu-id="45852-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span> <span data-ttu-id="45852-104">您可以修改預設<xref:System.Windows.Controls.ControlTemplate>來提供獨特的外觀的控制項。</span><span class="sxs-lookup"><span data-stu-id="45852-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="45852-105">如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="45852-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="documentviewer-parts"></a><span data-ttu-id="45852-106">DocumentViewer 的組件</span><span class="sxs-lookup"><span data-stu-id="45852-106">DocumentViewer Parts</span></span>  
 <span data-ttu-id="45852-107">下表列出的具名組件<xref:System.Windows.Controls.DocumentViewer>控制項。</span><span class="sxs-lookup"><span data-stu-id="45852-107">The following table lists the named parts for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
|<span data-ttu-id="45852-108">組件</span><span class="sxs-lookup"><span data-stu-id="45852-108">Part</span></span>|<span data-ttu-id="45852-109">類型</span><span class="sxs-lookup"><span data-stu-id="45852-109">Type</span></span>|<span data-ttu-id="45852-110">說明</span><span class="sxs-lookup"><span data-stu-id="45852-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="45852-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="45852-111">PART_ContentHost</span></span>|<xref:System.Windows.Controls.ScrollViewer>|<span data-ttu-id="45852-112">內容，而且可捲動區域。</span><span class="sxs-lookup"><span data-stu-id="45852-112">The content and scrolling area.</span></span>|  
|<span data-ttu-id="45852-113">PART_FindToolBarHost</span><span class="sxs-lookup"><span data-stu-id="45852-113">PART_FindToolBarHost</span></span>|<xref:System.Windows.Controls.ContentControl>|<span data-ttu-id="45852-114">搜尋方塊中，依預設底部。</span><span class="sxs-lookup"><span data-stu-id="45852-114">The search box, at the bottom by default.</span></span>|  
  
## <a name="documentviewer-states"></a><span data-ttu-id="45852-115">DocumentViewer 狀態</span><span class="sxs-lookup"><span data-stu-id="45852-115">DocumentViewer States</span></span>  
 <span data-ttu-id="45852-116">下表列出的視覺狀態<xref:System.Windows.Controls.DocumentViewer>控制項。</span><span class="sxs-lookup"><span data-stu-id="45852-116">The following table lists the visual states for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
|<span data-ttu-id="45852-117">VisualState 名稱</span><span class="sxs-lookup"><span data-stu-id="45852-117">VisualState Name</span></span>|<span data-ttu-id="45852-118">VisualStateGroup 名稱</span><span class="sxs-lookup"><span data-stu-id="45852-118">VisualStateGroup Name</span></span>|<span data-ttu-id="45852-119">描述</span><span class="sxs-lookup"><span data-stu-id="45852-119">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="45852-120">驗證</span><span class="sxs-lookup"><span data-stu-id="45852-120">Valid</span></span>|<span data-ttu-id="45852-121">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="45852-121">ValidationStates</span></span>|<span data-ttu-id="45852-122">此控制項會使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`false`。</span><span class="sxs-lookup"><span data-stu-id="45852-122">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="45852-123">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="45852-123">InvalidFocused</span></span>|<span data-ttu-id="45852-124">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="45852-124">ValidationStates</span></span>|<span data-ttu-id="45852-125"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`具有焦點的控制項。</span><span class="sxs-lookup"><span data-stu-id="45852-125">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="45852-126">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="45852-126">InvalidUnfocused</span></span>|<span data-ttu-id="45852-127">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="45852-127">ValidationStates</span></span>|<span data-ttu-id="45852-128"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`有控制項沒有焦點。</span><span class="sxs-lookup"><span data-stu-id="45852-128">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="documentviewer-controltemplate-example"></a><span data-ttu-id="45852-129">DocumentViewer ControlTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="45852-129">DocumentViewer ControlTemplate Example</span></span>  
 <span data-ttu-id="45852-130">下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.DocumentViewer>控制項。</span><span class="sxs-lookup"><span data-stu-id="45852-130">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#DocumentViewer](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/documentviewer.xaml#documentviewer)]  
  
 <span data-ttu-id="45852-131">上述範例使用下列一或多項資源。</span><span class="sxs-lookup"><span data-stu-id="45852-131">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="45852-132">如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](http://go.microsoft.com/fwlink/?LinkID=160041)。</span><span class="sxs-lookup"><span data-stu-id="45852-132">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45852-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45852-133">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="45852-134">控制項的樣式和範本</span><span class="sxs-lookup"><span data-stu-id="45852-134">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="45852-135">控制項自訂</span><span class="sxs-lookup"><span data-stu-id="45852-135">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="45852-136">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="45852-136">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="45852-137">透過建立 ControlTemplate 自訂現有控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="45852-137">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
