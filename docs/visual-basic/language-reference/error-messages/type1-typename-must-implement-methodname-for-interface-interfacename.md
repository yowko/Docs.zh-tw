---
title: <type1>'<typename>' 必須實作介面 '<interfacename>' 的 '<methodname>
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: 90d2b6d70390bfb732af4a5868c935de61d18f94
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408493"
---
# <a name="type1typename-must-implement-methodname-for-interface-interfacename"></a><span data-ttu-id="cece5-102">\<type1>'\<typename>' 必須實作介面 '\<interfacename>' 的 '\<methodname></span><span class="sxs-lookup"><span data-stu-id="cece5-102">\<type1>'\<typename>' must implement '\<methodname>' for interface '\<interfacename>'</span></span>
<span data-ttu-id="cece5-103">類別或結構宣告，用來執行介面，但不會執行介面所定義的程式。</span><span class="sxs-lookup"><span data-stu-id="cece5-103">A class or structure claims to implement an interface but does not implement a procedure defined by the interface.</span></span> <span data-ttu-id="cece5-104">介面的每個成員都必須實作為。</span><span class="sxs-lookup"><span data-stu-id="cece5-104">Every member of the interface must be implemented.</span></span>  
  
 <span data-ttu-id="cece5-105">**錯誤識別碼：** BC30149</span><span class="sxs-lookup"><span data-stu-id="cece5-105">**Error ID:** BC30149</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cece5-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="cece5-106">To correct this error</span></span>  
  
1. <span data-ttu-id="cece5-107">使用與介面中所定義相同的名稱和簽章來宣告程式。</span><span class="sxs-lookup"><span data-stu-id="cece5-107">Declare a procedure with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="cece5-108">請務必至少包含 `End Function` 或 `End Sub` 語句。</span><span class="sxs-lookup"><span data-stu-id="cece5-108">Be sure to include at least the `End Function` or `End Sub` statement.</span></span>  
  
2. <span data-ttu-id="cece5-109">將 `Implements` 子句加入至或語句的結尾 `Function` `Sub` 。</span><span class="sxs-lookup"><span data-stu-id="cece5-109">Add an `Implements` clause to the end of the `Function` or `Sub` statement.</span></span> <span data-ttu-id="cece5-110">例如：</span><span class="sxs-lookup"><span data-stu-id="cece5-110">For example:</span></span>  
  
    ```vb  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="cece5-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cece5-111">See also</span></span>

- [<span data-ttu-id="cece5-112">Implements 陳述式</span><span class="sxs-lookup"><span data-stu-id="cece5-112">Implements Statement</span></span>](../statements/implements-statement.md)
- [<span data-ttu-id="cece5-113">介面</span><span class="sxs-lookup"><span data-stu-id="cece5-113">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
