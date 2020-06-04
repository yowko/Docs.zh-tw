---
title: Handles 子句
ms.date: 07/20/2015
f1_keywords:
- Handles
- vb.Handles
helpviewer_keywords:
- Handles keyword [Visual Basic]
ms.assetid: 1b051c0e-f499-42f6-acb5-6f4f27824b40
ms.openlocfilehash: df786e4b0f0ab3795592ea57f7af17695b086cfa
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404572"
---
# <a name="handles-clause-visual-basic"></a>Handles 子句 (Visual Basic)
宣告程序會處理指定的事件。  
  
## <a name="syntax"></a>語法  
  
```vb  
proceduredeclaration Handles eventlist  
```  
  
## <a name="parts"></a>組件  
 `proceduredeclaration`  
 將會處理事件之程序的 `Sub` 程序宣告。  
  
 `eventlist`  
 要處理之 `proceduredeclaration` 的事件清單，以逗號分隔。 事件必須由目前類別的基底類別引發，或由使用 `WithEvents` 關鍵字宣告的物件引發。  
  
## <a name="remarks"></a>備註  
 在程序宣告結尾使用 `Handles` 關鍵字，讓它處理由使用 `WithEvents` 關鍵字宣告之物件變數引發的事件。 `Handles` 關鍵字也可以在衍生的類別中使用，以處理基底類別中的事件。  
  
 `Handles` 關鍵字和 `AddHandler` 陳述式都可以讓您指定由特定程序處理特定事件，但兩者存有差異。 當定義程序以指定它處理特定事件時，使用 `Handles` 關鍵字。 `AddHandler` 陳述式會在執行階段將程序連接到事件。 如需詳細資訊，請參閱[AddHandler 語句](addhandler-statement.md)。  
  
 對於自訂事件，當應用程式將程式新增為事件處理常式時，應用程式會叫用事件的 `AddHandler` 存取子。 如需自訂事件的詳細資訊，請參閱[Event 語句](event-statement.md)。  
  
## <a name="example"></a>範例  
 [!code-vb[VbVbalrEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#2)]  
  
 下列範例示範衍生的類別如何使用 `Handles` 陳述式來處理基底類別中的事件。  
  
 [!code-vb[VbVbalrEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#3)]  
  
## <a name="example"></a>範例  
 下列範例包含**WPF 應用程式**專案的兩個按鈕事件處理常式。  
  
 [!code-vb[VbVbalrEvents#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#41)]  
  
## <a name="example"></a>範例  
 下列範例等同於先前的範例。 `Handles` 子句中的 `eventlist` 包含兩個按鈕的事件。  
  
 [!code-vb[VbVbalrEvents#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#42)]  
  
## <a name="see-also"></a>另請參閱

- [WithEvents](../modifiers/withevents.md)
- [AddHandler 陳述式](addhandler-statement.md)
- [RemoveHandler 陳述式](removehandler-statement.md)
- [Event 陳述式](event-statement.md)
- [RaiseEvent 陳述式](raiseevent-statement.md)
- [事件](../../programming-guide/language-features/events/index.md)
