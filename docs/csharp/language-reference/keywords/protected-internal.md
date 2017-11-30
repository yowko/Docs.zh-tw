---
title: "保護內部 （C# 參考）"
ms.date: 11/15/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
author: sputier
ms.author: wiwagn
ms.openlocfilehash: f9004a5e8d65179c9ff2e30688e63c14c95ab431
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2017
---
# <a name="protected-internal-c-reference"></a><span data-ttu-id="72aba-102">保護內部 （C# 參考）</span><span class="sxs-lookup"><span data-stu-id="72aba-102">protected internal (C# Reference)</span></span>
<span data-ttu-id="72aba-103">`protected internal`關鍵字的組合都是成員的存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="72aba-103">The `protected internal` keyword combination is a member access modifier.</span></span> <span data-ttu-id="72aba-104">從目前的組件或型別衍生自包含類別，存取受保護內部成員。</span><span class="sxs-lookup"><span data-stu-id="72aba-104">A protected internal member is accessible from the current assembly or from types that are derived from the containing class.</span></span> <span data-ttu-id="72aba-105">如需 `protected internal` 和其他存取修飾詞的比較，請參閱[存取範圍層級](../../../csharp/language-reference/keywords/accessibility-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="72aba-105">For a comparison of `protected internal` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md).</span></span> 
   
## <a name="example"></a><span data-ttu-id="72aba-106">範例</span><span class="sxs-lookup"><span data-stu-id="72aba-106">Example</span></span>  
 <span data-ttu-id="72aba-107">從任何類型，其包含的組件內存取受保護內部成員的基底類別。</span><span class="sxs-lookup"><span data-stu-id="72aba-107">A protected internal member of a base class is accessible from any type within its containing assembly.</span></span> <span data-ttu-id="72aba-108">它也是在衍生類別位於另一個組件存取是透過衍生的類別類型的變數時，才可存取。</span><span class="sxs-lookup"><span data-stu-id="72aba-108">It is also accessible in a derived class located in another assembly only if the access occurs through a variable of the derived class type.</span></span> <span data-ttu-id="72aba-109">例如，請考慮下列程式碼區段：</span><span class="sxs-lookup"><span data-stu-id="72aba-109">For example, consider the following code segment:</span></span>  

```
// Assembly1.cs  
// Compile with: /target:library  
public class BaseClass   
{  
   protected internal int myValue = 0;  
}

class TestAccess 
{
    void Access()
    {
        BaseClass baseObject = new BaseClass();
        baseObject.myValue = 5;
    }
}  
```  
  
```  
// Assembly2.cs  
// Compile with: /reference:Assembly1.dll  
class DerivedClass : BaseClass   
{  
    static void Main()
    {
        BaseClass baseObject = new BaseClass();
        DerivedClass derivedObject = new DerivedClass();

        // Error CS1540, because myValue can only be accessed by
        // classes derived from BaseClass.
        // baseObject.myValue = 10; 

        // OK, because this class derives from BaseClass.
        derivedObject.myValue = 10;
    }
} 
```  
 <span data-ttu-id="72aba-110">此範例包含兩個檔案：`Assembly1.cs` 和 `Assembly2.cs`。</span><span class="sxs-lookup"><span data-stu-id="72aba-110">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span> <span data-ttu-id="72aba-111">第一個檔案包含公用的基底類別， `BaseClass`，和另一個類別， `TestAccess`。</span><span class="sxs-lookup"><span data-stu-id="72aba-111">The first file contains a public base class, `BaseClass`, and another class, `TestAccess`.</span></span> <span data-ttu-id="72aba-112">`BaseClass`擁有受保護的內部成員， `myValue`，這由存取`TestAccess`型別。</span><span class="sxs-lookup"><span data-stu-id="72aba-112">`BaseClass` owns a protected internal member, `myValue`, which is accessed by the `TestAccess` type.</span></span> <span data-ttu-id="72aba-113">在第二個檔案中，嘗試存取`myValue`的執行個體透過`BaseClass`都會產生錯誤，透過在衍生類別的執行個體，這個成員的存取時`DerivedClass`會成功。</span><span class="sxs-lookup"><span data-stu-id="72aba-113">In the second file, an attempt to access `myValue` through an instance of `BaseClass` will produce an error, while an access to this member through an instance of a derived class, `DerivedClass` will succeed.</span></span> 

 <span data-ttu-id="72aba-114">結構成員不能使用`protected internal`因為結構無法被繼承。</span><span class="sxs-lookup"><span data-stu-id="72aba-114">Struct members cannot be `protected internal` because the struct cannot be inherited.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="72aba-115">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="72aba-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="72aba-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72aba-116">See Also</span></span>  
 <span data-ttu-id="72aba-117">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="72aba-117">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="72aba-118">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="72aba-118">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="72aba-119">[C# 關鍵字](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="72aba-119">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="72aba-120">[存取修飾詞](../../../csharp/language-reference/keywords/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="72aba-120">[Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md) </span></span>  
 <span data-ttu-id="72aba-121">[存取範圍層級](../../../csharp/language-reference/keywords/accessibility-levels.md) </span><span class="sxs-lookup"><span data-stu-id="72aba-121">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) </span></span>  
 <span data-ttu-id="72aba-122">[修飾詞](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="72aba-122">[Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
 <span data-ttu-id="72aba-123">[public](../../../csharp/language-reference/keywords/public.md) </span><span class="sxs-lookup"><span data-stu-id="72aba-123">[public](../../../csharp/language-reference/keywords/public.md) </span></span>  
 <span data-ttu-id="72aba-124">[private](../../../csharp/language-reference/keywords/private.md) </span><span class="sxs-lookup"><span data-stu-id="72aba-124">[private](../../../csharp/language-reference/keywords/private.md) </span></span>  
 <span data-ttu-id="72aba-125">[internal](../../../csharp/language-reference/keywords/internal.md) </span><span class="sxs-lookup"><span data-stu-id="72aba-125">[internal](../../../csharp/language-reference/keywords/internal.md) </span></span>  
 <span data-ttu-id="72aba-126">[Internal virtual 關鍵字的安全性考量](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))</span><span class="sxs-lookup"><span data-stu-id="72aba-126">[Security concerns for internal virtual keywords](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))</span></span>
