---
title: 如何呼叫事件處理常式
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- event handlers [Visual Basic], calling
- event handlers
- procedures [Visual Basic], event handlers
- procedures [Visual Basic], calling
no-loc:
- WithEvents
ms.assetid: 72e18ef8-144e-40df-a1f4-066a57271e28
ms.openlocfilehash: 3762c79dd3d883ae2ccfe76b335cf98ac87d4246
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2020
ms.locfileid: "89464957"
---
# <a name="how-to-call-an-event-handler-in-visual-basic"></a>如何在 Visual Basic 中呼叫事件處理常式

*事件*是由某些程式元件辨識的動作或發生（例如滑鼠點擊或超過的點數限制），且您可以撰寫程式碼來回應。 *事件處理常式*是您為了回應事件而撰寫的程式碼。

Visual Basic 中的事件處理常式是程式 `Sub` 。 不過，您通常不會以與其他程式相同的方式來呼叫它 `Sub` 。 相反地，您會將程式識別為事件的處理常式。 您可以使用 [`Handles`](../../../language-reference/statements/handles-clause.md) 子句和 [`WithEvents`](../../../language-reference/modifiers/withevents.md) 變數，或使用 [AddHandler 語句](../../../language-reference/statements/addhandler-statement.md)來進行這項作業。 使用 `Handles` 子句是在 Visual Basic 中宣告事件處理常式的預設方式。 當您在整合式開發環境中進行程式設計時，當您在 (IDE) 中進行程式設計時，設計工具就會撰寫事件處理常式的方式。 `AddHandler`語句適合用來在執行時間動態引發事件。

當事件發生時，Visual Basic 會自動呼叫事件處理常式程式。 任何可存取事件的程式碼，都可以藉由執行 [RaiseEvent 語句](../../../language-reference/statements/raiseevent-statement.md)來使其發生。

您可以將一個以上的事件處理常式與相同事件產生關聯。 在某些情況下，您可以中斷處理常式與事件之間的關聯。 如需詳細資訊，請參閱[事件](../events/index.md)。

## <a name="call-an-event-handler-using-no-loc-texthandles-and-no-locwithevents"></a>使用和呼叫事件處理常式 :::no-loc text="Handles":::WithEvents

1. 請確定事件是使用 [事件語句](../../../language-reference/statements/event-statement.md)宣告的。

2. 使用關鍵字來宣告模組或類別層級的物件變數 [`WithEvents`](../../../language-reference/modifiers/withevents.md) 。 `As`這個變數的子句必須指定引發事件的類別。

3. 在事件處理常式的宣告中 `Sub` ，加入 [`Handles`](../../../language-reference/statements/handles-clause.md) 指定 `WithEvents` 變數和事件名稱的子句。

4. 當事件發生時，Visual Basic 會自動呼叫程式 `Sub` 。 您的程式碼可以使用 `RaiseEvent` 語句來讓事件發生。

    下列範例會定義事件，以及 `WithEvents` 參考引發事件之類別的變數。 事件處理常式 `Sub` `Handles` 會使用子句來指定它所處理的類別和事件。

    :::code language="vb" source="snippets/how-to-call-an-event-handler/SpecialForm.vb" id="4":::

## <a name="call-an-event-handler-using-addhandler"></a>使用 AddHandler 呼叫事件處理常式

1. 請確定事件是使用語句宣告的 `Event` 。

2. 執行 [AddHandler 語句](../../../language-reference/statements/addhandler-statement.md) ，以動態方式連接事件處理常式 `Sub` 和事件。

3. 當事件發生時，Visual Basic 會自動呼叫程式 `Sub` 。 您的程式碼可以使用 `RaiseEvent` 語句來讓事件發生。

    下列範例會在此函式中使用 [AddHandler 語句](../../../language-reference/statements/addhandler-statement.md) ，將 `OnFormClosing` 程式與的事件處理常式產生關聯 <xref:System.Windows.Forms.Form.FormClosing> 。

    :::code language="vb" source="snippets/how-to-call-an-event-handler/SpecialForm.vb" id="5":::

    您可以藉由執行 [RemoveHandler 語句](../../../language-reference/statements/removehandler-statement.md)來中斷事件處理常式與事件之間的關聯。

## <a name="see-also"></a>另請參閱

- [程序](index.md)
- [Sub 程序](sub-procedures.md)
- [Sub 陳述式](../../../language-reference/statements/sub-statement.md)
- [AddressOf 運算子](../../../language-reference/operators/addressof-operator.md)
- [如何：建立程序](how-to-create-a-procedure.md)
- [如何：呼叫不傳回值的程序](how-to-call-a-procedure-that-does-not-return-a-value.md)
