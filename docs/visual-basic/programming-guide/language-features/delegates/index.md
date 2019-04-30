---
title: 委派 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [Visual Basic]
- Visual Basic code, delegates
ms.assetid: 410b60dc-5e60-4ec0-bfae-426755a2ee28
ms.openlocfilehash: b3f333f1714a66a8ff462000385af92cf343a19e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62050593"
---
# <a name="delegates-visual-basic"></a>委派 (Visual Basic)

委派是參考方法的物件。 它們有時稱為「型別安全的函式指標」，因為它們類似於其他程式設計語言中使用的函式指標。 但不同於函式指標，Visual Basic 委派是參考類型，根據類別<xref:System.Delegate?displayProperty=nameWithType>。 委派可以同時參考共用的方法 (不需類別的特定執行個體就能呼叫的方法) 和執行個體方法。

## <a name="delegates-and-events"></a>委派和事件

當您在呼叫程序與被呼叫程序之間需要一個媒介時，委派就很有用。 例如，您想要讓引發事件的物件能夠在不同環境下呼叫不同的事件處理常式。 不過，引發事件的物件無法事先知道哪一個事件處理常式正在處理特定事件。 Visual Basic 可讓您以動態方式產生關聯的事件處理常式與事件藉由建立您的委派，當您使用`AddHandler`陳述式。 在執行階段，委派會將呼叫轉送到適當的事件處理常式。

雖然您可以建立自己的委派，在大部分情況下，Visual Basic 建立委派，並會為您處理的詳細資料。 例如，`Event` 陳述式會隱含定義名為 `<EventName>EventHandler` 的委派類別做為包含 `Event` 陳述式之類別的巢狀類別，並包含與事件相同的簽章。 `AddressOf` 陳述式會隱含建立參考特定程序之委派的執行個體。 下兩行程式碼的用法相同。 在第一行中，您會看到明確建立了 `EventHandler` 的執行個體，其中包含對傳送為引數之 `Button1_Click` 方法的參考。 第二行則是可執行相同動作的更便捷方法。

[!code-vb[VbVbalrDelegates#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#6)]

您可以使用在任意處建立委派的速成法，讓編譯器可依內容判斷委派的型別。

## <a name="declaring-events-that-use-an-existing-delegate-type"></a>宣告使用現有委派型別的事件

在某些情況下，您可能想要宣告事件，以使用現有的委派型別做為它的基礎委派。 下列語法示範做法：

[!code-vb[VbVbalrDelegates#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#7)]

當您想要將多個事件路由傳送到相同的處理常式時，這非常有用。

## <a name="delegate-variables-and-parameters"></a>委派變數和參數

您可以針對其他與事件無關的工作 (例如無限制執行緒) 使用委派，或搭配需要在執行階段呼叫不同函式版本的程序來使用委派。

例如，假設您具有分類廣告應用程式，其中包含具有車名的清單方塊。 廣告會依標題排序，通常是汽車製造商。 當某些汽車在製造商之前包含汽車的年份時，就會發生您可能面臨的問題。 問題是清單方塊的內建排序功能只會依照字元碼排序；它會先排序所有以日期開頭的廣告，接著才是以製造商開頭的廣告。

為了修正此問題，您可以在某個類別中使用排序程序 (該類別會在大部分清單方塊中使用標準的依字母順序排序)，但是可以在執行階段切換到自訂排序程序來進行汽車廣告。 若要這樣做，您可以使用委派，在執行階段將自訂排序程序傳遞到排序類別。

## <a name="addressof-and-lambda-expressions"></a>AddressOf 和 Lambda 運算式

每個委派類別會為傳遞的建構函式定義物件方法的規格。 對委派建構函式的引數必須是對方法的參考或 lambda 運算式。

若要指定對方法的參考，請使用下列語法：

`AddressOf` [`expression`.]`methodName`

`expression` 的編譯時期型別必須是類別或介面的名稱，而該類別或介面包含其簽章符合委派類別簽章的特定名稱方法。 `methodName` 可以是共用的方法或執行個體方法。 `methodName` 不是選擇性的，即使您為類別的預設方法建立了委派也一樣。

若要指定 lambda 運算式，請使用下列語法：

`Function` ([`parm` As `type`, `parm2` As `type2`, ...]) `expression`

下列範例示範用來指定委派參考的 `AddressOf` 和 lambda 運算式。

[!code-vb[VbVbalrDelegates#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class2.vb#15)]

函式的簽章必須符合委派型別的簽章。 如需 Lambda 運算式的詳細資訊，請參閱 [Lambda 運算式](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)。 如需 lambda 運算式以及要委派的 `AddressOf` 指派的更多範例，請參閱[寬鬆委派轉換](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)。

## <a name="related-topics"></a>相關主題

|標題|說明|
|-----------|-----------------|
|[如何：叫用委派方法](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)|提供範例，示範如何將方法和委派產生關聯，然後透過委派叫用該方法。|
|[如何：傳遞至另一個程序，在 Visual Basic 中的程序](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)|示範如何使用委派，將一個程序傳遞至另一個程序。|
|[寬鬆委派轉換](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)|描述即便是 Sub 和函式的簽章不同，如何將它們指派給委派或處理常式。|
|[事件](../../../../visual-basic/programming-guide/language-features/events/index.md)|提供 Visual Basic 中的事件概觀。|
