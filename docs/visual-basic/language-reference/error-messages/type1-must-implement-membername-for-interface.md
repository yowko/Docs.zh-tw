---
title: <type1>'<typename>'必須實作'<membername>'的介面'<interfacename>'
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: 86b0d46e0e27b2fd8d1fccb37f4a3c45e95f5f63
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61792089"
---
# <a name="type1typename-must-implement-membername-for-interface-interfacename"></a><span data-ttu-id="3e691-102">\<type1 >'\<類型名稱 >' 必須實作 '\<成員名稱 >' 的介面'\<介面名稱 >'</span><span class="sxs-lookup"><span data-stu-id="3e691-102">\<type1>'\<typename>' must implement '\<membername>' for interface '\<interfacename>'</span></span>
<span data-ttu-id="3e691-103">'\<類型名稱 >' 必須實作'\<成員名稱 >' 的介面 '\<介面名稱 >'。</span><span class="sxs-lookup"><span data-stu-id="3e691-103">'\<typename>' must implement '\<membername>' for interface '\<interfacename>'.</span></span> <span data-ttu-id="3e691-104">實作屬性必須比對 'ReadOnly '/' WriteOnly' 規範。</span><span class="sxs-lookup"><span data-stu-id="3e691-104">Implementing property must have matching 'ReadOnly'/'WriteOnly' specifiers.</span></span>  
  
 <span data-ttu-id="3e691-105">類別或結構宣告實作介面，但不會實作程序、 屬性或介面所定義的事件。</span><span class="sxs-lookup"><span data-stu-id="3e691-105">A class or structure claims to implement an interface but does not implement a procedure, property, or event defined by the interface.</span></span> <span data-ttu-id="3e691-106">必須實作介面的每個成員。</span><span class="sxs-lookup"><span data-stu-id="3e691-106">Every member of the interface must be implemented.</span></span>  
  
 <span data-ttu-id="3e691-107">**錯誤 ID:** BC30154</span><span class="sxs-lookup"><span data-stu-id="3e691-107">**Error ID:** BC30154</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3e691-108">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="3e691-108">To correct this error</span></span>  
  
1. <span data-ttu-id="3e691-109">宣告具有相同的名稱和簽章的介面中所定義的成員。</span><span class="sxs-lookup"><span data-stu-id="3e691-109">Declare a member with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="3e691-110">務必要包含在至少`End Function`， `End Sub`，或`End Property`陳述式。</span><span class="sxs-lookup"><span data-stu-id="3e691-110">Be sure to include at least the `End Function`, `End Sub`, or `End Property` statement.</span></span>  
  
2. <span data-ttu-id="3e691-111">新增`Implements`子句來結束`Function`， `Sub`， `Property`，或`Event`陳述式。</span><span class="sxs-lookup"><span data-stu-id="3e691-111">Add an `Implements` clause to the end of the `Function`, `Sub`, `Property`, or `Event` statement.</span></span> <span data-ttu-id="3e691-112">例如：</span><span class="sxs-lookup"><span data-stu-id="3e691-112">For example:</span></span>  
  
    ```  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3. <span data-ttu-id="3e691-113">當實作的屬性，請確定`ReadOnly`或`WriteOnly`用於介面定義的相同方式。</span><span class="sxs-lookup"><span data-stu-id="3e691-113">When implementing a property, make sure that `ReadOnly` or `WriteOnly` is used in the same way as in the interface definition.</span></span>  
  
4. <span data-ttu-id="3e691-114">當實作的屬性，宣告`Get`和`Set`程序，適當地。</span><span class="sxs-lookup"><span data-stu-id="3e691-114">When implementing a property, declare `Get` and `Set` procedures, as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e691-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e691-115">See also</span></span>

- [<span data-ttu-id="3e691-116">Implements 陳述式</span><span class="sxs-lookup"><span data-stu-id="3e691-116">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)
- [<span data-ttu-id="3e691-117">介面</span><span class="sxs-lookup"><span data-stu-id="3e691-117">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
