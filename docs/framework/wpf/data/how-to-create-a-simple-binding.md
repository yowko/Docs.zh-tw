---
title: HOW TO：建立簡單繫結
ms.date: 03/30/2017
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
ms.openlocfilehash: d617c8b97aa679398ed2d061a652f5164f1e499b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61931558"
---
# <a name="how-to-create-a-simple-binding"></a><span data-ttu-id="65766-102">HOW TO：建立簡單繫結</span><span class="sxs-lookup"><span data-stu-id="65766-102">How to: Create a Simple Binding</span></span>
<span data-ttu-id="65766-103">此範例將示範如何建立簡單<xref:System.Windows.Data.Binding>。</span><span class="sxs-lookup"><span data-stu-id="65766-103">This example shows you how to create a simple <xref:System.Windows.Data.Binding>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="65766-104">範例</span><span class="sxs-lookup"><span data-stu-id="65766-104">Example</span></span>  
 <span data-ttu-id="65766-105">在此範例中，您必須`Person`物件具有名為字串屬性`PersonName`。</span><span class="sxs-lookup"><span data-stu-id="65766-105">In this example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="65766-106">`Person`物件定義在命名空間中`SDKSample`。</span><span class="sxs-lookup"><span data-stu-id="65766-106">The `Person` object is defined in the namespace called `SDKSample`.</span></span>  
  
 <span data-ttu-id="65766-107">反白顯示包含的那一行`<src>`項目，在下列範例會具現化`Person`物件`PersonName`屬性值為`Joe`。</span><span class="sxs-lookup"><span data-stu-id="65766-107">The highlighted line that contains the `<src>` element in the following example instantiates the `Person` object with a `PersonName` property value of `Joe`.</span></span> <span data-ttu-id="65766-108">這在完成`Resources`區段，然後指派`x:Key`。</span><span class="sxs-lookup"><span data-stu-id="65766-108">This is done in the `Resources` section and assigned an `x:Key`.</span></span>  
  
 [!code-xaml[SimpleBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <span data-ttu-id="65766-109">包含反白顯示的列`<TextBlock>`項目再將繫結<xref:System.Windows.Controls.TextBlock>若要控制`PersonName`屬性。</span><span class="sxs-lookup"><span data-stu-id="65766-109">The highlighted line that contains the `<TextBlock>` element then binds the <xref:System.Windows.Controls.TextBlock> control to the `PersonName` property.</span></span> <span data-ttu-id="65766-110">如此一來， <xref:System.Windows.Controls.TextBlock> "Joe"的值會出現。</span><span class="sxs-lookup"><span data-stu-id="65766-110">As a result, the <xref:System.Windows.Controls.TextBlock> appears with the value "Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65766-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="65766-111">See also</span></span>

- [<span data-ttu-id="65766-112">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="65766-112">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="65766-113">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="65766-113">How-to Topics</span></span>](data-binding-how-to-topics.md)
