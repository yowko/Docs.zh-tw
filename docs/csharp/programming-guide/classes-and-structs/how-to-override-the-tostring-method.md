---
title: 作法：覆寫 ToString 方法 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- ToString method, overriding in C#
- inheritance [C#], overriding OnPaint and ToString
ms.assetid: 8016db69-1f19-420c-8e17-98e8bebb7749
ms.openlocfilehash: 18734627e299c696e23bb0ec9bc63ed37fe3e601
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59294973"
---
# <a name="how-to-override-the-tostring-method-c-programming-guide"></a><span data-ttu-id="4ff3c-102">作法：覆寫 ToString 方法 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="4ff3c-102">How to: Override the ToString Method (C# Programming Guide)</span></span>
<span data-ttu-id="4ff3c-103">C# 中的每個類別或結構都會隱含地繼承 <xref:System.Object> 類別。</span><span class="sxs-lookup"><span data-stu-id="4ff3c-103">Every class or struct in C# implicitly inherits the <xref:System.Object> class.</span></span> <span data-ttu-id="4ff3c-104">因此，C# 中的每個物件都會取得 <xref:System.Object.ToString%2A> 方法，以傳回該物件的字串表示。</span><span class="sxs-lookup"><span data-stu-id="4ff3c-104">Therefore, every object in C# gets the <xref:System.Object.ToString%2A> method, which returns a string representation of that object.</span></span> <span data-ttu-id="4ff3c-105">例如，所有 `int` 類型的變數都有 `ToString` 方法，並讓它們以字串傳回其內容︰</span><span class="sxs-lookup"><span data-stu-id="4ff3c-105">For example, all variables of type `int` have a `ToString` method, which enables them to return their contents as a string:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#37)]  
  
 <span data-ttu-id="4ff3c-106">當您建立自訂類別或結構時，應該覆寫 <xref:System.Object.ToString%2A> 方法，以將您的類型資訊提供給用戶端程式碼。</span><span class="sxs-lookup"><span data-stu-id="4ff3c-106">When you create a custom class or struct, you should override the <xref:System.Object.ToString%2A> method in order to provide information about your type to client code.</span></span>  
  
 <span data-ttu-id="4ff3c-107">如需如何使用 `ToString` 方法以使用格式字串和其他類型之自訂格式的資訊，請參閱[格式化類型](../../../standard/base-types/formatting-types.md)。</span><span class="sxs-lookup"><span data-stu-id="4ff3c-107">For information about how to use format strings and other types of custom formatting with the `ToString` method, see [Formatting Types](../../../standard/base-types/formatting-types.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4ff3c-108">當您決定要透過這種方法提供的資訊時，請考慮不受信任的程式碼是否要使用類別或結構。</span><span class="sxs-lookup"><span data-stu-id="4ff3c-108">When you decide what information to provide through this method, consider whether your class or struct will ever be used by untrusted code.</span></span> <span data-ttu-id="4ff3c-109">請務必確定您未提供任何可能會遭惡意程式碼利用的資訊。</span><span class="sxs-lookup"><span data-stu-id="4ff3c-109">Be careful to ensure that you do not provide any information that could be exploited by malicious code.</span></span>  
  
### <a name="to-override-the-tostring-method-in-your-class-or-struct"></a><span data-ttu-id="4ff3c-110">在類別或結構中覆寫 ToString 方法</span><span class="sxs-lookup"><span data-stu-id="4ff3c-110">To override the ToString method in your class or struct</span></span>  
  
1. <span data-ttu-id="4ff3c-111">宣告具有下列修飾詞和傳回型別的 `ToString` 方法︰</span><span class="sxs-lookup"><span data-stu-id="4ff3c-111">Declare a `ToString` method with the following modifiers and return type:</span></span>  
  
    ```csharp  
    public override string ToString(){}  
    ```  
  
2. <span data-ttu-id="4ff3c-112">實作方法，讓它傳回字串。</span><span class="sxs-lookup"><span data-stu-id="4ff3c-112">Implement the method so that it returns a string.</span></span>  
  
     <span data-ttu-id="4ff3c-113">下列範例除了會傳回類別的名稱，也會傳回此類別之特定執行個體 (Instance) 所特有的資料。</span><span class="sxs-lookup"><span data-stu-id="4ff3c-113">The following example returns the name of the class in addition to the data specific to a particular instance of the class.</span></span>  
  
     [!code-csharp[csProgGuideInheritance#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#36)]  
  
     <span data-ttu-id="4ff3c-114">您可以測試 `ToString` 方法，如下列程式碼範例所示：</span><span class="sxs-lookup"><span data-stu-id="4ff3c-114">You can test the `ToString` method as shown in the following code example:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#38)]  
  
## <a name="see-also"></a><span data-ttu-id="4ff3c-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ff3c-115">See also</span></span>

- <xref:System.IFormattable>
- [<span data-ttu-id="4ff3c-116">C# 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="4ff3c-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="4ff3c-117">類別和結構</span><span class="sxs-lookup"><span data-stu-id="4ff3c-117">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
- [<span data-ttu-id="4ff3c-118">字串</span><span class="sxs-lookup"><span data-stu-id="4ff3c-118">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)
- [<span data-ttu-id="4ff3c-119">字串</span><span class="sxs-lookup"><span data-stu-id="4ff3c-119">string</span></span>](../../../csharp/language-reference/keywords/string.md)
- [<span data-ttu-id="4ff3c-120">new</span><span class="sxs-lookup"><span data-stu-id="4ff3c-120">new</span></span>](../../../csharp/language-reference/keywords/new.md)
- [<span data-ttu-id="4ff3c-121">override</span><span class="sxs-lookup"><span data-stu-id="4ff3c-121">override</span></span>](../../../csharp/language-reference/keywords/override.md)
- [<span data-ttu-id="4ff3c-122">虛擬</span><span class="sxs-lookup"><span data-stu-id="4ff3c-122">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)
- [<span data-ttu-id="4ff3c-123">格式化類型</span><span class="sxs-lookup"><span data-stu-id="4ff3c-123">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)
