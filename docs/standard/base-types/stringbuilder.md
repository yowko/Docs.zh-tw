---
title: "在.NET 中使用 StringBuilder 類別"
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
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3a6c8f6dee9f2a1da6ed4a8219c1b4832464d9aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="using-the-stringbuilder-class-in-net"></a><span data-ttu-id="cfb7b-102">在.NET 中使用 StringBuilder 類別</span><span class="sxs-lookup"><span data-stu-id="cfb7b-102">Using the StringBuilder Class in .NET</span></span>
<span data-ttu-id="cfb7b-103"><xref:System.String>物件是不可變。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-103">The <xref:System.String> object is immutable.</span></span> <span data-ttu-id="cfb7b-104">每次您使用其中一種方法在<xref:System.String?displayProperty=nameWithType>類別，您建立新的字串物件在記憶體中，這需要為這個新物件的新配置的空間。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-104">Every time you use one of the methods in the <xref:System.String?displayProperty=nameWithType> class, you create a new string object in memory, which requires a new allocation of space for that new object.</span></span> <span data-ttu-id="cfb7b-105">建立新的在您要重複修改字串的情況下，關聯的額外負荷<xref:System.String>物件可能會很費時。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-105">In situations where you need to perform repeated modifications to a string, the overhead associated with creating a new <xref:System.String> object can be costly.</span></span> <span data-ttu-id="cfb7b-106"><xref:System.Text.StringBuilder?displayProperty=nameWithType>當您想要修改字串，而不需要建立新的物件時，可以使用類別。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-106">The <xref:System.Text.StringBuilder?displayProperty=nameWithType> class can be used when you want to modify a string without creating a new object.</span></span> <span data-ttu-id="cfb7b-107">例如，使用<xref:System.Text.StringBuilder>串連在一起在迴圈中的許多字串時，類別可以提升效能。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-107">For example, using the <xref:System.Text.StringBuilder> class can boost performance when concatenating many strings together in a loop.</span></span>  
  
## <a name="importing-the-systemtext-namespace"></a><span data-ttu-id="cfb7b-108">匯入 System.Text 命名空間</span><span class="sxs-lookup"><span data-stu-id="cfb7b-108">Importing the System.Text Namespace</span></span>  
 <span data-ttu-id="cfb7b-109"><xref:System.Text.StringBuilder>類別位於<xref:System.Text>命名空間。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-109">The <xref:System.Text.StringBuilder> class is found in the <xref:System.Text> namespace.</span></span>  <span data-ttu-id="cfb7b-110">若要避免提供程式碼中的完整限定的類型名稱，您可以匯入<xref:System.Text>命名空間：</span><span class="sxs-lookup"><span data-stu-id="cfb7b-110">To avoid having to provide a fully qualified type name in your code,  you can import the <xref:System.Text> namespace:</span></span>  
  
 [!code-cpp[Conceptual.StringBuilder#11](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#11)]
 [!code-csharp[Conceptual.StringBuilder#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#11)]
 [!code-vb[Conceptual.StringBuilder#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#11)]  
  
## <a name="instantiating-a-stringbuilder-object"></a><span data-ttu-id="cfb7b-111">具現化 StringBuilder 物件</span><span class="sxs-lookup"><span data-stu-id="cfb7b-111">Instantiating a StringBuilder Object</span></span>  
 <span data-ttu-id="cfb7b-112">您可以建立的新執行個體<xref:System.Text.StringBuilder>類別的其中一個多載建構函式方法，初始化變數，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-112">You can create a new instance of the <xref:System.Text.StringBuilder> class by initializing your variable with one of the overloaded constructor methods, as illustrated in the following example.</span></span>  
  
 [!code-cpp[Conceptual.StringBuilder#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#1)]
 [!code-csharp[Conceptual.StringBuilder#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#1)]
 [!code-vb[Conceptual.StringBuilder#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#1)]  
  
## <a name="setting-the-capacity-and-length"></a><span data-ttu-id="cfb7b-113">設定容量和長度</span><span class="sxs-lookup"><span data-stu-id="cfb7b-113">Setting the Capacity and Length</span></span>  
 <span data-ttu-id="cfb7b-114">雖然<xref:System.Text.StringBuilder>是動態的物件可讓您擴展它封裝時，字串中的字元數，您可以指定它能容納的字元的數目上限的值。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-114">Although the <xref:System.Text.StringBuilder> is a dynamic object that allows you to expand the number of characters in the string that it encapsulates, you can specify a value for the maximum number of characters that it can hold.</span></span> <span data-ttu-id="cfb7b-115">這個值會呼叫物件的容量，而且不應該與字串長度混淆，目前<xref:System.Text.StringBuilder>保存。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-115">This value is called the capacity of the object and should not be confused with the length of the string that the current <xref:System.Text.StringBuilder> holds.</span></span> <span data-ttu-id="cfb7b-116">例如，您可以建立的新執行個體<xref:System.Text.StringBuilder>類別與字串"Hello"，其長度為 5，而且您可能會指定物件是否具有最大容量為 25。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-116">For example, you might create a new instance of the <xref:System.Text.StringBuilder> class with the string "Hello", which has a length of 5, and you might specify that the object has a maximum capacity of 25.</span></span> <span data-ttu-id="cfb7b-117">當您修改<xref:System.Text.StringBuilder>，它不會重新配置大小本身直到到達此容量。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-117">When you modify the <xref:System.Text.StringBuilder>, it does not reallocate size for itself until the capacity is reached.</span></span> <span data-ttu-id="cfb7b-118">發生這種情況時，會自動配置新的空間，而且容量加倍。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-118">When this occurs, the new space is allocated automatically and the capacity is doubled.</span></span> <span data-ttu-id="cfb7b-119">您可以指定的容量<xref:System.Text.StringBuilder>類別使用其中一種多載建構函式。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-119">You can specify the capacity of the <xref:System.Text.StringBuilder> class using one of the overloaded constructors.</span></span> <span data-ttu-id="cfb7b-120">下列範例會指定 `MyStringBuilder` 物件可以擴展到最多 25 個空格。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-120">The following example specifies that the `MyStringBuilder` object can be expanded to a maximum of 25 spaces.</span></span>  
  
 [!code-cpp[Conceptual.StringBuilder#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#2)]
 [!code-csharp[Conceptual.StringBuilder#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#2)]
 [!code-vb[Conceptual.StringBuilder#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#2)]  
  
 <span data-ttu-id="cfb7b-121">此外，您可以使用讀取/寫入<xref:System.Text.StringBuilder.Capacity%2A>屬性來設定物件的最大長度。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-121">Additionally, you can use the read/write <xref:System.Text.StringBuilder.Capacity%2A> property to set the maximum length of your object.</span></span> <span data-ttu-id="cfb7b-122">下列範例會使用 **Capacity** 屬性來定義物件長度上限。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-122">The following example uses the **Capacity** property to define the maximum object length.</span></span>  
  
 [!code-cpp[Conceptual.StringBuilder#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#3)]
 [!code-csharp[Conceptual.StringBuilder#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#3)]
 [!code-vb[Conceptual.StringBuilder#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#3)]  
  
 <span data-ttu-id="cfb7b-123"><xref:System.Text.StringBuilder.EnsureCapacity%2A>方法可以用來檢查目前的容量**StringBuilder**。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-123">The <xref:System.Text.StringBuilder.EnsureCapacity%2A> method can be used to check the capacity of the current **StringBuilder**.</span></span> <span data-ttu-id="cfb7b-124">如果容量大於傳遞的值，不會進行任何變更。不過，如果容量小於傳遞的值，會變更目前的容量以符合傳遞的值。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-124">If the capacity is greater than the passed value, no change is made; however, if the capacity is smaller than the passed value, the current capacity is changed to match the passed value.</span></span>  
  
 <span data-ttu-id="cfb7b-125"><xref:System.Text.StringBuilder.Length%2A>屬性也可以檢視或設定。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-125">The <xref:System.Text.StringBuilder.Length%2A> property can also be viewed or set.</span></span> <span data-ttu-id="cfb7b-126">如果您將 **Length** 屬性的值設成大於 **Capacity** 屬性的值，則 **Capacity** 屬性會自動變更為與 **Length** 屬性相同的值。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-126">If you set the **Length** property to a value that is greater than the **Capacity** property, the **Capacity** property is automatically changed to the same value as the **Length** property.</span></span> <span data-ttu-id="cfb7b-127">若將 **Length** 屬性的值設成小於目前 **StringBuilder** 內字串長度的值，則會縮短該字串。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-127">Setting the **Length** property to a value that is less than the length of the string within the current **StringBuilder** shortens the string.</span></span>  
  
## <a name="modifying-the-stringbuilder-string"></a><span data-ttu-id="cfb7b-128">修改 StringBuilder 字串</span><span class="sxs-lookup"><span data-stu-id="cfb7b-128">Modifying the StringBuilder String</span></span>  
 <span data-ttu-id="cfb7b-129">下表列出您可用來修改 **StringBuilder** 內容的方法。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-129">The following table lists the methods you can use to modify the contents of a **StringBuilder**.</span></span>  
  
|<span data-ttu-id="cfb7b-130">方法名稱</span><span class="sxs-lookup"><span data-stu-id="cfb7b-130">Method name</span></span>|<span data-ttu-id="cfb7b-131">用法</span><span class="sxs-lookup"><span data-stu-id="cfb7b-131">Use</span></span>|  
|-----------------|---------|  
|<xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType>|<span data-ttu-id="cfb7b-132">將資訊附加至目前 **StringBuilder** 的結尾。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-132">Appends information to the end of the current **StringBuilder**.</span></span>|  
|<xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>|<span data-ttu-id="cfb7b-133">將字串中傳遞的格式規範取代為格式化的文字。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-133">Replaces a format specifier passed in a string with formatted text.</span></span>|  
|<xref:System.Text.StringBuilder.Insert%2A?displayProperty=nameWithType>|<span data-ttu-id="cfb7b-134">將字串或物件插入目前 **StringBuilder** 的指定索引。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-134">Inserts a string or object into the specified index of the current **StringBuilder**.</span></span>|  
|<xref:System.Text.StringBuilder.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="cfb7b-135">從目前 **StringBuilder** 移除指定的字元數。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-135">Removes a specified number of characters from the current **StringBuilder**.</span></span>|  
|<xref:System.Text.StringBuilder.Replace%2A?displayProperty=nameWithType>|<span data-ttu-id="cfb7b-136">取代指定索引處的指定字元。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-136">Replaces a specified character at a specified index.</span></span>|  
  
### <a name="append"></a><span data-ttu-id="cfb7b-137">附加</span><span class="sxs-lookup"><span data-stu-id="cfb7b-137">Append</span></span>  
 <span data-ttu-id="cfb7b-138">**附加**方法可以用來加入代表由目前的字串結尾的文字或物件的字串表示**StringBuilder**。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-138">The **Append** method can be used to add text or a string representation of an object to the end of a string represented by the current **StringBuilder**.</span></span> <span data-ttu-id="cfb7b-139">下列範例會將 **StringBuilder** 初始化為 "Hello World"，然後附加一些文字到物件的結尾。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-139">The following example initializes a **StringBuilder** to "Hello World" and then appends some text to the end of the object.</span></span> <span data-ttu-id="cfb7b-140">會視需要自動配置空格。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-140">Space is allocated automatically as needed.</span></span>  
  
 [!code-cpp[Conceptual.StringBuilder#4](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#4)]
 [!code-csharp[Conceptual.StringBuilder#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#4)]
 [!code-vb[Conceptual.StringBuilder#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#4)]  
  
### <a name="appendformat"></a><span data-ttu-id="cfb7b-141">AppendFormat</span><span class="sxs-lookup"><span data-stu-id="cfb7b-141">AppendFormat</span></span>  
 <span data-ttu-id="cfb7b-142"><xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>方法將文字加入結尾<xref:System.Text.StringBuilder>物件。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-142">The <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType> method adds text to the end of the <xref:System.Text.StringBuilder> object.</span></span> <span data-ttu-id="cfb7b-143">它支援複合格式功能 (如需詳細資訊，請參閱[複合格式化](../../../docs/standard/base-types/composite-formatting.md)) 藉由呼叫<xref:System.IFormattable>實作或多個要格式化的物件。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-143">It supports the composite formatting feature (for more information, see [Composite Formatting](../../../docs/standard/base-types/composite-formatting.md)) by calling the <xref:System.IFormattable> implementation of the object or objects to be formatted.</span></span> <span data-ttu-id="cfb7b-144">因此，它接受數值、日期和時間，以及列舉值的標準格式字串，數值及日期和時間的自訂格式字串，以及為自訂類型定義的格式字串。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-144">Therefore, it accepts the standard format strings for numeric, date and time, and enumeration values, the custom format strings for numeric and date and time values, and the format strings defined for custom types.</span></span> <span data-ttu-id="cfb7b-145">(如需格式設定的資訊，請參閱[格式化類型](../../../docs/standard/base-types/formatting-types.md)。)您可以使用這個方法，自訂變數的格式，並將那些值來附加<xref:System.Text.StringBuilder>。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-145">(For information about formatting, see [Formatting Types](../../../docs/standard/base-types/formatting-types.md).) You can use this method to customize the format of variables and append those values to a <xref:System.Text.StringBuilder>.</span></span> <span data-ttu-id="cfb7b-146">下列範例會使用<xref:System.Text.StringBuilder.AppendFormat%2A>方法，將整數值格式化為貨幣值的結尾<xref:System.Text.StringBuilder>物件。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-146">The following example uses the <xref:System.Text.StringBuilder.AppendFormat%2A> method to place an integer value formatted as a currency value at the end of a <xref:System.Text.StringBuilder> object.</span></span>  
  
 [!code-cpp[Conceptual.StringBuilder#5](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#5)]
 [!code-csharp[Conceptual.StringBuilder#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#5)]
 [!code-vb[Conceptual.StringBuilder#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#5)]  
  
### <a name="insert"></a><span data-ttu-id="cfb7b-147">Insert</span><span class="sxs-lookup"><span data-stu-id="cfb7b-147">Insert</span></span>  
 <span data-ttu-id="cfb7b-148"><xref:System.Text.StringBuilder.Insert%2A>方法會將字串或物件中目前指定的位置加入<xref:System.Text.StringBuilder>物件。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-148">The <xref:System.Text.StringBuilder.Insert%2A> method adds a string or object to a specified position in the current <xref:System.Text.StringBuilder> object.</span></span> <span data-ttu-id="cfb7b-149">下列範例會使用這個方法的第六個位置中插入一個字<xref:System.Text.StringBuilder>物件。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-149">The following example uses this method to insert a word into the sixth position of a <xref:System.Text.StringBuilder> object.</span></span>  
  
 [!code-cpp[Conceptual.StringBuilder#6](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#6)]
 [!code-csharp[Conceptual.StringBuilder#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#6)]
 [!code-vb[Conceptual.StringBuilder#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#6)]  
  
### <a name="remove"></a><span data-ttu-id="cfb7b-150">移除</span><span class="sxs-lookup"><span data-stu-id="cfb7b-150">Remove</span></span>  
 <span data-ttu-id="cfb7b-151">您可以使用**移除**方法來移除指定的字元數，從目前<xref:System.Text.StringBuilder>物件，指定以零為起始的索引處開始。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-151">You can use the **Remove** method to remove a specified number of characters from the current <xref:System.Text.StringBuilder> object, beginning at a specified zero-based index.</span></span> <span data-ttu-id="cfb7b-152">下列範例會使用**移除**方法來縮短<xref:System.Text.StringBuilder>物件。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-152">The following example uses the **Remove** method to shorten a <xref:System.Text.StringBuilder> object.</span></span>  
  
 [!code-cpp[Conceptual.StringBuilder#7](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#7)]
 [!code-csharp[Conceptual.StringBuilder#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#7)]
 [!code-vb[Conceptual.StringBuilder#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#7)]  
  
### <a name="replace"></a><span data-ttu-id="cfb7b-153">取代</span><span class="sxs-lookup"><span data-stu-id="cfb7b-153">Replace</span></span>  
 <span data-ttu-id="cfb7b-154">**取代**方法可以用來取代內的字元<xref:System.Text.StringBuilder>物件與另一個指定的字元。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-154">The **Replace** method can be used to replace characters within the <xref:System.Text.StringBuilder> object with another specified character.</span></span> <span data-ttu-id="cfb7b-155">下列範例會使用**取代**方法來搜尋<xref:System.Text.StringBuilder>物件的所有執行個體的驚嘆號字元 （！），並取代為問號字元 （？）。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-155">The following example uses the **Replace** method to search a <xref:System.Text.StringBuilder> object for all instances of the exclamation point character (!) and replace them with the question mark character (?).</span></span>  
  
 [!code-cpp[Conceptual.StringBuilder#8](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#8)]
 [!code-csharp[Conceptual.StringBuilder#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#8)]
 [!code-vb[Conceptual.StringBuilder#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#8)]  
  
## <a name="converting-a-stringbuilder-object-to-a-string"></a><span data-ttu-id="cfb7b-156">將 StringBuilder 物件轉換為字串</span><span class="sxs-lookup"><span data-stu-id="cfb7b-156">Converting a StringBuilder Object to a String</span></span>  
 <span data-ttu-id="cfb7b-157">您必須將轉換<xref:System.Text.StringBuilder>物件<xref:System.String>物件之前，您可以傳遞所代表的字串<xref:System.Text.StringBuilder>方法，該方法的物件<xref:System.String>參數或將它顯示在使用者介面。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-157">You must convert the <xref:System.Text.StringBuilder> object to a <xref:System.String> object before you can pass the string represented by the <xref:System.Text.StringBuilder> object to a method that has a <xref:System.String> parameter or display it in the user interface.</span></span> <span data-ttu-id="cfb7b-158">您執行這項轉換，藉由呼叫<xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-158">You do this conversion by calling the <xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="cfb7b-159">下列範例會呼叫數<xref:System.Text.StringBuilder>方法，然後呼叫<xref:System.Text.StringBuilder.ToString?displayProperty=nameWithType>顯示字串的方法。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-159">The following example calls a number of <xref:System.Text.StringBuilder> methods and then calls the <xref:System.Text.StringBuilder.ToString?displayProperty=nameWithType> method to display the string.</span></span>  
  
 [!code-csharp[Conceptual.StringBuilder#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/tostringexample1.cs#10)]
 [!code-vb[Conceptual.StringBuilder#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/tostringexample1.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="cfb7b-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cfb7b-160">See Also</span></span>  
 <xref:System.Text.StringBuilder?displayProperty=nameWithType>  
 [<span data-ttu-id="cfb7b-161">基本字串作業</span><span class="sxs-lookup"><span data-stu-id="cfb7b-161">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)  
 [<span data-ttu-id="cfb7b-162">格式化類型</span><span class="sxs-lookup"><span data-stu-id="cfb7b-162">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)
