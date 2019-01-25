---
title: HOW TO：定義 GroupBox 範本
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], GroupBox
- GroupBox control [WPF], creating templates
ms.assetid: 85a4d1a7-4753-4f4a-b26d-14fa10c1ddb5
ms.openlocfilehash: 0e1b0487629bba3550a8b6b4a31c163a7ade6a87
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54743714"
---
# <a name="how-to-define-a-groupbox-template"></a><span data-ttu-id="0939b-102">HOW TO：定義 GroupBox 範本</span><span class="sxs-lookup"><span data-stu-id="0939b-102">How to: Define a GroupBox Template</span></span>
<span data-ttu-id="0939b-103">此範例示範如何建立範本<xref:System.Windows.Controls.GroupBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="0939b-103">This example shows how to create a template for a <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0939b-104">範例</span><span class="sxs-lookup"><span data-stu-id="0939b-104">Example</span></span>  
 <span data-ttu-id="0939b-105">下列範例會定義<xref:System.Windows.Controls.GroupBox>使用的控制項範本<xref:System.Windows.Controls.Grid>版面配置控制項。</span><span class="sxs-lookup"><span data-stu-id="0939b-105">The following example defines a <xref:System.Windows.Controls.GroupBox> control template by using a <xref:System.Windows.Controls.Grid> control for layout.</span></span> <span data-ttu-id="0939b-106">此範本會使用<xref:System.Windows.Controls.BorderGapMaskConverter>定義的框線<xref:System.Windows.Controls.GroupBox>以便框線不會不會遮住<xref:System.Windows.Controls.HeaderedContentControl.Header%2A>內容。</span><span class="sxs-lookup"><span data-stu-id="0939b-106">The template uses a <xref:System.Windows.Controls.BorderGapMaskConverter> to define the border of the <xref:System.Windows.Controls.GroupBox> so that the border does not obscure the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> content.</span></span>  
  
 [!code-xaml[GroupBoxSnippet#GroupBoxTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#groupboxtemplate)]  
  
## <a name="see-also"></a><span data-ttu-id="0939b-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0939b-107">See also</span></span>
- <xref:System.Windows.Controls.GroupBox>
- [<span data-ttu-id="0939b-108">GroupBox how to 主題</span><span class="sxs-lookup"><span data-stu-id="0939b-108">GroupBox How-to Topics</span></span>](https://msdn.microsoft.com/library/7692e155-a4c6-428c-b7e0-64b3740daca7)
