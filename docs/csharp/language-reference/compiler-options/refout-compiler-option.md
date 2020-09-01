---
description: -refout (C# 編譯器選項)
title: -refout (C# 編譯器選項)
ms.date: 08/08/2017
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [C#]
- /refout compiler option [C#]
- -refout compiler option [C#]
ms.openlocfilehash: 424782e4607fea63130e95ab09a671c75fe1404d
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128710"
---
# <a name="-refout-c-compiler-options"></a><span data-ttu-id="3359b-103">-refout (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="3359b-103">-refout (C# Compiler Options)</span></span>

<span data-ttu-id="3359b-104">**-refout** 選項指定參考組件應該輸出的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="3359b-104">The **-refout** option specifies a file path where the reference assembly should be output.</span></span> <span data-ttu-id="3359b-105">這在發出 API 中會轉譯成 `metadataPeStream`。</span><span class="sxs-lookup"><span data-stu-id="3359b-105">This translates to `metadataPeStream` in the Emit API.</span></span> <span data-ttu-id="3359b-106">此選項會對應到 MSBuild 的 [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) 專案屬性。</span><span class="sxs-lookup"><span data-stu-id="3359b-106">This option corresponds to the [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) project property of MSBuild.</span></span>

## <a name="syntax"></a><span data-ttu-id="3359b-107">語法</span><span class="sxs-lookup"><span data-stu-id="3359b-107">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="3359b-108">引數</span><span class="sxs-lookup"><span data-stu-id="3359b-108">Arguments</span></span>

 <span data-ttu-id="3359b-109">`filepath` 參考組件的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="3359b-109">`filepath` The filepath for the reference assembly.</span></span> <span data-ttu-id="3359b-110">它通常應該符合主要組件的路徑。</span><span class="sxs-lookup"><span data-stu-id="3359b-110">It should generally match that of the primary assembly.</span></span> <span data-ttu-id="3359b-111">建議慣例 (由 MSBuild 使用) 是將參考組件放在相對於主要組件的 "ref/" 子資料夾中。</span><span class="sxs-lookup"><span data-stu-id="3359b-111">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span>

## <a name="remarks"></a><span data-ttu-id="3359b-112">備註</span><span class="sxs-lookup"><span data-stu-id="3359b-112">Remarks</span></span>

<span data-ttu-id="3359b-113">參考元件是一種特殊類型的元件，其中只包含代表程式庫公用 API 介面所需的最少量中繼資料。</span><span class="sxs-lookup"><span data-stu-id="3359b-113">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="3359b-114">它們包括在組建工具中參考元件時，所有重要成員的宣告，但排除對其 API 合約沒有任何影響的私用成員的所有成員執行和宣告。</span><span class="sxs-lookup"><span data-stu-id="3359b-114">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="3359b-115">如需詳細資訊，請參閱 .NET 指南中的 [參考元件](../../../standard/assembly/reference-assemblies.md) 。</span><span class="sxs-lookup"><span data-stu-id="3359b-115">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="3359b-116">`-refout`和 [`-refonly`](refonly-compiler-option.md) 選項都是互斥的。</span><span class="sxs-lookup"><span data-stu-id="3359b-116">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="3359b-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3359b-117">See also</span></span>

- [<span data-ttu-id="3359b-118">C # 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="3359b-118">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="3359b-119">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="3359b-119">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
