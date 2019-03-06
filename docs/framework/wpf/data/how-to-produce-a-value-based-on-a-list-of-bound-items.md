---
title: HOW TO：根據繫結項目的清單產生值
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], MultiBinding
- Multibinding [WPF]
ms.assetid: b3d06378-b511-4181-95aa-316d60c9229b
ms.openlocfilehash: 77c832c1460749ced58e7a20af333c5ed9dd1555
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368121"
---
# <a name="how-to-produce-a-value-based-on-a-list-of-bound-items"></a><span data-ttu-id="7d9a1-102">HOW TO：根據繫結項目的清單產生值</span><span class="sxs-lookup"><span data-stu-id="7d9a1-102">How to: Produce a Value Based on a List of Bound Items</span></span>
<span data-ttu-id="7d9a1-103"><xref:System.Windows.Data.MultiBinding> 可讓您將繫結目標屬性繫結來源屬性的清單，然後套用邏輯以產生具有指定的輸入值。</span><span class="sxs-lookup"><span data-stu-id="7d9a1-103"><xref:System.Windows.Data.MultiBinding> allows you to bind a binding target property to a list of source properties and then apply logic to produce a value with the given inputs.</span></span> <span data-ttu-id="7d9a1-104">此範例示範如何使用<xref:System.Windows.Data.MultiBinding>。</span><span class="sxs-lookup"><span data-stu-id="7d9a1-104">This example demonstrates how to use <xref:System.Windows.Data.MultiBinding>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d9a1-105">範例</span><span class="sxs-lookup"><span data-stu-id="7d9a1-105">Example</span></span>  
 <span data-ttu-id="7d9a1-106">在下列範例中，`NameListData` 參考 `PersonName` 物件的集合，這些物件都包含兩個屬性：`firstName` 和 `lastName`。</span><span class="sxs-lookup"><span data-stu-id="7d9a1-106">In the following example, `NameListData` refers to a collection of `PersonName` objects, which are objects that contain two properties, `firstName` and `lastName`.</span></span> <span data-ttu-id="7d9a1-107">下列範例會產生<xref:System.Windows.Controls.TextBlock>，會顯示第一個和最後一個名稱的個人姓氏第一個。</span><span class="sxs-lookup"><span data-stu-id="7d9a1-107">The following example produces a <xref:System.Windows.Controls.TextBlock> that shows the first and last names of a person with the last name first.</span></span>  
  
 [!code-xaml[MultiBinding#Resources1](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources1)]  
[!code-xaml[MultiBinding#Resources2](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources2)]  
[!code-xaml[MultiBinding#MultiBindingTextBox2](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#multibindingtextbox2)]  
[!code-xaml[MultiBinding#Window](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#window)]  
  
 <span data-ttu-id="7d9a1-108">為了解姓氏-名字格式是如何產生，我們一起看看 `NameConverter` 的實作：</span><span class="sxs-lookup"><span data-stu-id="7d9a1-108">To understand how the last-name-first format is produced, let's take a look at the implementation of the `NameConverter`:</span></span>  
  
 [!code-csharp[MultiBinding#3](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/NameConverter.cs#3)]
 [!code-vb[MultiBinding#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MultiBinding/VisualBasic/NameConverter.vb#3)]  
  
 <span data-ttu-id="7d9a1-109">`NameConverter` 會實作 <xref:System.Windows.Data.IMultiValueConverter> 介面。</span><span class="sxs-lookup"><span data-stu-id="7d9a1-109">`NameConverter` implements the <xref:System.Windows.Data.IMultiValueConverter> interface.</span></span> <span data-ttu-id="7d9a1-110">`NameConverter` 會從個別繫結取得值，然後將這些值儲存在 values 物件陣列中。</span><span class="sxs-lookup"><span data-stu-id="7d9a1-110">`NameConverter` takes the values from the individual bindings and stores them in the values object array.</span></span> <span data-ttu-id="7d9a1-111">順序<xref:System.Windows.Data.Binding>項目會出現在<xref:System.Windows.Data.MultiBinding>項目是陣列中儲存這些值的順序。</span><span class="sxs-lookup"><span data-stu-id="7d9a1-111">The order in which the <xref:System.Windows.Data.Binding> elements appear under the <xref:System.Windows.Data.MultiBinding> element is the order in which those values are stored in the array.</span></span> <span data-ttu-id="7d9a1-112">值<xref:System.Windows.Data.MultiBinding.ConverterParameter%2A>的 [參數] 引數所參考屬性<xref:System.Windows.Data.MultiBinding.Converter%2A>方法，對參數以決定如何格式化名稱的參數。</span><span class="sxs-lookup"><span data-stu-id="7d9a1-112">The value of the <xref:System.Windows.Data.MultiBinding.ConverterParameter%2A> attribute is referenced by the parameter argument of the <xref:System.Windows.Data.MultiBinding.Converter%2A> method, which performs a switch on the parameter to determine how to format the name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d9a1-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7d9a1-113">See also</span></span>
- [<span data-ttu-id="7d9a1-114">轉換繫結的資料</span><span class="sxs-lookup"><span data-stu-id="7d9a1-114">Convert Bound Data</span></span>](how-to-convert-bound-data.md)
- [<span data-ttu-id="7d9a1-115">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="7d9a1-115">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="7d9a1-116">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="7d9a1-116">How-to Topics</span></span>](data-binding-how-to-topics.md)
