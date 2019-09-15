---
title: Common language runtime 中的類型轉送
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], type forwarding
- type forwarding
ms.assetid: 51f8ffa3-c253-4201-a3d3-c4fad85ae097
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- cpp
ms.openlocfilehash: f71b56daf5e8a012a66f60805246b4164d1b0a07
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973016"
---
# <a name="type-forwarding-in-the-common-language-runtime"></a><span data-ttu-id="b70d6-102">Common language runtime 中的類型轉送</span><span class="sxs-lookup"><span data-stu-id="b70d6-102">Type forwarding in the common language runtime</span></span>
<span data-ttu-id="b70d6-103">型別轉送可讓您將型別移至另一個組件，而無須重新編譯使用原始組件的應用程式。</span><span class="sxs-lookup"><span data-stu-id="b70d6-103">Type forwarding allows you to move a type to another assembly without having to recompile applications that use the original assembly.</span></span>  
  
 <span data-ttu-id="b70d6-104">例如，假設應用程式在名為`Example` *Utility*的元件中使用類別。</span><span class="sxs-lookup"><span data-stu-id="b70d6-104">For example, suppose an application uses the `Example` class in an assembly named *Utility.dll*.</span></span> <span data-ttu-id="b70d6-105">*Utility*的開發人員可能會決定重構元件，而在進程中，他們可能會將`Example`類別移至另一個元件。</span><span class="sxs-lookup"><span data-stu-id="b70d6-105">The developers of *Utility.dll* might decide to refactor the assembly, and in the process they might move the `Example` class to another assembly.</span></span> <span data-ttu-id="b70d6-106">如果舊版*的公用程式 .dll 和其*隨附元件取代了舊版本的`Example` *utility* ，則使用類別的應用程式`Example`會失敗，因為它在新版的*中找不到類別公用程式 .dll*。</span><span class="sxs-lookup"><span data-stu-id="b70d6-106">If the old version of *Utility.dll* is replaced by the new version of *Utility.dll* and its companion assembly, the application that uses the `Example` class fails because it cannot locate the `Example` class in the new version of *Utility.dll*.</span></span>  
  
 <span data-ttu-id="b70d6-107">*Utility*的開發人員可以使用`Example` <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>屬性來轉送類別的要求，藉以避免這種情況。</span><span class="sxs-lookup"><span data-stu-id="b70d6-107">The developers of *Utility.dll* can avoid this by forwarding requests for the `Example` class, using the <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> attribute.</span></span> <span data-ttu-id="b70d6-108">如果屬性已套用至新版本的*公用程式 .dll*，則`Example`會將類別的要求轉送到現在包含類別的元件。</span><span class="sxs-lookup"><span data-stu-id="b70d6-108">If the attribute has been applied to the new version of *Utility.dll*, requests for the `Example` class are forwarded to the assembly that now contains the class.</span></span> <span data-ttu-id="b70d6-109">現有的應用程式會繼續正常運作，而不必重新編譯。</span><span class="sxs-lookup"><span data-stu-id="b70d6-109">The existing application continues to function normally, without recompilation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b70d6-110">在 .NET Framework 2.0 版中，您無法從在 Visual Basic 中撰寫的組件轉送型別。</span><span class="sxs-lookup"><span data-stu-id="b70d6-110">In the .NET Framework version 2.0, you cannot forward types from assemblies written in Visual Basic.</span></span> <span data-ttu-id="b70d6-111">不過，在 Visual Basic 中撰寫的應用程式可以使用轉送型別。</span><span class="sxs-lookup"><span data-stu-id="b70d6-111">However, an application written in Visual Basic can consume forwarded types.</span></span> <span data-ttu-id="b70d6-112">也就是說，如果應用程式使用以 C# 或 C++ 編碼的組件，且來自該組件的型別轉送至另一個組件，則 Visual Basic 應用程式可以使用轉送型別。</span><span class="sxs-lookup"><span data-stu-id="b70d6-112">That is, if the application uses an assembly coded in C# or C++, and a type from that assembly is forwarded to another assembly, the Visual Basic application can use the forwarded type.</span></span>  
  
## <a name="forward-types"></a><span data-ttu-id="b70d6-113">轉送類型</span><span class="sxs-lookup"><span data-stu-id="b70d6-113">Forward types</span></span>  
 <span data-ttu-id="b70d6-114">轉送型別有四個步驟︰</span><span class="sxs-lookup"><span data-stu-id="b70d6-114">There are four steps to forwarding a type:</span></span>  
  
1. <span data-ttu-id="b70d6-115">將型別的原始程式碼從原始組件移至目的地組件。</span><span class="sxs-lookup"><span data-stu-id="b70d6-115">Move the source code for the type from the original assembly to the destination assembly.</span></span>  
   
2. <span data-ttu-id="b70d6-116">在使用所尋找類型的組件中，為移動的類型新增 <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>。</span><span class="sxs-lookup"><span data-stu-id="b70d6-116">In the assembly where the type used to be located, add a <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> for the type that was moved.</span></span> <span data-ttu-id="b70d6-117">下列程式碼示範已移動之名為 `Example` 的型別的屬性。</span><span class="sxs-lookup"><span data-stu-id="b70d6-117">The following code shows the attribute for a type named `Example` that was moved.</span></span>  
   
   ```cpp  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
   ```
   
   ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
   ```  
   
3. <span data-ttu-id="b70d6-118">編譯現在包含型別的組件。</span><span class="sxs-lookup"><span data-stu-id="b70d6-118">Compile the assembly that now contains the type.</span></span>  
   
4. <span data-ttu-id="b70d6-119">重新編譯型別曾經所在的組件，具有現在包含型別之組件的參考。</span><span class="sxs-lookup"><span data-stu-id="b70d6-119">Recompile the assembly where the type used to be located, with a reference to the assembly that now contains the type.</span></span> <span data-ttu-id="b70d6-120">例如，如果您要從命令列C#編譯檔案，請使用[/reference （C#編譯器選項）](../../csharp/language-reference/compiler-options/reference-compiler-option.md)選項來指定包含型別的元件。</span><span class="sxs-lookup"><span data-stu-id="b70d6-120">For example, if you are compiling a C# file from the command line, use the [/reference (C# compiler options)](../../csharp/language-reference/compiler-options/reference-compiler-option.md) option to specify the assembly that contains the type.</span></span> <span data-ttu-id="b70d6-121">在 C++ 中，在來源檔案中使用 [#using](/cpp/preprocessor/hash-using-directive-cpp) 指示詞以指定包含型別的組件。</span><span class="sxs-lookup"><span data-stu-id="b70d6-121">In C++, use the [#using](/cpp/preprocessor/hash-using-directive-cpp) directive in the source file to specify the assembly that contains the type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b70d6-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b70d6-122">See also</span></span>

- <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>
- [<span data-ttu-id="b70d6-123">類型轉送（C++/cli）</span><span class="sxs-lookup"><span data-stu-id="b70d6-123">Type forwarding (C++/CLI)</span></span>](/cpp/windows/type-forwarding-cpp-cli)
- [<span data-ttu-id="b70d6-124">#using 指示詞</span><span class="sxs-lookup"><span data-stu-id="b70d6-124">#using directive</span></span>](/cpp/preprocessor/hash-using-directive-cpp)
