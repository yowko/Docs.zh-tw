---
title: 如何：建立簡單繫結
ms.date: 03/30/2017
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
ms.openlocfilehash: faef59ed426059eb2d488d0584d3325c8d46d415
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73453506"
---
# <a name="how-to-create-a-simple-binding"></a><span data-ttu-id="ca8c7-102">如何：建立簡單繫結</span><span class="sxs-lookup"><span data-stu-id="ca8c7-102">How to: Create a Simple Binding</span></span>
<span data-ttu-id="ca8c7-103">這個範例會示範如何建立簡單的 <xref:System.Windows.Data.Binding>。</span><span class="sxs-lookup"><span data-stu-id="ca8c7-103">This example shows you how to create a simple <xref:System.Windows.Data.Binding>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca8c7-104">範例</span><span class="sxs-lookup"><span data-stu-id="ca8c7-104">Example</span></span>  
 <span data-ttu-id="ca8c7-105">在此範例中，您有一個 `Person` 物件，其中具有名為 `PersonName`的字串屬性。</span><span class="sxs-lookup"><span data-stu-id="ca8c7-105">In this example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="ca8c7-106">`Person` 物件是在名為 `SDKSample`的命名空間中定義。</span><span class="sxs-lookup"><span data-stu-id="ca8c7-106">The `Person` object is defined in the namespace called `SDKSample`.</span></span>  
  
 <span data-ttu-id="ca8c7-107">在下列範例中包含 `<src>` 元素的反白顯示行，會以 `Joe`的 `PersonName` 屬性值來具現化 `Person` 物件。</span><span class="sxs-lookup"><span data-stu-id="ca8c7-107">The highlighted line that contains the `<src>` element in the following example instantiates the `Person` object with a `PersonName` property value of `Joe`.</span></span> <span data-ttu-id="ca8c7-108">這會在 `Resources` 區段中完成，並指派 `x:Key`。</span><span class="sxs-lookup"><span data-stu-id="ca8c7-108">This is done in the `Resources` section and assigned an `x:Key`.</span></span>  
  
 [!code-xaml[SimpleBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <span data-ttu-id="ca8c7-109">包含 `<TextBlock>` 元素的反白顯示行，接著會將 <xref:System.Windows.Controls.TextBlock> 控制項系結至 `PersonName` 屬性。</span><span class="sxs-lookup"><span data-stu-id="ca8c7-109">The highlighted line that contains the `<TextBlock>` element then binds the <xref:System.Windows.Controls.TextBlock> control to the `PersonName` property.</span></span> <span data-ttu-id="ca8c7-110">因此，<xref:System.Windows.Controls.TextBlock> 會出現 "Joe" 值。</span><span class="sxs-lookup"><span data-stu-id="ca8c7-110">As a result, the <xref:System.Windows.Controls.TextBlock> appears with the value "Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca8c7-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="ca8c7-111">See also</span></span>

- [<span data-ttu-id="ca8c7-112">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="ca8c7-112">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="ca8c7-113">「如何」主題</span><span class="sxs-lookup"><span data-stu-id="ca8c7-113">How-to Topics</span></span>](data-binding-how-to-topics.md)
