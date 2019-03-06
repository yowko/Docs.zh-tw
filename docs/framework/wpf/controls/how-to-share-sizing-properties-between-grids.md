---
title: HOW TO：在格線之間共用調整大小屬性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], sharing sizing data of columns
- sizing data in Grid controls [WPF]
- Grid control [WPF], sharing sizing data of rows
ms.assetid: a0535a6f-ff04-4b25-9912-7dd856e11044
ms.openlocfilehash: bd0f812ce9a15628bd0bddf3a88e898311f0a9d3
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57373123"
---
# <a name="how-to-share-sizing-properties-between-grids"></a><span data-ttu-id="a6004-102">HOW TO：在格線之間共用調整大小屬性</span><span class="sxs-lookup"><span data-stu-id="a6004-102">How to: Share Sizing Properties Between Grids</span></span>
<span data-ttu-id="a6004-103">本範例顯示如何共用調整大小資料行資料和資料列之間<xref:System.Windows.Controls.Grid>為了保留以一致的調整大小的項目。</span><span class="sxs-lookup"><span data-stu-id="a6004-103">This example shows how to share the sizing data of columns and rows between <xref:System.Windows.Controls.Grid> elements in order to keep sizing consistent.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6004-104">範例</span><span class="sxs-lookup"><span data-stu-id="a6004-104">Example</span></span>  
 <span data-ttu-id="a6004-105">下列範例介紹兩個<xref:System.Windows.Controls.Grid>項目與子項目的父代<xref:System.Windows.Controls.DockPanel>。</span><span class="sxs-lookup"><span data-stu-id="a6004-105">The following example introduces two <xref:System.Windows.Controls.Grid> elements as child elements of a parent <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="a6004-106"><xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A>附加屬性<xref:System.Windows.Controls.Grid>定義父代上<xref:System.Windows.Controls.DockPanel>。</span><span class="sxs-lookup"><span data-stu-id="a6004-106">The <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> attached property of <xref:System.Windows.Controls.Grid> is defined on the parent <xref:System.Windows.Controls.DockPanel>.</span></span>  
  
 <span data-ttu-id="a6004-107">此範例使用兩個操作屬性值<xref:System.Windows.Controls.Button>項目; 每個項目代表一個布林屬性值。</span><span class="sxs-lookup"><span data-stu-id="a6004-107">The example manipulates the property value by using two <xref:System.Windows.Controls.Button> elements; each element represents one of the Boolean property values.</span></span> <span data-ttu-id="a6004-108">當<xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A>屬性值設定為`true`，每個資料行或資料列成員<xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A>共用調整大小的資訊，不論資料列或資料行的內容。</span><span class="sxs-lookup"><span data-stu-id="a6004-108">When the <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> property value is set to `true`, each column or row member of a <xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A> shares sizing information, regardless of the content of a row or column.</span></span>  
  
 [!code-xaml[gridIssharedsizescopeProp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="a6004-109">...</span><span class="sxs-lookup"><span data-stu-id="a6004-109">...</span></span>  
  
 [!code-xaml[gridIssharedsizescopeProp#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="a6004-110">下列範例中，程式碼後置處理方法的按鈕<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件所引發。</span><span class="sxs-lookup"><span data-stu-id="a6004-110">The following code-behind example handles the methods that the button <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event raises.</span></span> <span data-ttu-id="a6004-111">此範例將方法呼叫的結果寫入<xref:System.Windows.Controls.TextBlock>使用相關的項目 get 方法，以輸出新的屬性值為字串。</span><span class="sxs-lookup"><span data-stu-id="a6004-111">The example writes the results of these method calls to <xref:System.Windows.Controls.TextBlock> elements that use related get methods to output the new property values as strings.</span></span>  
  
 [!code-csharp[gridIssharedsizescopeProp#3](~/samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml.cs#3)]
 [!code-vb[gridIssharedsizescopeProp#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gridIssharedsizescopeProp/VisualBasic/Window1.xaml.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="a6004-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6004-112">See also</span></span>
- <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A>
- [<span data-ttu-id="a6004-113">面板概觀</span><span class="sxs-lookup"><span data-stu-id="a6004-113">Panels Overview</span></span>](panels-overview.md)
