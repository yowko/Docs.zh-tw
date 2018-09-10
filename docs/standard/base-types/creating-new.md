---
title: 在 .NET 中建立新字串
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CopyTo method
- Join method
- Format method
- Concat method
- strings [.NET Framework], creating
- Insert method
ms.assetid: 06fdf123-2fac-4459-8904-eb48ab908a30
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 477791a0d62186b6cb88d0fae3aa9b4e38b3ef35
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43870106"
---
# <a name="creating-new-strings-in-net"></a><span data-ttu-id="b679f-102">在 .NET 中建立新字串</span><span class="sxs-lookup"><span data-stu-id="b679f-102">Creating New Strings in .NET</span></span>
<span data-ttu-id="b679f-103">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 允許使用簡單指派來建立字串，並且還可以多載類別建構函式，以支援使用多個不同參數來建立字串。</span><span class="sxs-lookup"><span data-stu-id="b679f-103">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] allows strings to be created using simple assignment, and also overloads a class constructor to support string creation using a number of different parameters.</span></span> <span data-ttu-id="b679f-104">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 也會在 <xref:System.String?displayProperty=nameWithType> 類別中提供數個方法，藉由組合多個字串、字串陣列或物件來建立新的字串物件。</span><span class="sxs-lookup"><span data-stu-id="b679f-104">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] also provides several methods in the <xref:System.String?displayProperty=nameWithType> class that create new string objects by combining several strings, arrays of strings, or objects.</span></span>  
  
## <a name="creating-strings-using-assignment"></a><span data-ttu-id="b679f-105">使用指派建立字串</span><span class="sxs-lookup"><span data-stu-id="b679f-105">Creating Strings Using Assignment</span></span>  
 <span data-ttu-id="b679f-106">建立新 <xref:System.String> 物件的最簡單方式，就是將字串常值指派給 <xref:System.String> 物件。</span><span class="sxs-lookup"><span data-stu-id="b679f-106">The easiest way to create a new <xref:System.String> object is simply to assign a string literal to a <xref:System.String> object.</span></span>  
  
## <a name="creating-strings-using-a-class-constructor"></a><span data-ttu-id="b679f-107">使用類別建構函式建立字串</span><span class="sxs-lookup"><span data-stu-id="b679f-107">Creating Strings Using a Class Constructor</span></span>  
 <span data-ttu-id="b679f-108">您可以使用 <xref:System.String> 類別建構函式的多載，從字元陣列建立字串。</span><span class="sxs-lookup"><span data-stu-id="b679f-108">You can use overloads of the <xref:System.String> class constructor to create strings from character arrays.</span></span> <span data-ttu-id="b679f-109">您也可以讓某個特定字元重複指定的次數，藉此建立新字串。</span><span class="sxs-lookup"><span data-stu-id="b679f-109">You can also create a new string by duplicating a particular character a specified number of times.</span></span>  
  
## <a name="methods-that-return-strings"></a><span data-ttu-id="b679f-110">傳回字串的方法</span><span class="sxs-lookup"><span data-stu-id="b679f-110">Methods that Return Strings</span></span>  
 <span data-ttu-id="b679f-111">下表列出數個可傳回新字串物件的有用方法。</span><span class="sxs-lookup"><span data-stu-id="b679f-111">The following table lists several useful methods that return new string objects.</span></span>  
  
|<span data-ttu-id="b679f-112">方法名稱</span><span class="sxs-lookup"><span data-stu-id="b679f-112">Method name</span></span>|<span data-ttu-id="b679f-113">使用</span><span class="sxs-lookup"><span data-stu-id="b679f-113">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|<span data-ttu-id="b679f-114">從一組輸入物件建立格式化的字串。</span><span class="sxs-lookup"><span data-stu-id="b679f-114">Builds a formatted string from a set of input objects.</span></span>|  
|<xref:System.String.Concat%2A?displayProperty=nameWithType>|<span data-ttu-id="b679f-115">從兩個或多個字串建立字串。</span><span class="sxs-lookup"><span data-stu-id="b679f-115">Builds strings from two or more strings.</span></span>|  
|<xref:System.String.Join%2A?displayProperty=nameWithType>|<span data-ttu-id="b679f-116">藉由組合字串陣列來建立新字串。</span><span class="sxs-lookup"><span data-stu-id="b679f-116">Builds a new string by combining an array of strings.</span></span>|  
|<xref:System.String.Insert%2A?displayProperty=nameWithType>|<span data-ttu-id="b679f-117">藉由將字串插入現有字串的指定索引中來建立新字串。</span><span class="sxs-lookup"><span data-stu-id="b679f-117">Builds a new string by inserting a string into the specified index of an existing string.</span></span>|  
|<xref:System.String.CopyTo%2A?displayProperty=nameWithType>|<span data-ttu-id="b679f-118">將字串中的指定字元複製到字元陣列中的指定位置。</span><span class="sxs-lookup"><span data-stu-id="b679f-118">Copies specified characters in a string into a specified position in an array of characters.</span></span>|  
  
### <a name="format"></a><span data-ttu-id="b679f-119">格式</span><span class="sxs-lookup"><span data-stu-id="b679f-119">Format</span></span>  
 <span data-ttu-id="b679f-120">您可以使用 **String.Format** 方法，來建立格式化的字串和串連代表多個物件的字串。</span><span class="sxs-lookup"><span data-stu-id="b679f-120">You can use the **String.Format** method to create formatted strings and concatenate strings representing multiple objects.</span></span> <span data-ttu-id="b679f-121">這個方法會自動將任何傳遞的物件轉換為字串。</span><span class="sxs-lookup"><span data-stu-id="b679f-121">This method automatically converts any passed object into a string.</span></span> <span data-ttu-id="b679f-122">例如，如果您的應用程式必須向使用者顯示 **Int32** 值和 **DateTime** 值，您可以使用 **Format** 方法，輕鬆地建構代表這些值的字串。</span><span class="sxs-lookup"><span data-stu-id="b679f-122">For example, if your application must display an **Int32** value and a **DateTime** value to the user, you can easily construct a string to represent these values using the **Format** method.</span></span> <span data-ttu-id="b679f-123">如需搭配此方法使用之格式慣例的資訊，請參閱[複合格式](../../../docs/standard/base-types/composite-formatting.md)一節。</span><span class="sxs-lookup"><span data-stu-id="b679f-123">For information about formatting conventions used with this method, see the section on [composite formatting](../../../docs/standard/base-types/composite-formatting.md).</span></span>  
  
 <span data-ttu-id="b679f-124">下列範例會使用 **Format** 方法來建立使用整數變數的字串。</span><span class="sxs-lookup"><span data-stu-id="b679f-124">The following example uses the **Format** method to create a string that uses an integer variable.</span></span>  
  
 [!code-csharp[Strings.Creating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#1)]
 [!code-vb[Strings.Creating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#1)]  
  
 <span data-ttu-id="b679f-125">在此範例中，<xref:System.DateTime.Now%2A?displayProperty=nameWithType> 會以和目前執行緒相關聯之文化特性所指定的方式來顯示目前的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="b679f-125">In this example,<xref:System.DateTime.Now%2A?displayProperty=nameWithType> displays the current date and time in a manner specified by the culture associated with the current thread.</span></span>  
  
### <a name="concat"></a><span data-ttu-id="b679f-126">Concat</span><span class="sxs-lookup"><span data-stu-id="b679f-126">Concat</span></span>  
 <span data-ttu-id="b679f-127">使用 **String.Concat** 方法，可輕鬆地從兩個或多個現有物件建立新的字串物件。</span><span class="sxs-lookup"><span data-stu-id="b679f-127">The **String.Concat** method can be used to easily create a new string object from two or more existing objects.</span></span> <span data-ttu-id="b679f-128">它提供與語言無關的方式來串連字串。</span><span class="sxs-lookup"><span data-stu-id="b679f-128">It provides a language-independent way to concatenate strings.</span></span> <span data-ttu-id="b679f-129">這個方法接受任何衍生自 **System.Object** 的類別。</span><span class="sxs-lookup"><span data-stu-id="b679f-129">This method accepts any class that derives from **System.Object**.</span></span> <span data-ttu-id="b679f-130">下列範例會從現有的兩個字串物件和一個分隔字元建立字串。</span><span class="sxs-lookup"><span data-stu-id="b679f-130">The following example creates a string from two existing string objects and a separating character.</span></span>  
  
 [!code-csharp[Strings.Creating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#2)]
 [!code-vb[Strings.Creating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#2)]  
  
### <a name="join"></a><span data-ttu-id="b679f-131">Join</span><span class="sxs-lookup"><span data-stu-id="b679f-131">Join</span></span>  
 <span data-ttu-id="b679f-132">**String.Join** 方法會從字串陣列和分隔符號字串建立新的字串。</span><span class="sxs-lookup"><span data-stu-id="b679f-132">The **String.Join** method creates a new string from an array of strings and a separator string.</span></span> <span data-ttu-id="b679f-133">如果您想要將多個字串串連在一起，建立以逗號分隔的清單，這個方法會很有用。</span><span class="sxs-lookup"><span data-stu-id="b679f-133">This method is useful if you want to concatenate multiple strings together, making a list perhaps separated by a comma.</span></span>  
  
 <span data-ttu-id="b679f-134">下列範例會使用空格來繫結字串陣列。</span><span class="sxs-lookup"><span data-stu-id="b679f-134">The following example uses a space to bind a string array.</span></span>  
  
 [!code-csharp[Strings.Creating#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#3)]
 [!code-vb[Strings.Creating#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#3)]  
  
### <a name="insert"></a><span data-ttu-id="b679f-135">Insert</span><span class="sxs-lookup"><span data-stu-id="b679f-135">Insert</span></span>  
 <span data-ttu-id="b679f-136">**String.Insert** 方法會將字串插入另一個字串中的指定位置，藉以建立新的字串。</span><span class="sxs-lookup"><span data-stu-id="b679f-136">The **String.Insert** method creates a new string by inserting a string into a specified position in another string.</span></span> <span data-ttu-id="b679f-137">這個方法會使用以零起始的索引。</span><span class="sxs-lookup"><span data-stu-id="b679f-137">This method uses a zero-based index.</span></span> <span data-ttu-id="b679f-138">下列範例會將字串插入 `MyString` 的第五個索引位置，並使用這個值來建立新的字串。</span><span class="sxs-lookup"><span data-stu-id="b679f-138">The following example inserts a string into the fifth index position of `MyString` and creates a new string with this value.</span></span>  
  
 [!code-csharp[Strings.Creating#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#4)]
 [!code-vb[Strings.Creating#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#4)]  
  
### <a name="copyto"></a><span data-ttu-id="b679f-139">CopyTo</span><span class="sxs-lookup"><span data-stu-id="b679f-139">CopyTo</span></span>  
 <span data-ttu-id="b679f-140">**String.CopyTo** 方法會將部分字串複製到字元陣列中。</span><span class="sxs-lookup"><span data-stu-id="b679f-140">The **String.CopyTo** method copies portions of a string into an array of characters.</span></span> <span data-ttu-id="b679f-141">您可以同時指定字串的開頭索引和要複製的字元數。</span><span class="sxs-lookup"><span data-stu-id="b679f-141">You can specify both the beginning index of the string and the number of characters to be copied.</span></span> <span data-ttu-id="b679f-142">這個方法會使用來源索引、字元陣列、目的索引和要複製的字元數。</span><span class="sxs-lookup"><span data-stu-id="b679f-142">This method takes the source index, an array of characters, the destination index, and the number of characters to copy.</span></span> <span data-ttu-id="b679f-143">所有索引都是以零起始。</span><span class="sxs-lookup"><span data-stu-id="b679f-143">All indexes are zero-based.</span></span>  
  
 <span data-ttu-id="b679f-144">下列範例會使用 **CopyTo** 方法，將 "Hello" 這個字的所有字元從字串物件複製到字元陣列的第一個索引位置。</span><span class="sxs-lookup"><span data-stu-id="b679f-144">The following example uses the **CopyTo** method to copy the characters of the word "Hello" from a string object to the first index position of an array of characters.</span></span>  
  
 [!code-csharp[Strings.Creating#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#5)]
 [!code-vb[Strings.Creating#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="b679f-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b679f-145">See also</span></span>

- [<span data-ttu-id="b679f-146">基本字串作業</span><span class="sxs-lookup"><span data-stu-id="b679f-146">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)  
- [<span data-ttu-id="b679f-147">複合格式</span><span class="sxs-lookup"><span data-stu-id="b679f-147">Composite Formatting</span></span>](../../../docs/standard/base-types/composite-formatting.md)
