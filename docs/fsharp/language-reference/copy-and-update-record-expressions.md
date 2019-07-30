---
title: 複製和更新記錄運算式
description: 瞭解如何撰寫「複製和更新運算式」來複製現有的記錄或匿名記錄、更新指定的欄位, 並傳回更新的記錄或匿名記錄。
author: ChrSteinert
ms.date: 06/12/2019
ms.openlocfilehash: dfb20a6ff8282ae5988772cc0f0841db23aad942
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630386"
---
# <a name="copy-and-update-record-expressions"></a><span data-ttu-id="4cbfd-103">複製和更新記錄運算式</span><span class="sxs-lookup"><span data-stu-id="4cbfd-103">Copy and Update Record Expressions</span></span>

<span data-ttu-id="4cbfd-104">*複製和更新記錄運算式*是一個運算式, 可複製現有的記錄、更新指定的欄位, 並傳回更新的記錄。</span><span class="sxs-lookup"><span data-stu-id="4cbfd-104">A *copy and update record expression* is an expression that copies an existing record, updates specified fields, and returns the updated record.</span></span>

## <a name="syntax"></a><span data-ttu-id="4cbfd-105">語法</span><span class="sxs-lookup"><span data-stu-id="4cbfd-105">Syntax</span></span>

```fsharp
{ record-name with
    updated-labels }

{| anonymous-record-name with
    updated-labels |}
```

## <a name="remarks"></a><span data-ttu-id="4cbfd-106">備註</span><span class="sxs-lookup"><span data-stu-id="4cbfd-106">Remarks</span></span>

<span data-ttu-id="4cbfd-107">記錄和匿名記錄預設為不變, 因此不會有現有記錄的更新。</span><span class="sxs-lookup"><span data-stu-id="4cbfd-107">Records and anonymous records are immutable by default, so that there is no update to an existing record possible.</span></span> <span data-ttu-id="4cbfd-108">若要建立已更新的記錄, 必須再次指定記錄的所有欄位。</span><span class="sxs-lookup"><span data-stu-id="4cbfd-108">To create an updated record all the fields of a record would have to be specified again.</span></span> <span data-ttu-id="4cbfd-109">為了簡化這項工作, 可以使用*複製和更新運算式*。</span><span class="sxs-lookup"><span data-stu-id="4cbfd-109">To simplify this task a *copy and update expression* can be used.</span></span> <span data-ttu-id="4cbfd-110">這個運算式會採用現有的記錄, 使用運算式中指定的欄位和運算式所指定的遺漏欄位, 建立相同類型的新。</span><span class="sxs-lookup"><span data-stu-id="4cbfd-110">This expression takes an existing record, creates a new one of the same type by using specified fields from the expression and the missing field specified by the expression.</span></span>

<span data-ttu-id="4cbfd-111">當您必須複製現有的記錄, 而且可能變更某些域值時, 這會很有用。</span><span class="sxs-lookup"><span data-stu-id="4cbfd-111">This can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span>

<span data-ttu-id="4cbfd-112">針對新建立的記錄取得實例。</span><span class="sxs-lookup"><span data-stu-id="4cbfd-112">Take for instance a newly created record.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="4cbfd-113">如果您只是在該記錄的欄位上更新, 您可以使用*複製和更新記錄運算式*, 如下所示:</span><span class="sxs-lookup"><span data-stu-id="4cbfd-113">If you were to update only on field of that record you could use the *copy and update record expression* like the following:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a><span data-ttu-id="4cbfd-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4cbfd-114">See also</span></span>

- [<span data-ttu-id="4cbfd-115">記錄</span><span class="sxs-lookup"><span data-stu-id="4cbfd-115">Records</span></span>](records.md)
- [<span data-ttu-id="4cbfd-116">匿名記錄</span><span class="sxs-lookup"><span data-stu-id="4cbfd-116">Anonymous Records</span></span>](anonymous-records.md)
- [<span data-ttu-id="4cbfd-117">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="4cbfd-117">F# Language Reference</span></span>](index.md)
