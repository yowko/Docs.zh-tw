---
description: -refonly (C# 編譯器選項)
title: -refonly (C# 編譯器選項)
ms.date: 07/08/2017
f1_keywords:
- /refonly
helpviewer_keywords:
- /refonly compiler option [C#]
- -refonly compiler option [C#]
- refonly compiler option [C#]
ms.openlocfilehash: f9a92462203bedff93a4a711ca8742465b7a561c
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "89124743"
---
# <a name="-refonly-c-compiler-options"></a><span data-ttu-id="ed7c1-103">-refonly (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="ed7c1-103">-refonly (C# Compiler Options)</span></span>

<span data-ttu-id="ed7c1-104">**-refonly** 選項指出參考組件應是主要輸出的輸出，而不是實作組件。</span><span class="sxs-lookup"><span data-stu-id="ed7c1-104">The **-refonly** option indicates that a reference assembly should be output instead of an implementation assembly, as the primary output.</span></span> <span data-ttu-id="ed7c1-105">`-refonly` 參數以無訊息模式停用輸出 PDB，因為無法執行參考組件。</span><span class="sxs-lookup"><span data-stu-id="ed7c1-105">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span> <span data-ttu-id="ed7c1-106">此選項會對應到 MSBuild 的 [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) 專案屬性。</span><span class="sxs-lookup"><span data-stu-id="ed7c1-106">This option corresponds to the [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) project property of MSBuild.</span></span>

## <a name="syntax"></a><span data-ttu-id="ed7c1-107">語法</span><span class="sxs-lookup"><span data-stu-id="ed7c1-107">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="ed7c1-108">備註</span><span class="sxs-lookup"><span data-stu-id="ed7c1-108">Remarks</span></span>

<span data-ttu-id="ed7c1-109">參考元件是一種特殊類型的元件，其中只包含代表程式庫公用 API 介面所需的最少量中繼資料。</span><span class="sxs-lookup"><span data-stu-id="ed7c1-109">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="ed7c1-110">它們包括在組建工具中參考元件時，所有重要成員的宣告，但排除對其 API 合約沒有任何影響的私用成員的所有成員執行和宣告。</span><span class="sxs-lookup"><span data-stu-id="ed7c1-110">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="ed7c1-111">如需詳細資訊，請參閱 .NET 指南中的 [參考元件](../../../standard/assembly/reference-assemblies.md) 。</span><span class="sxs-lookup"><span data-stu-id="ed7c1-111">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="ed7c1-112">`-refonly`和 [`-refout`](refout-compiler-option.md) 選項都是互斥的。</span><span class="sxs-lookup"><span data-stu-id="ed7c1-112">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="ed7c1-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed7c1-113">See also</span></span>

- [<span data-ttu-id="ed7c1-114">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="ed7c1-114">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="ed7c1-115">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="ed7c1-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
