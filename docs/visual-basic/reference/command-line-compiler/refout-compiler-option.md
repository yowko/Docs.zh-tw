---
title: -refout (Visual Basic)
ms.date: 03/16/2018
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [Visual Basic]
- /refout compiler option [Visual Basic]
- -refout compiler option [Visual Basic]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d6075b92efd1eec9797fca248e97a325bd5df4bb
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
---
# <a name="-refout-visual-basic"></a><span data-ttu-id="b12d3-102">-refout (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b12d3-102">-refout (Visual Basic)</span></span>

<span data-ttu-id="b12d3-103">**-refout** 選項指定參考組件應該輸出的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="b12d3-103">The **-refout** option specifies a file path where the reference assembly should be output.</span></span>

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a><span data-ttu-id="b12d3-104">語法</span><span class="sxs-lookup"><span data-stu-id="b12d3-104">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="b12d3-105">引數</span><span class="sxs-lookup"><span data-stu-id="b12d3-105">Arguments</span></span>

 <span data-ttu-id="b12d3-106">`filepath` 路徑和檔案名稱的參考組件。</span><span class="sxs-lookup"><span data-stu-id="b12d3-106">`filepath` The path and filename of the reference assembly.</span></span> <span data-ttu-id="b12d3-107">它通常應該在主要組件的子資料夾。</span><span class="sxs-lookup"><span data-stu-id="b12d3-107">It should generally be in a sub-folder of the primary assembly.</span></span> <span data-ttu-id="b12d3-108">建議慣例 (由 MSBuild 使用) 是將參考組件放在相對於主要組件的 "ref/" 子資料夾中。</span><span class="sxs-lookup"><span data-stu-id="b12d3-108">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span> <span data-ttu-id="b12d3-109">中的所有資料夾`filepath`必須存在，編譯器不會建立它們。</span><span class="sxs-lookup"><span data-stu-id="b12d3-109">All folders in `filepath` must exist; the compiler does not create them.</span></span> 

## <a name="remarks"></a><span data-ttu-id="b12d3-110">備註</span><span class="sxs-lookup"><span data-stu-id="b12d3-110">Remarks</span></span>

<span data-ttu-id="b12d3-111">Visual Basic 支援`-refout`切換版 15.3 開頭。</span><span class="sxs-lookup"><span data-stu-id="b12d3-111">Visual Basic supports the `-refout` switch starting with version 15.3.</span></span>

<span data-ttu-id="b12d3-112">參考組件是僅中繼資料的組件包含中繼資料但沒有實作程式碼。</span><span class="sxs-lookup"><span data-stu-id="b12d3-112">Reference assemblies are metadata-only assemblies that contain metadata but no implementation code.</span></span> <span data-ttu-id="b12d3-113">它們包含匿名型別以外的所有項目型別和成員資訊。</span><span class="sxs-lookup"><span data-stu-id="b12d3-113">They include type and member information for everything except anonymous types.</span></span> <span data-ttu-id="b12d3-114">其方法主體就會取代單一`throw null`陳述式。</span><span class="sxs-lookup"><span data-stu-id="b12d3-114">Their method bodies are replaced with a single `throw null` statement.</span></span> <span data-ttu-id="b12d3-115">使用的原因`throw null`（而不是沒有內文） 的方法主體，以便 PEVerify 可以執行和傳遞 （因此驗證中繼資料的完整性）。</span><span class="sxs-lookup"><span data-stu-id="b12d3-115">The reason for using `throw null` method bodies (as opposed to no bodies) is so that PEVerify can run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="b12d3-116">參考組件包含組件層級[ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute)屬性。</span><span class="sxs-lookup"><span data-stu-id="b12d3-116">Reference assemblies include an assembly-level [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) attribute.</span></span> <span data-ttu-id="b12d3-117">這個屬性可在來源中指定 (然後編譯器就不需要合成它)。</span><span class="sxs-lookup"><span data-stu-id="b12d3-117">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="b12d3-118">這個屬性，因為執行階段拒絕載入參考組件的執行 （但仍可以載入僅限反映的內容中）。</span><span class="sxs-lookup"><span data-stu-id="b12d3-118">Because of this attribute, runtimes refuse to load reference assemblies for execution (but they can still be loaded in a reflection-only context).</span></span> <span data-ttu-id="b12d3-119">反映的組件的工具需要以確保它們載入參考組件做為僅限反映的;否則，執行階段會擲回<xref:System.BadImageFormatException>。</span><span class="sxs-lookup"><span data-stu-id="b12d3-119">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only; otherwise, the runtime throws a <xref:System.BadImageFormatException>.</span></span>

<span data-ttu-id="b12d3-120">`-refout` 和 [`-refonly`](refonly-compiler-option.md) 選項互斥。</span><span class="sxs-lookup"><span data-stu-id="b12d3-120">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="b12d3-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b12d3-121">See Also</span></span>
<span data-ttu-id="b12d3-122">[-refonly](refonly-compiler-option.md) </span><span class="sxs-lookup"><span data-stu-id="b12d3-122">[-refonly](refonly-compiler-option.md) </span></span>  
[<span data-ttu-id="b12d3-123">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="b12d3-123">Visual Basic Command-Line Compiler</span></span>](index.md)  
[<span data-ttu-id="b12d3-124">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="b12d3-124">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)  

