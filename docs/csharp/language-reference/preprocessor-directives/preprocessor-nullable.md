---
description: '#nullable-c # 參考'
title: '#nullable-c # 參考'
ms.date: 11/18/2020
f1_keywords:
- '#nullable'
helpviewer_keywords:
- '#nullable directive [C#]'
ms.openlocfilehash: 4c114a09f29769fcc824bcdabdc1d523e33f199d
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2020
ms.locfileid: "95099458"
---
# <a name="nullable-c-reference"></a><span data-ttu-id="f8d10-103">#nullable (c # 參考) </span><span class="sxs-lookup"><span data-stu-id="f8d10-103">#nullable (C# Reference)</span></span>

<span data-ttu-id="f8d10-104">預處理器指示詞會 `#nullable` 設定 *可為 null 注釋內容* 和 *可為 null 的警告內容*。</span><span class="sxs-lookup"><span data-stu-id="f8d10-104">The `#nullable` preprocessor directive sets the *nullable annotation context* and *nullable warning context*.</span></span> <span data-ttu-id="f8d10-105">這個指示詞會控制可為 null 的注釋是否有效果，以及是否提供可 null 性警告。</span><span class="sxs-lookup"><span data-stu-id="f8d10-105">This directive controls whether nullable annotations have effect, and whether nullability warnings are given.</span></span> <span data-ttu-id="f8d10-106">每個內容都已 *停用* 或 *啟用*。</span><span class="sxs-lookup"><span data-stu-id="f8d10-106">Each context is either *disabled* or *enabled*.</span></span>

<span data-ttu-id="f8d10-107">這兩個內容可以在專案層級指定， (在 c # 原始程式碼) 之外。</span><span class="sxs-lookup"><span data-stu-id="f8d10-107">Both contexts can be specified at the project level (outside of C# source code).</span></span> <span data-ttu-id="f8d10-108">指示詞 `#nullable` 會控制注釋和警告內容，並優先于專案層級的設定。</span><span class="sxs-lookup"><span data-stu-id="f8d10-108">The `#nullable` directive controls the annotation and warning contexts and takes precedence over the project-level settings.</span></span> <span data-ttu-id="f8d10-109">指示詞會設定) 它控制的 (內容，直到另一個指示詞覆寫它，或直到原始程式檔結束為止。</span><span class="sxs-lookup"><span data-stu-id="f8d10-109">A directive sets the context(s) it controls until another directive overrides it, or until the end of the source file.</span></span>

<span data-ttu-id="f8d10-110">指示詞的效果如下所示：</span><span class="sxs-lookup"><span data-stu-id="f8d10-110">The effect of the directives is as follows:</span></span>

- <span data-ttu-id="f8d10-111">`#nullable disable`：將可為 null 的注釋和警告內容設定為 *停用*。</span><span class="sxs-lookup"><span data-stu-id="f8d10-111">`#nullable disable`: Sets the nullable annotation and warning contexts to *disabled*.</span></span>
- <span data-ttu-id="f8d10-112">`#nullable enable`：將可為 null 的注釋和警告內容設定為 *已啟用*。</span><span class="sxs-lookup"><span data-stu-id="f8d10-112">`#nullable enable`: Sets the nullable annotation and warning contexts to *enabled*.</span></span>
- <span data-ttu-id="f8d10-113">`#nullable restore`：將可為 null 的注釋和警告內容還原至專案設定。</span><span class="sxs-lookup"><span data-stu-id="f8d10-113">`#nullable restore`: Restores the nullable annotation and warning contexts to project settings.</span></span>
- <span data-ttu-id="f8d10-114">`#nullable disable annotations`：將可為 null 注釋內容設定為 *停用*。</span><span class="sxs-lookup"><span data-stu-id="f8d10-114">`#nullable disable annotations`: Sets the nullable annotation context to *disabled*.</span></span>
- <span data-ttu-id="f8d10-115">`#nullable enable annotations`：將可為 null 注釋內容設定為 *已啟用*。</span><span class="sxs-lookup"><span data-stu-id="f8d10-115">`#nullable enable annotations`: Sets the nullable annotation context to *enabled*.</span></span>
- <span data-ttu-id="f8d10-116">`#nullable restore annotations`：將可為 null 注釋內容還原至專案設定。</span><span class="sxs-lookup"><span data-stu-id="f8d10-116">`#nullable restore annotations`: Restores the nullable annotation context to project settings.</span></span>
- <span data-ttu-id="f8d10-117">`#nullable disable warnings`：將可為 null 的警告內容設定為 *停用*。</span><span class="sxs-lookup"><span data-stu-id="f8d10-117">`#nullable disable warnings`: Sets the nullable warning context to *disabled*.</span></span>
- <span data-ttu-id="f8d10-118">`#nullable enable warnings`：將可為 null 的警告內容設定為 *已啟用*。</span><span class="sxs-lookup"><span data-stu-id="f8d10-118">`#nullable enable warnings`: Sets the nullable warning context to *enabled*.</span></span>
- <span data-ttu-id="f8d10-119">`#nullable restore warnings`：將可為 null 警告內容還原至專案設定。</span><span class="sxs-lookup"><span data-stu-id="f8d10-119">`#nullable restore warnings`: Restores the nullable warning context to project settings.</span></span>

## <a name="see-also"></a><span data-ttu-id="f8d10-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f8d10-120">See also</span></span>

- [<span data-ttu-id="f8d10-121">C # 參考</span><span class="sxs-lookup"><span data-stu-id="f8d10-121">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f8d10-122">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="f8d10-122">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f8d10-123">C # 預處理器指示詞</span><span class="sxs-lookup"><span data-stu-id="f8d10-123">C# Preprocessor Directives</span></span>](./index.md)
