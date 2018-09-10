---
title: 在 .NET 中填補字串
ms.date: 03/15/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- strings [.NET Framework], padding
- white space
- PadRight method
- PadLeft method
- padding strings
ms.assetid: 84a9f142-3244-4c90-ba02-21af9bbaff71
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f58e1c3a9e42f48ecc219a2db1649051f9ca20b
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43890723"
---
# <a name="padding-strings-in-net"></a><span data-ttu-id="f0023-102">在 .NET 中填補字串</span><span class="sxs-lookup"><span data-stu-id="f0023-102">Padding Strings in .NET</span></span>

<span data-ttu-id="f0023-103">使用下列其中一個 <xref:System.String> 方法來建立由原始字串組成的新字串，而原始字串會使用前置或後置字元填補至指定的總長度。</span><span class="sxs-lookup"><span data-stu-id="f0023-103">Use one of the following <xref:System.String> methods to create a new string that consists of an original string that is padded with leading or trailing characters to a specified total length.</span></span> <span data-ttu-id="f0023-104">填補字元可為空白或指定的字元。</span><span class="sxs-lookup"><span data-stu-id="f0023-104">The padding character can be a space or a specified character.</span></span> <span data-ttu-id="f0023-105">產生的字串會靠右或靠左顯示。</span><span class="sxs-lookup"><span data-stu-id="f0023-105">The resulting string appears to be either right-aligned or left-aligned.</span></span> <span data-ttu-id="f0023-106">若原始字串的長度已經大於或等於需要的總長度，則填補方法會傳回原封不動的原始字串。如需詳細資訊，請參閱 <xref:System.String.PadLeft%2A?displayProperty=nameWithType> 與 <xref:System.String.PadRight%2A?displayProperty=nameWithType> 這兩個多載方法的**傳回**一節。</span><span class="sxs-lookup"><span data-stu-id="f0023-106">If the original string's length is already equal to or greater than the desired total length, the padding methods return the original string unchanged; for more information, see the **Returns** sections of the two overloads of the <xref:System.String.PadLeft%2A?displayProperty=nameWithType> and <xref:System.String.PadRight%2A?displayProperty=nameWithType> methods.</span></span>
  
|<span data-ttu-id="f0023-107">方法名稱</span><span class="sxs-lookup"><span data-stu-id="f0023-107">Method name</span></span>|<span data-ttu-id="f0023-108">使用</span><span class="sxs-lookup"><span data-stu-id="f0023-108">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.PadLeft%2A?displayProperty=nameWithType>|<span data-ttu-id="f0023-109">以指定總長度的前置字元填補字串。</span><span class="sxs-lookup"><span data-stu-id="f0023-109">Pads a string with leading characters to a specified total length.</span></span>|  
|<xref:System.String.PadRight%2A?displayProperty=nameWithType>|<span data-ttu-id="f0023-110">以指定總長度的後置字元填補字串。</span><span class="sxs-lookup"><span data-stu-id="f0023-110">Pads a string with trailing characters to a specified total length.</span></span>|  
  
## <a name="padleft"></a><span data-ttu-id="f0023-111">PadLeft</span><span class="sxs-lookup"><span data-stu-id="f0023-111">PadLeft</span></span>  
 <span data-ttu-id="f0023-112"><xref:System.String.PadLeft%2A?displayProperty=nameWithType> 方法會將足夠的前置填補字元串連到原始字串，以達到指定的總長度，藉以建立新的字串。</span><span class="sxs-lookup"><span data-stu-id="f0023-112">The <xref:System.String.PadLeft%2A?displayProperty=nameWithType> method creates a new string by concatenating enough leading pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="f0023-113"><xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> 方法會使用空白字元作為填補字元，而 <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> 方法可讓您指定自己的填補字元。</span><span class="sxs-lookup"><span data-stu-id="f0023-113">The <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="f0023-114">下列程式碼範例會使用 <xref:System.String.PadLeft%2A> 方法來建立長度為 20 個字元的新字串。</span><span class="sxs-lookup"><span data-stu-id="f0023-114">The following code example uses the <xref:System.String.PadLeft%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="f0023-115">此範例會在主控台顯示 "`--------Hello World!`"。</span><span class="sxs-lookup"><span data-stu-id="f0023-115">The example displays "`--------Hello World!`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## <a name="padright"></a><span data-ttu-id="f0023-116">PadRight</span><span class="sxs-lookup"><span data-stu-id="f0023-116">PadRight</span></span>  
 <span data-ttu-id="f0023-117"><xref:System.String.PadRight%2A?displayProperty=nameWithType> 方法會將足夠的後置填補字元串連到原始字串，以達到指定的總長度，藉以建立新的字串。</span><span class="sxs-lookup"><span data-stu-id="f0023-117">The <xref:System.String.PadRight%2A?displayProperty=nameWithType> method creates a new string by concatenating enough trailing pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="f0023-118"><xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> 方法會使用空白字元作為填補字元，而 <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> 方法可讓您指定自己的填補字元。</span><span class="sxs-lookup"><span data-stu-id="f0023-118">The <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="f0023-119">下列程式碼範例會使用 <xref:System.String.PadRight%2A> 方法來建立長度為 20 個字元的新字串。</span><span class="sxs-lookup"><span data-stu-id="f0023-119">The following code example uses the <xref:System.String.PadRight%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="f0023-120">此範例會在主控台顯示 "`Hello World!--------`"。</span><span class="sxs-lookup"><span data-stu-id="f0023-120">The example displays "`Hello World!--------`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="f0023-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f0023-121">See also</span></span>

- [<span data-ttu-id="f0023-122">基本字串作業</span><span class="sxs-lookup"><span data-stu-id="f0023-122">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)
