---
title: 如何：使用 FontSizeConverter 類別
ms.date: 03/30/2017
helpviewer_keywords:
- FontSizeConverter objects [WPF]
- typography [WPF], FontSizeConverter objects
ms.assetid: 3b0592bd-7223-4860-a108-a5d72f3a9178
ms.openlocfilehash: 625beb06b526e2753abc6f982cf5834bfae1f202
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545122"
---
# <a name="how-to-use-the-fontsizeconverter-class"></a><span data-ttu-id="d3a90-102">如何：使用 FontSizeConverter 類別</span><span class="sxs-lookup"><span data-stu-id="d3a90-102">How to: Use the FontSizeConverter Class</span></span>
## <a name="example"></a><span data-ttu-id="d3a90-103">範例</span><span class="sxs-lookup"><span data-stu-id="d3a90-103">Example</span></span>  
 <span data-ttu-id="d3a90-104">這個範例示範如何建立的執行個體<xref:System.Windows.FontSizeConverter>並用它來變更字型的大小。</span><span class="sxs-lookup"><span data-stu-id="d3a90-104">This example shows how to create an instance of <xref:System.Windows.FontSizeConverter> and use it to change a font size.</span></span>  
  
 <span data-ttu-id="d3a90-105">此範例會定義自訂的方法呼叫`changeSize`將轉換的內容<xref:System.Windows.Controls.ListBoxItem>定義在個別[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]檔案，以執行個體<xref:System.Double>，及更新版本為<xref:System.String>。</span><span class="sxs-lookup"><span data-stu-id="d3a90-105">The example defines a custom method called `changeSize` that converts the contents of a <xref:System.Windows.Controls.ListBoxItem>, as defined in a separate [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file, to an instance of <xref:System.Double>, and later into a <xref:System.String>.</span></span> <span data-ttu-id="d3a90-106">這個方法會傳遞<xref:System.Windows.Controls.ListBoxItem>至<xref:System.Windows.FontSizeConverter>物件，然後將轉換<xref:System.Windows.Controls.ContentControl.Content%2A>的<xref:System.Windows.Controls.ListBoxItem>的執行個體<xref:System.Double>。</span><span class="sxs-lookup"><span data-stu-id="d3a90-106">This method passes the <xref:System.Windows.Controls.ListBoxItem> to a <xref:System.Windows.FontSizeConverter> object, which converts the <xref:System.Windows.Controls.ContentControl.Content%2A> of a <xref:System.Windows.Controls.ListBoxItem> to an instance of <xref:System.Double>.</span></span> <span data-ttu-id="d3a90-107">此值接著會傳遞做為值回<xref:System.Windows.Controls.TextBlock.FontSize%2A>屬性<xref:System.Windows.Controls.TextBlock>項目。</span><span class="sxs-lookup"><span data-stu-id="d3a90-107">This value is then passed back as the value of the <xref:System.Windows.Controls.TextBlock.FontSize%2A> property of the <xref:System.Windows.Controls.TextBlock> element.</span></span>  
  
 <span data-ttu-id="d3a90-108">這個範例也會定義呼叫的第二個自訂方法`changeFamily`。</span><span class="sxs-lookup"><span data-stu-id="d3a90-108">This example also defines a second custom method that is called `changeFamily`.</span></span> <span data-ttu-id="d3a90-109">這個方法會將轉換<xref:System.Windows.Controls.ContentControl.Content%2A>的<xref:System.Windows.Controls.ListBoxItem>至<xref:System.String>，然後將傳送至該值<xref:System.Windows.Controls.TextBlock.FontFamily%2A>屬性<xref:System.Windows.Controls.TextBlock>項目。</span><span class="sxs-lookup"><span data-stu-id="d3a90-109">This method converts the <xref:System.Windows.Controls.ContentControl.Content%2A> of the <xref:System.Windows.Controls.ListBoxItem> to a <xref:System.String>, and then passes that value to the <xref:System.Windows.Controls.TextBlock.FontFamily%2A> property of the <xref:System.Windows.Controls.TextBlock> element.</span></span>  
  
 <span data-ttu-id="d3a90-110">此範例不會執行。</span><span class="sxs-lookup"><span data-stu-id="d3a90-110">This example does not run.</span></span>  
  
 [!code-csharp[FontSizeConverter#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSizeConverter/CSharp/Window1.xaml.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d3a90-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3a90-111">See Also</span></span>  
 <xref:System.Windows.FontSizeConverter>
