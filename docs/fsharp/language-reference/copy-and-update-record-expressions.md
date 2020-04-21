---
title: 複製和更新記錄運算式
description: 瞭解如何編寫複製現有記錄或匿名記錄、更新指定欄位以及返回更新的記錄或匿名記錄的"複製和更新表達式」。
author: ChrSteinert
ms.date: 06/12/2019
ms.openlocfilehash: bec3e0ac2fb34e358b199c509c4599b55d7bf35e
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739279"
---
# <a name="copy-and-update-record-expressions"></a><span data-ttu-id="44514-103">複製和更新記錄運算式</span><span class="sxs-lookup"><span data-stu-id="44514-103">Copy and Update Record Expressions</span></span>

<span data-ttu-id="44514-104">*複製和更新記錄表達式*是複製現有記錄、更新指定欄位並返回更新的記錄的運算式。</span><span class="sxs-lookup"><span data-stu-id="44514-104">A *copy and update record expression* is an expression that copies an existing record, updates specified fields, and returns the updated record.</span></span>

## <a name="syntax"></a><span data-ttu-id="44514-105">語法</span><span class="sxs-lookup"><span data-stu-id="44514-105">Syntax</span></span>

```fsharp
{ record-name with
    updated-labels }

{| anonymous-record-name with
    updated-labels |}
```

## <a name="remarks"></a><span data-ttu-id="44514-106">備註</span><span class="sxs-lookup"><span data-stu-id="44514-106">Remarks</span></span>

<span data-ttu-id="44514-107">預設情況下,記錄和匿名記錄是不可變的,因此無法更新現有記錄。</span><span class="sxs-lookup"><span data-stu-id="44514-107">Records and anonymous records are immutable by default, so it is not possible to update an existing record.</span></span> <span data-ttu-id="44514-108">要創建更新的記錄,必須再次指定記錄的所有欄位。</span><span class="sxs-lookup"><span data-stu-id="44514-108">To create an updated record all the fields of a record would have to be specified again.</span></span> <span data-ttu-id="44514-109">為了簡化此工作,可以使用*複製與更新表示式*。</span><span class="sxs-lookup"><span data-stu-id="44514-109">To simplify this task a *copy and update expression* can be used.</span></span> <span data-ttu-id="44514-110">此表示式採用現有記錄,使用運算式中的指定欄位和表示式指定的缺失欄位創建新的相同類型。</span><span class="sxs-lookup"><span data-stu-id="44514-110">This expression takes an existing record, creates a new one of the same type by using specified fields from the expression and the missing field specified by the expression.</span></span>

<span data-ttu-id="44514-111">當您必須複製現有記錄並可能更改某些欄位值時,這非常有用。</span><span class="sxs-lookup"><span data-stu-id="44514-111">This can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span>

<span data-ttu-id="44514-112">例如,以新創建的記錄為例。</span><span class="sxs-lookup"><span data-stu-id="44514-112">Take for instance a newly created record.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="44514-113">要僅更新該紀錄中的兩個字段,可以使用*複製和更新記錄表示式*:</span><span class="sxs-lookup"><span data-stu-id="44514-113">To update only two fields in that record you can use the *copy and update record expression*:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a><span data-ttu-id="44514-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44514-114">See also</span></span>

- [<span data-ttu-id="44514-115">記錄</span><span class="sxs-lookup"><span data-stu-id="44514-115">Records</span></span>](records.md)
- [<span data-ttu-id="44514-116">匿名記錄</span><span class="sxs-lookup"><span data-stu-id="44514-116">Anonymous Records</span></span>](anonymous-records.md)
- [<span data-ttu-id="44514-117">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="44514-117">F# Language Reference</span></span>](index.md)
