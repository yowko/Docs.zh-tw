---
title: "私用受保護 （C# 參考）"
ms.date: 11/15/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
author: sputier
ms.author: wiwagn
ms.openlocfilehash: 5f7abd2569d5bad5af64161042e4e5d21e741c8c
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2017
---
# <a name="private-protected-c-reference"></a><span data-ttu-id="4f38e-102">私用受保護 （C# 參考）</span><span class="sxs-lookup"><span data-stu-id="4f38e-102">private protected (C# Reference)</span></span>
<span data-ttu-id="4f38e-103">`private protected`關鍵字的組合都是成員的存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="4f38e-103">The `private protected` keyword combination is a member access modifier.</span></span> <span data-ttu-id="4f38e-104">型別衍生自包含類別，但只在其包含的組件內存取受保護的私用成員。</span><span class="sxs-lookup"><span data-stu-id="4f38e-104">A private protected member is accessible by types derived from the containing class, but only within its containing assembly.</span></span> <span data-ttu-id="4f38e-105">如需 `private protected` 和其他存取修飾詞的比較，請參閱[存取範圍層級](../../../csharp/language-reference/keywords/accessibility-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="4f38e-105">For a comparison of `private protected` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md).</span></span> 
   
## <a name="example"></a><span data-ttu-id="4f38e-106">範例</span><span class="sxs-lookup"><span data-stu-id="4f38e-106">Example</span></span>  
 <span data-ttu-id="4f38e-107">只有靜態類型的變數是在衍生的類別類型從衍生類型，其包含的組件中存取私用基底類別的 protected 的成員。</span><span class="sxs-lookup"><span data-stu-id="4f38e-107">A private protected member of a base class is accessible from derived types in its containing assembly only if the static type of the variable is the derived class type.</span></span> <span data-ttu-id="4f38e-108">例如，請考慮下列程式碼區段：</span><span class="sxs-lookup"><span data-stu-id="4f38e-108">For example, consider the following code segment:</span></span>  
  
 ```
 // Assembly1.cs  
 // Compile with: /target:library  
 public class BaseClass
 {
     private protected int myValue = 0;
 }
 
 public class DerivedClass1 : BaseClass
 {
     void Access()
     {
         BaseClass baseObject = new BaseClass();
 
         // Error CS1540, because myValue can only be accessed by
         // classes derived from BaseClass.
         // baseObject.myValue = 5;  
 
         // OK, accessed through the current derived class instance
         myValue = 5;
     }
 }
```  
  
```  
 // Assembly2.cs  
 // Compile with: /reference:Assembly1.dll  
 class DerivedClass2 : BaseClass
 {
     void Access()
     {
         // Error CS0122, because myValue can only be
         // accessed by types in Assembly1
         // myValue = 10;
     }
 }
```  
 <span data-ttu-id="4f38e-109">此範例包含兩個檔案：`Assembly1.cs` 和 `Assembly2.cs`。</span><span class="sxs-lookup"><span data-stu-id="4f38e-109">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span> <span data-ttu-id="4f38e-110">第一個檔案包含公用的基底類別， `BaseClass`，並從其衍生的型別`DerivedClass1`。</span><span class="sxs-lookup"><span data-stu-id="4f38e-110">The first file contains a public base class, `BaseClass`, and a type derived from it, `DerivedClass1`.</span></span> <span data-ttu-id="4f38e-111">`BaseClass`擁有私用受保護的成員， `myValue`、 哪些`DerivedClass1`嘗試存取有兩種。</span><span class="sxs-lookup"><span data-stu-id="4f38e-111">`BaseClass` owns a private protected member, `myValue`, which `DerivedClass1` tries to access in two ways.</span></span> <span data-ttu-id="4f38e-112">第一次嘗試存取`myValue`的執行個體透過`BaseClass`都會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="4f38e-112">The first attempt to access `myValue` through an instance of `BaseClass` will produce an error.</span></span> <span data-ttu-id="4f38e-113">不過，嘗試將它當做中的繼承成員`DerivedClass1`會成功。</span><span class="sxs-lookup"><span data-stu-id="4f38e-113">However, the attempt to use it as an inherited member in `DerivedClass1` will succeed.</span></span>
<span data-ttu-id="4f38e-114">在第二個檔案中，嘗試存取`myValue`之繼承成員`DerivedClass2`都會產生錯誤，因為它僅存取 Assembly1 內的衍生型別。</span><span class="sxs-lookup"><span data-stu-id="4f38e-114">In the second file, an attempt to access `myValue` as an inherited member of `DerivedClass2` will produce an error, as it is only accessible by derived types in Assembly1.</span></span> 

 <span data-ttu-id="4f38e-115">結構成員不能使用`private protected`因為結構無法被繼承。</span><span class="sxs-lookup"><span data-stu-id="4f38e-115">Struct members cannot be `private protected` because the struct cannot be inherited.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="4f38e-116">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="4f38e-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4f38e-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f38e-117">See Also</span></span>  
 <span data-ttu-id="4f38e-118">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="4f38e-118">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="4f38e-119">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="4f38e-119">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="4f38e-120">[C# 關鍵字](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="4f38e-120">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="4f38e-121">[存取修飾詞](../../../csharp/language-reference/keywords/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="4f38e-121">[Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md) </span></span>  
 <span data-ttu-id="4f38e-122">[存取範圍層級](../../../csharp/language-reference/keywords/accessibility-levels.md) </span><span class="sxs-lookup"><span data-stu-id="4f38e-122">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) </span></span>  
 <span data-ttu-id="4f38e-123">[修飾詞](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="4f38e-123">[Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
 <span data-ttu-id="4f38e-124">[public](../../../csharp/language-reference/keywords/public.md) </span><span class="sxs-lookup"><span data-stu-id="4f38e-124">[public](../../../csharp/language-reference/keywords/public.md) </span></span>  
 <span data-ttu-id="4f38e-125">[private](../../../csharp/language-reference/keywords/private.md) </span><span class="sxs-lookup"><span data-stu-id="4f38e-125">[private](../../../csharp/language-reference/keywords/private.md) </span></span>  
 <span data-ttu-id="4f38e-126">[internal](../../../csharp/language-reference/keywords/internal.md) </span><span class="sxs-lookup"><span data-stu-id="4f38e-126">[internal](../../../csharp/language-reference/keywords/internal.md) </span></span>  
 <span data-ttu-id="4f38e-127">[Internal virtual 關鍵字的安全性考量](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))</span><span class="sxs-lookup"><span data-stu-id="4f38e-127">[Security concerns for internal virtual keywords](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))</span></span>
