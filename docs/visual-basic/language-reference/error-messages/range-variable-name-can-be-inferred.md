---
title: 只能從不含引數的簡單或限定名稱來推斷範圍變數名稱
ms.date: 07/20/2015
f1_keywords:
- vbc36599
- bc36599
helpviewer_keywords:
- BC36599
ms.assetid: 17763dbe-f74f-4ccb-8086-cb7e45ec4d12
ms.openlocfilehash: d6b155de0bb62f667ca76ec9454dec1466976a9b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400405"
---
# <a name="range-variable-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a><span data-ttu-id="257da-102">只能從不含引數的簡單或限定名稱來推斷範圍變數名稱</span><span class="sxs-lookup"><span data-stu-id="257da-102">Range variable name can be inferred only from a simple or qualified name with no arguments</span></span>

<span data-ttu-id="257da-103">採用一或多個引數的程式設計項目會包含在 LINQ 查詢中。</span><span class="sxs-lookup"><span data-stu-id="257da-103">A programming element that takes one or more arguments is included in a LINQ query.</span></span> <span data-ttu-id="257da-104">編譯器無法從該程式設計項目推斷範圍變數。</span><span class="sxs-lookup"><span data-stu-id="257da-104">The compiler is unable to infer a range variable from that programming element.</span></span>

<span data-ttu-id="257da-105">**錯誤識別碼：** BC36599</span><span class="sxs-lookup"><span data-stu-id="257da-105">**Error ID:** BC36599</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="257da-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="257da-106">To correct this error</span></span>

<span data-ttu-id="257da-107">為程式設計項目提供明確的變數名稱，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="257da-107">Supply an explicit variable name for the programming element, as shown in the following code:</span></span>

```vb
Dim query = From var1 In collection1
            Select VariableAlias= SampleFunction(var1), var1
```

## <a name="see-also"></a><span data-ttu-id="257da-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="257da-108">See also</span></span>

- [<span data-ttu-id="257da-109">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="257da-109">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="257da-110">Select 子句</span><span class="sxs-lookup"><span data-stu-id="257da-110">Select Clause</span></span>](../queries/select-clause.md)
