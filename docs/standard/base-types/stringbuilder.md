---
title: "在 .NET 中使用 StringBuilder 類別"
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
- Remove method
- strings [.NET Framework], capacities
- StringBuilder object
- Replace method
- AppendFormat method
- Append method
- Insert method
- strings [.NET Framework], StringBuilder object
ms.assetid: 5c14867c-9a99-45bc-ae7f-2686700d377a
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: cf8755ae6530c22bac88d8d8c5a6e92d86432994
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="using-the-stringbuilder-class-in-net"></a><span data-ttu-id="8caba-102">在 .NET 中使用 StringBuilder 類別</span><span class="sxs-lookup"><span data-stu-id="8caba-102">Using the StringBuilder Class in .NET</span></span>
<span data-ttu-id="8caba-103"><xref:System.String> 物件不可變。</span><span class="sxs-lookup"><span data-stu-id="8caba-103">The <xref:System.String> object is immutable.</span></span> <span data-ttu-id="8caba-104">每次您使用 <xref:System.String?displayProperty=nameWithType> 類別的其中一個方法時，就會在記憶體中建立新的字串物件，這需要為該新物件配置新的空間。</span><span class="sxs-lookup"><span data-stu-id="8caba-104">Every time you use one of the methods in the <xref:System.String?displayProperty=nameWithType> class, you create a new string object in memory, which requires a new allocation of space for that new object.</span></span> <span data-ttu-id="8caba-105">在您需要重複修改字串的情況下，與建立新 <xref:System.String> 物件相關聯的額外負荷可能成本高昂。</span><span class="sxs-lookup"><span data-stu-id="8caba-105">In situations where you need to perform repeated modifications to a string, the overhead associated with creating a new <xref:System.String> object can be costly.</span></span> <span data-ttu-id="8caba-106">當您想要修改字串，而不建立新物件時，可以使用 <xref:System.Text.StringBuilder?displayProperty=nameWithType> 類別。</span><span class="sxs-lookup"><span data-stu-id="8caba-106">The <xref:System.Text.StringBuilder?displayProperty=nameWithType> class can be used when you want to modify a string without creating a new object.</span></span> <span data-ttu-id="8caba-107">例如，在迴圈中將許多字串串連在一起時，可以使用 <xref:System.Text.StringBuilder> 類別來提升效能。</span><span class="sxs-lookup"><span data-stu-id="8caba-107">For example, using the <xref:System.Text.StringBuilder> class can boost performance when concatenating many strings together in a loop.</span></span>  
  
## <a name="importing-the-systemtext-namespace"></a><span data-ttu-id="8caba-108">匯入 System.Text 命名空間</span><span class="sxs-lookup"><span data-stu-id="8caba-108">Importing the System.Text Namespace</span></span>  
 <span data-ttu-id="8caba-109"><xref:System.Text.StringBuilder> 類別位於 <xref:System.Text> 命名空間。</span><span class="sxs-lookup"><span data-stu-id="8caba-109">The <xref:System.Text.StringBuilder> class is found in the <xref:System.Text> namespace.</span></span>  <span data-ttu-id="8caba-110">為了避免在程式碼中提供完整的類型名稱，您可以匯入 <xref:System.Text> 命名空間：</span><span class="sxs-lookup"><span data-stu-id="8caba-110">To avoid having to provide a fully qualified type name in your code,  you can import the <xref:System.Text> namespace:</span></span>  
  
 [!code-cpp[Conceptual.StringBuilder#11](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#11)]
 [!code-csharp[Conceptual.StringBuilder#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#11)]
 [!code-vb[Conceptual.StringBuilder#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#11)]  
  
## <a name="instantiating-a-stringbuilder-object"></a><span data-ttu-id="8caba-111">具現化 StringBuilder 物件</span><span class="sxs-lookup"><span data-stu-id="8caba-111">Instantiating a StringBuilder Object</span></span>  
 <span data-ttu-id="8caba-112">您可以使用其中一個多載建構函式方法來將變數初始化，以建立 <xref:System.Text.StringBuilder> 類別的新執行個體，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="8caba-112">You can create a new instance of the <xref:System.Text.StringBuilder> class by initializing your variable with one of the overloaded constructor methods, as illustrated in the following example.</span></span>  
  
 [!code-cpp[Conceptual.StringBuilder#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#1)]
 [!code-csharp[Conceptual.StringBuilder#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#1)]
 [!code-vb[Conceptual.StringBuilder#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#1)]  
  
## <a name="setting-the-capacity-and-length"></a><span data-ttu-id="8caba-113">設定容量和長度</span><span class="sxs-lookup"><span data-stu-id="8caba-113">Setting the Capacity and Length</span></span>  
 <span data-ttu-id="8caba-114">雖然 <xref:System.Text.StringBuilder> 是一個動態物件，可讓您擴充其封裝之字串中的字元數，但您可以指定它能容納的字元數上限值。</span><span class="sxs-lookup"><span data-stu-id="8caba-114">Although the <xref:System.Text.StringBuilder> is a dynamic object that allows you to expand the number of characters in the string that it encapsulates, you can specify a value for the maximum number of characters that it can hold.</span></span> <span data-ttu-id="8caba-115">這個值稱為物件的容量，不應該與目前 <xref:System.Text.StringBuilder> 保存的字串長度混淆。</span><span class="sxs-lookup"><span data-stu-id="8caba-115">This value is called the capacity of the object and should not be confused with the length of the string that the current <xref:System.Text.StringBuilder> holds.</span></span> <span data-ttu-id="8caba-116">例如，您可以用字串 "Hello" 建立 <xref:System.Text.StringBuilder> 類別的新執行個體，其長度為 5，而您可能會將物件的最大容量指定為 25。</span><span class="sxs-lookup"><span data-stu-id="8caba-116">For example, you might create a new instance of the <xref:System.Text.StringBuilder> class with the string "Hello", which has a length of 5, and you might specify that the object has a maximum capacity of 25.</span></span> <span data-ttu-id="8caba-117">當您修改 <xref:System.Text.StringBuilder> 時，在到達容量上限之前，它不會重新配置自己的大小。</span><span class="sxs-lookup"><span data-stu-id="8caba-117">When you modify the <xref:System.Text.StringBuilder>, it does not reallocate size for itself until the capacity is reached.</span></span> <span data-ttu-id="8caba-118">發生這種情況時，會自動配置新的空間，而且容量加倍。</span><span class="sxs-lookup"><span data-stu-id="8caba-118">When this occurs, the new space is allocated automatically and the capacity is doubled.</span></span> <span data-ttu-id="8caba-119">您可以使用其中一個多載建構函式來指定 <xref:System.Text.StringBuilder> 類別的容量。</span><span class="sxs-lookup"><span data-stu-id="8caba-119">You can specify the capacity of the <xref:System.Text.StringBuilder> class using one of the overloaded constructors.</span></span> <span data-ttu-id="8caba-120">下列範例會指定 `MyStringBuilder` 物件可以擴展到最多 25 個空格。</span><span class="sxs-lookup"><span data-stu-id="8caba-120">The following example specifies that the `MyStringBuilder` object can be expanded to a maximum of 25 spaces.</span></span>  
  
 [!code-cpp[Conceptual.StringBuilder#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#2)]
 [!code-csharp[Conceptual.StringBuilder#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#2)]
 [!code-vb[Conceptual.StringBuilder#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#2)]  
  
 <span data-ttu-id="8caba-121">此外，您可以使用讀/寫 <xref:System.Text.StringBuilder.Capacity%2A> 屬性來設定物件的長度上限。</span><span class="sxs-lookup"><span data-stu-id="8caba-121">Additionally, you can use the read/write <xref:System.Text.StringBuilder.Capacity%2A> property to set the maximum length of your object.</span></span> <span data-ttu-id="8caba-122">下列範例會使用 **Capacity** 屬性來定義物件長度上限。</span><span class="sxs-lookup"><span data-stu-id="8caba-122">The following example uses the **Capacity** property to define the maximum object length.</span></span>  
  
 [!code-cpp[Conceptual.StringBuilder#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#3)]
 [!code-csharp[Conceptual.StringBuilder#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#3)]
 [!code-vb[Conceptual.StringBuilder#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#3)]  
  
 <span data-ttu-id="8caba-123"><xref:System.Text.StringBuilder.EnsureCapacity%2A> 方法可用來檢查目前 **StringBuilder** 的容量。</span><span class="sxs-lookup"><span data-stu-id="8caba-123">The <xref:System.Text.StringBuilder.EnsureCapacity%2A> method can be used to check the capacity of the current **StringBuilder**.</span></span> <span data-ttu-id="8caba-124">如果容量大於傳遞的值，不會進行任何變更。不過，如果容量小於傳遞的值，會變更目前的容量以符合傳遞的值。</span><span class="sxs-lookup"><span data-stu-id="8caba-124">If the capacity is greater than the passed value, no change is made; however, if the capacity is smaller than the passed value, the current capacity is changed to match the passed value.</span></span>  
  
 <span data-ttu-id="8caba-125">也可以檢視或設定 <xref:System.Text.StringBuilder.Length%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="8caba-125">The <xref:System.Text.StringBuilder.Length%2A> property can also be viewed or set.</span></span> <span data-ttu-id="8caba-126">如果您將 **Length** 屬性的值設成大於 **Capacity** 屬性的值，則 **Capacity** 屬性會自動變更為與 **Length** 屬性相同的值。</span><span class="sxs-lookup"><span data-stu-id="8caba-126">If you set the **Length** property to a value that is greater than the **Capacity** property, the **Capacity** property is automatically changed to the same value as the **Length** property.</span></span> <span data-ttu-id="8caba-127">若將 **Length** 屬性的值設成小於目前 **StringBuilder** 內字串長度的值，則會縮短該字串。</span><span class="sxs-lookup"><span data-stu-id="8caba-127">Setting the **Length** property to a value that is less than the length of the string within the current **StringBuilder** shortens the string.</span></span>  
  
## <a name="modifying-the-stringbuilder-string"></a><span data-ttu-id="8caba-128">修改 StringBuilder 字串</span><span class="sxs-lookup"><span data-stu-id="8caba-128">Modifying the StringBuilder String</span></span>  
 <span data-ttu-id="8caba-129">下表列出您可用來修改 **StringBuilder** 內容的方法。</span><span class="sxs-lookup"><span data-stu-id="8caba-129">The following table lists the methods you can use to modify the contents of a **StringBuilder**.</span></span>  
  
|<span data-ttu-id="8caba-130">方法名稱</span><span class="sxs-lookup"><span data-stu-id="8caba-130">Method name</span></span>|<span data-ttu-id="8caba-131">使用</span><span class="sxs-lookup"><span data-stu-id="8caba-131">Use</span></span>|  
|-----------------|---------|  
|<xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType>|<span data-ttu-id="8caba-132">將資訊附加至目前 **StringBuilder** 的結尾。</span><span class="sxs-lookup"><span data-stu-id="8caba-132">Appends information to the end of the current **StringBuilder**.</span></span>|  
|<xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>|<span data-ttu-id="8caba-133">將字串中傳遞的格式規範取代為格式化的文字。</span><span class="sxs-lookup"><span data-stu-id="8caba-133">Replaces a format specifier passed in a string with formatted text.</span></span>|  
|<xref:System.Text.StringBuilder.Insert%2A?displayProperty=nameWithType>|<span data-ttu-id="8caba-134">將字串或物件插入目前 **StringBuilder** 的指定索引。</span><span class="sxs-lookup"><span data-stu-id="8caba-134">Inserts a string or object into the specified index of the current **StringBuilder**.</span></span>|  
|<xref:System.Text.StringBuilder.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="8caba-135">從目前 **StringBuilder** 移除指定的字元數。</span><span class="sxs-lookup"><span data-stu-id="8caba-135">Removes a specified number of characters from the current **StringBuilder**.</span></span>|  
|<xref:System.Text.StringBuilder.Replace%2A?displayProperty=nameWithType>|<span data-ttu-id="8caba-136">取代指定索引處的指定字元。</span><span class="sxs-lookup"><span data-stu-id="8caba-136">Replaces a specified character at a specified index.</span></span>|  
  
### <a name="append"></a><span data-ttu-id="8caba-137">附加</span><span class="sxs-lookup"><span data-stu-id="8caba-137">Append</span></span>  
 <span data-ttu-id="8caba-138">**Append** 方法可以用來將物件的文字或字串表示加入至目前 **StringBuilder** 所代表的字串結尾。</span><span class="sxs-lookup"><span data-stu-id="8caba-138">The **Append** method can be used to add text or a string representation of an object to the end of a string represented by the current **StringBuilder**.</span></span> <span data-ttu-id="8caba-139">下列範例會將 **StringBuilder** 初始化為 "Hello World"，然後附加一些文字到物件的結尾。</span><span class="sxs-lookup"><span data-stu-id="8caba-139">The following example initializes a **StringBuilder** to "Hello World" and then appends some text to the end of the object.</span></span> <span data-ttu-id="8caba-140">會視需要自動配置空格。</span><span class="sxs-lookup"><span data-stu-id="8caba-140">Space is allocated automatically as needed.</span></span>  
  
 [!code-cpp[Conceptual.StringBuilder#4](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#4)]
 [!code-csharp[Conceptual.StringBuilder#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#4)]
 [!code-vb[Conceptual.StringBuilder#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#4)]  
  
### <a name="appendformat"></a><span data-ttu-id="8caba-141">AppendFormat</span><span class="sxs-lookup"><span data-stu-id="8caba-141">AppendFormat</span></span>  
 <span data-ttu-id="8caba-142"><xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType> 方法會將文字加入至 <xref:System.Text.StringBuilder> 物件的結尾。</span><span class="sxs-lookup"><span data-stu-id="8caba-142">The <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType> method adds text to the end of the <xref:System.Text.StringBuilder> object.</span></span> <span data-ttu-id="8caba-143">它藉由呼叫要格式化之一或多個物件的 <xref:System.IFormattable> 實作，來支援複合格式功能 (如需詳細資訊，請參閱[複合格式](../../../docs/standard/base-types/composite-formatting.md))。</span><span class="sxs-lookup"><span data-stu-id="8caba-143">It supports the composite formatting feature (for more information, see [Composite Formatting](../../../docs/standard/base-types/composite-formatting.md)) by calling the <xref:System.IFormattable> implementation of the object or objects to be formatted.</span></span> <span data-ttu-id="8caba-144">因此，它接受數值、日期和時間，以及列舉值的標準格式字串，數值及日期和時間的自訂格式字串，以及為自訂類型定義的格式字串。</span><span class="sxs-lookup"><span data-stu-id="8caba-144">Therefore, it accepts the standard format strings for numeric, date and time, and enumeration values, the custom format strings for numeric and date and time values, and the format strings defined for custom types.</span></span> <span data-ttu-id="8caba-145">(如需格式設定的資訊，請參閱[格式化類型](../../../docs/standard/base-types/formatting-types.md)。)您可以使用這個方法來自訂變數格式，並將那些值附加到 <xref:System.Text.StringBuilder>。</span><span class="sxs-lookup"><span data-stu-id="8caba-145">(For information about formatting, see [Formatting Types](../../../docs/standard/base-types/formatting-types.md).) You can use this method to customize the format of variables and append those values to a <xref:System.Text.StringBuilder>.</span></span> <span data-ttu-id="8caba-146">下列範例使用 <xref:System.Text.StringBuilder.AppendFormat%2A> 方法，將格式化為貨幣值的整數值放到 <xref:System.Text.StringBuilder> 物件的結尾。</span><span class="sxs-lookup"><span data-stu-id="8caba-146">The following example uses the <xref:System.Text.StringBuilder.AppendFormat%2A> method to place an integer value formatted as a currency value at the end of a <xref:System.Text.StringBuilder> object.</span></span>  
  
 [!code-cpp[Conceptual.StringBuilder#5](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#5)]
 [!code-csharp[Conceptual.StringBuilder#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#5)]
 [!code-vb[Conceptual.StringBuilder#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#5)]  
  
### <a name="insert"></a><span data-ttu-id="8caba-147">Insert</span><span class="sxs-lookup"><span data-stu-id="8caba-147">Insert</span></span>  
 <span data-ttu-id="8caba-148"><xref:System.Text.StringBuilder.Insert%2A> 方法會將字串或物件加入至目前 <xref:System.Text.StringBuilder> 物件中的指定位置。</span><span class="sxs-lookup"><span data-stu-id="8caba-148">The <xref:System.Text.StringBuilder.Insert%2A> method adds a string or object to a specified position in the current <xref:System.Text.StringBuilder> object.</span></span> <span data-ttu-id="8caba-149">下列範例會使用這個方法，在 <xref:System.Text.StringBuilder> 物件的第六個位置插入一個字組。</span><span class="sxs-lookup"><span data-stu-id="8caba-149">The following example uses this method to insert a word into the sixth position of a <xref:System.Text.StringBuilder> object.</span></span>  
  
 [!code-cpp[Conceptual.StringBuilder#6](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#6)]
 [!code-csharp[Conceptual.StringBuilder#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#6)]
 [!code-vb[Conceptual.StringBuilder#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#6)]  
  
### <a name="remove"></a><span data-ttu-id="8caba-150">移除</span><span class="sxs-lookup"><span data-stu-id="8caba-150">Remove</span></span>  
 <span data-ttu-id="8caba-151">您可以使用 **Remove** 方法，從目前 <xref:System.Text.StringBuilder> 物件移除指定的字元數 (從指定之以零為基礎的索引開始)。</span><span class="sxs-lookup"><span data-stu-id="8caba-151">You can use the **Remove** method to remove a specified number of characters from the current <xref:System.Text.StringBuilder> object, beginning at a specified zero-based index.</span></span> <span data-ttu-id="8caba-152">下列範例會使用 **Remove** 方法來縮短 <xref:System.Text.StringBuilder> 物件。</span><span class="sxs-lookup"><span data-stu-id="8caba-152">The following example uses the **Remove** method to shorten a <xref:System.Text.StringBuilder> object.</span></span>  
  
 [!code-cpp[Conceptual.StringBuilder#7](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#7)]
 [!code-csharp[Conceptual.StringBuilder#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#7)]
 [!code-vb[Conceptual.StringBuilder#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#7)]  
  
### <a name="replace"></a><span data-ttu-id="8caba-153">取代</span><span class="sxs-lookup"><span data-stu-id="8caba-153">Replace</span></span>  
 <span data-ttu-id="8caba-154">**Replace** 方法可以用來將 <xref:System.Text.StringBuilder> 物件內的字元取代為另一個指定的字元。</span><span class="sxs-lookup"><span data-stu-id="8caba-154">The **Replace** method can be used to replace characters within the <xref:System.Text.StringBuilder> object with another specified character.</span></span> <span data-ttu-id="8caba-155">下列範例會使用 **Replace** 方法，來搜尋 <xref:System.Text.StringBuilder> 物件中所有的驚嘆號字元 (!) 執行個體，並取代為問號字元 (?)。</span><span class="sxs-lookup"><span data-stu-id="8caba-155">The following example uses the **Replace** method to search a <xref:System.Text.StringBuilder> object for all instances of the exclamation point character (!) and replace them with the question mark character (?).</span></span>  
  
 [!code-cpp[Conceptual.StringBuilder#8](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#8)]
 [!code-csharp[Conceptual.StringBuilder#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#8)]
 [!code-vb[Conceptual.StringBuilder#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#8)]  
  
## <a name="converting-a-stringbuilder-object-to-a-string"></a><span data-ttu-id="8caba-156">將 StringBuilder 物件轉換為字串</span><span class="sxs-lookup"><span data-stu-id="8caba-156">Converting a StringBuilder Object to a String</span></span>  
 <span data-ttu-id="8caba-157">您必須先將 <xref:System.Text.StringBuilder> 物件轉換成 <xref:System.String> 物件，才能將 <xref:System.Text.StringBuilder> 物件所代表的字串傳遞給具有 <xref:System.String> 參數的方法，或在使用者介面中加以顯示。</span><span class="sxs-lookup"><span data-stu-id="8caba-157">You must convert the <xref:System.Text.StringBuilder> object to a <xref:System.String> object before you can pass the string represented by the <xref:System.Text.StringBuilder> object to a method that has a <xref:System.String> parameter or display it in the user interface.</span></span> <span data-ttu-id="8caba-158">您可以呼叫 <xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType> 方法來執行這項轉換。</span><span class="sxs-lookup"><span data-stu-id="8caba-158">You do this conversion by calling the <xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="8caba-159">下列範例會呼叫一些 <xref:System.Text.StringBuilder> 方法，然後呼叫 <xref:System.Text.StringBuilder.ToString?displayProperty=nameWithType> 方法來顯示字串。</span><span class="sxs-lookup"><span data-stu-id="8caba-159">The following example calls a number of <xref:System.Text.StringBuilder> methods and then calls the <xref:System.Text.StringBuilder.ToString?displayProperty=nameWithType> method to display the string.</span></span>  
  
 [!code-csharp[Conceptual.StringBuilder#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/tostringexample1.cs#10)]
 [!code-vb[Conceptual.StringBuilder#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/tostringexample1.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="8caba-160">請參閱</span><span class="sxs-lookup"><span data-stu-id="8caba-160">See Also</span></span>  
 <xref:System.Text.StringBuilder?displayProperty=nameWithType>  
 [<span data-ttu-id="8caba-161">基本字串作業</span><span class="sxs-lookup"><span data-stu-id="8caba-161">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)  
 [<span data-ttu-id="8caba-162">格式化類型</span><span class="sxs-lookup"><span data-stu-id="8caba-162">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)
