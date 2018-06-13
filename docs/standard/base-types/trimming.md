---
title: 在 .NET 中修剪和移除字串中的字元
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- strings [.NET Framework], removing characters
- Remove method
- TrimEnd method
- Trim method
- trimming characters
- TrimStart method
- removing characters
ms.assetid: ab248dab-70d4-4413-81c6-542d153fd195
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 02704ed5e396e973101bab4e5306d81f5a169d0c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569885"
---
# <a name="trimming-and-removing-characters-from-strings-in-net"></a><span data-ttu-id="986d5-102">在 .NET 中修剪和移除字串中的字元</span><span class="sxs-lookup"><span data-stu-id="986d5-102">Trimming and Removing Characters from Strings in .NET</span></span>
<span data-ttu-id="986d5-103">如果您將句子剖析成個別文字，最後可能會得到許多文字，但文字任一端有空格 (也稱為空白字元)。</span><span class="sxs-lookup"><span data-stu-id="986d5-103">If you are parsing a sentence into individual words, you might end up with words that have blank spaces (also called white spaces) on either end of the word.</span></span> <span data-ttu-id="986d5-104">在這種情況下，您可以使用 **System.String** 類別中的其中一個 Trim 方法，從字串中的指定位置移除任意數目的空格或其他字元。</span><span class="sxs-lookup"><span data-stu-id="986d5-104">In this situation, you can use one of the trim methods in the **System.String** class to remove any number of spaces or other characters from a specified position in the string.</span></span> <span data-ttu-id="986d5-105">下表描述可用的 Trim 方法。</span><span class="sxs-lookup"><span data-stu-id="986d5-105">The following table describes the available trim methods.</span></span>  
  
|<span data-ttu-id="986d5-106">方法名稱</span><span class="sxs-lookup"><span data-stu-id="986d5-106">Method name</span></span>|<span data-ttu-id="986d5-107">使用</span><span class="sxs-lookup"><span data-stu-id="986d5-107">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.Trim%2A?displayProperty=nameWithType>|<span data-ttu-id="986d5-108">將字元陣列中字串開頭和結尾指定的空格或空白字元移除。</span><span class="sxs-lookup"><span data-stu-id="986d5-108">Removes white spaces or characters specified in an array of characters from the beginning and end of a string.</span></span>|  
|<xref:System.String.TrimEnd%2A?displayProperty=nameWithType>|<span data-ttu-id="986d5-109">從字串尾端移除字元陣列中指定的字元。</span><span class="sxs-lookup"><span data-stu-id="986d5-109">Removes characters specified in an array of characters from the end of a string.</span></span>|  
|<xref:System.String.TrimStart%2A?displayProperty=nameWithType>|<span data-ttu-id="986d5-110">從字串開頭移除字元陣列中指定的字元。</span><span class="sxs-lookup"><span data-stu-id="986d5-110">Removes characters specified in an array of characters from the beginning of a string.</span></span>|  
|<xref:System.String.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="986d5-111">從字串中指定的索引位置移除指定的字元數。</span><span class="sxs-lookup"><span data-stu-id="986d5-111">Removes a specified number of characters from a specified index position in a string.</span></span>|  
  
## <a name="trim"></a><span data-ttu-id="986d5-112">Trim</span><span class="sxs-lookup"><span data-stu-id="986d5-112">Trim</span></span>  
 <span data-ttu-id="986d5-113">您可以使用 <xref:System.String.Trim%2A?displayProperty=nameWithType> 方法，輕鬆地移除字串頭尾的空格，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="986d5-113">You can easily remove white spaces from both ends of a string by using the <xref:System.String.Trim%2A?displayProperty=nameWithType> method, as shown in the following example.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#17)]
 [!code-csharp[Conceptual.String.BasicOps#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#17)]
 [!code-vb[Conceptual.String.BasicOps#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#17)]  
  
 <span data-ttu-id="986d5-114">您也可以將字元陣列中字串開頭和結尾指定的字元移除。</span><span class="sxs-lookup"><span data-stu-id="986d5-114">You can also remove characters that you specify in a character array from the beginning and end of a string.</span></span> <span data-ttu-id="986d5-115">下列範例將會移除空白字元、句號和星號。</span><span class="sxs-lookup"><span data-stu-id="986d5-115">The following example removes white-space characters, periods, and asterisks.</span></span>  
  
 [!code-csharp[Conceptual.String.BasicOps#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trim2.cs#22)]
 [!code-vb[Conceptual.String.BasicOps#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trim2.vb#22)]  
  
## <a name="trimend"></a><span data-ttu-id="986d5-116">TrimEnd</span><span class="sxs-lookup"><span data-stu-id="986d5-116">TrimEnd</span></span>  
 <span data-ttu-id="986d5-117">**String.TrimEnd** 方法會從字串結尾移除字元，並建立新的字串物件。</span><span class="sxs-lookup"><span data-stu-id="986d5-117">The **String.TrimEnd** method removes characters from the end of a string, creating a new string object.</span></span> <span data-ttu-id="986d5-118">系統會將字元陣列傳遞給這個方法，以指定要移除的字元。</span><span class="sxs-lookup"><span data-stu-id="986d5-118">An array of characters is passed to this method to specify the characters to be removed.</span></span> <span data-ttu-id="986d5-119">字元陣列中的項目順序不會影響修剪作業。</span><span class="sxs-lookup"><span data-stu-id="986d5-119">The order of the elements in the character array does not affect the trim operation.</span></span> <span data-ttu-id="986d5-120">一旦找到陣列中未指定的字元時，修剪作業就會停止。</span><span class="sxs-lookup"><span data-stu-id="986d5-120">The trim stops when a character not specified in the array is found.</span></span>  
  
 <span data-ttu-id="986d5-121">下列範例會使用 **TrimEnd** 方法，移除字串的最後一個字母。</span><span class="sxs-lookup"><span data-stu-id="986d5-121">The following example removes the last letters of a string using the **TrimEnd** method.</span></span> <span data-ttu-id="986d5-122">在此範例中，`'r'` 字元和 `'W'` 字元的位置顛倒，用以說明字元陣列中的順序並不重要。</span><span class="sxs-lookup"><span data-stu-id="986d5-122">In this example, the position of the `'r'` character and the `'W'` character are reversed to illustrate that the order of characters in the array does not matter.</span></span> <span data-ttu-id="986d5-123">請注意，此程式碼會移除 `MyString` 的最後一個字以及第一個字的一部分。</span><span class="sxs-lookup"><span data-stu-id="986d5-123">Notice that this code removes the last word of `MyString` plus part of the first.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#18)]
 [!code-csharp[Conceptual.String.BasicOps#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#18)]
 [!code-vb[Conceptual.String.BasicOps#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#18)]  
  
 <span data-ttu-id="986d5-124">此程式碼會讓主控台顯示 `He`。</span><span class="sxs-lookup"><span data-stu-id="986d5-124">This code displays `He` to the console.</span></span>  
  
 <span data-ttu-id="986d5-125">下列範例會使用 **TrimEnd** 方法，移除字串的最後一個文字。</span><span class="sxs-lookup"><span data-stu-id="986d5-125">The following example removes the last word of a string using the **TrimEnd** method.</span></span> <span data-ttu-id="986d5-126">在這個程式碼中，`Hello` 文字後接一個逗號，不過由於要修剪的字元陣列中未指定逗號，因此修剪作業會在逗號處停止。</span><span class="sxs-lookup"><span data-stu-id="986d5-126">In this code, a comma follows the word `Hello` and, because the comma is not specified in the array of characters to trim, the trim ends at the comma.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#19)]
 [!code-csharp[Conceptual.String.BasicOps#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#19)]
 [!code-vb[Conceptual.String.BasicOps#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#19)]  
  
 <span data-ttu-id="986d5-127">此程式碼會讓主控台顯示 `Hello,`。</span><span class="sxs-lookup"><span data-stu-id="986d5-127">This code displays `Hello,` to the console.</span></span>  
  
## <a name="trimstart"></a><span data-ttu-id="986d5-128">TrimStart</span><span class="sxs-lookup"><span data-stu-id="986d5-128">TrimStart</span></span>  
 <span data-ttu-id="986d5-129">**String.TrimStart** 方法與 **String.TrimEnd** 方法類似，只是它會移除現有字串物件開頭的字元以建立新字串。</span><span class="sxs-lookup"><span data-stu-id="986d5-129">The **String.TrimStart** method is similar to the **String.TrimEnd** method except that it creates a new string by removing characters from the beginning of an existing string object.</span></span> <span data-ttu-id="986d5-130">系統會將字元陣列傳遞給 **TrimStart** 方法，以指定要移除的字元。</span><span class="sxs-lookup"><span data-stu-id="986d5-130">An array of characters is passed to the **TrimStart** method to specify the characters to be removed.</span></span> <span data-ttu-id="986d5-131">使用 **TrimEnd** 時，字元陣列中的項目順序不會影響修剪作業。</span><span class="sxs-lookup"><span data-stu-id="986d5-131">As with the **TrimEnd** method, the order of the elements in the character array does not affect the trim operation.</span></span> <span data-ttu-id="986d5-132">一旦找到陣列中未指定的字元時，修剪作業就會停止。</span><span class="sxs-lookup"><span data-stu-id="986d5-132">The trim stops when a character not specified in the array is found.</span></span>  
  
 <span data-ttu-id="986d5-133">下列範例會移除字串的第一個文字。</span><span class="sxs-lookup"><span data-stu-id="986d5-133">The following example removes the first word of a string.</span></span> <span data-ttu-id="986d5-134">在此範例中，`'l'` 字元和 `'H'` 字元的位置顛倒，用以說明字元陣列中的順序並不重要。</span><span class="sxs-lookup"><span data-stu-id="986d5-134">In this example, the position of the `'l'` character and the `'H'` character are reversed to illustrate that the order of characters in the array does not matter.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#20)]
 [!code-csharp[Conceptual.String.BasicOps#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#20)]
 [!code-vb[Conceptual.String.BasicOps#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#20)]  
  
 <span data-ttu-id="986d5-135">此程式碼會讓主控台顯示 `World!`。</span><span class="sxs-lookup"><span data-stu-id="986d5-135">This code displays `World!` to the console.</span></span>  
  
## <a name="remove"></a><span data-ttu-id="986d5-136">移除</span><span class="sxs-lookup"><span data-stu-id="986d5-136">Remove</span></span>  
 <span data-ttu-id="986d5-137"><xref:System.String.Remove%2A?displayProperty=nameWithType> 方法會從現有字串中的指定位置開始，移除指定的字元數。</span><span class="sxs-lookup"><span data-stu-id="986d5-137">The <xref:System.String.Remove%2A?displayProperty=nameWithType> method removes a specified number of characters that begin at a specified position in an existing string.</span></span> <span data-ttu-id="986d5-138">這個方法會假設以零為起始的索引。</span><span class="sxs-lookup"><span data-stu-id="986d5-138">This method assumes a zero-based index.</span></span>  
  
 <span data-ttu-id="986d5-139">下列範例會於字串中以零為起始之索引的位置五開始，從字串中移除 10 個字元。</span><span class="sxs-lookup"><span data-stu-id="986d5-139">The following example removes ten characters from a string beginning at position five of a zero-based index of the string.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#21)]
 [!code-csharp[Conceptual.String.BasicOps#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#21)]
 [!code-vb[Conceptual.String.BasicOps#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#21)]  
  
 <span data-ttu-id="986d5-140">您也可以從字串中移除指定的字元或子字串，方法是呼叫 <xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> 方法並指定空字串 (<xref:System.String.Empty?displayProperty=nameWithType>) 做為取代。</span><span class="sxs-lookup"><span data-stu-id="986d5-140">You can also remove a specified character or substring from a string by calling the <xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> method and specifying an empty string (<xref:System.String.Empty?displayProperty=nameWithType>) as the replacement.</span></span> <span data-ttu-id="986d5-141">下列範例將會從字串中移除所有逗號。</span><span class="sxs-lookup"><span data-stu-id="986d5-141">The following example removes all commas from a string.</span></span>  
  
 [!code-csharp[Conceptual.String.BasicOps#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/replace1.cs#23)]
 [!code-vb[Conceptual.String.BasicOps#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/replace1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="986d5-142">請參閱</span><span class="sxs-lookup"><span data-stu-id="986d5-142">See Also</span></span>  
 [<span data-ttu-id="986d5-143">基本字串作業</span><span class="sxs-lookup"><span data-stu-id="986d5-143">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)
