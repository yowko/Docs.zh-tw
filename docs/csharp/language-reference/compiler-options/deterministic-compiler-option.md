---
description: -deterministic (C# 編譯器選項)
title: -deterministic (C# 編譯器選項)
ms.date: 04/12/2018
f1_keywords:
- /deterministic
helpviewer_keywords:
- -deterministic compiler option [C#]
- deterministic compiler option [C#]
- /deterministic compiler option [C#]
ms.openlocfilehash: d64f4d4b0d4e9b5ed2cc1ee40662dc669fc6660d
ms.sourcegitcommit: 4f5f1855849cb02c3b610c7006ac21d7429f3348
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/15/2021
ms.locfileid: "98235322"
---
# <a name="-deterministic"></a><span data-ttu-id="cccf8-103">-deterministic</span><span class="sxs-lookup"><span data-stu-id="cccf8-103">-deterministic</span></span>

<span data-ttu-id="cccf8-104">可讓編譯器產生相同輸入之編譯間的逐一位元組輸出相同的組件。</span><span class="sxs-lookup"><span data-stu-id="cccf8-104">Causes the compiler to produce an assembly whose byte-for-byte output is identical across compilations for identical inputs.</span></span>

## <a name="syntax"></a><span data-ttu-id="cccf8-105">語法</span><span class="sxs-lookup"><span data-stu-id="cccf8-105">Syntax</span></span>

```console
-deterministic
```

## <a name="remarks"></a><span data-ttu-id="cccf8-106">備註</span><span class="sxs-lookup"><span data-stu-id="cccf8-106">Remarks</span></span>

<span data-ttu-id="cccf8-107">根據預設，指定輸入集合中的編譯器輸出是唯一的，因為編譯器會新增從亂數字產生的時間戳記和 MVID。</span><span class="sxs-lookup"><span data-stu-id="cccf8-107">By default, compiler output from a given set of inputs is unique, since the compiler adds a timestamp and a MVID that is generated from random numbers.</span></span> <span data-ttu-id="cccf8-108">您可以使用 `-deterministic` 選項來產生「確定性組件」，這是只要輸入維持不變，其二進位內容在編譯之間就相同的組件。</span><span class="sxs-lookup"><span data-stu-id="cccf8-108">You use the `-deterministic` option to produce a *deterministic assembly*, one whose binary content is identical across compilations as long as the input remains the same.</span></span> <span data-ttu-id="cccf8-109">在這種組建中，時間戳記和 MVID 欄位將會取代為從所有編譯輸入的雜湊衍生的值。</span><span class="sxs-lookup"><span data-stu-id="cccf8-109">In such a build, the timestamp and MVID fields will be replaced with values derived from a hash of all the compilation inputs.</span></span>

<span data-ttu-id="cccf8-110">編譯器會基於確定性而考慮下列輸入：</span><span class="sxs-lookup"><span data-stu-id="cccf8-110">The compiler considers the following inputs for the purpose of determinism:</span></span>

- <span data-ttu-id="cccf8-111">命令列參數序列。</span><span class="sxs-lookup"><span data-stu-id="cccf8-111">The sequence of command-line parameters.</span></span>
- <span data-ttu-id="cccf8-112">編譯器之 .rsp 回應檔的內容。</span><span class="sxs-lookup"><span data-stu-id="cccf8-112">The contents of the compiler's .rsp response file.</span></span>
- <span data-ttu-id="cccf8-113">使用的編譯器精確版本和其參考的組件。</span><span class="sxs-lookup"><span data-stu-id="cccf8-113">The precise version of the compiler used, and its referenced assemblies.</span></span>
- <span data-ttu-id="cccf8-114">目前的目錄路徑。</span><span class="sxs-lookup"><span data-stu-id="cccf8-114">The current directory path.</span></span>
- <span data-ttu-id="cccf8-115">以直接或間接方式明確地傳遞給編譯器之所有檔案的二進位內容，包含：</span><span class="sxs-lookup"><span data-stu-id="cccf8-115">The binary contents of all files explicitly passed to the compiler either directly or indirectly, including:</span></span>
  - <span data-ttu-id="cccf8-116">原始程式檔</span><span class="sxs-lookup"><span data-stu-id="cccf8-116">Source files</span></span>
  - <span data-ttu-id="cccf8-117">參考的組件</span><span class="sxs-lookup"><span data-stu-id="cccf8-117">Referenced assemblies</span></span>
  - <span data-ttu-id="cccf8-118">參考的模組</span><span class="sxs-lookup"><span data-stu-id="cccf8-118">Referenced modules</span></span>
  - <span data-ttu-id="cccf8-119">資源</span><span class="sxs-lookup"><span data-stu-id="cccf8-119">Resources</span></span>
  - <span data-ttu-id="cccf8-120">強式名稱金鑰檔</span><span class="sxs-lookup"><span data-stu-id="cccf8-120">The strong name key file</span></span>
  - <span data-ttu-id="cccf8-121">@ 回應檔</span><span class="sxs-lookup"><span data-stu-id="cccf8-121">@ response files</span></span>
  - <span data-ttu-id="cccf8-122">分析器</span><span class="sxs-lookup"><span data-stu-id="cccf8-122">Analyzers</span></span>
  - <span data-ttu-id="cccf8-123">規則集</span><span class="sxs-lookup"><span data-stu-id="cccf8-123">Rulesets</span></span>
  - <span data-ttu-id="cccf8-124">分析器可能使用的其他檔案</span><span class="sxs-lookup"><span data-stu-id="cccf8-124">Additional files that may be used by analyzers</span></span>
- <span data-ttu-id="cccf8-125">目前文化特性 (Culture) (適用於用來產生診斷和例外狀況訊息的語言)。</span><span class="sxs-lookup"><span data-stu-id="cccf8-125">The current culture (for the language in which diagnostics and exception messages are produced).</span></span>
- <span data-ttu-id="cccf8-126">如果未指定編碼，則為預設編碼 (或目前字碼頁)。</span><span class="sxs-lookup"><span data-stu-id="cccf8-126">The default encoding (or the current code page) if the encoding is not specified.</span></span>
- <span data-ttu-id="cccf8-127">存在、不存在，以及編譯器搜尋路徑 (例如，透過 `-lib` 或 `-recurse` 指定) 上檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="cccf8-127">The existence, non-existence, and contents of files on the compiler's search paths (specified, for example, by `-lib` or `-recurse`).</span></span>
- <span data-ttu-id="cccf8-128">在其上執行編譯器的 CLR 平台。</span><span class="sxs-lookup"><span data-stu-id="cccf8-128">The CLR platform on which the compiler is run.</span></span>
- <span data-ttu-id="cccf8-129">`%LIBPATH%` 的值，可能會影響分析器相依性載入。</span><span class="sxs-lookup"><span data-stu-id="cccf8-129">The value of `%LIBPATH%`, which can affect analyzer dependency loading.</span></span>

<span data-ttu-id="cccf8-130">來源公開可用時，確定性編譯可以用於建立是否從信任的來源編譯二進位檔。</span><span class="sxs-lookup"><span data-stu-id="cccf8-130">When sources are publicly available, deterministic compilation can be used for establishing whether a binary is compiled from a trusted source.</span></span> <span data-ttu-id="cccf8-131">它也可以用於持續建置系統，確定是否需要執行與二進位檔變更相依的建置步驟。</span><span class="sxs-lookup"><span data-stu-id="cccf8-131">It can also be useful in a continuous build system for determining whether build steps that are dependent on changes to a binary need to be executed.</span></span>

## <a name="see-also"></a><span data-ttu-id="cccf8-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cccf8-132">See also</span></span>

- [<span data-ttu-id="cccf8-133">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="cccf8-133">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="cccf8-134">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="cccf8-134">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
