---
title: Declare Statement
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Declare
- vb.Lib
- vb.Any
helpviewer_keywords:
- Lib keyword [Visual Basic]
- declaring procedures [Visual Basic], Declare statement
- functions [Visual Basic], function procedures
- declarations [Visual Basic], procedures
- procedures [Visual Basic], declaration
- procedures [Visual Basic], external
- Alias keyword [Visual Basic]
- external references [Visual Basic], Visual Basic
- DLLs, declaring procedures
- Declare statement [Visual Basic]
- declarations [Visual Basic], external
- Visual Basic code, Function procedures
- As keyword [Visual Basic], in Declare statement
- resources [Visual Basic], declaring
- Public keyword [Visual Basic], Declare statement
- platform invoke, Visual Basic external references
- Sub procedures [Visual Basic], declarations
- APIs, declaring API functions
- Visual Basic code, Sub procedures
- Function procedures [Visual Basic], declaring
ms.assetid: d3f21fb0-b804-4c99-97ed-583b23894cf1
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2560f34a5130ef7453b50ffb4495b67bf1dfa4c8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="declare-statement"></a>Declare Statement
宣告實作的外部檔案中的程序的參考。  
  
## <a name="syntax"></a>語法  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ Overloads ] _  
Declare [ charsetmodifier ] [ Sub ] name Lib "libname" _  
[ Alias "aliasname" ] [ ([ parameterlist ]) ]  
' -or-  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ Overloads ] _  
Declare [ charsetmodifier ] [ Function ] name Lib "libname" _  
[ Alias "aliasname" ] [ ([ parameterlist ]) ] [ As returntype ]  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`attributelist`|選擇項。 請參閱[屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)。|  
|`accessmodifier`|選擇項。 可以是下列其中一項：<br /><br /> -   [公用](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [受保護](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [私用](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> 請參閱[存取 Visual Basic 中的層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。|  
|`Shadows`|選擇項。 請參閱[陰影](../../../visual-basic/language-reference/modifiers/shadows.md)。|  
|`charsetmodifier`|選擇項。 指定字元集和檔案資訊中搜尋。 可以是下列其中一項：<br /><br /> -   [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md) （預設值）<br />-   [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)<br />-   [自動](../../../visual-basic/language-reference/modifiers/auto.md)|  
|`Sub`|選擇性，但請`Sub`或`Function`必須出現。 表示外部程序不會傳回值。|  
|`Function`|選擇性，但請`Sub`或`Function`必須出現。 表示外部程序傳回值。|  
|`name`|必要項。 這個外部參考的名稱。 如需詳細資訊，請參閱[宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。|  
|`Lib`|必要項。 導入了`Lib`子句，用來識別包含外部程序的外部檔案 （DLL 或程式碼資源）。|  
|`libname`|必要項。 包含宣告的程序的檔案名稱。|  
|`Alias`|選擇項。 指出所宣告的程序無法識別其檔案內，名稱中指定`name`。 指定在其識別`aliasname`。|  
|`aliasname`|如果您使用所需`Alias`關鍵字。 識別在其中一種程序的字串：<br /><br /> 在其檔案中，括在引號內的程序的進入點名稱 (`""`)<br /><br /> -或-<br /><br /> 數字符號 (`#`) 後面接著整數，指定其檔案中的程序的進入點的序號|  
|`parameterlist`|所需的程序如果使用參數。 請參閱[參數清單](../../../visual-basic/language-reference/statements/parameter-list.md)。|  
|`returntype`|若`Function`指定和`Option Strict`是`On`。 此程序所傳回之值的資料類型。|  
  
## <a name="remarks"></a>備註  
 有時候您需要呼叫您的專案之外的檔案 （例如 DLL 或程式碼的資源） 中定義的程序。 當您這樣做時，Visual Basic 編譯器並沒有存取它需要正確地呼叫程序的資訊，例如程序所在的位置、 如何識別、 其呼叫的順序和傳回型別，它會使用字串字元組。 `Declare`陳述式會建立外部程序的參考，並提供此必要資訊。  
  
 您只能在模組層級使用 `Declare`。 這表示*宣告內容*外部參考必須是類別、 結構或模組，並且不能是原始程式檔、 命名空間、 介面、 程序或區塊。 如需詳細資訊，請參閱[宣告內容和預設存取層級](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。  
  
 外部參考預設為[公用](../../../visual-basic/language-reference/modifiers/public.md)存取。 您可以調整其存取層級，使用存取修飾詞。  
  
## <a name="rules"></a>規則  
  
-   **屬性。** 您可以將屬性套用到外部參考。 只有在您的專案，在外部檔案中，任何您所套用的屬性才有效果。  
  
-   **修飾詞。** 外部程序會以隱含方式[共用](../../../visual-basic/language-reference/modifiers/shared.md)。 您無法使用`Shared`關鍵字宣告的外部參考，而且您無法變更其共用的狀態時。  
  
     外部程序不能參與覆寫、 實作介面成員，或處理的事件。 因此，您不能使用`Overrides`， `Overridable`， `NotOverridable`， `MustOverride`， `Implements`，或`Handles`關鍵字`Declare`陳述式。  
  
-   **外部程序名稱。** 您沒有提供這個外部參考相同的名稱 (在`name`) 做為其外部檔案中的程序的進入點名稱 (`aliasname`)。 您可以使用`Alias`子句來指定進入點名稱。 這可以是外部程序有相同的名稱，在 Visual Basic 保留修飾詞、 變數、 程序或任何其他程式設計項目的相同範圍中很有用。  
  
    > [!NOTE]
    >  大部分 Dll 中的進入點名稱不區分大小寫。  
  
-   **外部程序數目。** 或者，您可以使用`Alias`子句來指定外部檔案的進入點的匯出資料表內的序號。 若要這樣做，首先請`aliasname`以 number sign (`#`)。 這可以是很有用，如果在 Visual Basic 中不允許外部程序名稱中的任何字元，或外部檔案匯出不含名稱的程序。  
  
## <a name="data-type-rules"></a>資料類型的規則  
  
-   **參數資料類型。** 如果`Option Strict`是`On`，您必須指定每個參數中的資料型別`parameterlist`。 這可以是任何資料類型或列舉、 結構、 類別或介面的名稱。 內`parameterlist`，您使用`As`子句來指定要傳遞給每個參數的引數的資料類型。  
  
    > [!NOTE]
    >  如果不適用於.NET Framework 所撰寫外部的程序，您必須特別注意，資料類型對應。 例如，如果您宣告的 Visual Basic 6.0 程序的外部參考`Integer`參數 （16 位元 Visual Basic 6.0 中），您必須識別相對應的引數做`Short`中`Declare`陳述式，因為這是 16-在 Visual Basic 中的位元整數類型。 同樣地， `Long` Visual Basic 6.0 中都有不同的資料寬度和`Date`的實作方式不同。  
  
-   **傳回的資料類型。** 如果外部程序是`Function`和`Option Strict`是`On`，您必須指定傳回呼叫程式碼的值的資料類型。 這可以是任何資料類型或列舉、 結構、 類別或介面的名稱。  
  
    > [!NOTE]
    >  Visual Basic 編譯器不會驗證您的資料類型會與外部程序相容。 如果不相符，就會產生 common language runtime<xref:System.Runtime.InteropServices.MarshalDirectiveException>在執行階段的例外狀況。  
  
-   **預設資料類型。** 如果`Option Strict`是`Off`且未指定的參數中的資料型別`parameterlist`，Visual Basic 編譯器會將轉換的對應引數[物件資料類型](../../../visual-basic/language-reference/data-types/object-data-type.md)。 同樣地，如果您未指定`returntype`，編譯器會採用要傳回的資料類型`Object`。  
  
    > [!NOTE]
    >  因為您正在處理可能在不同的平台上撰寫外部程序，是很危險提出任何假設資料型別，或允許這些預設值。 如果有的話，它會比較安全指定每一個參數和傳回值的資料類型。 這也會改善程式碼的可讀性。  
  
## <a name="behavior"></a>行為  
  
-   **範圍。** 外部參考都會在範圍中的類別、 結構或模組。  
  
-   **存留期。** 外部參考具有相同的存留期為類別、 結構或模組宣告它。  
  
-   **呼叫外部程序。** 呼叫外部程序相同的方式，您呼叫`Function`或`Sub`程序，藉由使用運算式中，如果它傳回的值，或指定在[Call 陳述式](../../../visual-basic/language-reference/statements/call-statement.md)如果它不會傳回值。  
  
     您將引數傳遞至所指定的完全相同的外部程序`parameterlist`中`Declare`陳述式。 不考慮到帳戶如何參數原本宣告外部檔案中。 同樣地，如果沒有傳回值，使用它所指定的完全相同`returntype`中`Declare`陳述式。  
  
-   **字元集。** 您可以指定在`charsetmodifier`如何 Visual Basic 應封送處理字串時，它會呼叫外部程序。 `Ansi`修飾詞會指示 Visual Basic 來封送處理成 ANSI 值，所有字串和`Unicode`修飾詞會將其導向封送處理為 Unicode 值的所有字串。 `Auto`修飾詞會指示 Visual Basic 根據.NET Framework 的封送處理字串規則根據外部參考`name`，或`aliasname`如果指定。 預設值是 `Ansi`。  
  
     `charsetmodifier`也會指定 Visual Basic 應如何查詢其外部檔案內的外部程序。 `Ansi`和`Unicode`兩者都直接 Visual Basic 而不需在搜尋期間修改其名稱查閱。 `Auto`會指示 Visual Basic 來判斷執行階段平台的基底字元集，並可能修改外部程序名稱，如下所示：  
  
    -   ANSI 平台上，例如 Windows 95、 Windows 98 或 Windows Millennium Edition、 先尋找具有任何名稱修改的外部程序。 如果失敗，將外部程序名稱的結尾附加"A"，並再次進行查閱。  
  
    -   Unicode 平台上，例如 Windows NT、 Windows 2000 或 Windows XP 中，先尋找具有任何名稱修改的外部程序。 如果失敗，附加"W"結尾的外部程序的名稱，並再次進行查閱。  
  
-   **機制。** Visual Basic 會使用.NET Framework*平台叫用*(PInvoke) 機制來解析和存取外部程序。 `Declare`陳述式和<xref:System.Runtime.InteropServices.DllImportAttribute>這兩個類別，自動使用這項機制，您不需要知道 PInvoke。 如需詳細資訊，請參閱[逐步解說： 呼叫 Windows Api](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)。  
  
> [!IMPORTANT]
>  如果外部程序執行 common language runtime (CLR) 外部，它是*unmanaged 程式碼*。 當您呼叫這類程序，例如 Win32 API 函式或 COM 方法中，您可能會公開您的應用程式的安全性風險。 如需詳細資訊，請參閱[Unmanaged 程式碼的安全程式碼撰寫指導方針](../../../framework/security/secure-coding-guidelines-for-unmanaged-code.md)。  
  
## <a name="example"></a>範例  
 下列範例宣告的外部參考`Function`程序，傳回目前使用者的名稱。 然後它會呼叫外部程序`GetUserNameA`一部分`getUser`程序。  
  
 [!code-vb[VbVbalrStatements#15](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/declare-statement_1.vb)]  
  
## <a name="example"></a>範例  
 <xref:System.Runtime.InteropServices.DllImportAttribute>提供在 unmanaged 程式碼中使用函式的替代方式。 下列範例會宣告匯入的函式而不使用`Declare`陳述式。  
  
 [!code-vb[VbVbalrStatements#16](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/declare-statement_2.vb)]  
  
 [!code-vb[VbVbalrStatements#1](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/declare-statement_3.vb)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>  
 [Imports 陳述式 (.NET 命名空間和類型)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [AddressOf 運算子](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [參數清單](../../../visual-basic/language-reference/statements/parameter-list.md)  
 [Call 陳述式](../../../visual-basic/language-reference/statements/call-statement.md)  
 [逐步解說：呼叫 Windows API](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
