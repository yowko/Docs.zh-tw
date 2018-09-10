---
title: 外部別名 (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- alias_CSharpKeyword
helpviewer_keywords:
- extern alias keyword [C#]
- aliases [C#], extern keyword
- aliases, extern keyword
ms.assetid: f487bf4f-c943-4fca-851b-e540c83d9027
ms.openlocfilehash: 66210bc1a84e2c3239dcac72cdc194b14dcccf30
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43524024"
---
# <a name="extern-alias-c-reference"></a><span data-ttu-id="b943f-102">外部別名 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="b943f-102">extern alias (C# Reference)</span></span>
<span data-ttu-id="b943f-103">您可能必須參考兩個具有相同完整類型名稱的組件版本。</span><span class="sxs-lookup"><span data-stu-id="b943f-103">You might have to reference two versions of assemblies that have the same fully-qualified type names.</span></span> <span data-ttu-id="b943f-104">例如，您可能必須在相同的應用程式中使用兩個或多個組件版本。</span><span class="sxs-lookup"><span data-stu-id="b943f-104">For example, you might have to use two or more versions of an assembly in the same application.</span></span> <span data-ttu-id="b943f-105">藉由使用外部組件別名，來自每個組件的命名空間可包裝在別名所命名的根層級命名空間內，這樣即可讓它們在相同的檔案中使用。</span><span class="sxs-lookup"><span data-stu-id="b943f-105">By using an external assembly alias, the namespaces from each assembly can be wrapped inside root-level namespaces named by the alias, which enables them to be used in the same file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b943f-106">[extern](../../../csharp/language-reference/keywords/extern.md) 關鍵字也可作為方法修飾詞，用於宣告以 Unmanaged 程式碼撰寫的方法。</span><span class="sxs-lookup"><span data-stu-id="b943f-106">The [extern](../../../csharp/language-reference/keywords/extern.md) keyword is also used as a method modifier, declaring a method written in unmanaged code.</span></span>  
  
 <span data-ttu-id="b943f-107">若要參考兩個具有相同完整類型名稱的組件，則必須在命令提示字元中指定別名，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b943f-107">To reference two assemblies with the same fully-qualified type names, an alias must be specified at a command prompt, as follows:</span></span>  
  
 `/r:GridV1=grid.dll`  
  
 `/r:GridV2=grid20.dll`  
  
 <span data-ttu-id="b943f-108">這會建立外部別名 `GridV1` 和 `GridV2`。</span><span class="sxs-lookup"><span data-stu-id="b943f-108">This creates the external aliases `GridV1` and `GridV2`.</span></span> <span data-ttu-id="b943f-109">若要從程式內使用這些別名，請使用 `extern` 關鍵字參考別名。</span><span class="sxs-lookup"><span data-stu-id="b943f-109">To use these aliases from within a program, reference them by using the `extern` keyword.</span></span> <span data-ttu-id="b943f-110">例如: </span><span class="sxs-lookup"><span data-stu-id="b943f-110">For example:</span></span>  
  
 `extern alias GridV1;`  
  
 `extern alias GridV2;`  
  
 <span data-ttu-id="b943f-111">每個外部別名宣告會引進另一個與全域命名空間平行 (但不在其內) 的根層級命名空間。</span><span class="sxs-lookup"><span data-stu-id="b943f-111">Each extern alias declaration introduces an additional root-level namespace that parallels (but does not lie within) the global namespace.</span></span> <span data-ttu-id="b943f-112">因此，來自每個組件的類型可使用其完整名稱 (源自適當的命名空間別名) 來參考，而不會有模擬兩可的情況。</span><span class="sxs-lookup"><span data-stu-id="b943f-112">Thus types from each assembly can be referred to without ambiguity by using their fully qualified name, rooted in the appropriate namespace-alias.</span></span>  
  
 <span data-ttu-id="b943f-113">在上述範例中，`GridV1::Grid` 是來自 `grid.dll` 的方格控制項，而 `GridV2::Grid` 是來自 `grid20.dll` 的方格控制項。</span><span class="sxs-lookup"><span data-stu-id="b943f-113">In the previous example, `GridV1::Grid` would be the grid control from `grid.dll`, and `GridV2::Grid` would be the grid control from `grid20.dll`.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="b943f-114">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="b943f-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b943f-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="b943f-115">See Also</span></span>

- [<span data-ttu-id="b943f-116">C# 參考</span><span class="sxs-lookup"><span data-stu-id="b943f-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="b943f-117">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="b943f-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="b943f-118">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="b943f-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="b943f-119">命名空間關鍵字</span><span class="sxs-lookup"><span data-stu-id="b943f-119">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
- [<span data-ttu-id="b943f-120">:: 運算子</span><span class="sxs-lookup"><span data-stu-id="b943f-120">:: Operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
- [<span data-ttu-id="b943f-121">/reference (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="b943f-121">/reference (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)
