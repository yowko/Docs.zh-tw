---
title: Declare 陳述式 (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 343ee168809fc63ef63559eda0fd018abde684e7
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2018
ms.locfileid: "43485738"
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
|`attributelist`|選擇性。 請參閱[屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)。|  
|`accessmodifier`|選擇性。 可以是下列其中一項：<br /><br /> -   [公用](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [受保護](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [私用](../../../visual-basic/language-reference/modifiers/private.md)<br />- [為 protected 的 Friend](../../language-reference/modifiers/protected-friend.md)<br />- [受保護的私用](../../language-reference/modifiers/private-protected.md)<br /><br /> 請參閱[存取 Visual Basic 中的層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。|  
|`Shadows`|選擇性。 請參閱[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)。|  
|`charsetmodifier`|選擇性。 指定 字元集和檔案搜尋的資訊。 可以是下列其中一項：<br /><br /> -   [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md) （預設值）<br />-   [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)<br />-   [自動](../../../visual-basic/language-reference/modifiers/auto.md)|  
|`Sub`|選擇性，但是`Sub`或`Function`必須出現。 表示外部程序不會傳回值。|  
|`Function`|選擇性，但是`Sub`或`Function`必須出現。 表示外部程序傳回值。|  
|`name`|必要。 這個外部參考的名稱。 如需詳細資訊，請參閱 <<c0> [ 宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。|  
|`Lib`|必要。 導入了`Lib`子句可識別包含外部程序的外部檔案 （DLL 或程式碼的資源）。|  
|`libname`|必要。 包含宣告的程序的檔案名稱。|  
|`Alias`|選擇性。 表示所宣告的程序無法識別其檔案內，名稱中指定`name`。 指定在其識別`aliasname`。|  
|`aliasname`|如果您使用所需`Alias`關鍵字。 字串，識別下列其中一種程序：<br /><br /> 在其檔案中，括在引號內的程序的進入點名稱 (`""`)<br /><br /> -或-<br /><br /> 數字符號 (`#`) 後面接著一個整數，指定其檔案中的程序的進入點的序號|  
|`parameterlist`|所需的程序如果接受參數。 請參閱[參數清單](../../../visual-basic/language-reference/statements/parameter-list.md)。|  
|`returntype`|需要`Function`指定並`Option Strict`是`On`。 此程序所傳回之值的資料型別。|  
  
## <a name="remarks"></a>備註  
 有時候您需要呼叫中的檔案 （如 DLL 或程式碼的資源） 在專案以外定義的程序。 當您這樣做時，Visual Basic 編譯器並沒有存取還需要正確地呼叫程序的資訊，例如程序所在的位置、 其識別方式、 其呼叫的順序傳回型別和字串字元組，它會使用。 `Declare`陳述式會建立外部程序的參考，並提供這些必要的資訊。  
  
 您只能在模組層級使用 `Declare`。 這表示*宣告內容*外部參考必須是類別、 結構或模組，而且不能是原始程式檔、 命名空間、 介面、 程序或區塊。 如需詳細資訊，請參閱[宣告內容和預設存取層級](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。  
  
 外部參考的預設[公開](../../../visual-basic/language-reference/modifiers/public.md)存取。 您可以調整它們的存取層級，使用存取修飾詞。  
  
## <a name="rules"></a>規則  
  
-   **屬性。** 您可以將屬性套用至外部參考。 只在您的專案中，在外部檔案中，您將套用的任何屬性才有效果。  
  
-   **修飾詞。** 外部程序都是隱含[共用](../../../visual-basic/language-reference/modifiers/shared.md)。 您無法使用`Shared`關鍵字宣告的外部參考，而且您無法變更其共用的狀態。  
  
     外部程序不能參與覆寫、 實作介面成員，或處理事件。 因此，您無法使用`Overrides`， `Overridable`， `NotOverridable`， `MustOverride`， `Implements`，或`Handles`關鍵字`Declare`陳述式。  
  
-   **外部程序名稱。** 您沒有提供這個外部參考相同的名稱 (在`name`) 做為其外部檔案中的程序的進入點名稱 (`aliasname`)。 您可以使用`Alias`子句，以指定進入點名稱。 這可以是很有用，如果外部的程序與 Visual Basic 保留修飾詞、 變數、 程序或任何其他程式設計項目相同的名稱相同的範圍中。  
  
    > [!NOTE]
    >  在大部分的 Dll 中的進入點名稱會區分大小寫。  
  
-   **外部程序數目。** 或者，您可以使用`Alias`子句來指定外部檔案中匯出資料表中的進入點的序號。 若要這樣做，請先`aliasname`井字號 (`#`)。 如果在 Visual Basic 中不允許外部程序名稱中的任何字元，或外部檔案匯出不含名稱的程序，這非常有用。  
  
## <a name="data-type-rules"></a>資料型別規則  
  
-   **參數資料類型。** 如果`Option Strict`已`On`，您必須指定每個參數中的資料型別`parameterlist`。 這可以是任何資料類型或列舉、 結構、 類別或介面的名稱。 內`parameterlist`，您使用`As`子句來指定要傳遞至每個參數的引數的資料類型。  
  
    > [!NOTE]
    >  如果外部的程序不針對.NET Framework 撰寫的您必須小心的資料類型對應。 比方說，如果您宣告的外部參考到 Visual Basic 6.0 程序`Integer`參數 （16 位元 Visual Basic 6.0 中），您必須識別相對應的引數當做`Short`中`Declare`陳述式，因為這是 16-在 Visual Basic 中的位元整數類型。 同樣地，`Long`在 Visual Basic 6.0 中，會有不同的資料寬度和`Date`的實作方式不同。  
  
-   **傳回資料類型。** 如果外部程序`Function`並`Option Strict`是`On`，您必須指定值傳回給呼叫程式碼的資料類型。 這可以是任何資料類型或列舉、 結構、 類別或介面的名稱。  
  
    > [!NOTE]
    >  Visual Basic 編譯器不會驗證您的資料類型是相容的外部程序。 如果不相符，就會產生 common language runtime<xref:System.Runtime.InteropServices.MarshalDirectiveException>在執行階段的例外狀況。  
  
-   **預設資料類型。** 如果`Option Strict`已`Off`且未指定資料類型中的參數`parameterlist`，Visual Basic 編譯器會將轉換的對應引數[Object 資料型別](../../../visual-basic/language-reference/data-types/object-data-type.md)。 同樣地，如果您未指定`returntype`，編譯器會採用要傳回的資料型別`Object`。  
  
    > [!NOTE]
    >  因為您正在處理可能在不同的平台上寫入的外部程序，是很危險做出任何假設資料類型，或允許其為預設值。 如果有的話，它是較為安全，以指定的每個參數和傳回值，資料型別。 這也可改善程式碼的可讀性。  
  
## <a name="behavior"></a>行為  
  
-   **範圍。** 外部參考都會在範圍中其類別、 結構或模組。  
  
-   **存留期。** 外部參考具有相同的存留期，為類別、 結構或宣告它的模組。  
  
-   **呼叫外部程序。** 您呼叫外部程序呼叫的相同方式`Function`或`Sub`程序，使用運算式中，如果它的傳回值，或藉由指定在[Call 陳述式](../../../visual-basic/language-reference/statements/call-statement.md)如果它不會傳回值。  
  
     您將引數傳遞至所指定的完全相同的外部程序`parameterlist`在`Declare`陳述式。 才會考慮參數原本宣告方式在外部檔案中。 同樣地，如果沒有傳回值，使用它所指定的完全相同`returntype`在`Declare`陳述式。  
  
-   **字元集。** 您可以指定`charsetmodifier`如何 Visual Basic 應封送處理字串時，它會呼叫外部程序。 `Ansi`修飾詞會指示 Visual Basic 來封送處理為 ANSI 值的所有字串和`Unicode`修飾詞會指示它封送都處理為 Unicode 值的所有字串。 `Auto`修飾詞會指示 Visual Basic，根據.NET Framework 的封送處理字串以規則為基礎的外部參考`name`，或`aliasname`如果指定。 預設值是 `Ansi`。  
  
     `charsetmodifier` 也會指定 Visual Basic 外部的程序，其外部檔案中所呈現的外觀。 `Ansi` 和`Unicode`兩者都直接 Visual Basic，以查閱而不需要在搜尋期間修改它的名稱。 `Auto` 會指示 Visual Basic，以判斷執行階段平台的基底字元集，並可能修改外部程序名稱，如下所示：  
  
    -   ANSI 平台，例如 Windows 95、 Windows 98 或 Windows Millennium Edition 上第一次查閱外部的程序，與未修改的名稱。 如果失敗，將"A"附加至外部程序名稱的結尾，並一次查閱。  
  
    -   在 Unicode 平台，例如 Windows NT、 Windows 2000 或 Windows XP 上第一次查閱外部的程序，與未修改的名稱。 如果失敗，附加"W"結尾的外部程序的名稱，並重新查閱。  
  
-   **機制。** Visual Basic 會使用.NET Framework*平台叫用*(PInvoke) 解析及存取外部程序的機制。 `Declare`陳述式和<xref:System.Runtime.InteropServices.DllImportAttribute>這兩個類別會自動使用這項機制並不需要任何 PInvoke 的知識。 如需詳細資訊，請參閱 <<c0> [ 逐步解說： 呼叫 Windows Api](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)。  
  
> [!IMPORTANT]
>  如果外部的程序執行 common language runtime (CLR) 外部，就*unmanaged 程式碼*。 當您呼叫這類的程序，例如 Win32 API 函式或 COM 方法，您可能會公開您的應用程式的安全性風險。 如需詳細資訊，請參閱 < [Unmanaged 程式碼的安全程式碼撰寫指導方針](../../../framework/security/secure-coding-guidelines-for-unmanaged-code.md)。  
  
## <a name="example"></a>範例  
 下列範例宣告的外部參考`Function`傳回目前的使用者名稱的程序。 然後它會呼叫外部程序`GetUserNameA`一部分`getUser`程序。  
  
 [!code-vb[VbVbalrStatements#15](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/declare-statement_1.vb)]  
  
## <a name="example"></a>範例  
 <xref:System.Runtime.InteropServices.DllImportAttribute>提供的 unmanaged 程式碼中使用函式的替代方式。 下列範例會宣告匯入的函式，而不需使用`Declare`陳述式。  
  
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
