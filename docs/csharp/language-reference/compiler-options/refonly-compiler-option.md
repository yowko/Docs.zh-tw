---
title: -refonly (C# 編譯器選項)
ms.date: 07/08/2017
f1_keywords:
- /refonly
helpviewer_keywords:
- /refonly compiler option [C#]
- -refonly compiler option [C#]
- refonly compiler option [C#]
ms.openlocfilehash: 856b65d3b2217dbe5d53ecda00723b47247d80a4
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72773858"
---
# <a name="-refonly-c-compiler-options"></a><span data-ttu-id="40f44-102">-refonly (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="40f44-102">-refonly (C# Compiler Options)</span></span>

<span data-ttu-id="40f44-103">**-refonly** 選項指出參考組件應是主要輸出的輸出，而不是實作組件。</span><span class="sxs-lookup"><span data-stu-id="40f44-103">The **-refonly** option indicates that a reference assembly should be output instead of an implementation assembly, as the primary output.</span></span> <span data-ttu-id="40f44-104">`-refonly` 參數以無訊息模式停用輸出 PDB，因為無法執行參考組件。</span><span class="sxs-lookup"><span data-stu-id="40f44-104">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span> <span data-ttu-id="40f44-105">此選項會對應到 MSBuild 的 [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) 專案屬性。</span><span class="sxs-lookup"><span data-stu-id="40f44-105">This option corresponds to the [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) project property of MSBuild.</span></span>

## <a name="syntax"></a><span data-ttu-id="40f44-106">語法</span><span class="sxs-lookup"><span data-stu-id="40f44-106">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="40f44-107">備註</span><span class="sxs-lookup"><span data-stu-id="40f44-107">Remarks</span></span>

<span data-ttu-id="40f44-108">參考元件是一種特殊類型的元件，其中只包含代表程式庫公用 API 介面所需的最小中繼資料量。</span><span class="sxs-lookup"><span data-stu-id="40f44-108">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="40f44-109">其中包括在建立工具中參考元件時，所有重要成員的宣告，但會排除所有成員的執行，以及對其 API 合約沒有明顯影響的私用成員宣告。</span><span class="sxs-lookup"><span data-stu-id="40f44-109">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="40f44-110">如需詳細資訊，請參閱 .NET 中的[參考元件](../../../standard/assembly/reference-assemblies.md)指南。</span><span class="sxs-lookup"><span data-stu-id="40f44-110">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="40f44-111">`-refonly` 和 [`-refout`](refout-compiler-option.md) 選項互斥。</span><span class="sxs-lookup"><span data-stu-id="40f44-111">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="40f44-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="40f44-112">See also</span></span>

- [<span data-ttu-id="40f44-113">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="40f44-113">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="40f44-114">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="40f44-114">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
