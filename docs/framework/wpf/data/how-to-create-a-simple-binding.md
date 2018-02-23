---
title: "如何：建立簡單繫結"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a595f255b014e08b4b5b2036a7b1940e46df268f
ms.sourcegitcommit: 973a12d1e6962cd9a9c263fbfaad040ec8267fe9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2018
---
# <a name="how-to-create-a-simple-binding"></a><span data-ttu-id="01bbd-102">如何：建立簡單繫結</span><span class="sxs-lookup"><span data-stu-id="01bbd-102">How to: Create a Simple Binding</span></span>
<span data-ttu-id="01bbd-103">此範例將示範如何建立簡單<xref:System.Windows.Data.Binding>。</span><span class="sxs-lookup"><span data-stu-id="01bbd-103">This example shows you how to create a simple <xref:System.Windows.Data.Binding>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01bbd-104">範例</span><span class="sxs-lookup"><span data-stu-id="01bbd-104">Example</span></span>  
 <span data-ttu-id="01bbd-105">在此範例中，您必須`Person`物件具有名為字串屬性`PersonName`。</span><span class="sxs-lookup"><span data-stu-id="01bbd-105">In this example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="01bbd-106">`Person`物件定義在命名空間稱為`SDKSample`。</span><span class="sxs-lookup"><span data-stu-id="01bbd-106">The `Person` object is defined in the namespace called `SDKSample`.</span></span>  
  
 <span data-ttu-id="01bbd-107">包含反白顯示的列`<src>`項目，在下列範例會具現化`Person`物件`PersonName`屬性值為`Joe`。</span><span class="sxs-lookup"><span data-stu-id="01bbd-107">The highlighted line that contains the `<src>` element in the following example instantiates the `Person` object with a `PersonName` property value of `Joe`.</span></span> <span data-ttu-id="01bbd-108">這是`Resources`區段，並指派`x:Key`。</span><span class="sxs-lookup"><span data-stu-id="01bbd-108">This is done in the `Resources` section and assigned an `x:Key`.</span></span>  
  
 [!code-xaml[SimpleBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <span data-ttu-id="01bbd-109">包含反白顯示的列`<TextBlock>`接著繫結項目<xref:System.Windows.Controls.TextBlock>控制權傳輸至`PersonName`屬性。</span><span class="sxs-lookup"><span data-stu-id="01bbd-109">The highlighted line that contains the `<TextBlock>` element then binds the <xref:System.Windows.Controls.TextBlock> control to the `PersonName` property.</span></span> <span data-ttu-id="01bbd-110">如此一來，<xref:System.Windows.Controls.TextBlock>隨即出現，並 「 Joe"的值。</span><span class="sxs-lookup"><span data-stu-id="01bbd-110">As a result, the <xref:System.Windows.Controls.TextBlock> appears with the value "Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01bbd-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="01bbd-111">See Also</span></span>  
 [<span data-ttu-id="01bbd-112">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="01bbd-112">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="01bbd-113">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="01bbd-113">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
