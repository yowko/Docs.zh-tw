---
title: ".NET 中剖析其他字串"
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
- Char data type, parsing strings
- enumerations [.NET Framework], parsing strings
- base types, parsing strings
- parsing strings, other strings
- Boolean data type, parsing strings
ms.assetid: d139bc00-3c4e-4d78-ac9a-5c951b258d28
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: edd48993f50ec8b91ba7941a682d7de9f22aa12e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="parsing-other-strings-in-net"></a><span data-ttu-id="c7a99-102">.NET 中剖析其他字串</span><span class="sxs-lookup"><span data-stu-id="c7a99-102">Parsing Other Strings in .NET</span></span>
<span data-ttu-id="c7a99-103">除了數字和<xref:System.DateTime>字串，您可以剖析字串，表示類型<xref:System.Char>， <xref:System.Boolean>，和<xref:System.Enum>為資料類型。</span><span class="sxs-lookup"><span data-stu-id="c7a99-103">In addition to numeric and <xref:System.DateTime> strings, you can also parse strings that represent the types <xref:System.Char>, <xref:System.Boolean>, and <xref:System.Enum> into data types.</span></span>  
  
## <a name="char"></a><span data-ttu-id="c7a99-104">Char</span><span class="sxs-lookup"><span data-stu-id="c7a99-104">Char</span></span>  
 <span data-ttu-id="c7a99-105">與 **Char** 資料類型相關聯的靜態 parse 方法，可用於將包含單一字元的字串轉換成其 Unicode 值。</span><span class="sxs-lookup"><span data-stu-id="c7a99-105">The static parse method associated with the **Char** data type is useful for converting a string that contains a single character into its Unicode value.</span></span> <span data-ttu-id="c7a99-106">下列程式碼範例會將字串剖析成 Unicode 字元。</span><span class="sxs-lookup"><span data-stu-id="c7a99-106">The following code example parses a string into a Unicode character.</span></span>  
  
 [!code-cpp[Conceptual.String.Parse#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#2)]
 [!code-csharp[Conceptual.String.Parse#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#2)]
 [!code-vb[Conceptual.String.Parse#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#2)]  
  
## <a name="boolean"></a><span data-ttu-id="c7a99-107">Boolean</span><span class="sxs-lookup"><span data-stu-id="c7a99-107">Boolean</span></span>  
 <span data-ttu-id="c7a99-108">**布林**資料型別包含**剖析**方法可讓您將表示成實際的布林值的字串轉換**布林**型別。</span><span class="sxs-lookup"><span data-stu-id="c7a99-108">The **Boolean** data type contains a **Parse** method that you can use to convert a string that represents a Boolean value into an actual **Boolean** type.</span></span> <span data-ttu-id="c7a99-109">這個方法不區分大小寫，而且可以成功剖析包含 "True" 或 "False" 的字串。</span><span class="sxs-lookup"><span data-stu-id="c7a99-109">This method is not case-sensitive and can successfully parse a string containing "True" or "False."</span></span> <span data-ttu-id="c7a99-110">**剖析**方法相關聯**布林**類型也可以剖析會包圍泛空白字元的字串。</span><span class="sxs-lookup"><span data-stu-id="c7a99-110">The **Parse** method associated with the **Boolean** type can also parse strings that are surrounded by white spaces.</span></span> <span data-ttu-id="c7a99-111">如果傳遞任何其他字串，<xref:System.FormatException>就會擲回。</span><span class="sxs-lookup"><span data-stu-id="c7a99-111">If any other string is passed, a <xref:System.FormatException> is thrown.</span></span>  
  
 <span data-ttu-id="c7a99-112">下列程式碼範例使用**剖析**方法，將字串轉換成布林值。</span><span class="sxs-lookup"><span data-stu-id="c7a99-112">The following code example uses the **Parse** method to convert a string into a Boolean value.</span></span>  
  
 [!code-cpp[Conceptual.String.Parse#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#3)]
 [!code-csharp[Conceptual.String.Parse#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#3)]
 [!code-vb[Conceptual.String.Parse#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#3)]  
  
## <a name="enumeration"></a><span data-ttu-id="c7a99-113">列舉</span><span class="sxs-lookup"><span data-stu-id="c7a99-113">Enumeration</span></span>  
 <span data-ttu-id="c7a99-114">您可以使用靜態的 **Parse** 方法初始化字串值的列舉類型。</span><span class="sxs-lookup"><span data-stu-id="c7a99-114">You can use the static **Parse** method to initialize an enumeration type to the value of a string.</span></span> <span data-ttu-id="c7a99-115">這個方法會接受您剖析的列舉類型、 要剖析的字串和選擇性的布林旗標，以指出會區分大小寫剖析。</span><span class="sxs-lookup"><span data-stu-id="c7a99-115">This method accepts the enumeration type you are parsing, the string to parse, and an optional Boolean flag indicating whether or not the parse is case-sensitive.</span></span> <span data-ttu-id="c7a99-116">您要剖析的字串可以包含數個以逗號分隔的值，前後可有一或多個空格 (也稱為空白字元)。</span><span class="sxs-lookup"><span data-stu-id="c7a99-116">The string you are parsing can contain several values separated by commas, which can be preceded or followed by one or more empty spaces (also called white spaces).</span></span> <span data-ttu-id="c7a99-117">當字串包含多個值時，傳回物件的值就是結合了位元 OR 運算的所有指定值的值。</span><span class="sxs-lookup"><span data-stu-id="c7a99-117">When the string contains multiple values, the value of the returned object is the value of all specified values combined with a bitwise OR operation.</span></span>  
  
 <span data-ttu-id="c7a99-118">下列範例會使用**剖析**方法，將字串表示轉換成列舉值。</span><span class="sxs-lookup"><span data-stu-id="c7a99-118">The following example uses the **Parse** method to convert a string representation into an enumeration value.</span></span> <span data-ttu-id="c7a99-119"><xref:System.DayOfWeek>列舉型別會初始化為**星期四**從字串。</span><span class="sxs-lookup"><span data-stu-id="c7a99-119">The <xref:System.DayOfWeek> enumeration is initialized to **Thursday** from a string.</span></span>  
  
 [!code-cpp[Conceptual.String.Parse#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#4)]
 [!code-csharp[Conceptual.String.Parse#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#4)]
 [!code-vb[Conceptual.String.Parse#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="c7a99-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c7a99-120">See Also</span></span>  
 [<span data-ttu-id="c7a99-121">剖析字串</span><span class="sxs-lookup"><span data-stu-id="c7a99-121">Parsing Strings</span></span>](../../../docs/standard/base-types/parsing-strings.md)  
 [<span data-ttu-id="c7a99-122">格式化類型</span><span class="sxs-lookup"><span data-stu-id="c7a99-122">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)  
 [<span data-ttu-id="c7a99-123">在.NET 中的型別轉換</span><span class="sxs-lookup"><span data-stu-id="c7a99-123">Type Conversion in the .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)
