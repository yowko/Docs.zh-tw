---
title: "Event 陳述式 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Event
- vb.Custom
dev_langs:
- VB
helpviewer_keywords:
- Event statement
- declaring events, syntax
- Public keyword, Event statements
- Custom keyword
- declarations, events
- event keyword [Visual Basic]
- WithEvents keyword, Event statements
- events [Visual Basic], declaring
- ByVal keyword, Event statements
- events [Visual Basic], custom
- ByRef keyword, Event statements
- declaring user-defined events
ms.assetid: 306ff8ed-74dd-4b6a-bd2f-e91b17474042
caps.latest.revision: 33
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b0ea8074f996622df3cd88a7e87fc1156b63dcaf
ms.lasthandoff: 03/13/2017

---
# <a name="event-statement"></a>Event 陳述式
宣告使用者定義的事件。  
  
## <a name="syntax"></a>語法  
  
```  
[ <attrlist> ] [ accessmodifier ] _  
[ Shared ] [ Shadows ] Event eventname[(parameterlist)] _  
[ Implements implementslist ]  
' -or-  
[ <attrlist> ] [ accessmodifier ] _  
[ Shared ] [ Shadows ] Event eventname As delegatename _  
[ Implements implementslist ]  
' -or-  
 [ <attrlist> ] [ accessmodifier ] _  
[ Shared ] [ Shadows ] Custom Event eventname As delegatename _  
[ Implements implementslist ]  
   [ <attrlist> ] AddHandler(ByVal value As delegatename)  
      [ statements ]  
   End AddHandler  
   [ <attrlist> ] RemoveHandler(ByVal value As delegatename)  
      [ statements ]  
   End RemoveHandler  
   [ <attrlist> ] RaiseEvent(delegatesignature)  
      [ statements ]  
   End RaiseEvent  
End Event  
```  
  
## <a name="parts"></a>組件  
  
|組件|描述|  
|---|---|  
|`attrlist`|選擇項。 套用至此事件的屬性清單。 以逗號分隔多個屬性。 您必須將[屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)角括弧括住 (「`<`"和"`>`")。|  
|`accessmodifier`|選擇項。 指定哪些程式碼可以存取此事件。 可以是下列其中一項：<br /><br /> -   [公用](../../../visual-basic/language-reference/modifiers/public.md)— 可以存取的項目宣告它的任何程式碼可以存取它。<br />-   [受保護的](../../../visual-basic/language-reference/modifiers/protected.md)— 只有在其類別或衍生的類別中的程式碼可以存取它。<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)— 只有在相同的組件中的程式碼可以存取它。<br />-   [私用](../../../visual-basic/language-reference/modifiers/private.md)— 會將其宣告的項目中的程式碼可以存取它。<br /><br /> 您可以指定 `Protected Friend` 以存取事件類別、衍生類別或相同組件中的程式碼。|  
|`Shared`|選擇項。 指定此事件與類別或結構的特定執行個體不相關。|  
|`Shadows`|選擇項。 指出這個事件會在基底類別中重新宣告並隱藏相同名稱的程式設計項目，或一組多載項目。 您可以使用任何其他類型遮蔽任何一種已宣告的項目。<br /><br /> 無法從遮蔽項目的衍生類別內使用遮蔽的項目，除了從無法存取遮蔽項目的位置以外。 例如，如果 `Private` 項目會遮蔽基底類別項目，沒有 `Private` 項目存取權限的程式碼會改為存取基底類別項目。|  
|`eventname`|必要項。 事件的名稱；依照標準變數命名慣例。|  
|`parameterlist`|選擇項。 本機變數清單，表示此事件的參數。 您必須將[參數清單](../../../visual-basic/language-reference/statements/parameter-list.md)括號括住。|  
|`Implements`|選擇項。 指出此事件會實作介面的事件。|  
|`implementslist`|如果使用 `Implements`，則為必要項。 實作之 `Sub` 程序的清單。 以逗號分隔多個程序：<br /><br /> *implementedprocedure* [， *implementedprocedure* ...]<br /><br /> 每個 `implementedprocedure` 都具有下列語法和組件：<br /><br /> `interface`.`definedname`<br /><br /> -   `interface`-必要。 介面名稱，該介面實作包含類別或結構的此程序。<br />-   `Definedname`-必要。 名稱，據以在 `interface` 中定義程序。 不一定要與 `name` 相同，這是此程序用來實作已定義程序的名稱。|  
|`Custom`|必要項。 事件宣告為 `Custom` 必須定義自訂 `AddHandler`、`RemoveHandler` 和 `RaiseEvent` 存取子。|  
|`delegatename`|選擇項。 委派的名稱，指定事件處理常式簽章。|  
|`AddHandler`|必要項。 宣告 `AddHandler` 存取子，指定加入事件處理常式時要執行的陳述式，可以明確地使用 `AddHandler` 陳述式或隱含地使用 `Handles` 子句。|  
|`End AddHandler`|必要項。 終止 `AddHandler` 區塊。|  
|`value`|必要項。 參數名稱。|  
|`RemoveHandler`|必要項。 宣告 `RemoveHandler` 存取子，指定使用 `RemoveHandler` 陳述式移除事件處理常式時要執行的陳述式。|  
|`End RemoveHandler`|必要項。 終止 `RemoveHandler` 區塊。|  
|`RaiseEvent`|必要項。 宣告 `RaiseEvent` 存取子，指定使用 `RaiseEvent` 陳述式引發事件處理常式時要執行的陳述式。 一般而言，這樣會叫用 `AddHandler` 和 `RemoveHandler` 存取子所維護的委派。|  
|`End RaiseEvent`|必要項。 終止 `RaiseEvent` 區塊。|  
|`delegatesignature`|必要項。 參數的清單，符合 `delegatename` 委派所需的參數。 您必須將[參數清單](../../../visual-basic/language-reference/statements/parameter-list.md)括號括住。|  
|`statements`|選擇項。 陳述式，包含 `AddHandler`、`RemoveHandler` 和 `RaiseEvent` 方法的內文。|  
|`End Event`|必要項。 終止 `Event` 區塊。|  
  
## <a name="remarks"></a>備註  
 一旦已經宣告事件，使用 `RaiseEvent` 陳述式來引發事件。 一般事件可能會如下列片段所示宣告和引發：  
  
 [!code-vb[VbVbalrEvents #&13;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/event-statement_1.vb)]  
  
> [!NOTE]
>  您可以宣告事件引數，就像宣告程序的引數一樣，但下列情況除外：事件不可擁有具名引數、`ParamArray` 引數或 `Optional` 引數。 事件沒有傳回值。  
  
 若要處理事件，您必須使用 `Handles` 或 `AddHandler` 陳述式，建立它與事件處理常式副程式的關聯。 副程式與事件的簽章必須相符。 若要處理共用的事件，您必須使用 `AddHandler` 陳述式。  
  
 您只能在模組層級使用 `Event`。 這表示*宣告內容*事件必須是類別、 結構、 模組或介面，而且不能是原始程式檔、 命名空間、 程序或區塊。 如需詳細資訊，請參閱[宣告內容和預設存取層級](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。  
  
 在大部分情況下，您可以使用本主題「語法」一節中的第一個語法來宣告事件。 不過，某些情況下需要您對詳細事件行為有更多掌控。 本主題中「語法」一節中的最後一個語法使用 `Custom` 關鍵字，藉由讓您定義自訂事件以提供控制權。 在自訂事件中，您完整指定當程式碼於事件中加入或移除事件處理常式，或是當程式碼引發事件時，會發生什麼情況。 如需範例，請參閱[如何︰ 宣告自訂事件以節省記憶體](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)和[如何︰ 宣告自訂事件以避免封鎖](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用事件以從 10 秒到 0 秒倒數計時。 程式碼會說明數個事件相關的方法、屬性和陳述式。 包括 `RaiseEvent` 陳述式。  
  
 引發事件的類別是事件來源，處理事件的方法為事件處理常式。 事件來源對於它所產生的事件可以有多個處理常式。 當類別引發事件時，該事件是在每個類別 (已被選擇來處理該物件執行個體的事件) 上引發。  
  
 此範例也會使用表單 (`Form1`) 與按鈕 (`Button1`) 和文字方塊 (`TextBox1`)。 當您按一下按鈕時時，第一個文字方塊會顯示從 10 秒到 0 秒的倒數計時。 在經過完整時間 (10 秒) 之後，第一個文字方塊會顯示 [完成]。  
  
 `Form1` 的程式碼會指定表單的初始和終止狀態。 它也包含引發事件時執行的程式碼。  
  
 若要使用此範例，請建立新的 Windows Form 專案。 然後新增一個名為 `Button1` 的按鈕，和名為 `TextBox1` 的文字方塊到名為 `Form1` 的主表單中。 然後以滑鼠右鍵按一下表單，並按一下 **檢視程式碼**開啟程式碼編輯器。  
  
 將 `WithEvents` 變數加入至 `Form1` 類別的宣告區段：  
  
 [!code-vb[VbVbalrEvents #&14;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/event-statement_2.vb)]  
  
 將下列程式碼加入至 `Form1` 的程式碼。 取代可能存在的任何重複程序，例如 `Form_Load` 或 `Button_Click`。  
  
 [!code-vb[VbVbalrEvents #&15;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/event-statement_3.vb)]  
  
 按 F5 以執行上述範例中，並按一下 按鈕**啟動**。 第一個文字方塊會開始倒數計時。 在經過完整時間 (10 秒) 之後，第一個文字方塊會顯示 [完成]。  
  
> [!NOTE]
>  `My.Application.DoEvents` 方法不會以與表單相同的方式處理事件。 若要啟用表單以直接處理事件，您可以使用多執行緒。 如需詳細資訊，請參閱[執行緒](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c)。  
  
## <a name="see-also"></a>另請參閱  
 [RaiseEvent 陳述式](../../../visual-basic/language-reference/statements/raiseevent-statement.md)   
 [Implements 陳述式](../../../visual-basic/language-reference/statements/implements-statement.md)   
 [事件](../../../visual-basic/programming-guide/language-features/events/index.md)   
 [AddHandler 陳述式](../../../visual-basic/language-reference/statements/addhandler-statement.md)   
 [RemoveHandler 陳述式](../../../visual-basic/language-reference/statements/removehandler-statement.md)   
 [控制代碼](../../../visual-basic/language-reference/statements/handles-clause.md)   
 [Delegate 陳述式](../../../visual-basic/language-reference/statements/delegate-statement.md)   
 [如何︰ 宣告自訂事件以節省記憶體](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)   
 [如何︰ 宣告自訂事件以避免封鎖](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)   
 [共用](../../../visual-basic/language-reference/modifiers/shared.md)   
 [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)
