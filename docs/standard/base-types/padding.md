---
title: "在.NET 中填補字串"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
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
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 29cd40645cf06ac9babb4738259938a3da04a155
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="padding-strings-in-net"></a><span data-ttu-id="edc4e-102">在.NET 中填補字串</span><span class="sxs-lookup"><span data-stu-id="edc4e-102">Padding Strings in .NET</span></span>
<span data-ttu-id="edc4e-103">使用下列其中一種<xref:System.String>方法來建立新的字串開頭或結尾指定的總長度的字元填補的原始字串所組成。</span><span class="sxs-lookup"><span data-stu-id="edc4e-103">Use one of the following <xref:System.String> methods to create a new string that consists of an original string that is padded with leading or trailing characters to a specified total length.</span></span> <span data-ttu-id="edc4e-104">填補字元可以是空格或指定的字元，最後要靠右或靠左對齊。</span><span class="sxs-lookup"><span data-stu-id="edc4e-104">The padding character can be spaces or a specified character, and consequently appears to be either right-aligned or left-aligned.</span></span>  
  
|<span data-ttu-id="edc4e-105">方法名稱</span><span class="sxs-lookup"><span data-stu-id="edc4e-105">Method name</span></span>|<span data-ttu-id="edc4e-106">用法</span><span class="sxs-lookup"><span data-stu-id="edc4e-106">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.PadLeft%2A?displayProperty=nameWithType>|<span data-ttu-id="edc4e-107">以指定總長度的前置字元填補字串。</span><span class="sxs-lookup"><span data-stu-id="edc4e-107">Pads a string with leading characters to a specified total length.</span></span>|  
|<xref:System.String.PadRight%2A?displayProperty=nameWithType>|<span data-ttu-id="edc4e-108">以指定總長度的後置字元填補字串。</span><span class="sxs-lookup"><span data-stu-id="edc4e-108">Pads a string with trailing characters to a specified total length.</span></span>|  
  
## <a name="padleft"></a><span data-ttu-id="edc4e-109">PadLeft</span><span class="sxs-lookup"><span data-stu-id="edc4e-109">PadLeft</span></span>  
 <span data-ttu-id="edc4e-110"><xref:System.String.PadLeft%2A?displayProperty=nameWithType>方法會建立新的字串串連到原始的字串，以便達到指定的總長度足夠前置填補字元。</span><span class="sxs-lookup"><span data-stu-id="edc4e-110">The <xref:System.String.PadLeft%2A?displayProperty=nameWithType> method creates a new string by concatenating enough leading pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="edc4e-111"><xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType>方法會使用做為填補字元的空白字元和<xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType>方法可讓您指定的填補字元。</span><span class="sxs-lookup"><span data-stu-id="edc4e-111">The <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="edc4e-112">下列程式碼範例使用<xref:System.String.PadLeft%2A>方法來建立新的字串長度的 20 個字元。</span><span class="sxs-lookup"><span data-stu-id="edc4e-112">The following code example uses the <xref:System.String.PadLeft%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="edc4e-113">此範例會在主控台顯示 "`--------Hello World!`"。</span><span class="sxs-lookup"><span data-stu-id="edc4e-113">The example displays "`--------Hello World!`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## <a name="padright"></a><span data-ttu-id="edc4e-114">PadRight</span><span class="sxs-lookup"><span data-stu-id="edc4e-114">PadRight</span></span>  
 <span data-ttu-id="edc4e-115"><xref:System.String.PadRight%2A?displayProperty=nameWithType>方法會建立新的字串串連到原始的字串，以便達到指定的總長度足夠尾端填補字元。</span><span class="sxs-lookup"><span data-stu-id="edc4e-115">The <xref:System.String.PadRight%2A?displayProperty=nameWithType> method creates a new string by concatenating enough trailing pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="edc4e-116"><xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType>方法會使用做為填補字元的空白字元和<xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType>方法可讓您指定的填補字元。</span><span class="sxs-lookup"><span data-stu-id="edc4e-116">The <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="edc4e-117">下列程式碼範例使用<xref:System.String.PadRight%2A>方法來建立新的字串長度的 20 個字元。</span><span class="sxs-lookup"><span data-stu-id="edc4e-117">The following code example uses the <xref:System.String.PadRight%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="edc4e-118">此範例會在主控台顯示 "`Hello World!--------`"。</span><span class="sxs-lookup"><span data-stu-id="edc4e-118">The example displays "`Hello World!--------`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="edc4e-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="edc4e-119">See Also</span></span>  
 [<span data-ttu-id="edc4e-120">基本字串作業</span><span class="sxs-lookup"><span data-stu-id="edc4e-120">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)
