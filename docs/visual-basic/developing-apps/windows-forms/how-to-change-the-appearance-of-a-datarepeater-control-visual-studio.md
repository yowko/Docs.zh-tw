---
title: "如何：變更 DataRepeater 控制項的外觀 (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, customizing
- DataRepeater, changing run time appearance
ms.assetid: 2af6dfce-760b-489e-b863-8da967f315c3
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 585ff4c942185f3199fe6e9e47a4ebd9f1f0a478
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-appearance-of-a-datarepeater-control-visual-studio"></a><span data-ttu-id="7b67b-102">如何：變更 DataRepeater 控制項的外觀 (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="7b67b-102">How to: Change the Appearance of a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="7b67b-103">您可以變更的外觀<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項在設計階段藉由設定屬性，或在執行階段處理<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>事件。</span><span class="sxs-lookup"><span data-stu-id="7b67b-103">You can change the appearance of a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control at design time by setting properties or at run time by handling the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event.</span></span>  
  
 <span data-ttu-id="7b67b-104">您在設計階段選取控制項的項目範本區段時設定的屬性會針對每個重複<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>在執行階段。</span><span class="sxs-lookup"><span data-stu-id="7b67b-104">Properties that you set at design time when the item template section of the control is selected will be repeated for each <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> at run time.</span></span> <span data-ttu-id="7b67b-105">將屬性與外觀相關的<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項本身會顯示在執行階段容器的部分才將處於未涵蓋範圍 (例如，如果<xref:System.Windows.Forms.Control.Padding%2A>屬性設定為較大的值)。</span><span class="sxs-lookup"><span data-stu-id="7b67b-105">Appearance-related properties of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control itself will be visible at run time only if a part of the container is left uncovered (for example, if the <xref:System.Windows.Forms.Control.Padding%2A> property is set to a large value).</span></span>  
  
 <span data-ttu-id="7b67b-106">在執行階段，與外觀相關的屬性可以是根據設定的條件。</span><span class="sxs-lookup"><span data-stu-id="7b67b-106">At run time, appearance-related properties can be set based on conditions.</span></span> <span data-ttu-id="7b67b-107">例如，在排程的應用程式中，您可能會變更項目過期的項目時，警告使用者的背景色彩。</span><span class="sxs-lookup"><span data-stu-id="7b67b-107">For example, in a scheduling application, you might change the background color of an item to warn users when an item is past due.</span></span> <span data-ttu-id="7b67b-108">在<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>事件處理常式，如果您將屬性設定條件陳述式，例如`If…Then`，您也必須使用`Else`子句來指定當不符合條件的外觀。</span><span class="sxs-lookup"><span data-stu-id="7b67b-108">In the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event handler, if you set a property in a conditional statement such as `If…Then`, you must also use an `Else` clause to specify the appearance when the condition is not met.</span></span>  
  
### <a name="to-change-the-appearance-at-design-time"></a><span data-ttu-id="7b67b-109">若要變更設計階段外觀</span><span class="sxs-lookup"><span data-stu-id="7b67b-109">To change the appearance at design time</span></span>  
  
1.  <span data-ttu-id="7b67b-110">在 Windows Form 設計工具中，選取的項目範本 （上方） 區域<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。</span><span class="sxs-lookup"><span data-stu-id="7b67b-110">In the Windows Forms Designer, select the item template (upper) region of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
2.  <span data-ttu-id="7b67b-111">在 [屬性] 視窗中，選取屬性，變更值。</span><span class="sxs-lookup"><span data-stu-id="7b67b-111">In the Properties window, select a property and change the value.</span></span> <span data-ttu-id="7b67b-112">影響外觀的通用屬性包括<xref:System.Windows.Forms.Control.BackColor%2A>， <xref:System.Windows.Forms.Control.BackgroundImage%2A>， <xref:System.Windows.Forms.Panel.BorderStyle%2A>，和<xref:System.Windows.Forms.Control.ForeColor%2A>。</span><span class="sxs-lookup"><span data-stu-id="7b67b-112">Common properties that affect appearance include <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Panel.BorderStyle%2A>, and <xref:System.Windows.Forms.Control.ForeColor%2A>.</span></span>  
  
### <a name="to-change-the-appearance-at-run-time"></a><span data-ttu-id="7b67b-113">若要變更執行階段外觀</span><span class="sxs-lookup"><span data-stu-id="7b67b-113">To change the appearance at run time</span></span>  
  
1.  <span data-ttu-id="7b67b-114">在 [程式碼編輯器] 中，按一下 [事件] 下拉式清單中的 [DrawItem] 。</span><span class="sxs-lookup"><span data-stu-id="7b67b-114">In the Code Editor, in the Event drop-down list, click **DrawItem**.</span></span>  
  
2.  <span data-ttu-id="7b67b-115">在<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>事件處理常式，加入程式碼來設定屬性：</span><span class="sxs-lookup"><span data-stu-id="7b67b-115">In the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event handler, add code to set the properties:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterAppearance#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterAppearance#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="7b67b-116">範例</span><span class="sxs-lookup"><span data-stu-id="7b67b-116">Example</span></span>  
 <span data-ttu-id="7b67b-117">某些常見的自訂<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項包含替代色彩的方式和變更的色彩為基礎的欄位中顯示資料列。</span><span class="sxs-lookup"><span data-stu-id="7b67b-117">Some common customizations for the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control include displaying the rows in alternating colors and changing the color of a field based on a condition.</span></span> <span data-ttu-id="7b67b-118">下列範例會示範如何執行這些自訂項目。</span><span class="sxs-lookup"><span data-stu-id="7b67b-118">The following example shows how to perform these customizations.</span></span> <span data-ttu-id="7b67b-119">這個範例假設您有<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>繫結至 Northwind 資料庫中的 [產品] 資料表的控制項。</span><span class="sxs-lookup"><span data-stu-id="7b67b-119">This example assumes that you have a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control that is bound to the Products table in the Northwind database.</span></span>  
  
 [!code-vb[VbPowerPacksDataRepeaterAlternateBackColor#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_2.vb)]
 [!code-csharp[VbPowerPacksDataRepeaterAlternateBackColor#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_2.cs)]  
  
 <span data-ttu-id="7b67b-120">請注意，這兩個自訂項目，您必須提供程式碼以設定條件的兩端的屬性。</span><span class="sxs-lookup"><span data-stu-id="7b67b-120">Note that for both of these customizations, you must provide code to set the properties for both sides of the condition.</span></span> <span data-ttu-id="7b67b-121">如果您未指定`Else`條件，您會看到非預期的結果在執行階段。</span><span class="sxs-lookup"><span data-stu-id="7b67b-121">If you do not specify the `Else` condition, you will see unexpected results at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b67b-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b67b-122">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>  
 [<span data-ttu-id="7b67b-123">DataRepeater 控制項簡介</span><span class="sxs-lookup"><span data-stu-id="7b67b-123">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="7b67b-124"> DataRepeater 控制項進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="7b67b-124">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="7b67b-125">操作說明：在 DataRepeater 控制項中顯示繫結資料</span><span class="sxs-lookup"><span data-stu-id="7b67b-125">How to: Display Bound Data in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="7b67b-126">操作說明：在 DataRepeater 控制項中顯示未繫結的控制項</span><span class="sxs-lookup"><span data-stu-id="7b67b-126">How to: Display Unbound Controls in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="7b67b-127">操作說明：在 DataRepeater 控制項中顯示項目標題</span><span class="sxs-lookup"><span data-stu-id="7b67b-127">How to: Display Item Headers in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)
