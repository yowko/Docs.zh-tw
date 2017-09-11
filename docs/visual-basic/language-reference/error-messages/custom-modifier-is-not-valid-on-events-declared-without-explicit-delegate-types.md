---
title: "&quot;Custom&quot; 修飾詞宣告沒有以明確委派類型的事件無效 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31122
- bc31122
dev_langs:
- VB
helpviewer_keywords:
- BC31122
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 449e5a690f06ce35d1ccc799daf5f2c1ad1c6dac
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="39custom39-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a><span data-ttu-id="63138-102">'Custom' 修飾詞宣告沒有以明確委派類型的事件無效</span><span class="sxs-lookup"><span data-stu-id="63138-102">&#39;Custom&#39; modifier is not valid on events declared without explicit delegate types</span></span>
<span data-ttu-id="63138-103">不同於非自訂事件`Custom Event`宣告需要`As`明確指定事件的委派類型的事件名稱後面的子句。</span><span class="sxs-lookup"><span data-stu-id="63138-103">Unlike a non-custom event, a `Custom Event` declaration requires an `As` clause following the event name that explicitly specifies the delegate type for the event.</span></span>  
  
 <span data-ttu-id="63138-104">非自訂事件可能會定義與`As`子句和明確委派類型，或立即使用參數清單之後的事件名稱。</span><span class="sxs-lookup"><span data-stu-id="63138-104">Non-custom events can be defined either with an `As` clause and an explicit delegate type, or with a parameter list immediately following the event name.</span></span>  
  
 <span data-ttu-id="63138-105">**錯誤識別碼︰** BC31122</span><span class="sxs-lookup"><span data-stu-id="63138-105">**Error ID:** BC31122</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="63138-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="63138-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="63138-107">定義自訂事件的委派具有相同的參數清單。</span><span class="sxs-lookup"><span data-stu-id="63138-107">Define a delegate with the same parameter list as the custom event.</span></span>  
  
     <span data-ttu-id="63138-108">例如，如果`Custom Event`所定義`Custom Event Test(ByVal sender As Object, ByVal i As Integer)`，則對應的委派會是下列。</span><span class="sxs-lookup"><span data-stu-id="63138-108">For example, if the `Custom Event` was defined by `Custom Event Test(ByVal sender As Object, ByVal i As Integer)`, then the corresponding delegate would be the following.</span></span>  
  
     <span data-ttu-id="63138-109">[!code-vb[VbVbalrEventError #&18;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="63138-109">[!code-vb[VbVbalrEventError#18](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_1.vb)]</span></span>  
  
2.  <span data-ttu-id="63138-110">取代參數清單的自訂事件`As`子句指定的委派型別。</span><span class="sxs-lookup"><span data-stu-id="63138-110">Replace the parameter list of the custom event with an `As` clause specifying the delegate type.</span></span>  
  
     <span data-ttu-id="63138-111">此範例中，繼續`Custom Event`宣告重新撰寫，如下所示。</span><span class="sxs-lookup"><span data-stu-id="63138-111">Continuing with the example, `Custom Event` declaration would be rewritten as follows.</span></span>  
  
     <span data-ttu-id="63138-112">[!code-vb[VbVbalrEventError #&19;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="63138-112">[!code-vb[VbVbalrEventError#19](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_2.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="63138-113">範例</span><span class="sxs-lookup"><span data-stu-id="63138-113">Example</span></span>  
 <span data-ttu-id="63138-114">這個範例會宣告`Custom Event`，並指定必要`As`具有委派型別子句。</span><span class="sxs-lookup"><span data-stu-id="63138-114">This example declares a `Custom Event` and specifies the required `As` clause with a delegate type.</span></span>  
  
 <span data-ttu-id="63138-115">[!code-vb[VbVbalrEventError #&2;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="63138-115">[!code-vb[VbVbalrEventError#2](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_3.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63138-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63138-116">See Also</span></span>  
 <span data-ttu-id="63138-117">[Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md) </span><span class="sxs-lookup"><span data-stu-id="63138-117">[Event Statement](../../../visual-basic/language-reference/statements/event-statement.md) </span></span>  
<span data-ttu-id="63138-118"> [Delegate 陳述式](../../../visual-basic/language-reference/statements/delegate-statement.md) </span><span class="sxs-lookup"><span data-stu-id="63138-118"> [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) </span></span>  
<span data-ttu-id="63138-119"> [事件](../../../visual-basic/programming-guide/language-features/events/index.md)</span><span class="sxs-lookup"><span data-stu-id="63138-119"> [Events](../../../visual-basic/programming-guide/language-features/events/index.md)</span></span>
