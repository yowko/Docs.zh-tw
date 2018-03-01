---
title: "如何：修改字串內容 (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- strings [C#], modifying
ms.assetid: b6c20bba-ce22-43d7-ad1b-5ce65f714055
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b0810d5722c2c32f7884187bb2e3fc5a039825c9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-modify-string-contents-c-programming-guide"></a><span data-ttu-id="cd407-102">如何：修改字串內容 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="cd407-102">How to: Modify String Contents (C# Programming Guide)</span></span>
<span data-ttu-id="cd407-103">由於字串「不可變」，所以不可能 (不使用不安全的程式碼) 在建立後修改字串物件的值。</span><span class="sxs-lookup"><span data-stu-id="cd407-103">Because strings are *immutable*, it is not possible (without using unsafe code) to modify the value of a string object after it has been created.</span></span> <span data-ttu-id="cd407-104">不過，有許多方法可以修改字串值，並將結果儲存在新的字串物件中。</span><span class="sxs-lookup"><span data-stu-id="cd407-104">However, there are many ways to modify the value of a string and store the result in a new string object.</span></span> <span data-ttu-id="cd407-105"><xref:System.String?displayProperty=nameWithType> 類別會提供在輸入字串上運作的方法，並傳回新的字串物件。</span><span class="sxs-lookup"><span data-stu-id="cd407-105">The <xref:System.String?displayProperty=nameWithType> class provides methods that operate on an input string and return a new string object.</span></span> <span data-ttu-id="cd407-106">在許多情況下，您可以將新的物件指派給保留原始字串的變數。</span><span class="sxs-lookup"><span data-stu-id="cd407-106">In many cases, you can assign the new object to the variable that held the original string.</span></span> <span data-ttu-id="cd407-107"><xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> 類別會提供其他以類似方式運作的方法。</span><span class="sxs-lookup"><span data-stu-id="cd407-107">The <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> class provides additional methods that work in a similar manner.</span></span> <span data-ttu-id="cd407-108"><xref:System.Text.StringBuilder?displayProperty=nameWithType> 類別提供您可以「就地」修改的字元緩衝區。</span><span class="sxs-lookup"><span data-stu-id="cd407-108">The <xref:System.Text.StringBuilder?displayProperty=nameWithType> class provides a character buffer that you can modify "in-place."</span></span> <span data-ttu-id="cd407-109">您呼叫 <xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType> 方法建立的新字串物件，包含目前的緩衝區內容。</span><span class="sxs-lookup"><span data-stu-id="cd407-109">You call the <xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType> method to create a new string object that contains the current contents of the buffer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd407-110">範例</span><span class="sxs-lookup"><span data-stu-id="cd407-110">Example</span></span>  
 <span data-ttu-id="cd407-111">下例示範各種方式，取代或移除指定字串中的子字串。</span><span class="sxs-lookup"><span data-stu-id="cd407-111">The following example shows various ways to replace or remove substrings in a specified string.</span></span>  
  
 [!code-csharp[csProgGuideStrings#28](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="cd407-112">範例</span><span class="sxs-lookup"><span data-stu-id="cd407-112">Example</span></span>  
 <span data-ttu-id="cd407-113">若要使用陣列標記法來存取字串中的個別字元，您可以使用 <xref:System.Text.StringBuilder> 物件，多載 `[]` 運算子以存取其內部的字元緩衝區。</span><span class="sxs-lookup"><span data-stu-id="cd407-113">To access the individual characters in a string by using array notation, you can use the <xref:System.Text.StringBuilder> object, which overloads the `[]` operator to provide access to its internal character buffer.</span></span> <span data-ttu-id="cd407-114">您也可以使用 <xref:System.String.ToCharArray%2A> 方法，將字串轉換成字元陣列。</span><span class="sxs-lookup"><span data-stu-id="cd407-114">You can also convert the string to an array of chars by using the <xref:System.String.ToCharArray%2A> method.</span></span> <span data-ttu-id="cd407-115">下例會使用 `ToCharArray` 建立陣列。</span><span class="sxs-lookup"><span data-stu-id="cd407-115">The following example uses `ToCharArray` to create the array.</span></span> <span data-ttu-id="cd407-116">然後就會修改此陣列的某些元素。</span><span class="sxs-lookup"><span data-stu-id="cd407-116">Some elements of this array are then modified.</span></span> <span data-ttu-id="cd407-117">將字元陣列當做輸入參數的字串建構函式，接著會被呼叫以建立新的字串。</span><span class="sxs-lookup"><span data-stu-id="cd407-117">A string constructor that takes a char array as an input parameter is then called to create a new string.</span></span>  
  
 [!code-csharp[csProgGuideStrings#24](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="cd407-118">範例</span><span class="sxs-lookup"><span data-stu-id="cd407-118">Example</span></span>  
 <span data-ttu-id="cd407-119">下列範例是針對極其罕見的情況：您可能想要以類似 C 樣式字元陣列的方式，使用不安全的程式碼就地修改字串。</span><span class="sxs-lookup"><span data-stu-id="cd407-119">The following example is provided for those very rare situations in which you may want to modify a string in-place by using unsafe code in a manner similar to C-style char arrays.</span></span> <span data-ttu-id="cd407-120">本例示範如何使用 fixed 關鍵字「就地」存取個別字元。</span><span class="sxs-lookup"><span data-stu-id="cd407-120">The example shows how to access the individual characters "in-place" by using the fixed keyword.</span></span> <span data-ttu-id="cd407-121">它也示範因為 C# 編譯器在內部儲存 (實習生) 字串的方式，可能造成的字串不安全作業的一個副作用。</span><span class="sxs-lookup"><span data-stu-id="cd407-121">It also demonstrates one possible side effect of unsafe operations on strings that results from the way that the C# compiler stores (interns) strings internally.</span></span> <span data-ttu-id="cd407-122">一般情況下，除非絕對必要，您不應該使用這項技術。</span><span class="sxs-lookup"><span data-stu-id="cd407-122">In general, you should not use this technique unless it is absolutely necessary.</span></span>  
  
 [!code-csharp[csProgGuideStrings#29](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="cd407-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd407-123">See Also</span></span>  
 [<span data-ttu-id="cd407-124">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="cd407-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="cd407-125">字串</span><span class="sxs-lookup"><span data-stu-id="cd407-125">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)
