---
title: HOW TO：使用 FontSizeConverter 類別
ms.date: 03/30/2017
helpviewer_keywords:
- FontSizeConverter objects [WPF]
- typography [WPF], FontSizeConverter objects
ms.assetid: 3b0592bd-7223-4860-a108-a5d72f3a9178
ms.openlocfilehash: f33a297ae07d5509d2b4d9a98636086ac433a57f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59088180"
---
# <a name="how-to-use-the-fontsizeconverter-class"></a><span data-ttu-id="76daa-102">HOW TO：使用 FontSizeConverter 類別</span><span class="sxs-lookup"><span data-stu-id="76daa-102">How to: Use the FontSizeConverter Class</span></span>
## <a name="example"></a><span data-ttu-id="76daa-103">範例</span><span class="sxs-lookup"><span data-stu-id="76daa-103">Example</span></span>  
 <span data-ttu-id="76daa-104">此範例示範如何建立的執行個體<xref:System.Windows.FontSizeConverter>並用它來變更字型大小。</span><span class="sxs-lookup"><span data-stu-id="76daa-104">This example shows how to create an instance of <xref:System.Windows.FontSizeConverter> and use it to change a font size.</span></span>  
  
 <span data-ttu-id="76daa-105">此範例會定義呼叫的自訂方法`changeSize`可將轉換的內容<xref:System.Windows.Controls.ListBoxItem>，因為定義於個別[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]檔案，以執行個體<xref:System.Double>，和更新版本到<xref:System.String>。</span><span class="sxs-lookup"><span data-stu-id="76daa-105">The example defines a custom method called `changeSize` that converts the contents of a <xref:System.Windows.Controls.ListBoxItem>, as defined in a separate [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file, to an instance of <xref:System.Double>, and later into a <xref:System.String>.</span></span> <span data-ttu-id="76daa-106">此方法會傳遞<xref:System.Windows.Controls.ListBoxItem>要<xref:System.Windows.FontSizeConverter>物件，然後將轉換<xref:System.Windows.Controls.ContentControl.Content%2A>的<xref:System.Windows.Controls.ListBoxItem>的執行個體<xref:System.Double>。</span><span class="sxs-lookup"><span data-stu-id="76daa-106">This method passes the <xref:System.Windows.Controls.ListBoxItem> to a <xref:System.Windows.FontSizeConverter> object, which converts the <xref:System.Windows.Controls.ContentControl.Content%2A> of a <xref:System.Windows.Controls.ListBoxItem> to an instance of <xref:System.Double>.</span></span> <span data-ttu-id="76daa-107">此值接著會傳遞的值<xref:System.Windows.Controls.TextBlock.FontSize%2A>屬性<xref:System.Windows.Controls.TextBlock>項目。</span><span class="sxs-lookup"><span data-stu-id="76daa-107">This value is then passed back as the value of the <xref:System.Windows.Controls.TextBlock.FontSize%2A> property of the <xref:System.Windows.Controls.TextBlock> element.</span></span>  
  
 <span data-ttu-id="76daa-108">此範例也會定義第二個自訂方法，稱為`changeFamily`。</span><span class="sxs-lookup"><span data-stu-id="76daa-108">This example also defines a second custom method that is called `changeFamily`.</span></span> <span data-ttu-id="76daa-109">這個方法會轉換<xref:System.Windows.Controls.ContentControl.Content%2A>的<xref:System.Windows.Controls.ListBoxItem>要<xref:System.String>，然後將該值傳遞<xref:System.Windows.Controls.TextBlock.FontFamily%2A>屬性<xref:System.Windows.Controls.TextBlock>項目。</span><span class="sxs-lookup"><span data-stu-id="76daa-109">This method converts the <xref:System.Windows.Controls.ContentControl.Content%2A> of the <xref:System.Windows.Controls.ListBoxItem> to a <xref:System.String>, and then passes that value to the <xref:System.Windows.Controls.TextBlock.FontFamily%2A> property of the <xref:System.Windows.Controls.TextBlock> element.</span></span>  
  
 <span data-ttu-id="76daa-110">此範例不會執行。</span><span class="sxs-lookup"><span data-stu-id="76daa-110">This example does not run.</span></span>  
  
 [!code-csharp[FontSizeConverter#1](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSizeConverter/CSharp/Window1.xaml.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="76daa-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76daa-111">See also</span></span>

- <xref:System.Windows.FontSizeConverter>
