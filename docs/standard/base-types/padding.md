---
title: 在 .NET 中填補字串
description: 瞭解如何在 .NET 中填補字串。 使用 PadLeft 和 PadRight 方法來新增開頭或尾端字元，以達到指定的總長度。
ms.date: 03/15/2018
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- strings [.NET], padding
- white space
- PadRight method
- PadLeft method
- padding strings
ms.assetid: 84a9f142-3244-4c90-ba02-21af9bbaff71
ms.openlocfilehash: b8dbea862acb87c1db2d23b11bac597eaa27d6b6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683780"
---
# <a name="padding-strings-in-net"></a><span data-ttu-id="e0436-104">在 .NET 中填補字串</span><span class="sxs-lookup"><span data-stu-id="e0436-104">Padding Strings in .NET</span></span>

<span data-ttu-id="e0436-105">使用下列其中一個 <xref:System.String> 方法來建立由原始字串組成的新字串，而原始字串會使用前置或後置字元填補至指定的總長度。</span><span class="sxs-lookup"><span data-stu-id="e0436-105">Use one of the following <xref:System.String> methods to create a new string that consists of an original string that is padded with leading or trailing characters to a specified total length.</span></span> <span data-ttu-id="e0436-106">填補字元可為空白或指定的字元。</span><span class="sxs-lookup"><span data-stu-id="e0436-106">The padding character can be a space or a specified character.</span></span> <span data-ttu-id="e0436-107">產生的字串會靠右或靠左顯示。</span><span class="sxs-lookup"><span data-stu-id="e0436-107">The resulting string appears to be either right-aligned or left-aligned.</span></span> <span data-ttu-id="e0436-108">若原始字串的長度已經大於或等於需要的總長度，則填補方法會傳回原封不動的原始字串。如需詳細資訊，請參閱 <xref:System.String.PadLeft%2A?displayProperty=nameWithType> 與 <xref:System.String.PadRight%2A?displayProperty=nameWithType> 這兩個多載方法的 **傳回** 一節。</span><span class="sxs-lookup"><span data-stu-id="e0436-108">If the original string's length is already equal to or greater than the desired total length, the padding methods return the original string unchanged; for more information, see the **Returns** sections of the two overloads of the <xref:System.String.PadLeft%2A?displayProperty=nameWithType> and <xref:System.String.PadRight%2A?displayProperty=nameWithType> methods.</span></span>
  
|<span data-ttu-id="e0436-109">方法名稱</span><span class="sxs-lookup"><span data-stu-id="e0436-109">Method name</span></span>|<span data-ttu-id="e0436-110">使用</span><span class="sxs-lookup"><span data-stu-id="e0436-110">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.PadLeft%2A?displayProperty=nameWithType>|<span data-ttu-id="e0436-111">以指定總長度的前置字元填補字串。</span><span class="sxs-lookup"><span data-stu-id="e0436-111">Pads a string with leading characters to a specified total length.</span></span>|  
|<xref:System.String.PadRight%2A?displayProperty=nameWithType>|<span data-ttu-id="e0436-112">以指定總長度的後置字元填補字串。</span><span class="sxs-lookup"><span data-stu-id="e0436-112">Pads a string with trailing characters to a specified total length.</span></span>|  
  
## <a name="padleft"></a><span data-ttu-id="e0436-113">PadLeft</span><span class="sxs-lookup"><span data-stu-id="e0436-113">PadLeft</span></span>  

 <span data-ttu-id="e0436-114"><xref:System.String.PadLeft%2A?displayProperty=nameWithType> 方法會將足夠的前置填補字元串連到原始字串，以達到指定的總長度，藉以建立新的字串。</span><span class="sxs-lookup"><span data-stu-id="e0436-114">The <xref:System.String.PadLeft%2A?displayProperty=nameWithType> method creates a new string by concatenating enough leading pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="e0436-115"><xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> 方法會使用空白字元作為填補字元，而 <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> 方法可讓您指定自己的填補字元。</span><span class="sxs-lookup"><span data-stu-id="e0436-115">The <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="e0436-116">下列程式碼範例會使用 <xref:System.String.PadLeft%2A> 方法來建立長度為 20 個字元的新字串。</span><span class="sxs-lookup"><span data-stu-id="e0436-116">The following code example uses the <xref:System.String.PadLeft%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="e0436-117">此範例會在主控台顯示 "`--------Hello World!`"。</span><span class="sxs-lookup"><span data-stu-id="e0436-117">The example displays "`--------Hello World!`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## <a name="padright"></a><span data-ttu-id="e0436-118">PadRight</span><span class="sxs-lookup"><span data-stu-id="e0436-118">PadRight</span></span>  

 <span data-ttu-id="e0436-119"><xref:System.String.PadRight%2A?displayProperty=nameWithType> 方法會將足夠的後置填補字元串連到原始字串，以達到指定的總長度，藉以建立新的字串。</span><span class="sxs-lookup"><span data-stu-id="e0436-119">The <xref:System.String.PadRight%2A?displayProperty=nameWithType> method creates a new string by concatenating enough trailing pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="e0436-120"><xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> 方法會使用空白字元作為填補字元，而 <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> 方法可讓您指定自己的填補字元。</span><span class="sxs-lookup"><span data-stu-id="e0436-120">The <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="e0436-121">下列程式碼範例會使用 <xref:System.String.PadRight%2A> 方法來建立長度為 20 個字元的新字串。</span><span class="sxs-lookup"><span data-stu-id="e0436-121">The following code example uses the <xref:System.String.PadRight%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="e0436-122">此範例會在主控台顯示 "`Hello World!--------`"。</span><span class="sxs-lookup"><span data-stu-id="e0436-122">The example displays "`Hello World!--------`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="e0436-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0436-123">See also</span></span>

- [<span data-ttu-id="e0436-124">基底字元串作業</span><span class="sxs-lookup"><span data-stu-id="e0436-124">Basic String Operations</span></span>](basic-string-operations.md)
