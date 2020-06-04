---
title: "'Custom' 修飾詞在沒有以明確委派類型宣告的事件中無效"
ms.date: 07/20/2015
f1_keywords:
- vbc31122
- bc31122
helpviewer_keywords:
- BC31122
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
ms.openlocfilehash: 0c5a4188fedf9685afdd1cde4c1de93a0b43b919
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409775"
---
# <a name="custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a><span data-ttu-id="7e37c-102">'Custom' 修飾詞在沒有以明確委派類型宣告的事件中無效</span><span class="sxs-lookup"><span data-stu-id="7e37c-102">'Custom' modifier is not valid on events declared without explicit delegate types</span></span>
<span data-ttu-id="7e37c-103">不同于非自訂事件，宣告 `Custom Event` 需要 `As` 遵循事件名稱的子句，以明確指定事件的委派類型。</span><span class="sxs-lookup"><span data-stu-id="7e37c-103">Unlike a non-custom event, a `Custom Event` declaration requires an `As` clause following the event name that explicitly specifies the delegate type for the event.</span></span>  
  
 <span data-ttu-id="7e37c-104">非自訂事件可以使用 `As` 子句和明確委派類型，或緊接在事件名稱後面的參數清單來定義。</span><span class="sxs-lookup"><span data-stu-id="7e37c-104">Non-custom events can be defined either with an `As` clause and an explicit delegate type, or with a parameter list immediately following the event name.</span></span>  
  
 <span data-ttu-id="7e37c-105">**錯誤識別碼：** BC31122</span><span class="sxs-lookup"><span data-stu-id="7e37c-105">**Error ID:** BC31122</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7e37c-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="7e37c-106">To correct this error</span></span>  
  
1. <span data-ttu-id="7e37c-107">使用與自訂事件相同的參數清單來定義委派。</span><span class="sxs-lookup"><span data-stu-id="7e37c-107">Define a delegate with the same parameter list as the custom event.</span></span>  
  
     <span data-ttu-id="7e37c-108">例如，如果 `Custom Event` 是由所定義 `Custom Event Test(ByVal sender As Object, ByVal i As Integer)` ，則對應的委派會如下所示。</span><span class="sxs-lookup"><span data-stu-id="7e37c-108">For example, if the `Custom Event` was defined by `Custom Event Test(ByVal sender As Object, ByVal i As Integer)`, then the corresponding delegate would be the following.</span></span>  
  
     [!code-vb[VbVbalrEventError#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#18)]  
  
2. <span data-ttu-id="7e37c-109">將自訂事件的參數清單取代為 `As` 指定委派類型的子句。</span><span class="sxs-lookup"><span data-stu-id="7e37c-109">Replace the parameter list of the custom event with an `As` clause specifying the delegate type.</span></span>  
  
     <span data-ttu-id="7e37c-110">繼續執行此範例時，會 `Custom Event` 以下列方式改寫宣告。</span><span class="sxs-lookup"><span data-stu-id="7e37c-110">Continuing with the example, `Custom Event` declaration would be rewritten as follows.</span></span>  
  
     [!code-vb[VbVbalrEventError#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#19)]  
  
## <a name="example"></a><span data-ttu-id="7e37c-111">範例</span><span class="sxs-lookup"><span data-stu-id="7e37c-111">Example</span></span>  
 <span data-ttu-id="7e37c-112">這個範例會宣告 `Custom Event` ，並使用委派類型來指定必要的 `As` 子句。</span><span class="sxs-lookup"><span data-stu-id="7e37c-112">This example declares a `Custom Event` and specifies the required `As` clause with a delegate type.</span></span>  
  
 [!code-vb[VbVbalrEventError#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="7e37c-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e37c-113">See also</span></span>

- [<span data-ttu-id="7e37c-114">Event 陳述式</span><span class="sxs-lookup"><span data-stu-id="7e37c-114">Event Statement</span></span>](../statements/event-statement.md)
- [<span data-ttu-id="7e37c-115">Delegate 陳述式</span><span class="sxs-lookup"><span data-stu-id="7e37c-115">Delegate Statement</span></span>](../statements/delegate-statement.md)
- [<span data-ttu-id="7e37c-116">事件</span><span class="sxs-lookup"><span data-stu-id="7e37c-116">Events</span></span>](../../programming-guide/language-features/events/index.md)
