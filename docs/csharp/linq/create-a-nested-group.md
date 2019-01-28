---
title: 建立巢狀群組 (C# 中的 LINQ)
description: 了解如何在 C# 之 LINQ 查詢運算式中建立巢狀群組。
ms.date: 12/01/2016
ms.assetid: e9f00708-362e-4d13-98c5-d77549347ba0
ms.openlocfilehash: 7d056c9e215ccc7ca24d621b64e2328bed79f22e
ms.sourcegitcommit: 5dcfeb59179e81071f54840d4902cbe00b184294
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "54857667"
---
# <a name="create-a-nested-group"></a><span data-ttu-id="7d366-103">建立巢狀群組</span><span class="sxs-lookup"><span data-stu-id="7d366-103">Create a nested group</span></span>

<span data-ttu-id="7d366-104">下列範例示範如何在 LINQ 查詢運算式中建立巢狀群組。</span><span class="sxs-lookup"><span data-stu-id="7d366-104">The following example shows how to create nested groups in a LINQ query expression.</span></span> <span data-ttu-id="7d366-105">每個根據學年或年級層級建立的群組，接著會根據每個人的姓名進一步細分為群組。</span><span class="sxs-lookup"><span data-stu-id="7d366-105">Each group that is created according to student year or grade level is then further subdivided into groups based on the individuals' names.</span></span>

## <a name="example"></a><span data-ttu-id="7d366-106">範例</span><span class="sxs-lookup"><span data-stu-id="7d366-106">Example</span></span>

> [!NOTE]
> <span data-ttu-id="7d366-107">這個範例包含[查詢物件的集合](query-a-collection-of-objects.md)中範例程式碼中定義的物件參考。</span><span class="sxs-lookup"><span data-stu-id="7d366-107">This example contains references to objects that are defined in the sample code in [Query a collection of objects](query-a-collection-of-objects.md).</span></span>

[!code-csharp[csProgGuideLINQ#24](~/samples/snippets/csharp/concepts/linq/how-to-create-a-nested-group_1.cs)]

<span data-ttu-id="7d366-108">請注意，需要有三個巢狀 `foreach` 迴圈，才能逐一查看巢狀群組的內部項目。</span><span class="sxs-lookup"><span data-stu-id="7d366-108">Note that three nested `foreach` loops are required to iterate over the inner elements of a nested group.</span></span>

## <a name="see-also"></a><span data-ttu-id="7d366-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7d366-109">See also</span></span>

- [<span data-ttu-id="7d366-110">Language-Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="7d366-110">Language Integrated Query (LINQ)</span></span>](index.md)
