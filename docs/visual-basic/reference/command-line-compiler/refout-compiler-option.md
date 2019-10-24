---
title: -refout （Visual Basic）
ms.date: 03/16/2018
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [Visual Basic]
- /refout compiler option [Visual Basic]
- -refout compiler option [Visual Basic]
ms.openlocfilehash: 552e611f222bfcc3ce12520ecdb891fd7b8b21de
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775554"
---
# <a name="-refout-visual-basic"></a><span data-ttu-id="3dad8-102">-refout （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="3dad8-102">-refout (Visual Basic)</span></span>

<span data-ttu-id="3dad8-103">**-refout** 選項指定參考組件應該輸出的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="3dad8-103">The **-refout** option specifies a file path where the reference assembly should be output.</span></span>

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a><span data-ttu-id="3dad8-104">語法</span><span class="sxs-lookup"><span data-stu-id="3dad8-104">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="3dad8-105">引數</span><span class="sxs-lookup"><span data-stu-id="3dad8-105">Arguments</span></span>

`filepath`  
<span data-ttu-id="3dad8-106">參考元件的路徑和檔案名。</span><span class="sxs-lookup"><span data-stu-id="3dad8-106">The path and filename of the reference assembly.</span></span> <span data-ttu-id="3dad8-107">它通常應該位於主要元件的子資料夾中。</span><span class="sxs-lookup"><span data-stu-id="3dad8-107">It should generally be in a sub-folder of the primary assembly.</span></span> <span data-ttu-id="3dad8-108">建議慣例 (由 MSBuild 使用) 是將參考組件放在相對於主要組件的 "ref/" 子資料夾中。</span><span class="sxs-lookup"><span data-stu-id="3dad8-108">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span> <span data-ttu-id="3dad8-109">@No__t_0 中的所有資料夾都必須存在;編譯器不會建立它們。</span><span class="sxs-lookup"><span data-stu-id="3dad8-109">All folders in `filepath` must exist; the compiler does not create them.</span></span>

## <a name="remarks"></a><span data-ttu-id="3dad8-110">備註</span><span class="sxs-lookup"><span data-stu-id="3dad8-110">Remarks</span></span>

<span data-ttu-id="3dad8-111">Visual Basic 支援從15.3 版開始的 `-refout` 交換器。</span><span class="sxs-lookup"><span data-stu-id="3dad8-111">Visual Basic supports the `-refout` switch starting with version 15.3.</span></span>

<span data-ttu-id="3dad8-112">參考元件是一種特殊類型的元件，其中只包含代表程式庫公用 API 介面所需的最小中繼資料量。</span><span class="sxs-lookup"><span data-stu-id="3dad8-112">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="3dad8-113">其中包括在建立工具中參考元件時，所有重要成員的宣告，但會排除所有成員的執行，以及對其 API 合約沒有明顯影響的私用成員宣告。</span><span class="sxs-lookup"><span data-stu-id="3dad8-113">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="3dad8-114">如需詳細資訊，請參閱 .NET 中的[參考元件](../../../standard/assembly/reference-assemblies.md)指南。</span><span class="sxs-lookup"><span data-stu-id="3dad8-114">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="3dad8-115">`-refout` 和 [`-refonly`](refonly-compiler-option.md) 選項互斥。</span><span class="sxs-lookup"><span data-stu-id="3dad8-115">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="3dad8-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="3dad8-116">See also</span></span>

- [<span data-ttu-id="3dad8-117">-refonly</span><span class="sxs-lookup"><span data-stu-id="3dad8-117">-refonly</span></span>](refonly-compiler-option.md)
- [<span data-ttu-id="3dad8-118">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="3dad8-118">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="3dad8-119">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="3dad8-119">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
