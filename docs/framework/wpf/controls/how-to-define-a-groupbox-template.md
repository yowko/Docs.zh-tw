---
title: HOW TO：定義 GroupBox 範本
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], GroupBox
- GroupBox control [WPF], creating templates
ms.assetid: 85a4d1a7-4753-4f4a-b26d-14fa10c1ddb5
ms.openlocfilehash: 6294a52d5914b52d191b564330f904e6a865c283
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2019
ms.locfileid: "56745194"
---
# <a name="how-to-define-a-groupbox-template"></a><span data-ttu-id="68b42-102">HOW TO：定義 GroupBox 範本</span><span class="sxs-lookup"><span data-stu-id="68b42-102">How to: Define a GroupBox Template</span></span>
<span data-ttu-id="68b42-103">此範例示範如何建立範本<xref:System.Windows.Controls.GroupBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="68b42-103">This example shows how to create a template for a <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="68b42-104">範例</span><span class="sxs-lookup"><span data-stu-id="68b42-104">Example</span></span>  
 <span data-ttu-id="68b42-105">下列範例會定義<xref:System.Windows.Controls.GroupBox>使用的控制項範本<xref:System.Windows.Controls.Grid>版面配置控制項。</span><span class="sxs-lookup"><span data-stu-id="68b42-105">The following example defines a <xref:System.Windows.Controls.GroupBox> control template by using a <xref:System.Windows.Controls.Grid> control for layout.</span></span> <span data-ttu-id="68b42-106">此範本會使用<xref:System.Windows.Controls.BorderGapMaskConverter>定義的框線<xref:System.Windows.Controls.GroupBox>以便框線不會不會遮住<xref:System.Windows.Controls.HeaderedContentControl.Header%2A>內容。</span><span class="sxs-lookup"><span data-stu-id="68b42-106">The template uses a <xref:System.Windows.Controls.BorderGapMaskConverter> to define the border of the <xref:System.Windows.Controls.GroupBox> so that the border does not obscure the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> content.</span></span>  
  
 [!code-xaml[GroupBoxSnippet#GroupBoxTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#groupboxtemplate)]  
  
## <a name="see-also"></a><span data-ttu-id="68b42-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68b42-107">See also</span></span>
- <xref:System.Windows.Controls.GroupBox>
- <span data-ttu-id="68b42-108">[如何：建立群組方塊](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms748321(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="68b42-108">[How to: Create a GroupBox](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms748321(v=vs.90))</span></span>
