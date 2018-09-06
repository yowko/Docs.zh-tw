---
title: '複製和更新記錄運算式 （F #）'
description: 了解如何撰寫 '複製和更新記錄運算式'，複製現有的記錄，更新指定的欄位，並傳回更新的記錄。
author: ChrSteinert
ms.date: 06/04/2016
ms.openlocfilehash: d2b089e8a7fc5c7ee26139003e23d2eaa8a3174e
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43745901"
---
# <a name="copy-and-update-record-expressions"></a><span data-ttu-id="cbff8-103">複製和更新記錄運算式</span><span class="sxs-lookup"><span data-stu-id="cbff8-103">Copy and Update Record Expressions</span></span>

<span data-ttu-id="cbff8-104">A*複製並更新記錄運算式*是複製現有的記錄、 更新指定的欄位，並傳回更新的資料錄的運算式。</span><span class="sxs-lookup"><span data-stu-id="cbff8-104">A *copy and update record expression* is an expression that copies an existing record, updates specified fields, and returns the updated record.</span></span>

## <a name="syntax"></a><span data-ttu-id="cbff8-105">語法</span><span class="sxs-lookup"><span data-stu-id="cbff8-105">Syntax</span></span>

```fsharp
{ record-name with
    updated-member-definitions }
```

## <a name="remarks"></a><span data-ttu-id="cbff8-106">備註</span><span class="sxs-lookup"><span data-stu-id="cbff8-106">Remarks</span></span>

<span data-ttu-id="cbff8-107">使其沒有可能不會更新現有的記錄，記錄會依預設，不可變。</span><span class="sxs-lookup"><span data-stu-id="cbff8-107">Records are immutable by default, so that there is no update to an existing record possible.</span></span> <span data-ttu-id="cbff8-108">若要建立已更新的資料錄的一筆記錄的所有欄位必須指定一次。</span><span class="sxs-lookup"><span data-stu-id="cbff8-108">To create an updated record all the fields of a record would have to be specified again.</span></span> <span data-ttu-id="cbff8-109">若要簡化這項工作*複製並更新記錄運算式*可用。</span><span class="sxs-lookup"><span data-stu-id="cbff8-109">To simplify this task a *copy and update record expression* can be used.</span></span> <span data-ttu-id="cbff8-110">這個運算式會採用現有的記錄，使用運算式指定的欄位和運算式所指定的遺漏欄位會建立一個新的同一個型別。</span><span class="sxs-lookup"><span data-stu-id="cbff8-110">This expression takes an existing record, creates a new one of the same type by using specified fields from the expression and the missing field specified by the expression.</span></span>
<span data-ttu-id="cbff8-111">當您必須複製現有的記錄，並可能變更的某些欄位值時，這非常有用。</span><span class="sxs-lookup"><span data-stu-id="cbff8-111">This can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span>

<span data-ttu-id="cbff8-112">需要執行個體的新建立的記錄。</span><span class="sxs-lookup"><span data-stu-id="cbff8-112">Take for instance a newly created record.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="cbff8-113">如果您只在您可以使用該記錄的欄位更新*複製並更新記錄運算式*如下所示：</span><span class="sxs-lookup"><span data-stu-id="cbff8-113">If you were to update only on field of that record you could use the *copy and update record expression* like the following:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a><span data-ttu-id="cbff8-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cbff8-114">See also</span></span>

- [<span data-ttu-id="cbff8-115">記錄</span><span class="sxs-lookup"><span data-stu-id="cbff8-115">Records</span></span>](records.md)
- [<span data-ttu-id="cbff8-116">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="cbff8-116">F# Language Reference</span></span>](index.md)
