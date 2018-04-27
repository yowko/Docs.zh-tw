---
title: -具決定性
ms.date: 04/11/2018
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- deterministic compiler option [Visual Basic]
- -deterministic compiler option [Visual Basic]
- -deterministic compiler option [Visual Basic]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 273abf8811f04cd7f58599ce3421ca1f17c740d9
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="-deterministic"></a><span data-ttu-id="65923-102">-具決定性</span><span class="sxs-lookup"><span data-stu-id="65923-102">-deterministic</span></span>

<span data-ttu-id="65923-103">可讓編譯器產生其位元組的輸出編譯針對相同的輸入是相同的組件。</span><span class="sxs-lookup"><span data-stu-id="65923-103">Causes the compiler to produce an assembly whose byte-for-byte output is identical across compilations for identical inputs.</span></span> 

## <a name="syntax"></a><span data-ttu-id="65923-104">語法</span><span class="sxs-lookup"><span data-stu-id="65923-104">Syntax</span></span>

```
-deterministic
```

## <a name="remarks"></a><span data-ttu-id="65923-105">備註</span><span class="sxs-lookup"><span data-stu-id="65923-105">Remarks</span></span>

<span data-ttu-id="65923-106">根據預設，編譯器輸出一組給定的輸入是唯一的因為編譯器會加入時間戳記和 GUID 產生的隨機數字。</span><span class="sxs-lookup"><span data-stu-id="65923-106">By default, compiler output from a given set of inputs is unique, since the compiler adds a timestamp and a GUID that is generated from random numbers.</span></span> <span data-ttu-id="65923-107">您使用`-deterministic`選項來產生*具決定性的組件*，其二進位內容是相同跨編譯，只要輸入維持不變。</span><span class="sxs-lookup"><span data-stu-id="65923-107">You use the `-deterministic` option to produce a *deterministic assembly*, one whose binary content is identical across compilations as long as the input remains the same.</span></span>

<span data-ttu-id="65923-108">編譯器會考慮以決定性的下列輸入：</span><span class="sxs-lookup"><span data-stu-id="65923-108">The compiler considers the following inputs for the purpose of determinism:</span></span>

- <span data-ttu-id="65923-109">命令列參數的順序。</span><span class="sxs-lookup"><span data-stu-id="65923-109">The sequence of command-line parameters.</span></span>
- <span data-ttu-id="65923-110">編譯器的.rsp 回應檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="65923-110">The contents of the compiler's .rsp response file.</span></span>
- <span data-ttu-id="65923-111">精確的編譯器版本使用，以及其參考組件。</span><span class="sxs-lookup"><span data-stu-id="65923-111">The precise version of the compiler used, and its referenced assemblies.</span></span>
- <span data-ttu-id="65923-112">目前的目錄路徑。</span><span class="sxs-lookup"><span data-stu-id="65923-112">The current directory path.</span></span>
- <span data-ttu-id="65923-113">所有檔案的二進位內容明確地傳遞給編譯器以直接或間接方式包括：</span><span class="sxs-lookup"><span data-stu-id="65923-113">The binary contents of all files explicitly passed to the compiler either directly or indirectly, including:</span></span> 
    - <span data-ttu-id="65923-114">原始程式檔</span><span class="sxs-lookup"><span data-stu-id="65923-114">Source files</span></span>
    - <span data-ttu-id="65923-115">參考的組件</span><span class="sxs-lookup"><span data-stu-id="65923-115">Referenced assemblies</span></span>
    - <span data-ttu-id="65923-116">參考的模組</span><span class="sxs-lookup"><span data-stu-id="65923-116">Referenced modules</span></span>
    - <span data-ttu-id="65923-117">資源</span><span class="sxs-lookup"><span data-stu-id="65923-117">Resources</span></span>
    - <span data-ttu-id="65923-118">強式名稱金鑰檔</span><span class="sxs-lookup"><span data-stu-id="65923-118">The strong name key file</span></span>
    - <span data-ttu-id="65923-119">@ 回應檔</span><span class="sxs-lookup"><span data-stu-id="65923-119">@ response files</span></span>
    - <span data-ttu-id="65923-120">分析器</span><span class="sxs-lookup"><span data-stu-id="65923-120">Analyzers</span></span>
    - <span data-ttu-id="65923-121">Ruleset</span><span class="sxs-lookup"><span data-stu-id="65923-121">Rulesets</span></span>
    - <span data-ttu-id="65923-122">其他可能被分析器用的檔案</span><span class="sxs-lookup"><span data-stu-id="65923-122">Additional files that may be used by analyzers</span></span>
- <span data-ttu-id="65923-123">（適用於診斷和例外狀況訊息所產生的語言） 目前的文化特性。</span><span class="sxs-lookup"><span data-stu-id="65923-123">The current culture (for the language in which diagnostics and exception messages are produced).</span></span>
- <span data-ttu-id="65923-124">預設編碼方式 （或目前的字碼頁） 如果未指定編碼方式。</span><span class="sxs-lookup"><span data-stu-id="65923-124">The default encoding (or the current code page) if the encoding is not specified.</span></span>
- <span data-ttu-id="65923-125">是否存在、 不存在，並在編譯器搜尋路徑上檔案的內容 (例如，所指定`/lib`或`/recurse`)。</span><span class="sxs-lookup"><span data-stu-id="65923-125">The existence, non-existence, and contents of files on the compiler's search paths (specified, for example, by `/lib` or `/recurse`).</span></span>
- <span data-ttu-id="65923-126">CLR 平台編譯器會在其執行。</span><span class="sxs-lookup"><span data-stu-id="65923-126">The CLR platform on which the compiler is run.</span></span>
- <span data-ttu-id="65923-127">值`%LIBPATH%`，而影響分析器相依性的載入。</span><span class="sxs-lookup"><span data-stu-id="65923-127">The value of `%LIBPATH%`, which can affect analyzer dependency loading.</span></span>

<span data-ttu-id="65923-128">來源可公開可用時，具決定性的編譯可以用於建立是否來自信任來源編譯二進位檔。</span><span class="sxs-lookup"><span data-stu-id="65923-128">When sources are publicly available, deterministic compilation can be used for establishing whether a binary is compiled from a trusted source.</span></span> <span data-ttu-id="65923-129">它也可用於連續的建置系統，以判斷是否需要執行建置步驟會取決於二進位檔的變更。</span><span class="sxs-lookup"><span data-stu-id="65923-129">It can also be useful in a continuous build system for determining whether build steps that are dependent on changes to a binary need to be executed.</span></span> 

## <a name="see-also"></a><span data-ttu-id="65923-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="65923-130">See Also</span></span>
[<span data-ttu-id="65923-131">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="65923-131">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
[<span data-ttu-id="65923-132">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="65923-132">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
