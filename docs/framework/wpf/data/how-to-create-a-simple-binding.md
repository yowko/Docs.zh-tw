---
title: 如何：建立簡單繫結
description: 透過 Windows Presentation Foundation （WPF）中的此作法範例，為您的應用程式建立簡單的系結。
ms.date: 03/30/2017
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
ms.openlocfilehash: 63dc44b442bb4658382bf12faf57b51c8e0698bb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618697"
---
# <a name="how-to-create-a-simple-binding"></a><span data-ttu-id="c465a-103">如何：建立簡單繫結</span><span class="sxs-lookup"><span data-stu-id="c465a-103">How to: Create a Simple Binding</span></span>
<span data-ttu-id="c465a-104">這個範例會示範如何建立簡單的 <xref:System.Windows.Data.Binding> 。</span><span class="sxs-lookup"><span data-stu-id="c465a-104">This example shows you how to create a simple <xref:System.Windows.Data.Binding>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c465a-105">範例</span><span class="sxs-lookup"><span data-stu-id="c465a-105">Example</span></span>  
 <span data-ttu-id="c465a-106">在此範例中，您的 `Person` 物件具有名為的字串屬性 `PersonName` 。</span><span class="sxs-lookup"><span data-stu-id="c465a-106">In this example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="c465a-107">`Person`物件是在名為的命名空間中定義 `SDKSample` 。</span><span class="sxs-lookup"><span data-stu-id="c465a-107">The `Person` object is defined in the namespace called `SDKSample`.</span></span>  
  
 <span data-ttu-id="c465a-108">在下列範例中包含元素的反白顯示行會 `<src>` 具現化 `Person` 具有 `PersonName` 屬性值的物件 `Joe` 。</span><span class="sxs-lookup"><span data-stu-id="c465a-108">The highlighted line that contains the `<src>` element in the following example instantiates the `Person` object with a `PersonName` property value of `Joe`.</span></span> <span data-ttu-id="c465a-109">這會在區段中完成 `Resources` ，並指派 `x:Key` 。</span><span class="sxs-lookup"><span data-stu-id="c465a-109">This is done in the `Resources` section and assigned an `x:Key`.</span></span>  
  
 [!code-xaml[SimpleBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <span data-ttu-id="c465a-110">包含元素的反白顯示行接著會將控制項系結 `<TextBlock>` <xref:System.Windows.Controls.TextBlock> 至 `PersonName` 屬性。</span><span class="sxs-lookup"><span data-stu-id="c465a-110">The highlighted line that contains the `<TextBlock>` element then binds the <xref:System.Windows.Controls.TextBlock> control to the `PersonName` property.</span></span> <span data-ttu-id="c465a-111">因此， <xref:System.Windows.Controls.TextBlock> 會顯示值為 "Joe" 的。</span><span class="sxs-lookup"><span data-stu-id="c465a-111">As a result, the <xref:System.Windows.Controls.TextBlock> appears with the value "Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c465a-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c465a-112">See also</span></span>

- [<span data-ttu-id="c465a-113">資料系結總覽</span><span class="sxs-lookup"><span data-stu-id="c465a-113">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="c465a-114">操作說明主題</span><span class="sxs-lookup"><span data-stu-id="c465a-114">How-to Topics</span></span>](data-binding-how-to-topics.md)
