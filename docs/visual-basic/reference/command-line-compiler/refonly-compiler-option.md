---
title: -refonly (Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- -refonly
helpviewer_keywords:
- /refonly compiler option [Visual Basic]
- -refonly compiler option [Visual Basic]
- refonly compiler option [Visual Basic]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e8f6c15084ac9b1a07aef8a0311edfcc4a93337c
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2018
ms.locfileid: "42932659"
---
# <a name="-refonly-visual-basic"></a><span data-ttu-id="11225-102">-refonly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="11225-102">-refonly (Visual Basic)</span></span>

<span data-ttu-id="11225-103">**-Refonly**選項表示編譯的主要輸出應為參考組件，而不是實作組件。</span><span class="sxs-lookup"><span data-stu-id="11225-103">The **-refonly** option indicates that the primary output of the compilation should be a reference assembly instead of an implementation assembly.</span></span> <span data-ttu-id="11225-104">`-refonly` 參數以無訊息模式停用輸出 PDB，因為無法執行參考組件。</span><span class="sxs-lookup"><span data-stu-id="11225-104">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span>

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a><span data-ttu-id="11225-105">語法</span><span class="sxs-lookup"><span data-stu-id="11225-105">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="11225-106">備註</span><span class="sxs-lookup"><span data-stu-id="11225-106">Remarks</span></span>

<span data-ttu-id="11225-107">Visual Basic 支援`-refout`切換 15.3 版開始。</span><span class="sxs-lookup"><span data-stu-id="11225-107">Visual Basic supports the `-refout` switch starting with version 15.3.</span></span>

<span data-ttu-id="11225-108">參考組件是僅中繼資料的組件包含中繼資料，但沒有實作程式碼。</span><span class="sxs-lookup"><span data-stu-id="11225-108">Reference assemblies are metadata-only assemblies that contain metadata but no implementation code.</span></span> <span data-ttu-id="11225-109">它們包含匿名型別以外的所有項目的型別和成員資訊。</span><span class="sxs-lookup"><span data-stu-id="11225-109">They include type and member information for everything except anonymous types.</span></span> <span data-ttu-id="11225-110">使用 `throw null` 主體的原因 (相對於沒有主體)，是這樣 PEVerify 便可執行和傳遞 (因此驗證中繼資料的完整性)。</span><span class="sxs-lookup"><span data-stu-id="11225-110">The reason for using `throw null` bodies (as opposed to no bodies) is so that PEVerify could run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="11225-111">參考組件包含組件層級[ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute)屬性。</span><span class="sxs-lookup"><span data-stu-id="11225-111">Reference assemblies include an assembly-level [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) attribute.</span></span> <span data-ttu-id="11225-112">這個屬性可在來源中指定 (然後編譯器就不需要合成它)。</span><span class="sxs-lookup"><span data-stu-id="11225-112">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="11225-113">因為此屬性中，執行階段會拒絕載入參考組件的執行 （但仍可載入僅限反映的內容中）。</span><span class="sxs-lookup"><span data-stu-id="11225-113">Because of this attribute, runtimes will refuse to load reference assemblies for execution (but they can still be loaded in a reflection-only context).</span></span> <span data-ttu-id="11225-114">在組件反映的工具需要確保它們載入參考組件為僅限反映的;否則，執行階段會擲回<xref:System.BadImageFormatException>。</span><span class="sxs-lookup"><span data-stu-id="11225-114">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only; otherwise, the runtime throws a <xref:System.BadImageFormatException>.</span></span>

<span data-ttu-id="11225-115">`-refonly` 和 [`-refout`](refout-compiler-option.md) 選項互斥。</span><span class="sxs-lookup"><span data-stu-id="11225-115">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="11225-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11225-116">See also</span></span>
<span data-ttu-id="11225-117">[-refout](refout-compiler-option.md) </span><span class="sxs-lookup"><span data-stu-id="11225-117">[-refout](refout-compiler-option.md) </span></span>  
[<span data-ttu-id="11225-118">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="11225-118">Visual Basic Command-Line Compiler</span></span>](index.md)  
[<span data-ttu-id="11225-119">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="11225-119">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)   
