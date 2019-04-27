---
title: Default (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Default
helpviewer_keywords:
- defaults, properties
- properties [Visual Basic], default
- default properties, in Visual Basic
- Default keyword [Visual Basic]
- default properties
ms.assetid: 45fce9b9-d212-4b2d-ab86-6e359b8b57af
ms.openlocfilehash: f78ffe42a9d618d44da2a50c0de831396576430c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61800928"
---
# <a name="default-visual-basic"></a><span data-ttu-id="043e9-102">Default (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="043e9-102">Default (Visual Basic)</span></span>
<span data-ttu-id="043e9-103">將屬性識別為其類別、 結構或介面的預設屬性。</span><span class="sxs-lookup"><span data-stu-id="043e9-103">Identifies a property as the default property of its class, structure, or interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="043e9-104">備註</span><span class="sxs-lookup"><span data-stu-id="043e9-104">Remarks</span></span>  
 <span data-ttu-id="043e9-105">類別、 結構或介面可以指定最多為其屬性之一*屬性預設*，前提是屬性會採用至少一個參數。</span><span class="sxs-lookup"><span data-stu-id="043e9-105">A class, structure, or interface can designate at most one of its properties as the *default property*, provided that property takes at least one parameter.</span></span> <span data-ttu-id="043e9-106">如果程式碼會產生類別或結構的參考，但沒有指定成員，Visual Basic 會解析該參考的預設屬性。</span><span class="sxs-lookup"><span data-stu-id="043e9-106">If code makes a reference to a class or structure without specifying a member, Visual Basic resolves that reference to the default property.</span></span>  
  
 <span data-ttu-id="043e9-107">預設屬性可能會導致小型減少原始程式碼字元，但它們可以讓您的程式碼更難讀取。</span><span class="sxs-lookup"><span data-stu-id="043e9-107">Default properties can result in a small reduction in source code-characters, but they can make your code more difficult to read.</span></span> <span data-ttu-id="043e9-108">如果類別或結構名稱的參考時呼叫的程式碼不熟悉如何使用您自己的類別或結構，它無法確定該參考是存取類別或結構本身或預設屬性。</span><span class="sxs-lookup"><span data-stu-id="043e9-108">If the calling code is not familiar with your class or structure, when it makes a reference to the class or structure name it cannot be certain whether that reference accesses the class or structure itself, or a default property.</span></span> <span data-ttu-id="043e9-109">這可能會導致編譯器錯誤或難以察覺的執行階段邏輯錯誤。</span><span class="sxs-lookup"><span data-stu-id="043e9-109">This can lead to compiler errors or subtle run-time logic errors.</span></span>  
  
 <span data-ttu-id="043e9-110">您可以一律使用，以稍微降低預設屬性錯誤的機會[Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)設定檢查的編譯器型別`On`。</span><span class="sxs-lookup"><span data-stu-id="043e9-110">You can somewhat reduce the chance of default property errors by always using the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md) to set compiler type checking to `On`.</span></span>  
  
 <span data-ttu-id="043e9-111">如果您打算使用預先定義的類別或結構中您的程式碼中，您必須判斷是否有預設屬性，而如果是的話，它的名稱為何。</span><span class="sxs-lookup"><span data-stu-id="043e9-111">If you are planning to use a predefined class or structure in your code, you must determine whether it has a default property, and if so, what its name is.</span></span>  
  
 <span data-ttu-id="043e9-112">由於這些缺點，您應該考慮不要定義預設屬性。</span><span class="sxs-lookup"><span data-stu-id="043e9-112">Because of these disadvantages, you should consider not defining default properties.</span></span> <span data-ttu-id="043e9-113">程式碼的可讀性，您應該也要考慮一律明確地參考的所有屬性，甚至是預設屬性。</span><span class="sxs-lookup"><span data-stu-id="043e9-113">For code readability, you should also consider always referring to all properties explicitly, even default properties.</span></span>  
  
 <span data-ttu-id="043e9-114">`Default`修飾詞，請使用此內容中：</span><span class="sxs-lookup"><span data-stu-id="043e9-114">The `Default` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="043e9-115">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="043e9-115">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="043e9-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="043e9-116">See also</span></span>

- [<span data-ttu-id="043e9-117">如何：宣告，並在 Visual Basic 中呼叫預設屬性</span><span class="sxs-lookup"><span data-stu-id="043e9-117">How to: Declare and Call a Default Property in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="043e9-118">關鍵字</span><span class="sxs-lookup"><span data-stu-id="043e9-118">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
