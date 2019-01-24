---
title: '&lt;type1&gt;&#39;&lt;typename&gt; &#39;必須實作&#39; &lt;membername&gt; &#39;介面&#39;&lt;介面名稱&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: 14e7bd199215764676a4b563eafc68bd6dabadc7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574738"
---
# <a name="lttype1gt39lttypenamegt39-must-implement-39ltmembernamegt39-for-interface-39ltinterfacenamegt39"></a><span data-ttu-id="e5b39-102">&lt;type1&gt;&#39;&lt;typename&gt; &#39;必須實作&#39; &lt;membername&gt; &#39;介面&#39;&lt;介面名稱&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="e5b39-102">&lt;type1&gt;&#39;&lt;typename&gt;&#39; must implement &#39;&lt;membername&gt;&#39; for interface &#39;&lt;interfacename&gt;&#39;</span></span>
<span data-ttu-id="e5b39-103">'\<類型名稱 >' 必須實作'\<成員名稱 >' 的介面 '\<介面名稱 >'。</span><span class="sxs-lookup"><span data-stu-id="e5b39-103">'\<typename>' must implement '\<membername>' for interface '\<interfacename>'.</span></span> <span data-ttu-id="e5b39-104">實作屬性必須比對 'ReadOnly '/' WriteOnly' 規範。</span><span class="sxs-lookup"><span data-stu-id="e5b39-104">Implementing property must have matching 'ReadOnly'/'WriteOnly' specifiers.</span></span>  
  
 <span data-ttu-id="e5b39-105">類別或結構宣告實作介面，但不會實作程序、 屬性或介面所定義的事件。</span><span class="sxs-lookup"><span data-stu-id="e5b39-105">A class or structure claims to implement an interface but does not implement a procedure, property, or event defined by the interface.</span></span> <span data-ttu-id="e5b39-106">必須實作介面的每個成員。</span><span class="sxs-lookup"><span data-stu-id="e5b39-106">Every member of the interface must be implemented.</span></span>  
  
 <span data-ttu-id="e5b39-107">**錯誤 ID:** BC30154</span><span class="sxs-lookup"><span data-stu-id="e5b39-107">**Error ID:** BC30154</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e5b39-108">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="e5b39-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="e5b39-109">宣告具有相同的名稱和簽章的介面中所定義的成員。</span><span class="sxs-lookup"><span data-stu-id="e5b39-109">Declare a member with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="e5b39-110">務必要包含在至少`End Function`， `End Sub`，或`End Property`陳述式。</span><span class="sxs-lookup"><span data-stu-id="e5b39-110">Be sure to include at least the `End Function`, `End Sub`, or `End Property` statement.</span></span>  
  
2.  <span data-ttu-id="e5b39-111">新增`Implements`子句來結束`Function`， `Sub`， `Property`，或`Event`陳述式。</span><span class="sxs-lookup"><span data-stu-id="e5b39-111">Add an `Implements` clause to the end of the `Function`, `Sub`, `Property`, or `Event` statement.</span></span> <span data-ttu-id="e5b39-112">例如: </span><span class="sxs-lookup"><span data-stu-id="e5b39-112">For example:</span></span>  
  
    ```  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3.  <span data-ttu-id="e5b39-113">當實作的屬性，請確定`ReadOnly`或`WriteOnly`用於介面定義的相同方式。</span><span class="sxs-lookup"><span data-stu-id="e5b39-113">When implementing a property, make sure that `ReadOnly` or `WriteOnly` is used in the same way as in the interface definition.</span></span>  
  
4.  <span data-ttu-id="e5b39-114">當實作的屬性，宣告`Get`和`Set`程序，適當地。</span><span class="sxs-lookup"><span data-stu-id="e5b39-114">When implementing a property, declare `Get` and `Set` procedures, as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5b39-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5b39-115">See also</span></span>
- [<span data-ttu-id="e5b39-116">Implements 陳述式</span><span class="sxs-lookup"><span data-stu-id="e5b39-116">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)
- [<span data-ttu-id="e5b39-117">介面</span><span class="sxs-lookup"><span data-stu-id="e5b39-117">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
