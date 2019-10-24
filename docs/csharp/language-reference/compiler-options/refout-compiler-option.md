---
title: -refout (C# 編譯器選項)
ms.date: 08/08/2017
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [C#]
- /refout compiler option [C#]
- -refout compiler option [C#]
ms.openlocfilehash: f48316a1e6f657e3bd0190d269dfe0e875a833d9
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771765"
---
# <a name="-refout-c-compiler-options"></a><span data-ttu-id="b79fe-102">-refout (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="b79fe-102">-refout (C# Compiler Options)</span></span>

<span data-ttu-id="b79fe-103">**-refout** 選項指定參考組件應該輸出的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="b79fe-103">The **-refout** option specifies a file path where the reference assembly should be output.</span></span> <span data-ttu-id="b79fe-104">這在發出 API 中會轉譯成 `metadataPeStream`。</span><span class="sxs-lookup"><span data-stu-id="b79fe-104">This translates to `metadataPeStream` in the Emit API.</span></span> <span data-ttu-id="b79fe-105">此選項會對應到 MSBuild 的 [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) 專案屬性。</span><span class="sxs-lookup"><span data-stu-id="b79fe-105">This option corresponds to the [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) project property of MSBuild.</span></span>

## <a name="syntax"></a><span data-ttu-id="b79fe-106">語法</span><span class="sxs-lookup"><span data-stu-id="b79fe-106">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="b79fe-107">引數</span><span class="sxs-lookup"><span data-stu-id="b79fe-107">Arguments</span></span>

 <span data-ttu-id="b79fe-108">`filepath` 參考組件的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="b79fe-108">`filepath` The filepath for the reference assembly.</span></span> <span data-ttu-id="b79fe-109">它通常應該符合主要組件的路徑。</span><span class="sxs-lookup"><span data-stu-id="b79fe-109">It should generally match that of the primary assembly.</span></span> <span data-ttu-id="b79fe-110">建議慣例 (由 MSBuild 使用) 是將參考組件放在相對於主要組件的 "ref/" 子資料夾中。</span><span class="sxs-lookup"><span data-stu-id="b79fe-110">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span>

## <a name="remarks"></a><span data-ttu-id="b79fe-111">備註</span><span class="sxs-lookup"><span data-stu-id="b79fe-111">Remarks</span></span>

<span data-ttu-id="b79fe-112">參考元件是一種特殊類型的元件，其中只包含代表程式庫公用 API 介面所需的最小中繼資料量。</span><span class="sxs-lookup"><span data-stu-id="b79fe-112">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="b79fe-113">其中包括在建立工具中參考元件時，所有重要成員的宣告，但會排除所有成員的執行，以及對其 API 合約沒有明顯影響的私用成員宣告。</span><span class="sxs-lookup"><span data-stu-id="b79fe-113">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="b79fe-114">如需詳細資訊，請參閱 .NET 中的[參考元件](../../../standard/assembly/reference-assemblies.md)指南。</span><span class="sxs-lookup"><span data-stu-id="b79fe-114">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="b79fe-115">`-refout` 和 [`-refonly`](refonly-compiler-option.md) 選項互斥。</span><span class="sxs-lookup"><span data-stu-id="b79fe-115">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="b79fe-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="b79fe-116">See also</span></span>

- [<span data-ttu-id="b79fe-117">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="b79fe-117">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="b79fe-118">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="b79fe-118">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
