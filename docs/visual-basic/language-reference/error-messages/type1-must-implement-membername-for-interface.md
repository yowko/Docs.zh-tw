---
title: <type1>'<typename>' 必須實作介面 '<interfacename>' 的 '<membername>
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: 4ffe18e11c388a8c69ef0592bde1b78f5b219680
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84386850"
---
# <a name="type1typename-must-implement-membername-for-interface-interfacename"></a><span data-ttu-id="2c6c6-102">\<type1>'\<typename>' 必須實作介面 '\<interfacename>' 的 '\<membername></span><span class="sxs-lookup"><span data-stu-id="2c6c6-102">\<type1>'\<typename>' must implement '\<membername>' for interface '\<interfacename>'</span></span>
<span data-ttu-id="2c6c6-103">' \<typename> ' 必須 \<membername> 為介面 ' ' 執行 ' ' \<interfacename> 。</span><span class="sxs-lookup"><span data-stu-id="2c6c6-103">'\<typename>' must implement '\<membername>' for interface '\<interfacename>'.</span></span> <span data-ttu-id="2c6c6-104">執行屬性必須有相符的 ' ReadOnly '/' WriteOnly ' 規範。</span><span class="sxs-lookup"><span data-stu-id="2c6c6-104">Implementing property must have matching 'ReadOnly'/'WriteOnly' specifiers.</span></span>  
  
 <span data-ttu-id="2c6c6-105">類別或結構宣告，用來執行介面，但不會執行介面所定義的程式、屬性或事件。</span><span class="sxs-lookup"><span data-stu-id="2c6c6-105">A class or structure claims to implement an interface but does not implement a procedure, property, or event defined by the interface.</span></span> <span data-ttu-id="2c6c6-106">介面的每個成員都必須實作為。</span><span class="sxs-lookup"><span data-stu-id="2c6c6-106">Every member of the interface must be implemented.</span></span>  
  
 <span data-ttu-id="2c6c6-107">**錯誤識別碼：** BC30154</span><span class="sxs-lookup"><span data-stu-id="2c6c6-107">**Error ID:** BC30154</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2c6c6-108">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="2c6c6-108">To correct this error</span></span>  
  
1. <span data-ttu-id="2c6c6-109">宣告具有與介面中所定義相同名稱和簽章的成員。</span><span class="sxs-lookup"><span data-stu-id="2c6c6-109">Declare a member with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="2c6c6-110">請務必至少包含 `End Function` 、 `End Sub` 或 `End Property` 語句。</span><span class="sxs-lookup"><span data-stu-id="2c6c6-110">Be sure to include at least the `End Function`, `End Sub`, or `End Property` statement.</span></span>  
  
2. <span data-ttu-id="2c6c6-111">將 `Implements` 子句加入至 `Function` 、 `Sub` 、 `Property` 或 `Event` 語句的結尾。</span><span class="sxs-lookup"><span data-stu-id="2c6c6-111">Add an `Implements` clause to the end of the `Function`, `Sub`, `Property`, or `Event` statement.</span></span> <span data-ttu-id="2c6c6-112">例如：</span><span class="sxs-lookup"><span data-stu-id="2c6c6-112">For example:</span></span>  
  
    ```vb  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3. <span data-ttu-id="2c6c6-113">在執行屬性時，請確定 `ReadOnly` 使用或的 `WriteOnly` 方式與在介面定義中相同。</span><span class="sxs-lookup"><span data-stu-id="2c6c6-113">When implementing a property, make sure that `ReadOnly` or `WriteOnly` is used in the same way as in the interface definition.</span></span>  
  
4. <span data-ttu-id="2c6c6-114">在執行屬性時，請 `Get` 適當地宣告和 `Set` 程式。</span><span class="sxs-lookup"><span data-stu-id="2c6c6-114">When implementing a property, declare `Get` and `Set` procedures, as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c6c6-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2c6c6-115">See also</span></span>

- [<span data-ttu-id="2c6c6-116">Implements 陳述式</span><span class="sxs-lookup"><span data-stu-id="2c6c6-116">Implements Statement</span></span>](../statements/implements-statement.md)
- [<span data-ttu-id="2c6c6-117">介面</span><span class="sxs-lookup"><span data-stu-id="2c6c6-117">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
