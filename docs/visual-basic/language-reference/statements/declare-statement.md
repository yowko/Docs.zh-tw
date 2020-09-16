---
title: Declare Statement
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
ms.openlocfilehash: 8a5802583db53bfd0444ec9df0de9a0b9346d424
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90545515"
---
# <a name="declare-statement"></a>Declare Statement

宣告對外部檔案中所執行之程式的參考。

## <a name="syntax"></a>語法

```vb
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
|`attributelist`|選擇性。 請參閱 [屬性清單](attribute-list.md)。|
|`accessmodifier`|選擇性。 可以是下列其中一項：<br /><br /> -   [公共](../modifiers/public.md)<br />-   [保護](../modifiers/protected.md)<br />-   [朋友](../modifiers/friend.md)<br />-   [私人](../modifiers/private.md)<br />- [受保護的 Friend](../modifiers/protected-friend.md)<br />- [私用保護](../modifiers/private-protected.md)<br /><br /> 請參閱 [Visual Basic 中的存取層級](../../programming-guide/language-features/declared-elements/access-levels.md)。|
|`Shadows`|選擇性。 請參閱 [陰影](../modifiers/shadows.md)。|
|`charsetmodifier`|選擇性。 指定字元集和檔案搜尋資訊。 可以是下列其中一項：<br /><br /> -   [Ansi](../modifiers/ansi.md) (預設) <br />-   [Unicode](../modifiers/unicode.md)<br />-   [自動](../modifiers/auto.md)|
|`Sub`|選擇性，但 `Sub` `Function` 必須出現或。 指出外部程式不會傳回值。|
|`Function`|選擇性，但 `Sub` `Function` 必須出現或。 指出外部程式會傳回值。|
|`name`|必要。 此外部參考的名稱。 如需詳細資訊，請參閱宣告的 [元素名稱](../../programming-guide/language-features/declared-elements/declared-element-names.md)。|
|`Lib`|必要。 引進 `Lib` 子句，這個子句會識別包含外部程式 (DLL 或程式碼資源) 的外部檔案。|
|`libname`|必要。 包含已宣告之程式的檔案名。|
|`Alias`|選擇性。 指出所宣告的程式無法以中指定的名稱在其檔案內識別 `name` 。 您可以在中指定它的識別 `aliasname` 。|
|`aliasname`|如果您使用關鍵字，則為必要 `Alias` 。 以下列兩種方式之一來識別程式的字串：<br /><br /> 程式在其檔案內的進入點名稱，在引號內 (`""`) <br /><br /> -或-<br /><br /> 數位記號 (`#`) 後面接著一個整數，以指定程式在其檔案內的進入點序號|
|`parameterlist`|如果程式接受參數，則為必要。 請參閱 [參數清單](parameter-list.md)。|
|`returntype`|如果 `Function` 指定且為，則為必要項 `Option Strict` `On` 。 程式所傳回之值的資料類型。|

## <a name="remarks"></a>備註

有時候您需要呼叫檔案中定義的程式 (例如，DLL 或程式碼資源) 在專案之外。 當您這樣做時，Visual Basic 編譯器無法存取正確呼叫程式所需的資訊，例如程式所在位置、其識別方式、其呼叫順序和傳回型別，以及它所使用的字串字元集。 `Declare`語句會建立外部程式的參考，並提供必要的資訊。

您只能在模組層級使用 `Declare`。 這表示外部參考的宣告 *內容* 必須是類別、結構或模組，且不能是原始程式檔、命名空間、介面、程式或區塊。 如需詳細資訊，請參閱[宣告內容和預設存取層級](declaration-contexts-and-default-access-levels.md)。

外部參考預設為 [公開](../modifiers/public.md) 存取。 您可以使用存取修飾詞來調整其存取層級。

## <a name="rules"></a>規則

- **屬性。** 您可以將屬性套用至外部參考。 您套用的任何屬性只會在您的專案中生效，而不是在外部檔案中。

- **修飾 符。** 外部程式會隱含地 [共用](../modifiers/shared.md)。 您無法在宣告 `Shared` 外部參考時使用關鍵字，也無法改變其共用狀態。

  外部程式無法參與覆寫、執行介面成員或處理事件。 因此，您無法 `Overrides` `Overridable` `NotOverridable` 在語句中使用、、、、 `MustOverride` `Implements` 或 `Handles` 關鍵字 `Declare` 。

- **外部程式名稱。** 您不需要為此外部參考提供與) 中的相同名稱 (， `name` 如同其外部檔案 () 中程式的進入點名稱 `aliasname` 。 您可以使用 `Alias` 子句來指定進入點名稱。 如果外部程式與相同範圍內的 Visual Basic 保留的修飾詞或變數、程式或任何其他程式設計專案具有相同的名稱，這個方法會很有用。

  > [!NOTE]
  > 大部分 Dll 中的進入點名稱都會區分大小寫。

- **外部程式編號。** 或者，您可以使用 `Alias` 子句來指定外部檔案匯出資料表內進入點的序數。 若要這樣做，請從 `aliasname` 數位記號 (`#`) 開始。 如果 Visual Basic 中不允許外部程式名稱中的任何字元，或外部檔案匯出沒有名稱的程式，這個方法會很有用。

## <a name="data-type-rules"></a>資料類型規則

- **參數資料類型。** 如果 `Option Strict` 為 `On` ，則您必須在中指定每個參數的資料類型 `parameterlist` 。 這可以是任何資料類型，也可以是列舉、結構、類別或介面的名稱。 在中 `parameterlist` ，您可以使用 `As` 子句來指定要傳遞至每個參數之引數的資料類型。

  > [!NOTE]
  > 如果未針對 .NET Framework 撰寫外部程式，您必須注意資料類型是否對應。 例如，如果您在 Visual Basic 6.0) 中宣告具有參數 (16 位之 Visual Basic 6.0 程式的外部參考 `Integer` ，則必須在語句中識別對應的引數 `Short` `Declare` ，因為這是 Visual Basic 中的16位整數類型。 同樣地， `Long` 在 Visual Basic 6.0 中有不同的資料寬度，並 `Date` 以不同的方式執行。

- **傳回資料類型。** 如果外部程式是 `Function` `Option Strict` ，而且是 `On` ，您必須指定傳回給呼叫程式碼之值的資料類型。 這可以是任何資料類型，也可以是列舉、結構、類別或介面的名稱。

  > [!NOTE]
  > Visual Basic 編譯器不會驗證您的資料類型是否與外部程式相容。 如果有不相符的情況，則 common language runtime 會 <xref:System.Runtime.InteropServices.MarshalDirectiveException> 在執行時間產生例外狀況。

- **預設資料類型。** 如果 `Option Strict` 是， `Off` 而且您沒有在中指定參數的資料類型 `parameterlist` ，則 Visual Basic 編譯器會將對應的引數轉換成 [物件資料類型](../data-types/object-data-type.md)。 同樣地，如果您未指定 `returntype` ，編譯器會將傳回資料類型視為 `Object` 。

  > [!NOTE]
  > 因為您正在處理的外部程式可能是在不同的平臺上撰寫的，所以對資料類型的任何假設或允許其預設值是很危險的。 您可以更安全地指定每個參數的資料類型和傳回值（如果有的話）。 這也可提升程式碼的可讀性。

## <a name="behavior"></a>行為

- **範圍。** 外部參考在其所有類別、結構或模組的範圍內。

- **一生。** 外部參考的存留期與其宣告所在之類別、結構或模組的存留期相同。

- **呼叫外部程式。** 您可以使用呼叫或程式的相同方式來呼叫 `Function` 外部 `Sub` 程式，方法是在運算式傳回值時，或是在 [呼叫語句](call-statement.md) 中指定它（如果它不會傳回值）。

  您可以將引數傳遞給外部程式，完全如同 `parameterlist` 在語句中所指定 `Declare` 。 請勿考慮最初如何在外部檔案中宣告參數。 同樣地，如果有傳回值，請使用與語句中指定的完全相同的值 `returntype` `Declare` 。

- **字元集。** 您可以指定 `charsetmodifier` Visual Basic 在呼叫外部程式時，如何封送處理字串。 `Ansi`修飾詞會指示 Visual Basic 將所有字串封送處理成 ANSI 值，而 `Unicode` 修飾詞會將所有字串封送處理為 Unicode 值。 此 `Auto` 修飾詞會根據外部參考的 .NET Framework 規則 `name` 或指定，將 Visual Basic 導向封送處理字串 `aliasname` 。 預設值是 `Ansi`。

  `charsetmodifier` 此外也會指定 Visual Basic 應如何查詢外部檔案中的外部程式。 `Ansi` 而且 `Unicode` 直接 Visual Basic 在搜尋期間不修改其名稱即可查閱。 `Auto` 指示 Visual Basic 判斷執行時間平臺的基底字元集，並可能修改外部程式名稱，如下所示：

  - 在 ANSI 平臺上（例如 Windows 95、Windows 98 或 Windows Millennium Edition），請先查閱不修改名稱的外部程式。 如果失敗，請將 "A" 附加至外部程式名稱的結尾，然後重新查詢。

  - 在 Unicode 平臺上，例如 Windows NT、Windows 2000 或 Windows XP，請先查閱外部程式，而不修改名稱。 如果失敗，請將 "W" 附加至外部程式名稱的結尾，然後重新查詢。

- **機制。** Visual Basic 使用 .NET Framework *platform invoke* (PInvoke) 機制來解析和存取外部程式。 `Declare`語句和類別都會 <xref:System.Runtime.InteropServices.DllImportAttribute> 自動使用這項機制，而且您不需要任何 PInvoke 知識。 如需詳細資訊，請參閱 [逐步解說：呼叫 Windows api](../../programming-guide/com-interop/walkthrough-calling-windows-apis.md)。

> [!IMPORTANT]
> 如果外部程式是在 common language runtime (CLR) 之外執行，則它是未 *受管理*的程式碼。 當您呼叫這類程式（例如 Windows API 函式或 COM 方法）時，可能會讓應用程式暴露在安全性風險之下。 如需詳細資訊，請參閱 [非受控碼的安全程式碼撰寫方針](/previous-versions/dotnet/framework/security/secure-coding-guidelines-for-unmanaged-code)。

## <a name="example"></a>範例

下列範例會宣告傳回目前使用者名稱之程式的外部參考 `Function` 。 然後，它會在程式中呼叫外部程式 `GetUserNameA` `getUser` 。

[!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]

## <a name="example"></a>範例

<xref:System.Runtime.InteropServices.DllImportAttribute>提供在非受控程式碼中使用函式的替代方法。 下列範例會宣告已匯入的函式，而不使用 `Declare` 語句。

[!code-vb[VbVbalrStatements#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#16)]

[!code-vb[VbVbalrStatements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#1)]

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>
- [Imports 陳述式 (.NET 命名空間和類型)](imports-statement-net-namespace-and-type.md)
- [AddressOf 運算子](../operators/addressof-operator.md)
- [Function 陳述式](function-statement.md)
- [Sub 陳述式](sub-statement.md)
- [參數清單](parameter-list.md)
- [Call 陳述式](call-statement.md)
- [逐步解說：呼叫 Windows API](../../programming-guide/com-interop/walkthrough-calling-windows-apis.md)
