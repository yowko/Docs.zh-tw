---
title: "如何：覆寫 ToString 方法 (C# 程式設計手冊) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- ToString method, overriding in C#
- inheritance [C#], overriding OnPaint and ToString
ms.assetid: 8016db69-1f19-420c-8e17-98e8bebb7749
caps.latest.revision: 21
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 400dfda51d978f35c3995f90840643aaff1b9c13
ms.openlocfilehash: 2dde281d439a07d7736949294772a57e926eb587
ms.contentlocale: zh-tw
ms.lasthandoff: 03/24/2017

---
# <a name="how-to-override-the-tostring-method-c-programming-guide"></a><span data-ttu-id="c37d5-102">如何：覆寫 ToString 方法 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="c37d5-102">How to: Override the ToString Method (C# Programming Guide)</span></span>
<span data-ttu-id="c37d5-103">C# 中的每個類別或結構都會隱含地繼承 <xref:System.Object> 類別。</span><span class="sxs-lookup"><span data-stu-id="c37d5-103">Every class or struct in C# implicitly inherits the <xref:System.Object> class.</span></span> <span data-ttu-id="c37d5-104">因此，C# 中的每個物件都會取得 <xref:System.Object.ToString%2A> 方法，以傳回該物件的字串表示。</span><span class="sxs-lookup"><span data-stu-id="c37d5-104">Therefore, every object in C# gets the <xref:System.Object.ToString%2A> method, which returns a string representation of that object.</span></span> <span data-ttu-id="c37d5-105">例如，所有 `int` 類型的變數都有 `ToString` 方法，並讓它們以字串傳回其內容︰</span><span class="sxs-lookup"><span data-stu-id="c37d5-105">For example, all variables of type `int` have a `ToString` method, which enables them to return their contents as a string:</span></span>  
  
 <span data-ttu-id="c37d5-106">[!code-cs[csProgGuideInheritance#37](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="c37d5-106">[!code-cs[csProgGuideInheritance#37](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_1.cs)]</span></span>  
  
 <span data-ttu-id="c37d5-107">當您建立自訂類別或結構時，應該覆寫 <xref:System.Object.ToString%2A> 方法，以將您的類型資訊提供給用戶端程式碼。</span><span class="sxs-lookup"><span data-stu-id="c37d5-107">When you create a custom class or struct, you should override the <xref:System.Object.ToString%2A> method in order to provide information about your type to client code.</span></span>  
  
 <span data-ttu-id="c37d5-108">如需如何使用 `ToString` 方法以使用格式字串和其他類型之自訂格式的資訊，請參閱[格式化類型](../../../standard/base-types/formatting-types.md)。</span><span class="sxs-lookup"><span data-stu-id="c37d5-108">For information about how to use format strings and other types of custom formatting with the `ToString` method, see [Formatting Types](../../../standard/base-types/formatting-types.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c37d5-109">當您決定要透過這種方法提供的資訊時，請考慮不受信任的程式碼是否要使用類別或結構。</span><span class="sxs-lookup"><span data-stu-id="c37d5-109">When you decide what information to provide through this method, consider whether your class or struct will ever be used by untrusted code.</span></span> <span data-ttu-id="c37d5-110">請務必確定您未提供任何可能會遭惡意程式碼利用的資訊。</span><span class="sxs-lookup"><span data-stu-id="c37d5-110">Be careful to ensure that you do not provide any information that could be exploited by malicious code.</span></span>  
  
### <a name="to-override-the-tostring-method-in-your-class-or-struct"></a><span data-ttu-id="c37d5-111">在類別或結構中覆寫 ToString 方法</span><span class="sxs-lookup"><span data-stu-id="c37d5-111">To override the ToString method in your class or struct</span></span>  
  
1.  <span data-ttu-id="c37d5-112">宣告具有下列修飾詞和傳回型別的 `ToString` 方法︰</span><span class="sxs-lookup"><span data-stu-id="c37d5-112">Declare a `ToString` method with the following modifiers and return type:</span></span>  
  
    ```csharp  
    public override string ToString(){}  
    ```  
  
2.  <span data-ttu-id="c37d5-113">實作方法，讓它傳回字串。</span><span class="sxs-lookup"><span data-stu-id="c37d5-113">Implement the method so that it returns a string.</span></span>  
  
     <span data-ttu-id="c37d5-114">下列範例除了類別之特定執行個體的特定資料之外還會傳回類別名稱。</span><span class="sxs-lookup"><span data-stu-id="c37d5-114">The following example returns the name of the class in addition to the data specific to a particular instance of the class.</span></span>  
  
     <span data-ttu-id="c37d5-115">[!code-cs[csProgGuideInheritance#36](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="c37d5-115">[!code-cs[csProgGuideInheritance#36](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_2.cs)]</span></span>  
  
     <span data-ttu-id="c37d5-116">您可以測試 `ToString` 方法，如下列程式碼範例所示：</span><span class="sxs-lookup"><span data-stu-id="c37d5-116">You can test the `ToString` method as shown in the following code example:</span></span>  
  
     <span data-ttu-id="c37d5-117">[!code-cs[csProgGuideInheritance#38](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="c37d5-117">[!code-cs[csProgGuideInheritance#38](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_3.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c37d5-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c37d5-118">See Also</span></span>  
 <span data-ttu-id="c37d5-119"><xref:System.IFormattable></span><span class="sxs-lookup"><span data-stu-id="c37d5-119"><xref:System.IFormattable></span></span>   
<span data-ttu-id="c37d5-120"> [C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="c37d5-120"> [C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
<span data-ttu-id="c37d5-121"> [類別和結構](../../../csharp/programming-guide/classes-and-structs/index.md) </span><span class="sxs-lookup"><span data-stu-id="c37d5-121"> [Classes and Structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span></span>  
<span data-ttu-id="c37d5-122"> [字串](../../../csharp/programming-guide/strings/index.md) </span><span class="sxs-lookup"><span data-stu-id="c37d5-122"> [Strings](../../../csharp/programming-guide/strings/index.md) </span></span>  
<span data-ttu-id="c37d5-123"> [string](../../../csharp/language-reference/keywords/string.md) </span><span class="sxs-lookup"><span data-stu-id="c37d5-123"> [string](../../../csharp/language-reference/keywords/string.md) </span></span>  
<span data-ttu-id="c37d5-124"> [new](../../../csharp/language-reference/keywords/new.md) </span><span class="sxs-lookup"><span data-stu-id="c37d5-124"> [new](../../../csharp/language-reference/keywords/new.md) </span></span>  
<span data-ttu-id="c37d5-125"> [override](../../../csharp/language-reference/keywords/override.md) </span><span class="sxs-lookup"><span data-stu-id="c37d5-125"> [override](../../../csharp/language-reference/keywords/override.md) </span></span>  
<span data-ttu-id="c37d5-126"> [virtual](../../../csharp/language-reference/keywords/virtual.md) </span><span class="sxs-lookup"><span data-stu-id="c37d5-126"> [virtual](../../../csharp/language-reference/keywords/virtual.md) </span></span>  
<span data-ttu-id="c37d5-127"> [格式化類型](../../../standard/base-types/formatting-types.md)</span><span class="sxs-lookup"><span data-stu-id="c37d5-127"> [Formatting Types](../../../standard/base-types/formatting-types.md)</span></span>
