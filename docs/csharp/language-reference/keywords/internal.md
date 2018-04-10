---
title: internal (C# 參考)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- internal_CSharpKeyword
- internal
helpviewer_keywords:
- internal keyword [C#]
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
caps.latest.revision: 23
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a3b115022ed2b38dfcfbbfad3c5fc00e0203b255
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="internal-c-reference"></a><span data-ttu-id="9bc00-102">internal (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="9bc00-102">internal (C# Reference)</span></span>
<span data-ttu-id="9bc00-103">`internal` 關鍵字是類型和類型成員的[存取修飾詞](../../../csharp/language-reference/keywords/access-modifiers.md)。</span><span class="sxs-lookup"><span data-stu-id="9bc00-103">The `internal` keyword is an [access modifier](../../../csharp/language-reference/keywords/access-modifiers.md) for types and type members.</span></span> 
  
 > <span data-ttu-id="9bc00-104">此頁面都涵蓋`internal`存取。</span><span class="sxs-lookup"><span data-stu-id="9bc00-104">This page covers `internal` access.</span></span> <span data-ttu-id="9bc00-105">`internal`關鍵字也是屬於[ `protected internal` ](./protected-internal.md)存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="9bc00-105">The `internal` keyword is also part of the [`protected internal`](./protected-internal.md) access modifier.</span></span>
  
<span data-ttu-id="9bc00-106">內部類型或成員只能在相同組件的檔案內存取，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="9bc00-106">Internal types or members are accessible only within files in the same assembly, as in this example:</span></span>  
  
```  
public class BaseClass   
{  
    // Only accessible within the same assembly  
    internal static int x = 0;  
}  
```  

 <span data-ttu-id="9bc00-107">如需 `internal` 和其他存取修飾詞的比較，請參閱[存取範圍層級](../../../csharp/language-reference/keywords/accessibility-levels.md)和[存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)。</span><span class="sxs-lookup"><span data-stu-id="9bc00-107">For a comparison of `internal` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) and [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="9bc00-108">如需組件的詳細資訊，請參閱[組件和全域組件快取](../../../csharp/programming-guide/concepts/assemblies-gac/index.md)。</span><span class="sxs-lookup"><span data-stu-id="9bc00-108">For more information about assemblies, see [Assemblies and the Global Assembly Cache](../../../csharp/programming-guide/concepts/assemblies-gac/index.md).</span></span>  
  
 <span data-ttu-id="9bc00-109">內部存取常用於以元件為基礎的開發作業，因為它可讓一組元件私下相互合作，而不會公開給應用程式的其餘程式碼。</span><span class="sxs-lookup"><span data-stu-id="9bc00-109">A common use of internal access is in component-based development because it enables a group of components to cooperate in a private manner without being exposed to the rest of the application code.</span></span> <span data-ttu-id="9bc00-110">例如，建立圖形化使用者介面的架構可提供 `Control` 和 `Form` 類別，這兩個類別會以內部存取方式透過成員來相互合作。</span><span class="sxs-lookup"><span data-stu-id="9bc00-110">For example, a framework for building graphical user interfaces could provide `Control` and `Form` classes that cooperate by using members with internal access.</span></span> <span data-ttu-id="9bc00-111">由於這些是內部成員，因此不會公開給使用此架構的程式碼。</span><span class="sxs-lookup"><span data-stu-id="9bc00-111">Since these members are internal, they are not exposed to code that is using the framework.</span></span>  
  
 <span data-ttu-id="9bc00-112">在定義類型或成員的組件外部，以內部存取方式來參考此類型或成員是錯誤的做法。</span><span class="sxs-lookup"><span data-stu-id="9bc00-112">It is an error to reference a type or a member with internal access outside the assembly within which it was defined.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9bc00-113">範例</span><span class="sxs-lookup"><span data-stu-id="9bc00-113">Example</span></span>  
 <span data-ttu-id="9bc00-114">此範例包含兩個檔案：`Assembly1.cs` 和 `Assembly1_a.cs`。</span><span class="sxs-lookup"><span data-stu-id="9bc00-114">This example contains two files, `Assembly1.cs` and `Assembly1_a.cs`.</span></span> <span data-ttu-id="9bc00-115">第一個檔案包含內部基底類別 `BaseClass`。</span><span class="sxs-lookup"><span data-stu-id="9bc00-115">The first file contains an internal base class, `BaseClass`.</span></span> <span data-ttu-id="9bc00-116">在第二個檔案中，嘗試具現化 `BaseClass` 會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="9bc00-116">In the second file, an attempt to instantiate `BaseClass` will produce an error.</span></span>  
  
```  
// Assembly1.cs  
// Compile with: /target:library  
internal class BaseClass   
{  
   public static int intM = 0;  
}  
```  
  
```  
// Assembly1_a.cs  
// Compile with: /reference:Assembly1.dll  
class TestAccess   
{  
   static void Main()   
   {  
      BaseClass myBase = new BaseClass();   // CS0122  
   }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="9bc00-117">範例</span><span class="sxs-lookup"><span data-stu-id="9bc00-117">Example</span></span>  
 <span data-ttu-id="9bc00-118">在此範例中，請使用您在範例 1 中所用的相同檔案，並將 `BaseClass` 的存取範圍層級變更為 `public`。</span><span class="sxs-lookup"><span data-stu-id="9bc00-118">In this example, use the same files you used in example 1, and change the accessibility level of `BaseClass` to `public`.</span></span> <span data-ttu-id="9bc00-119">同時將成員 `IntM` 的存取範圍層級變更為 `internal`。</span><span class="sxs-lookup"><span data-stu-id="9bc00-119">Also change the accessibility level of the member `IntM` to `internal`.</span></span> <span data-ttu-id="9bc00-120">在此情況下，您可以具現化類別，但無法存取內部成員。</span><span class="sxs-lookup"><span data-stu-id="9bc00-120">In this case, you can instantiate the class, but you cannot access the internal member.</span></span>  
  
```  
// Assembly2.cs  
// Compile with: /target:library  
public class BaseClass   
{  
   internal static int intM = 0;  
}  
```  
  
```  
// Assembly2_a.cs  
// Compile with: /reference:Assembly1.dll  
public class TestAccess   
{  
   static void Main()   
   {  
      BaseClass myBase = new BaseClass();   // Ok.  
      BaseClass.intM = 444;    // CS0117  
   }  
}  
```  
  
## <a name="c-language-specification"></a><span data-ttu-id="9bc00-121">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="9bc00-121">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9bc00-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9bc00-122">See Also</span></span>  
 [<span data-ttu-id="9bc00-123">C# 參考</span><span class="sxs-lookup"><span data-stu-id="9bc00-123">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="9bc00-124">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="9bc00-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="9bc00-125">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="9bc00-125">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="9bc00-126">存取修飾詞</span><span class="sxs-lookup"><span data-stu-id="9bc00-126">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [<span data-ttu-id="9bc00-127">存取範圍層級</span><span class="sxs-lookup"><span data-stu-id="9bc00-127">Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [<span data-ttu-id="9bc00-128">修飾詞</span><span class="sxs-lookup"><span data-stu-id="9bc00-128">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="9bc00-129">public</span><span class="sxs-lookup"><span data-stu-id="9bc00-129">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
 [<span data-ttu-id="9bc00-130">private</span><span class="sxs-lookup"><span data-stu-id="9bc00-130">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
 [<span data-ttu-id="9bc00-131">protected</span><span class="sxs-lookup"><span data-stu-id="9bc00-131">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)
