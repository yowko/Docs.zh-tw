---
title: "-define (C# 編譯器選項)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /define
helpviewer_keywords:
- -define compiler option [C#]
- /define compiler option [C#]
- -d compiler option [C#]
- define compiler option [C#]
- /d compiler option [C#]
- d compiler option [C#]
ms.assetid: f17d7b4d-82d0-4133-8563-68cced1cac6e
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 273437a4250a393274fa20ad4c02b61dce35ed34
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="-define-c-compiler-options"></a><span data-ttu-id="92bc5-102">-define (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="92bc5-102">-define (C# Compiler Options)</span></span>
<span data-ttu-id="92bc5-103">**-define** 選項會將 `name` 定義為程式中所有原始程式碼檔的符號。</span><span class="sxs-lookup"><span data-stu-id="92bc5-103">The **-define** option defines `name` as a symbol in all source code files your program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92bc5-104">語法</span><span class="sxs-lookup"><span data-stu-id="92bc5-104">Syntax</span></span>  
  
```console  
-define:name[;name2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="92bc5-105">引數</span><span class="sxs-lookup"><span data-stu-id="92bc5-105">Arguments</span></span>  
 <span data-ttu-id="92bc5-106">`name`, `name2`</span><span class="sxs-lookup"><span data-stu-id="92bc5-106">`name`, `name2`</span></span>  
 <span data-ttu-id="92bc5-107">您要定義的一或多個符號之名稱。</span><span class="sxs-lookup"><span data-stu-id="92bc5-107">The name of one or more symbols that you want to define.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92bc5-108">備註</span><span class="sxs-lookup"><span data-stu-id="92bc5-108">Remarks</span></span>  
 <span data-ttu-id="92bc5-109">**-define** 選項的作用與使用 [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) 前置處理器指示詞相同，不同之處在於編譯器選項對專案中的所有檔案都有效。</span><span class="sxs-lookup"><span data-stu-id="92bc5-109">The **-define** option has the same effect as using a [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) preprocessor directive except that the compiler option is in effect for all files in the project.</span></span> <span data-ttu-id="92bc5-110">直到原始程式檔中的 [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) 指示詞移除符號的定義之前，符號在原始程式檔中都會維持已定義狀態。</span><span class="sxs-lookup"><span data-stu-id="92bc5-110">A symbol remains defined in a source file until an [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) directive in the source file removes the definition.</span></span> <span data-ttu-id="92bc5-111">使用 -define 選項時，某個檔案中的 `#undef` 指示詞不會對專案中的其他原始程式碼檔造成影響。</span><span class="sxs-lookup"><span data-stu-id="92bc5-111">When you use the -define option, an `#undef` directive in one file has no effect on other source code files in the project.</span></span>  
  
 <span data-ttu-id="92bc5-112">您可以使用此選項建立的符號，搭配 [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)、[#else](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md)、[#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md) 和 [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md)，有條件地編譯原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="92bc5-112">You can use symbols created by this option with [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md), [#else](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md), [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md), and [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) to compile source files conditionally.</span></span>  
  
 <span data-ttu-id="92bc5-113">**-d** 是 **-define** 的簡短形式。</span><span class="sxs-lookup"><span data-stu-id="92bc5-113">**-d** is the short form of **-define**.</span></span>  
  
 <span data-ttu-id="92bc5-114">您可以使用分號或逗號分隔符號名稱，以 **-define** 定義多個符號。</span><span class="sxs-lookup"><span data-stu-id="92bc5-114">You can define multiple symbols with **-define** by using a semicolon or comma to separate symbol names.</span></span> <span data-ttu-id="92bc5-115">例如: </span><span class="sxs-lookup"><span data-stu-id="92bc5-115">For example:</span></span>  
  
```console  
-define:DEBUG;TUESDAY  
```  
  
 <span data-ttu-id="92bc5-116">C# 編譯器本身不會定義任何您可以在原始程式碼中使用的符號或巨集；所有符號定義都必須是使用者定義。</span><span class="sxs-lookup"><span data-stu-id="92bc5-116">The C# compiler itself defines no symbols or macros that you can use in your source code; all symbol definitions must be user-defined.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="92bc5-117">C# `#define` 不允許指定數值給符號，這點和 C++ 語言相同。</span><span class="sxs-lookup"><span data-stu-id="92bc5-117">The C# `#define` does not allow a symbol to be given a value, as in languages such as C++.</span></span> <span data-ttu-id="92bc5-118">例如，`#define` 不能用來建立巨集或定義常數。</span><span class="sxs-lookup"><span data-stu-id="92bc5-118">For example, `#define` cannot be used to create a macro or to define a constant.</span></span> <span data-ttu-id="92bc5-119">如果您需要定義常數，請使用 `enum` 變數。</span><span class="sxs-lookup"><span data-stu-id="92bc5-119">If you need to define a constant, use an `enum` variable.</span></span> <span data-ttu-id="92bc5-120">如果您想要建立 C++ 樣式巨集，請考慮替代項目，例如泛型。</span><span class="sxs-lookup"><span data-stu-id="92bc5-120">If you want to create a C++ style macro, consider alternatives such as generics.</span></span> <span data-ttu-id="92bc5-121">由於巨集非常可能發生錯誤，因此 C# 不允許使用巨集，而是提供較為安全的替代項目。</span><span class="sxs-lookup"><span data-stu-id="92bc5-121">Since macros are notoriously error-prone, C# disallows their use but provides safer alternatives.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="92bc5-122">在 Visual Studio 開發環境中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="92bc5-122">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="92bc5-123">開啟專案的 [屬性] 頁面。</span><span class="sxs-lookup"><span data-stu-id="92bc5-123">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="92bc5-124">在 [建置] 索引標籤的 [條件式編譯的符號] 方塊中，輸入要定義的符號。</span><span class="sxs-lookup"><span data-stu-id="92bc5-124">On the **Build** tab, type the symbol that is to be defined in the **Conditional compilation symbols** box.</span></span> <span data-ttu-id="92bc5-125">例如，如果您想要使用下列程式碼範例，只要在文字方塊中鍵入 `xx` 即可。</span><span class="sxs-lookup"><span data-stu-id="92bc5-125">For example, if you are using the code example that follows, just type `xx` into the text box.</span></span>  
  
 <span data-ttu-id="92bc5-126">如需如何以程式設計方式設定這個編譯器選項的資訊，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>。</span><span class="sxs-lookup"><span data-stu-id="92bc5-126">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92bc5-127">範例</span><span class="sxs-lookup"><span data-stu-id="92bc5-127">Example</span></span>  
  
```csharp  
// preprocessor_define.cs  
// compile with: -define:xx  
// or uncomment the next line  
// #define xx  
using System;  
public class Test   
{  
    public static void Main()   
    {  
        #if (xx)   
            Console.WriteLine("xx defined");  
        #else  
            Console.WriteLine("xx not defined");  
        #endif  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="92bc5-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="92bc5-128">See Also</span></span>  
 [<span data-ttu-id="92bc5-129">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="92bc5-129">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="92bc5-130">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="92bc5-130">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
