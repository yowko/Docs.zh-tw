---
title: '&#39;自訂 &#39;修飾詞宣告沒有以明確委派類型的事件中無效'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31122
- bc31122
helpviewer_keywords:
- BC31122
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 844bd033ea05e373b04a04f80777af77179c1263
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="39custom39-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a><span data-ttu-id="52128-102">&#39;自訂 &#39;修飾詞宣告沒有以明確委派類型的事件中無效</span><span class="sxs-lookup"><span data-stu-id="52128-102">&#39;Custom&#39; modifier is not valid on events declared without explicit delegate types</span></span>
<span data-ttu-id="52128-103">不同於非自訂事件`Custom Event`宣告需要`As`子句之後明確地指定事件的委派類型的事件名稱。</span><span class="sxs-lookup"><span data-stu-id="52128-103">Unlike a non-custom event, a `Custom Event` declaration requires an `As` clause following the event name that explicitly specifies the delegate type for the event.</span></span>  
  
 <span data-ttu-id="52128-104">非自訂的事件可能會定義與`As`子句和明確委派類型，或立即使用參數清單之後的事件名稱。</span><span class="sxs-lookup"><span data-stu-id="52128-104">Non-custom events can be defined either with an `As` clause and an explicit delegate type, or with a parameter list immediately following the event name.</span></span>  
  
 <span data-ttu-id="52128-105">**錯誤 ID:** BC31122</span><span class="sxs-lookup"><span data-stu-id="52128-105">**Error ID:** BC31122</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="52128-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="52128-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="52128-107">為自訂的事件定義相同的參數清單的委派。</span><span class="sxs-lookup"><span data-stu-id="52128-107">Define a delegate with the same parameter list as the custom event.</span></span>  
  
     <span data-ttu-id="52128-108">例如，如果`Custom Event`所定義`Custom Event Test(ByVal sender As Object, ByVal i As Integer)`，則對應的委派會是如下所示。</span><span class="sxs-lookup"><span data-stu-id="52128-108">For example, if the `Custom Event` was defined by `Custom Event Test(ByVal sender As Object, ByVal i As Integer)`, then the corresponding delegate would be the following.</span></span>  
  
     [!code-vb[VbVbalrEventError#18](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_1.vb)]  
  
2.  <span data-ttu-id="52128-109">取代參數清單的自訂事件`As`子句指定委派類型。</span><span class="sxs-lookup"><span data-stu-id="52128-109">Replace the parameter list of the custom event with an `As` clause specifying the delegate type.</span></span>  
  
     <span data-ttu-id="52128-110">此範例中，再繼續`Custom Event`宣告重新撰寫，如下所示。</span><span class="sxs-lookup"><span data-stu-id="52128-110">Continuing with the example, `Custom Event` declaration would be rewritten as follows.</span></span>  
  
     [!code-vb[VbVbalrEventError#19](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="52128-111">範例</span><span class="sxs-lookup"><span data-stu-id="52128-111">Example</span></span>  
 <span data-ttu-id="52128-112">這個範例會宣告`Custom Event`，並指定所需`As`具有委派型別子句。</span><span class="sxs-lookup"><span data-stu-id="52128-112">This example declares a `Custom Event` and specifies the required `As` clause with a delegate type.</span></span>  
  
 [!code-vb[VbVbalrEventError#2](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="52128-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="52128-113">See Also</span></span>  
 [<span data-ttu-id="52128-114">Event 陳述式</span><span class="sxs-lookup"><span data-stu-id="52128-114">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="52128-115">Delegate 陳述式</span><span class="sxs-lookup"><span data-stu-id="52128-115">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [<span data-ttu-id="52128-116">事件</span><span class="sxs-lookup"><span data-stu-id="52128-116">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
