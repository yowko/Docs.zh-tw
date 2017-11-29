---
title: "複製並更新記錄運算式 （F #）"
description: "了解如何撰寫 '複製並更新記錄運算式' 複製現有的記錄，更新指定的欄位，並傳回更新的記錄。"
keywords: "Visual F#, F#, 函式程式設計"
author: ChrSteinert
ms.author: phcart
ms.date: 06/04/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: b5fc4ef0-64eb-4272-96a7-bb4dffbb634a
ms.openlocfilehash: 2eb51842b678780a1d6da96e237ebb92d1ea5cec
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="copy-and-update-record-expressions"></a><span data-ttu-id="740fb-104">複製和更新記錄運算式</span><span class="sxs-lookup"><span data-stu-id="740fb-104">Copy and Update Record Expressions</span></span>

<span data-ttu-id="740fb-105">A*複製並更新記錄運算式*是複製現有的記錄，更新指定的欄位，並傳回更新的資料錄的運算式。</span><span class="sxs-lookup"><span data-stu-id="740fb-105">A *copy and update record expression* is an expression that copies an existing record, updates specified fields, and returns the updated record.</span></span>


## <a name="syntax"></a><span data-ttu-id="740fb-106">語法</span><span class="sxs-lookup"><span data-stu-id="740fb-106">Syntax</span></span>

```fsharp
{ record-name with
    updated-member-definitions }
```

## <a name="remarks"></a><span data-ttu-id="740fb-107">備註</span><span class="sxs-lookup"><span data-stu-id="740fb-107">Remarks</span></span>
<span data-ttu-id="740fb-108">記錄是根據預設，不變的使得沒有可能不會更新現有的記錄。</span><span class="sxs-lookup"><span data-stu-id="740fb-108">Records are immutable by default, so that there is no update to an existing record possible.</span></span> <span data-ttu-id="740fb-109">若要建立更新的記錄之記錄的所有欄位必須指定一次。</span><span class="sxs-lookup"><span data-stu-id="740fb-109">To create an updated record all the fields of a record would have to be specified again.</span></span> <span data-ttu-id="740fb-110">為了簡化這項工作*複製並更新記錄運算式*可用。</span><span class="sxs-lookup"><span data-stu-id="740fb-110">To simplify this task a *copy and update record expression* can be used.</span></span> <span data-ttu-id="740fb-111">這個運算式會採用現有的記錄，使用指定的欄位，從運算式和運算式所指定的遺漏欄位會建立一個新的相同型別。</span><span class="sxs-lookup"><span data-stu-id="740fb-111">This expression takes an existing record, creates a new one of the same type by using specified fields from the expression and the missing field specified by the expression.</span></span>
<span data-ttu-id="740fb-112">當您必須複製現有的記錄，並可能變更的某些欄位值，這非常有用。</span><span class="sxs-lookup"><span data-stu-id="740fb-112">This can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span>

<span data-ttu-id="740fb-113">取得執行個體的新建立的記錄。</span><span class="sxs-lookup"><span data-stu-id="740fb-113">Take for instance a newly created record.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="740fb-114">如果您要更新只能在您可以使用該記錄的欄位上*複製並更新記錄運算式*像下面這樣：</span><span class="sxs-lookup"><span data-stu-id="740fb-114">If you were to update only on field of that record you could use the *copy and update record expression* like the following:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a><span data-ttu-id="740fb-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="740fb-115">See Also</span></span>
[<span data-ttu-id="740fb-116">記錄</span><span class="sxs-lookup"><span data-stu-id="740fb-116">Records</span></span>](records.md)

[<span data-ttu-id="740fb-117">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="740fb-117">F# Language Reference</span></span>](index.md)
