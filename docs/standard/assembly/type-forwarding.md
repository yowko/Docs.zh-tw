---
title: Common Language Runtime 中的類型轉送
description: 類型轉送可讓您將類型移至另一個 .NET 元件，而不需要重新編譯使用原始元件的應用程式。
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET], type forwarding
- type forwarding
ms.assetid: 51f8ffa3-c253-4201-a3d3-c4fad85ae097
dev_langs:
- csharp
- cpp
ms.openlocfilehash: cd166068993fb5d1a5164615de3926a06dda8098
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92687662"
---
# <a name="type-forwarding-in-the-common-language-runtime"></a><span data-ttu-id="3be57-103">Common Language Runtime 中的類型轉送</span><span class="sxs-lookup"><span data-stu-id="3be57-103">Type forwarding in the common language runtime</span></span>

<span data-ttu-id="3be57-104">型別轉送可讓您將型別移至另一個組件，而無須重新編譯使用原始組件的應用程式。</span><span class="sxs-lookup"><span data-stu-id="3be57-104">Type forwarding allows you to move a type to another assembly without having to recompile applications that use the original assembly.</span></span>  
  
 <span data-ttu-id="3be57-105">例如，假設應用程式 `Example` 在名為 *Utility.dll* 的元件中使用類別。</span><span class="sxs-lookup"><span data-stu-id="3be57-105">For example, suppose an application uses the `Example` class in an assembly named *Utility.dll* .</span></span> <span data-ttu-id="3be57-106">*Utility.dll* 的開發人員可能會決定重構元件，並在程式中將此 `Example` 類別移至另一個元件。</span><span class="sxs-lookup"><span data-stu-id="3be57-106">The developers of *Utility.dll* might decide to refactor the assembly, and in the process they might move the `Example` class to another assembly.</span></span> <span data-ttu-id="3be57-107">如果舊版的 *Utility.dll* 取代為新版本的 *Utility.dll* 和其附屬元件，則使用類別的應用程式 `Example` 會失敗，因為它 `Example` 在新版本的 *Utility.dll* 中找不到類別。</span><span class="sxs-lookup"><span data-stu-id="3be57-107">If the old version of *Utility.dll* is replaced by the new version of *Utility.dll* and its companion assembly, the application that uses the `Example` class fails because it cannot locate the `Example` class in the new version of *Utility.dll* .</span></span>  
  
 <span data-ttu-id="3be57-108">*Utility.dll* 的開發人員可以使用屬性轉送類別的要求，來避免這個情況 `Example` <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="3be57-108">The developers of *Utility.dll* can avoid this by forwarding requests for the `Example` class, using the <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> attribute.</span></span> <span data-ttu-id="3be57-109">如果屬性已套用至 *Utility.dll* 的新版本，則會將類別的要求 `Example` 轉送至現在包含類別的元件。</span><span class="sxs-lookup"><span data-stu-id="3be57-109">If the attribute has been applied to the new version of *Utility.dll* , requests for the `Example` class are forwarded to the assembly that now contains the class.</span></span> <span data-ttu-id="3be57-110">現有的應用程式會繼續正常運作，而不必重新編譯。</span><span class="sxs-lookup"><span data-stu-id="3be57-110">The existing application continues to function normally, without recompilation.</span></span>

## <a name="forward-a-type"></a><span data-ttu-id="3be57-111">轉寄型別</span><span class="sxs-lookup"><span data-stu-id="3be57-111">Forward a type</span></span>

 <span data-ttu-id="3be57-112">轉送型別有四個步驟︰</span><span class="sxs-lookup"><span data-stu-id="3be57-112">There are four steps to forwarding a type:</span></span>  
  
1. <span data-ttu-id="3be57-113">將型別的原始程式碼從原始組件移至目的地組件。</span><span class="sxs-lookup"><span data-stu-id="3be57-113">Move the source code for the type from the original assembly to the destination assembly.</span></span>  

2. <span data-ttu-id="3be57-114">在使用所尋找類型的組件中，為移動的類型新增 <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>。</span><span class="sxs-lookup"><span data-stu-id="3be57-114">In the assembly where the type used to be located, add a <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> for the type that was moved.</span></span> <span data-ttu-id="3be57-115">下列程式碼示範已移動之名為 `Example` 的型別的屬性。</span><span class="sxs-lookup"><span data-stu-id="3be57-115">The following code shows the attribute for a type named `Example` that was moved.</span></span>  

   ```cpp  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
   ```

   ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
   ```  

3. <span data-ttu-id="3be57-116">編譯現在包含型別的組件。</span><span class="sxs-lookup"><span data-stu-id="3be57-116">Compile the assembly that now contains the type.</span></span>  

4. <span data-ttu-id="3be57-117">重新編譯型別曾經所在的組件，具有現在包含型別之組件的參考。</span><span class="sxs-lookup"><span data-stu-id="3be57-117">Recompile the assembly where the type used to be located, with a reference to the assembly that now contains the type.</span></span> <span data-ttu-id="3be57-118">例如，如果您要從命令列編譯 c # 檔案，請使用 [-reference (c # 編譯器選項) ](../../csharp/language-reference/compiler-options/reference-compiler-option.md) 選項來指定包含型別的元件。</span><span class="sxs-lookup"><span data-stu-id="3be57-118">For example, if you are compiling a C# file from the command line, use the [-reference (C# compiler options)](../../csharp/language-reference/compiler-options/reference-compiler-option.md) option to specify the assembly that contains the type.</span></span> <span data-ttu-id="3be57-119">在 C++ 中，在來源檔案中使用 [#using](/cpp/preprocessor/hash-using-directive-cpp) 指示詞以指定包含型別的組件。</span><span class="sxs-lookup"><span data-stu-id="3be57-119">In C++, use the [#using](/cpp/preprocessor/hash-using-directive-cpp) directive in the source file to specify the assembly that contains the type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3be57-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="3be57-120">See also</span></span>

- <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>
- [<span data-ttu-id="3be57-121">類型轉送 (c + +/CLI) </span><span class="sxs-lookup"><span data-stu-id="3be57-121">Type forwarding (C++/CLI)</span></span>](/cpp/windows/type-forwarding-cpp-cli)
- [<span data-ttu-id="3be57-122">#using 指示詞</span><span class="sxs-lookup"><span data-stu-id="3be57-122">#using directive</span></span>](/cpp/preprocessor/hash-using-directive-cpp)
