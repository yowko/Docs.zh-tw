---
title: "internal (C# 參考) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- internal_CSharpKeyword
- internal
dev_langs:
- CSharp
helpviewer_keywords:
- internal keyword [C#]
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
caps.latest.revision: 23
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
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: a9eb45ee714f8a56de4ac408d51f5f893a407d51
ms.contentlocale: zh-tw
ms.lasthandoff: 05/26/2017

---
# <a name="internal-c-reference"></a><span data-ttu-id="2cdf2-102">internal (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="2cdf2-102">internal (C# Reference)</span></span>
<span data-ttu-id="2cdf2-103">`internal` 關鍵字是類型和類型成員的[存取修飾詞](../../../csharp/language-reference/keywords/access-modifiers.md)。</span><span class="sxs-lookup"><span data-stu-id="2cdf2-103">The `internal` keyword is an [access modifier](../../../csharp/language-reference/keywords/access-modifiers.md) for types and type members.</span></span> <span data-ttu-id="2cdf2-104">內部類型或成員只能在相同組件的檔案內存取，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="2cdf2-104">Internal types or members are accessible only within files in the same assembly, as in this example:</span></span>  
  
```  
public class BaseClass   
{  
    // Only accessible within the same assembly  
    internal static int x = 0;  
}  
```  
  
 <span data-ttu-id="2cdf2-105">具有存取修飾詞 `protected internal` 的類型或成員，可以從目前的組件或衍生自包含類別的類型存取。</span><span class="sxs-lookup"><span data-stu-id="2cdf2-105">Types or members that have access modifier `protected internal` can be accessed from the current assembly or from types that are derived from the containing class.</span></span>  
  
 <span data-ttu-id="2cdf2-106">如需 `internal` 和其他存取修飾詞的比較，請參閱[存取範圍層級](../../../csharp/language-reference/keywords/accessibility-levels.md)和[存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)。</span><span class="sxs-lookup"><span data-stu-id="2cdf2-106">For a comparison of `internal` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) and [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="2cdf2-107">如需組件的詳細資訊，請參閱[組件和全域組件快取](../../../csharp/programming-guide/concepts/assemblies-gac/index.md)。</span><span class="sxs-lookup"><span data-stu-id="2cdf2-107">For more information about assemblies, see [Assemblies and the Global Assembly Cache](../../../csharp/programming-guide/concepts/assemblies-gac/index.md).</span></span>  
  
 <span data-ttu-id="2cdf2-108">內部存取常用於以元件為基礎的開發作業，因為它可讓一組元件私下相互合作，而不會公開給應用程式的其餘程式碼。</span><span class="sxs-lookup"><span data-stu-id="2cdf2-108">A common use of internal access is in component-based development because it enables a group of components to cooperate in a private manner without being exposed to the rest of the application code.</span></span> <span data-ttu-id="2cdf2-109">例如，建立圖形化使用者介面的架構可提供 `Control` 和 `Form` 類別，這兩個類別會以內部存取方式透過成員來相互合作。</span><span class="sxs-lookup"><span data-stu-id="2cdf2-109">For example, a framework for building graphical user interfaces could provide `Control` and `Form` classes that cooperate by using members with internal access.</span></span> <span data-ttu-id="2cdf2-110">由於這些是內部成員，因此不會公開給使用此架構的程式碼。</span><span class="sxs-lookup"><span data-stu-id="2cdf2-110">Since these members are internal, they are not exposed to code that is using the framework.</span></span>  
  
 <span data-ttu-id="2cdf2-111">在定義類型或成員的組件外部，以內部存取方式來參考此類型或成員是錯誤的做法。</span><span class="sxs-lookup"><span data-stu-id="2cdf2-111">It is an error to reference a type or a member with internal access outside the assembly within which it was defined.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2cdf2-112">範例</span><span class="sxs-lookup"><span data-stu-id="2cdf2-112">Example</span></span>  
 <span data-ttu-id="2cdf2-113">此範例包含兩個檔案：`Assembly1.cs` 和 `Assembly1`_`a.cs`。</span><span class="sxs-lookup"><span data-stu-id="2cdf2-113">This example contains two files, `Assembly1.cs` and `Assembly1`_`a.cs`.</span></span> <span data-ttu-id="2cdf2-114">第一個檔案包含內部基底類別 `BaseClass`。</span><span class="sxs-lookup"><span data-stu-id="2cdf2-114">The first file contains an internal base class, `BaseClass`.</span></span> <span data-ttu-id="2cdf2-115">在第二個檔案中，嘗試具現化 `BaseClass` 會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="2cdf2-115">In the second file, an attempt to instantiate `BaseClass` will produce an error.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="2cdf2-116">範例</span><span class="sxs-lookup"><span data-stu-id="2cdf2-116">Example</span></span>  
 <span data-ttu-id="2cdf2-117">在此範例中，請使用您在範例 1 中所用的相同檔案，並將 `BaseClass` 的存取範圍層級變更為 `public`。</span><span class="sxs-lookup"><span data-stu-id="2cdf2-117">In this example, use the same files you used in example 1, and change the accessibility level of `BaseClass` to `public`.</span></span> <span data-ttu-id="2cdf2-118">同時將成員 `IntM` 的存取範圍層級變更為 `internal`。</span><span class="sxs-lookup"><span data-stu-id="2cdf2-118">Also change the accessibility level of the member `IntM` to `internal`.</span></span> <span data-ttu-id="2cdf2-119">在此情況下，您可以具現化類別，但無法存取內部成員。</span><span class="sxs-lookup"><span data-stu-id="2cdf2-119">In this case, you can instantiate the class, but you cannot access the internal member.</span></span>  
  
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
  
## <a name="c-language-specification"></a><span data-ttu-id="2cdf2-120">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="2cdf2-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2cdf2-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2cdf2-121">See Also</span></span>  
 <span data-ttu-id="2cdf2-122">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="2cdf2-122">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
<span data-ttu-id="2cdf2-123"> [C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="2cdf2-123"> [C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
<span data-ttu-id="2cdf2-124"> [C# 關鍵字](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="2cdf2-124"> [C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
<span data-ttu-id="2cdf2-125"> [存取修飾詞](../../../csharp/language-reference/keywords/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="2cdf2-125"> [Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md) </span></span>  
<span data-ttu-id="2cdf2-126"> [存取範圍層級](../../../csharp/language-reference/keywords/accessibility-levels.md) </span><span class="sxs-lookup"><span data-stu-id="2cdf2-126"> [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) </span></span>  
<span data-ttu-id="2cdf2-127"> [修飾詞](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="2cdf2-127"> [Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
<span data-ttu-id="2cdf2-128"> [public](../../../csharp/language-reference/keywords/public.md) </span><span class="sxs-lookup"><span data-stu-id="2cdf2-128"> [public](../../../csharp/language-reference/keywords/public.md) </span></span>  
<span data-ttu-id="2cdf2-129"> [private](../../../csharp/language-reference/keywords/private.md) </span><span class="sxs-lookup"><span data-stu-id="2cdf2-129"> [private](../../../csharp/language-reference/keywords/private.md) </span></span>  
<span data-ttu-id="2cdf2-130"> [protected](../../../csharp/language-reference/keywords/protected.md)</span><span class="sxs-lookup"><span data-stu-id="2cdf2-130"> [protected](../../../csharp/language-reference/keywords/protected.md)</span></span>
