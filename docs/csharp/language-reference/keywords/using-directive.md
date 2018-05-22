---
title: using 指示詞 (C# 參考)
ms.date: 07/20/2015
helpviewer_keywords:
- using directive [C#]
ms.assetid: b42b8e61-5e7e-439c-bb71-370094b44ae8
ms.openlocfilehash: 180c038987e7de6b39a8eae0e86871eea41a40bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="using-directive-c-reference"></a><span data-ttu-id="8fc9b-102">using 指示詞 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="8fc9b-102">using Directive (C# Reference)</span></span>
<span data-ttu-id="8fc9b-103">`using` 指示詞有三個用途：</span><span class="sxs-lookup"><span data-stu-id="8fc9b-103">The `using` directive has three uses:</span></span>  
  
-   <span data-ttu-id="8fc9b-104">若要允許在命名空間中使用類型，使得您不需限定在該命名空間中使用的類型：</span><span class="sxs-lookup"><span data-stu-id="8fc9b-104">To allow the use of types in a namespace so that you do not have to qualify the use of a type in that namespace:</span></span>  
  
    ```csharp  
    using System.Text;  
    ```  
  
-   <span data-ttu-id="8fc9b-105">若要允許您存取類型的靜態成員，而不需以類型名稱限定存取。</span><span class="sxs-lookup"><span data-stu-id="8fc9b-105">To allow you to access static members of a type without having to qualify the access with the type name.</span></span> 
  
    ```csharp  
    using static System.Math;  
    ```  
     
    <span data-ttu-id="8fc9b-106">如需詳細資訊，請參閱 [using static 指示詞](using-static.md)。</span><span class="sxs-lookup"><span data-stu-id="8fc9b-106">For more information, see the [using static directive](using-static.md).</span></span>

-   <span data-ttu-id="8fc9b-107">若要建立命名空間或類型的別名。</span><span class="sxs-lookup"><span data-stu-id="8fc9b-107">To create an alias for a namespace or a type.</span></span> <span data-ttu-id="8fc9b-108">這稱為 *using alias 指示詞*。</span><span class="sxs-lookup"><span data-stu-id="8fc9b-108">This is called a *using alias directive*.</span></span>  
  
    ```csharp  
    using Project = PC.MyCompany.Project;  
    ```  
  
 <span data-ttu-id="8fc9b-109">`using` 關鍵字也用來建立 *using 陳述式*，協助確保能夠正確處理 <xref:System.IDisposable> 物件 (例如檔案和字型)。</span><span class="sxs-lookup"><span data-stu-id="8fc9b-109">The `using` keyword is also used to create *using statements*, which help ensure that <xref:System.IDisposable> objects such as files and fonts are handled correctly.</span></span> <span data-ttu-id="8fc9b-110">如需詳細資訊，請參閱 [sing 陳述式](../../../csharp/language-reference/keywords/using-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="8fc9b-110">See [using Statement](../../../csharp/language-reference/keywords/using-statement.md) for more information.</span></span>  
  
## <a name="using-static-type"></a><span data-ttu-id="8fc9b-111">使用靜態類型</span><span class="sxs-lookup"><span data-stu-id="8fc9b-111">Using Static Type</span></span>  
 <span data-ttu-id="8fc9b-112">您可以存取類型的靜態成員，而不需以類型名稱限定存取：</span><span class="sxs-lookup"><span data-stu-id="8fc9b-112">You can access static members of a type without having to qualify the access with the type name:</span></span>  
  
```csharp  
using static System.Console;   
using static System.Math;  
class Program   
{   
    static void Main()   
    {   
        WriteLine(Sqrt(3*3 + 4*4));   
    }   
}  
```  
  
## <a name="remarks"></a><span data-ttu-id="8fc9b-113">備註</span><span class="sxs-lookup"><span data-stu-id="8fc9b-113">Remarks</span></span>  
 <span data-ttu-id="8fc9b-114">`using` 指示詞的範圍僅限於其出現的檔案。</span><span class="sxs-lookup"><span data-stu-id="8fc9b-114">The scope of a `using` directive is limited to the file in which it appears.</span></span>  
  
 <span data-ttu-id="8fc9b-115">建立 `using` 別名，讓您更輕鬆地將識別項限定在命名空間或類型。</span><span class="sxs-lookup"><span data-stu-id="8fc9b-115">Create a `using` alias to make it easier to qualify an identifier to a namespace or type.</span></span> <span data-ttu-id="8fc9b-116">using alias 指示詞的右邊一律必須是完整限定的類型，不論在它前面的 using 指示詞為何。</span><span class="sxs-lookup"><span data-stu-id="8fc9b-116">The right side of a using alias directive must always be a fully-qualified type regardless of the using directives that come before it.</span></span>  
  
 <span data-ttu-id="8fc9b-117">建立 `using` 指示詞，以在命名空間中使用類型，而無需指定命名空間。</span><span class="sxs-lookup"><span data-stu-id="8fc9b-117">Create a `using` directive to use the types in a namespace without having to specify the namespace.</span></span> <span data-ttu-id="8fc9b-118">`using` 指示詞不會授予巢狀於您指定的命名空間中的任何命名空間的存取權。</span><span class="sxs-lookup"><span data-stu-id="8fc9b-118">A `using` directive does not give you access to any namespaces that are nested in the namespace you specify.</span></span>  
  
 <span data-ttu-id="8fc9b-119">命名空間有兩種類型：使用者定義和系統定義。</span><span class="sxs-lookup"><span data-stu-id="8fc9b-119">Namespaces come in two categories: user-defined and system-defined.</span></span> <span data-ttu-id="8fc9b-120">使用者定義的命名空間是在程式碼中定義的命名空間。</span><span class="sxs-lookup"><span data-stu-id="8fc9b-120">User-defined namespaces are namespaces defined in your code.</span></span> <span data-ttu-id="8fc9b-121">如需系統定義之命名空間的清單，請參閱 [.NET Framework 類別庫概觀](../../../standard/class-library-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="8fc9b-121">For a list of the system-defined namespaces, see [.NET Framework Class Library Overview](../../../standard/class-library-overview.md).</span></span>  
  
 <span data-ttu-id="8fc9b-122">如需參考其他組件中的方法的範例，請參閱[以命令列建立和使用組件](../../programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md)。</span><span class="sxs-lookup"><span data-stu-id="8fc9b-122">For examples on referencing methods in other assemblies, see [Create and Use Assemblies Using the Command Line](../../programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="8fc9b-123">範例 1</span><span class="sxs-lookup"><span data-stu-id="8fc9b-123">Example 1</span></span>  
  
 <span data-ttu-id="8fc9b-124">下列範例示範如何定義和使用命名空間的 `using` 別名：</span><span class="sxs-lookup"><span data-stu-id="8fc9b-124">The following example shows how to define and use a `using` alias for a namespace:</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-directive_1.cs)]  
  
 <span data-ttu-id="8fc9b-125">using alias 指示詞的右邊不能有開放式的泛型類型。</span><span class="sxs-lookup"><span data-stu-id="8fc9b-125">A using alias directive cannot have an open generic type on the right hand side.</span></span> <span data-ttu-id="8fc9b-126">例如，您無法為 List\<T> 建立 using alias，但是您可以為 List\<int> 建立。</span><span class="sxs-lookup"><span data-stu-id="8fc9b-126">For example, you cannot create a using alias for a List\<T>, but you can create one for a List\<int>.</span></span>  
  
## <a name="example-2"></a><span data-ttu-id="8fc9b-127">範例 2</span><span class="sxs-lookup"><span data-stu-id="8fc9b-127">Example 2</span></span>  
  
 <span data-ttu-id="8fc9b-128">下列範例示範如何定義類別的 `using` 指示詞和 `using` 別名：</span><span class="sxs-lookup"><span data-stu-id="8fc9b-128">The following example shows how to define a `using` directive and a `using` alias for a class:</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-directive_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="8fc9b-129">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="8fc9b-129">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8fc9b-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="8fc9b-130">See Also</span></span>  
 [<span data-ttu-id="8fc9b-131">C# 參考</span><span class="sxs-lookup"><span data-stu-id="8fc9b-131">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="8fc9b-132">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="8fc9b-132">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="8fc9b-133">使用命名空間</span><span class="sxs-lookup"><span data-stu-id="8fc9b-133">Using Namespaces</span></span>](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
 [<span data-ttu-id="8fc9b-134">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="8fc9b-134">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="8fc9b-135">命名空間關鍵字</span><span class="sxs-lookup"><span data-stu-id="8fc9b-135">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [<span data-ttu-id="8fc9b-136">命名空間</span><span class="sxs-lookup"><span data-stu-id="8fc9b-136">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)  
 [<span data-ttu-id="8fc9b-137">using 陳述式</span><span class="sxs-lookup"><span data-stu-id="8fc9b-137">using Statement</span></span>](../../../csharp/language-reference/keywords/using-statement.md)
