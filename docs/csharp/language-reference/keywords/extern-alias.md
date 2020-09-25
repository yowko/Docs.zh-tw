---
description: 外部別名 - C# 參考
title: 外部別名 - C# 參考
ms.date: 07/20/2015
f1_keywords:
- alias_CSharpKeyword
helpviewer_keywords:
- extern alias keyword [C#]
- aliases [C#], extern keyword
- aliases, extern keyword
ms.assetid: f487bf4f-c943-4fca-851b-e540c83d9027
ms.openlocfilehash: 5ecafa5a989bc183d7f52ac3d4b4d50a81b36014
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203341"
---
# <a name="extern-alias-c-reference"></a><span data-ttu-id="34990-103">外部別名 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="34990-103">extern alias (C# Reference)</span></span>

<span data-ttu-id="34990-104">您可能必須參考兩個具有相同完整類型名稱的組件版本。</span><span class="sxs-lookup"><span data-stu-id="34990-104">You might have to reference two versions of assemblies that have the same fully-qualified type names.</span></span> <span data-ttu-id="34990-105">例如，您可能必須在相同的應用程式中使用兩個或多個組件版本。</span><span class="sxs-lookup"><span data-stu-id="34990-105">For example, you might have to use two or more versions of an assembly in the same application.</span></span> <span data-ttu-id="34990-106">藉由使用外部組件別名，來自每個組件的命名空間可包裝在別名所命名的根層級命名空間內，這樣即可讓它們在相同的檔案中使用。</span><span class="sxs-lookup"><span data-stu-id="34990-106">By using an external assembly alias, the namespaces from each assembly can be wrapped inside root-level namespaces named by the alias, which enables them to be used in the same file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="34990-107">[extern](./extern.md) 關鍵字也可作為方法修飾詞，用於宣告以 Unmanaged 程式碼撰寫的方法。</span><span class="sxs-lookup"><span data-stu-id="34990-107">The [extern](./extern.md) keyword is also used as a method modifier, declaring a method written in unmanaged code.</span></span>  
  
 <span data-ttu-id="34990-108">若要參考兩個具有相同完整類型名稱的組件，則必須在命令提示字元中指定別名，如下所示：</span><span class="sxs-lookup"><span data-stu-id="34990-108">To reference two assemblies with the same fully-qualified type names, an alias must be specified at a command prompt, as follows:</span></span>  
  
 `/r:GridV1=grid.dll`  
  
 `/r:GridV2=grid20.dll`  
  
 <span data-ttu-id="34990-109">這會建立外部別名 `GridV1` 和 `GridV2`。</span><span class="sxs-lookup"><span data-stu-id="34990-109">This creates the external aliases `GridV1` and `GridV2`.</span></span> <span data-ttu-id="34990-110">若要從程式內使用這些別名，請使用 `extern` 關鍵字參考別名。</span><span class="sxs-lookup"><span data-stu-id="34990-110">To use these aliases from within a program, reference them by using the `extern` keyword.</span></span> <span data-ttu-id="34990-111">例如：</span><span class="sxs-lookup"><span data-stu-id="34990-111">For example:</span></span>  
  
 `extern alias GridV1;`  
  
 `extern alias GridV2;`  
  
 <span data-ttu-id="34990-112">每個外部別名宣告會引進另一個與全域命名空間平行 (但不在其內) 的根層級命名空間。</span><span class="sxs-lookup"><span data-stu-id="34990-112">Each extern alias declaration introduces an additional root-level namespace that parallels (but does not lie within) the global namespace.</span></span> <span data-ttu-id="34990-113">因此，來自每個組件的類型可使用其完整名稱 (源自適當的命名空間別名) 來參考，而不會有模擬兩可的情況。</span><span class="sxs-lookup"><span data-stu-id="34990-113">Thus types from each assembly can be referred to without ambiguity by using their fully qualified name, rooted in the appropriate namespace-alias.</span></span>  
  
 <span data-ttu-id="34990-114">在上述範例中，`GridV1::Grid` 是來自 `grid.dll` 的方格控制項，而 `GridV2::Grid` 是來自 `grid20.dll` 的方格控制項。</span><span class="sxs-lookup"><span data-stu-id="34990-114">In the previous example, `GridV1::Grid` would be the grid control from `grid.dll`, and `GridV2::Grid` would be the grid control from `grid20.dll`.</span></span>  
  
## <a name="using-visual-studio"></a><span data-ttu-id="34990-115">使用 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="34990-115">Using Visual Studio</span></span>

<span data-ttu-id="34990-116">如果您使用 Visual Studio，就可以用類似的方式提供別名。</span><span class="sxs-lookup"><span data-stu-id="34990-116">If you are using Visual Studio, aliases can be provided in similar way.</span></span>

<span data-ttu-id="34990-117">在 Visual Studio 中將 *grid.dll* 和 *grid20.dll* 的參考新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="34990-117">Add reference of *grid.dll* and *grid20.dll* to your project in Visual Studio.</span></span> <span data-ttu-id="34990-118">開啟 [內容] 索引標籤，並分別將別名從 global 變更為 GridV1 和 GridV2。</span><span class="sxs-lookup"><span data-stu-id="34990-118">Open a property tab and change the Aliases from global to GridV1 and GridV2 respectively.</span></span>

<span data-ttu-id="34990-119">使用上述相同方式來使用這些別名</span><span class="sxs-lookup"><span data-stu-id="34990-119">Use these aliases the same way above</span></span>

```csharp
 extern alias GridV1;  
  
 extern alias GridV2;  
```

<span data-ttu-id="34990-120">現在您可以 *使用 alias*指示詞來建立命名空間或類型的別名。</span><span class="sxs-lookup"><span data-stu-id="34990-120">Now you can create alias for a namespace or a type by *using alias directive*.</span></span> <span data-ttu-id="34990-121">如需詳細資訊，請參閱 [using](using-directive.md)指示詞。</span><span class="sxs-lookup"><span data-stu-id="34990-121">For more information, see [using directive](using-directive.md).</span></span>

```csharp
using Class1V1 = GridV1::Namespace.Class1;

using Class1V2 = GridV2::Namespace.Class1;
```

## <a name="c-language-specification"></a><span data-ttu-id="34990-122">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="34990-122">C# Language Specification</span></span>  

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="34990-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34990-123">See also</span></span>

- [<span data-ttu-id="34990-124">C # 參考</span><span class="sxs-lookup"><span data-stu-id="34990-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="34990-125">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="34990-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="34990-126">C # 關鍵字</span><span class="sxs-lookup"><span data-stu-id="34990-126">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="34990-127">：：運算子</span><span class="sxs-lookup"><span data-stu-id="34990-127">:: Operator</span></span>](../operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="34990-128">-reference (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="34990-128">-reference (C# Compiler Options)</span></span>](../compiler-options/reference-compiler-option.md)
