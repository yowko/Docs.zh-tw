---
title: <type1>'<typename>' 必須實作介面 '<interfacename>' 的 '<methodname>
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: 68c6f65e6be229cc74458fa56fe3d3aa889c18f7
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161864"
---
# <a name="bc30149-type1typename-must-implement-methodname-for-interface-interfacename"></a><span data-ttu-id="9a185-102">BC30149： \<type1> ' \<typename> ' 必須 \<methodname> 針對介面 ' ' 執行 ' ' \<interfacename></span><span class="sxs-lookup"><span data-stu-id="9a185-102">BC30149: \<type1>'\<typename>' must implement '\<methodname>' for interface '\<interfacename>'</span></span>

<span data-ttu-id="9a185-103">類別或結構宣告來執行介面，但不會執行介面所定義的程式。</span><span class="sxs-lookup"><span data-stu-id="9a185-103">A class or structure claims to implement an interface but does not implement a procedure defined by the interface.</span></span> <span data-ttu-id="9a185-104">介面的每個成員都必須執行。</span><span class="sxs-lookup"><span data-stu-id="9a185-104">Every member of the interface must be implemented.</span></span>

 <span data-ttu-id="9a185-105">**錯誤識別碼：** BC30149</span><span class="sxs-lookup"><span data-stu-id="9a185-105">**Error ID:** BC30149</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="9a185-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="9a185-106">To correct this error</span></span>

1. <span data-ttu-id="9a185-107">使用與介面中定義的相同名稱和簽章來宣告程式。</span><span class="sxs-lookup"><span data-stu-id="9a185-107">Declare a procedure with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="9a185-108">請務必至少包含 `End Function` 或 `End Sub` 語句。</span><span class="sxs-lookup"><span data-stu-id="9a185-108">Be sure to include at least the `End Function` or `End Sub` statement.</span></span>

2. <span data-ttu-id="9a185-109">將 `Implements` 子句加入至或語句的結尾 `Function` `Sub` 。</span><span class="sxs-lookup"><span data-stu-id="9a185-109">Add an `Implements` clause to the end of the `Function` or `Sub` statement.</span></span> <span data-ttu-id="9a185-110">例如：</span><span class="sxs-lookup"><span data-stu-id="9a185-110">For example:</span></span>

    ```vb
    Public Sub DoSomething() Implements IBaseInterface.DoSomething
    ```

## <a name="see-also"></a><span data-ttu-id="9a185-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9a185-111">See also</span></span>

- [<span data-ttu-id="9a185-112">Implements 陳述式</span><span class="sxs-lookup"><span data-stu-id="9a185-112">Implements Statement</span></span>](../statements/implements-statement.md)
- [<span data-ttu-id="9a185-113">介面</span><span class="sxs-lookup"><span data-stu-id="9a185-113">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
