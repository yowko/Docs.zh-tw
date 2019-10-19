---
title: -refout （Visual Basic）
ms.date: 03/16/2018
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [Visual Basic]
- /refout compiler option [Visual Basic]
- -refout compiler option [Visual Basic]
ms.openlocfilehash: c11d83ff37da41faa3dc6b66a87e2c52c5f6c7ac
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582865"
---
# <a name="-refout-visual-basic"></a><span data-ttu-id="b02a1-102">-refout （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="b02a1-102">-refout (Visual Basic)</span></span>

<span data-ttu-id="b02a1-103">**-refout** 選項指定參考組件應該輸出的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="b02a1-103">The **-refout** option specifies a file path where the reference assembly should be output.</span></span>

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a><span data-ttu-id="b02a1-104">語法</span><span class="sxs-lookup"><span data-stu-id="b02a1-104">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="b02a1-105">引數</span><span class="sxs-lookup"><span data-stu-id="b02a1-105">Arguments</span></span>

`filepath`  
<span data-ttu-id="b02a1-106">參考元件的路徑和檔案名。</span><span class="sxs-lookup"><span data-stu-id="b02a1-106">The path and filename of the reference assembly.</span></span> <span data-ttu-id="b02a1-107">它通常應該位於主要元件的子資料夾中。</span><span class="sxs-lookup"><span data-stu-id="b02a1-107">It should generally be in a sub-folder of the primary assembly.</span></span> <span data-ttu-id="b02a1-108">建議慣例 (由 MSBuild 使用) 是將參考組件放在相對於主要組件的 "ref/" 子資料夾中。</span><span class="sxs-lookup"><span data-stu-id="b02a1-108">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span> <span data-ttu-id="b02a1-109">@No__t_0 中的所有資料夾都必須存在;編譯器不會建立它們。</span><span class="sxs-lookup"><span data-stu-id="b02a1-109">All folders in `filepath` must exist; the compiler does not create them.</span></span>

## <a name="remarks"></a><span data-ttu-id="b02a1-110">備註</span><span class="sxs-lookup"><span data-stu-id="b02a1-110">Remarks</span></span>

<span data-ttu-id="b02a1-111">Visual Basic 支援從15.3 版開始的 `-refout` 交換器。</span><span class="sxs-lookup"><span data-stu-id="b02a1-111">Visual Basic supports the `-refout` switch starting with version 15.3.</span></span>

<span data-ttu-id="b02a1-112">參考元件是僅限中繼資料的元件，其中包含中繼資料，但沒有任何實作為程式碼。</span><span class="sxs-lookup"><span data-stu-id="b02a1-112">Reference assemblies are metadata-only assemblies that contain metadata but no implementation code.</span></span> <span data-ttu-id="b02a1-113">其中包括匿名型別以外所有專案的類型和成員資訊。</span><span class="sxs-lookup"><span data-stu-id="b02a1-113">They include type and member information for everything except anonymous types.</span></span> <span data-ttu-id="b02a1-114">其方法主體會取代為單一 `throw null` 語句。</span><span class="sxs-lookup"><span data-stu-id="b02a1-114">Their method bodies are replaced with a single `throw null` statement.</span></span> <span data-ttu-id="b02a1-115">使用 `throw null` 方法主體（而不是任何主體）的原因，是為了讓 PEVerify 能夠執行和傳遞（藉此驗證中繼資料的完整性）。</span><span class="sxs-lookup"><span data-stu-id="b02a1-115">The reason for using `throw null` method bodies (as opposed to no bodies) is so that PEVerify can run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="b02a1-116">參考元件包含元件層級的[ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute)屬性。</span><span class="sxs-lookup"><span data-stu-id="b02a1-116">Reference assemblies include an assembly-level [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) attribute.</span></span> <span data-ttu-id="b02a1-117">這個屬性可在來源中指定 (然後編譯器就不需要合成它)。</span><span class="sxs-lookup"><span data-stu-id="b02a1-117">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="b02a1-118">由於這個屬性，執行時間會拒絕載入參考元件以執行（但仍可在僅限反映的內容中載入）。</span><span class="sxs-lookup"><span data-stu-id="b02a1-118">Because of this attribute, runtimes refuse to load reference assemblies for execution (but they can still be loaded in a reflection-only context).</span></span> <span data-ttu-id="b02a1-119">在元件上反映的工具必須確保它們將參考元件載入為僅限反映;否則，執行時間會擲回 <xref:System.BadImageFormatException>。</span><span class="sxs-lookup"><span data-stu-id="b02a1-119">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only; otherwise, the runtime throws a <xref:System.BadImageFormatException>.</span></span>

<span data-ttu-id="b02a1-120">`-refout` 和 [`-refonly`](refonly-compiler-option.md) 選項互斥。</span><span class="sxs-lookup"><span data-stu-id="b02a1-120">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="b02a1-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="b02a1-121">See also</span></span>

- [<span data-ttu-id="b02a1-122">-refonly</span><span class="sxs-lookup"><span data-stu-id="b02a1-122">-refonly</span></span>](refonly-compiler-option.md)
- [<span data-ttu-id="b02a1-123">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="b02a1-123">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="b02a1-124">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="b02a1-124">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
