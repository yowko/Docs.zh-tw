---
title: "在 .NET 中填補字串"
ms.custom: 
ms.date: 03/15/2018
ms.prod: .net
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: bf90c841c8fff21dd423fcd19613b5eb46a2c80c
ms.sourcegitcommit: 1c0b0f082b3f300e54b4d069b317ac724c88ddc3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2018
---
# <a name="padding-strings-in-net"></a><span data-ttu-id="cbebd-102">在 .NET 中填補字串</span><span class="sxs-lookup"><span data-stu-id="cbebd-102">Padding Strings in .NET</span></span>

<span data-ttu-id="cbebd-103">使用下列其中一個 <xref:System.String> 方法來建立由原始字串組成的新字串，而原始字串會使用前置或後置字元填補至指定的總長度。</span><span class="sxs-lookup"><span data-stu-id="cbebd-103">Use one of the following <xref:System.String> methods to create a new string that consists of an original string that is padded with leading or trailing characters to a specified total length.</span></span> <span data-ttu-id="cbebd-104">填補字元可為空白或指定的字元。</span><span class="sxs-lookup"><span data-stu-id="cbebd-104">The padding character can be a space or a specified character.</span></span> <span data-ttu-id="cbebd-105">產生的字串會靠右或靠左顯示。</span><span class="sxs-lookup"><span data-stu-id="cbebd-105">The resulting string appears to be either right-aligned or left-aligned.</span></span> <span data-ttu-id="cbebd-106">若原始字串的長度已經大於或等於需要的總長度，則填補方法會傳回原封不動的原始字串。如需詳細資訊，請參閱 <xref:System.String.PadLeft%2A?displayProperty=nameWithType> 與 <xref:System.String.PadRight%2A?displayProperty=nameWithType> 這兩個多載方法的**傳回**一節。</span><span class="sxs-lookup"><span data-stu-id="cbebd-106">If the original string's length is already equal to or greater than the desired total length, the padding methods return the original string unchanged; for more information, see the **Returns** sections of the two overloads of the <xref:System.String.PadLeft%2A?displayProperty=nameWithType> and <xref:System.String.PadRight%2A?displayProperty=nameWithType> methods.</span></span>
  
|<span data-ttu-id="cbebd-107">方法名稱</span><span class="sxs-lookup"><span data-stu-id="cbebd-107">Method name</span></span>|<span data-ttu-id="cbebd-108">使用</span><span class="sxs-lookup"><span data-stu-id="cbebd-108">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.PadLeft%2A?displayProperty=nameWithType>|<span data-ttu-id="cbebd-109">以指定總長度的前置字元填補字串。</span><span class="sxs-lookup"><span data-stu-id="cbebd-109">Pads a string with leading characters to a specified total length.</span></span>|  
|<xref:System.String.PadRight%2A?displayProperty=nameWithType>|<span data-ttu-id="cbebd-110">以指定總長度的後置字元填補字串。</span><span class="sxs-lookup"><span data-stu-id="cbebd-110">Pads a string with trailing characters to a specified total length.</span></span>|  
  
## <a name="padleft"></a><span data-ttu-id="cbebd-111">PadLeft</span><span class="sxs-lookup"><span data-stu-id="cbebd-111">PadLeft</span></span>  
 <span data-ttu-id="cbebd-112"><xref:System.String.PadLeft%2A?displayProperty=nameWithType> 方法會將足夠的前置填補字元串連到原始字串，以達到指定的總長度，藉以建立新的字串。</span><span class="sxs-lookup"><span data-stu-id="cbebd-112">The <xref:System.String.PadLeft%2A?displayProperty=nameWithType> method creates a new string by concatenating enough leading pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="cbebd-113"><xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> 方法會使用空白字元作為填補字元，而 <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> 方法可讓您指定自己的填補字元。</span><span class="sxs-lookup"><span data-stu-id="cbebd-113">The <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="cbebd-114">下列程式碼範例會使用 <xref:System.String.PadLeft%2A> 方法來建立長度為 20 個字元的新字串。</span><span class="sxs-lookup"><span data-stu-id="cbebd-114">The following code example uses the <xref:System.String.PadLeft%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="cbebd-115">此範例會在主控台顯示 "`--------Hello World!`"。</span><span class="sxs-lookup"><span data-stu-id="cbebd-115">The example displays "`--------Hello World!`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## <a name="padright"></a><span data-ttu-id="cbebd-116">PadRight</span><span class="sxs-lookup"><span data-stu-id="cbebd-116">PadRight</span></span>  
 <span data-ttu-id="cbebd-117"><xref:System.String.PadRight%2A?displayProperty=nameWithType> 方法會將足夠的後置填補字元串連到原始字串，以達到指定的總長度，藉以建立新的字串。</span><span class="sxs-lookup"><span data-stu-id="cbebd-117">The <xref:System.String.PadRight%2A?displayProperty=nameWithType> method creates a new string by concatenating enough trailing pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="cbebd-118"><xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> 方法會使用空白字元作為填補字元，而 <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> 方法可讓您指定自己的填補字元。</span><span class="sxs-lookup"><span data-stu-id="cbebd-118">The <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="cbebd-119">下列程式碼範例會使用 <xref:System.String.PadRight%2A> 方法來建立長度為 20 個字元的新字串。</span><span class="sxs-lookup"><span data-stu-id="cbebd-119">The following code example uses the <xref:System.String.PadRight%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="cbebd-120">此範例會在主控台顯示 "`Hello World!--------`"。</span><span class="sxs-lookup"><span data-stu-id="cbebd-120">The example displays "`Hello World!--------`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="cbebd-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="cbebd-121">See Also</span></span>  
 [<span data-ttu-id="cbebd-122">基本字串作業</span><span class="sxs-lookup"><span data-stu-id="cbebd-122">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)
