---
title: 在 .NET 中剖析其他字串
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 85bb6dcdaa198b6b038cc80e1e38fa7d11123678
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44086377"
---
# <a name="parsing-other-strings-in-net"></a><span data-ttu-id="6570d-102">在 .NET 中剖析其他字串</span><span class="sxs-lookup"><span data-stu-id="6570d-102">Parsing Other Strings in .NET</span></span>
<span data-ttu-id="6570d-103">除了數值和 <xref:System.DateTime> 字串，您也可以將表示 <xref:System.Char>、<xref:System.Boolean> 和 <xref:System.Enum> 類型的字串剖析為資料類型。</span><span class="sxs-lookup"><span data-stu-id="6570d-103">In addition to numeric and <xref:System.DateTime> strings, you can also parse strings that represent the types <xref:System.Char>, <xref:System.Boolean>, and <xref:System.Enum> into data types.</span></span>  
  
## <a name="char"></a><span data-ttu-id="6570d-104">Char</span><span class="sxs-lookup"><span data-stu-id="6570d-104">Char</span></span>  
 <span data-ttu-id="6570d-105">與 **Char** 資料類型相關聯的靜態 parse 方法，可用於將包含單一字元的字串轉換成其 Unicode 值。</span><span class="sxs-lookup"><span data-stu-id="6570d-105">The static parse method associated with the **Char** data type is useful for converting a string that contains a single character into its Unicode value.</span></span> <span data-ttu-id="6570d-106">下列程式碼範例會將字串剖析成 Unicode 字元。</span><span class="sxs-lookup"><span data-stu-id="6570d-106">The following code example parses a string into a Unicode character.</span></span>  
  
 [!code-cpp[Conceptual.String.Parse#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#2)]
 [!code-csharp[Conceptual.String.Parse#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#2)]
 [!code-vb[Conceptual.String.Parse#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#2)]  
  
## <a name="boolean"></a><span data-ttu-id="6570d-107">Boolean</span><span class="sxs-lookup"><span data-stu-id="6570d-107">Boolean</span></span>  
 <span data-ttu-id="6570d-108">**Boolean** 資料類型包含的 **Parse** 方法，可用來將代表 Boolean 值的字串轉換成實際的 **Boolean** 類型。</span><span class="sxs-lookup"><span data-stu-id="6570d-108">The **Boolean** data type contains a **Parse** method that you can use to convert a string that represents a Boolean value into an actual **Boolean** type.</span></span> <span data-ttu-id="6570d-109">這個方法不區分大小寫，而且可以成功剖析包含 "True" 或 "False" 的字串。</span><span class="sxs-lookup"><span data-stu-id="6570d-109">This method is not case-sensitive and can successfully parse a string containing "True" or "False."</span></span> <span data-ttu-id="6570d-110">與 **Boolean** 類型相關聯的 **Parse** 方法也可剖析由空白字元所包圍的字串。</span><span class="sxs-lookup"><span data-stu-id="6570d-110">The **Parse** method associated with the **Boolean** type can also parse strings that are surrounded by white spaces.</span></span> <span data-ttu-id="6570d-111">如果傳遞任何其他字串，則會擲回 <xref:System.FormatException>。</span><span class="sxs-lookup"><span data-stu-id="6570d-111">If any other string is passed, a <xref:System.FormatException> is thrown.</span></span>  
  
 <span data-ttu-id="6570d-112">下列程式碼範例會使用 **Parse** 方法來將字串轉換為 Boolean 值。</span><span class="sxs-lookup"><span data-stu-id="6570d-112">The following code example uses the **Parse** method to convert a string into a Boolean value.</span></span>  
  
 [!code-cpp[Conceptual.String.Parse#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#3)]
 [!code-csharp[Conceptual.String.Parse#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#3)]
 [!code-vb[Conceptual.String.Parse#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#3)]  
  
## <a name="enumeration"></a><span data-ttu-id="6570d-113">列舉</span><span class="sxs-lookup"><span data-stu-id="6570d-113">Enumeration</span></span>  
 <span data-ttu-id="6570d-114">您可以使用靜態的 **Parse** 方法初始化字串值的列舉類型。</span><span class="sxs-lookup"><span data-stu-id="6570d-114">You can use the static **Parse** method to initialize an enumeration type to the value of a string.</span></span> <span data-ttu-id="6570d-115">此方法接受您剖析的列舉類型、要剖析的字串，以及指出剖析是否區分大小寫的選擇性 Boolean 旗標。</span><span class="sxs-lookup"><span data-stu-id="6570d-115">This method accepts the enumeration type you are parsing, the string to parse, and an optional Boolean flag indicating whether or not the parse is case-sensitive.</span></span> <span data-ttu-id="6570d-116">您要剖析的字串可以包含數個以逗號分隔的值，前後可有一或多個空格 (也稱為空白字元)。</span><span class="sxs-lookup"><span data-stu-id="6570d-116">The string you are parsing can contain several values separated by commas, which can be preceded or followed by one or more empty spaces (also called white spaces).</span></span> <span data-ttu-id="6570d-117">當字串包含多個值時，傳回物件的值就是結合了位元 OR 運算的所有指定值的值。</span><span class="sxs-lookup"><span data-stu-id="6570d-117">When the string contains multiple values, the value of the returned object is the value of all specified values combined with a bitwise OR operation.</span></span>  
  
 <span data-ttu-id="6570d-118">下列範例會使用 **Parse** 方法來將字串表示轉換為列舉值。</span><span class="sxs-lookup"><span data-stu-id="6570d-118">The following example uses the **Parse** method to convert a string representation into an enumeration value.</span></span> <span data-ttu-id="6570d-119"><xref:System.DayOfWeek> 列舉會從字串初始化為 **Thursday**。</span><span class="sxs-lookup"><span data-stu-id="6570d-119">The <xref:System.DayOfWeek> enumeration is initialized to **Thursday** from a string.</span></span>  
  
 [!code-cpp[Conceptual.String.Parse#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#4)]
 [!code-csharp[Conceptual.String.Parse#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#4)]
 [!code-vb[Conceptual.String.Parse#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="6570d-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6570d-120">See also</span></span>

- [<span data-ttu-id="6570d-121">剖析字串</span><span class="sxs-lookup"><span data-stu-id="6570d-121">Parsing Strings</span></span>](../../../docs/standard/base-types/parsing-strings.md)  
- [<span data-ttu-id="6570d-122">格式化類型</span><span class="sxs-lookup"><span data-stu-id="6570d-122">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)  
- [<span data-ttu-id="6570d-123">.NET 中的類型轉換</span><span class="sxs-lookup"><span data-stu-id="6570d-123">Type Conversion in the .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)
