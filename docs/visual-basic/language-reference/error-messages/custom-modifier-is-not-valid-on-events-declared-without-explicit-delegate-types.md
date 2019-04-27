---
title: "'Custom' 修飾詞在沒有以明確委派類型宣告的事件中無效"
ms.date: 07/20/2015
f1_keywords:
- vbc31122
- bc31122
helpviewer_keywords:
- BC31122
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
ms.openlocfilehash: 169cb49cc5abc76b7c52785392d0083b81a99450
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61803879"
---
# <a name="custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a><span data-ttu-id="6654e-102">'Custom' 修飾詞在沒有以明確委派類型宣告的事件中無效</span><span class="sxs-lookup"><span data-stu-id="6654e-102">'Custom' modifier is not valid on events declared without explicit delegate types</span></span>
<span data-ttu-id="6654e-103">不同於非自訂事件`Custom Event`宣告需要`As`事件名稱，明確地指定事件的委派型別後面的子句。</span><span class="sxs-lookup"><span data-stu-id="6654e-103">Unlike a non-custom event, a `Custom Event` declaration requires an `As` clause following the event name that explicitly specifies the delegate type for the event.</span></span>  
  
 <span data-ttu-id="6654e-104">非自訂事件可以是定義使用`As`子句和明確委派類型，或立即使用參數清單後面的事件名稱。</span><span class="sxs-lookup"><span data-stu-id="6654e-104">Non-custom events can be defined either with an `As` clause and an explicit delegate type, or with a parameter list immediately following the event name.</span></span>  
  
 <span data-ttu-id="6654e-105">**錯誤 ID:** BC31122</span><span class="sxs-lookup"><span data-stu-id="6654e-105">**Error ID:** BC31122</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6654e-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="6654e-106">To correct this error</span></span>  
  
1. <span data-ttu-id="6654e-107">定義自訂事件的委派具有相同的參數清單。</span><span class="sxs-lookup"><span data-stu-id="6654e-107">Define a delegate with the same parameter list as the custom event.</span></span>  
  
     <span data-ttu-id="6654e-108">例如，如果`Custom Event`已定義`Custom Event Test(ByVal sender As Object, ByVal i As Integer)`，則對應的委派會是如下所示。</span><span class="sxs-lookup"><span data-stu-id="6654e-108">For example, if the `Custom Event` was defined by `Custom Event Test(ByVal sender As Object, ByVal i As Integer)`, then the corresponding delegate would be the following.</span></span>  
  
     [!code-vb[VbVbalrEventError#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#18)]  
  
2. <span data-ttu-id="6654e-109">將自訂事件的參數清單`As`子句指定的委派型別。</span><span class="sxs-lookup"><span data-stu-id="6654e-109">Replace the parameter list of the custom event with an `As` clause specifying the delegate type.</span></span>  
  
     <span data-ttu-id="6654e-110">此範例中，再繼續`Custom Event`宣告重新撰寫，如下所示。</span><span class="sxs-lookup"><span data-stu-id="6654e-110">Continuing with the example, `Custom Event` declaration would be rewritten as follows.</span></span>  
  
     [!code-vb[VbVbalrEventError#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#19)]  
  
## <a name="example"></a><span data-ttu-id="6654e-111">範例</span><span class="sxs-lookup"><span data-stu-id="6654e-111">Example</span></span>  
 <span data-ttu-id="6654e-112">這個範例會宣告`Custom Event`，並指定必要`As`子句與委派型別。</span><span class="sxs-lookup"><span data-stu-id="6654e-112">This example declares a `Custom Event` and specifies the required `As` clause with a delegate type.</span></span>  
  
 [!code-vb[VbVbalrEventError#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="6654e-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6654e-113">See also</span></span>

- [<span data-ttu-id="6654e-114">Event 陳述式</span><span class="sxs-lookup"><span data-stu-id="6654e-114">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="6654e-115">Delegate 陳述式</span><span class="sxs-lookup"><span data-stu-id="6654e-115">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="6654e-116">事件</span><span class="sxs-lookup"><span data-stu-id="6654e-116">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
