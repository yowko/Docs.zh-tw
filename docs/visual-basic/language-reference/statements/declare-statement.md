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
ms.openlocfilehash: 9895709076634ce156ba9d1009f79ba7ddd2ba56
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646375"
---
# <a name="declare-statement"></a>Declare Statement

聲明對外部文件中實現的過程的引用。

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
|`attributelist`|選擇性。 請參考[屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)。|
|`accessmodifier`|選擇性。 可以是下列其中一項：<br /><br /> -   [公共](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [保護](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [朋友](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [私人](../../../visual-basic/language-reference/modifiers/private.md)<br />- [受保護的好友](../../language-reference/modifiers/protected-friend.md)<br />- [私人保護](../../language-reference/modifiers/private-protected.md)<br /><br /> 請參考[視覺基礎 中的存取等級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。|
|`Shadows`|選擇性。 請參考[陰影](../../../visual-basic/language-reference/modifiers/shadows.md)。|
|`charsetmodifier`|選擇性。 指定字元集和檔搜索資訊。 可以是下列其中一項：<br /><br /> -   [安西](../../../visual-basic/language-reference/modifiers/ansi.md)(預設)<br />-   [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)<br />-   [自動](../../../visual-basic/language-reference/modifiers/auto.md)|
|`Sub`|可選,但必須`Sub``Function`顯示 或必須顯示。 指示外部過程不返回值。|
|`Function`|可選,但必須`Sub``Function`顯示 或必須顯示。 指示外部過程返回值。|
|`name`|必要。 此外部引用的名稱。 有關詳細資訊,請參閱[此名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。|
|`Lib`|必要。 引入一`Lib`個子句,用於標識包含外部過程的外部檔(DLL 或代碼資源)。|
|`libname`|必要。 包含聲明過程的檔的名稱。|
|`Alias`|選擇性。 指示無法通過`name`中 指定的名稱在其檔中標識正在聲明的過程。 在`aliasname`中 指定其標識。|
|`aliasname`|如果使用關鍵字,`Alias`則需要。 以兩種方式之一識別過程的字串:<br /><br /> 此檔案中的過程的入口點名稱, 在引號`""`( ) 內<br /><br /> -或-<br /><br /> 編號`#`( ), 後跟整數,指定程式在其檔案中的入口點的序號|
|`parameterlist`|如果過程採用參數,則為必填項。 請參考[參數清單](../../../visual-basic/language-reference/statements/parameter-list.md)。|
|`returntype`|如果指定`Function``Option Strict`並且`On`為 ,則為"必需" 過程返回的值的數據類型。|

## <a name="remarks"></a>備註

有時,您需要調用在專案外部的檔(如 DLL 或代碼資源)中定義的過程。 執行此操作時,Visual Basic 編譯器無法存取正確呼叫該過程所需的資訊,例如過程的位置、標識方式、其呼叫序列和返回類型以及它使用的字串字串集。 該`Declare`語句創建對外部過程的引用,並提供此必要的資訊。

您只能在模組層級使用 `Declare`。 這意味著外部引用*的聲明上下文*必須是類、結構或模組,不能是源檔、命名空間、介面、過程或塊。 如需詳細資訊，請參閱[宣告內容和預設存取層級](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。

外部引用預設為[公共](../../../visual-basic/language-reference/modifiers/public.md)訪問。 您可以使用訪問修改器調整其訪問級別。

## <a name="rules"></a>規則

- **屬性。** 您可以將屬性應用於外部引用。 應用的任何屬性僅在專案中生效,而在外部檔中無效。

- **修飾 符。** 外部程序隱式[共用](../../../visual-basic/language-reference/modifiers/shared.md)。 聲明外部引用時`Shared`不能使用關鍵字,也不能更改其共享狀態。

  外部過程不能參與重寫、實現介面成員或處理事件。 因此`Overrides`,您不能在`Overridable``NotOverridable``MustOverride``Implements``Handles`語句中使用、、、、、、、、、在語句中使用關鍵字。 `Declare`

- **外部過程名稱。** 您不需要為外部檔案 ( 中區端的`name`名稱 ) 中選擇此外部的名稱`aliasname`( in ) 。 可以使用子`Alias`句指定入口點名稱。 如果外部過程的名稱與 Visual Basic 保留修改器或變數、過程或同一作用域中的任何其他程式設計元素具有相同的名稱,則此功能非常有用。

  > [!NOTE]
  > 大多數 DLL 中的入口點名稱區分大小寫。

- **外部程式編號。** 或者,可以使用`Alias`子句指定外部檔匯出表中的入口點的批號。 為此,您從`aliasname`數位符號 (`#`開始。 如果在 Visual Basic 中不允許外部過程名稱中的任何字元,或者如果外部檔匯出沒有名稱的過程,則此功能非常有用。

## <a name="data-type-rules"></a>資料類型規則

- **參數數據類型。** 如果是`Option Strict``On`,則必須在`parameterlist`中指定每個參數的數據類型。 這可以是任何數據類型或枚舉、結構、類或介面的名稱。 在`parameterlist`中,`As`使用子句指定要傳遞給每個參數的參數的數據類型。

  > [!NOTE]
  > 如果未為 .NET 框架編寫外部過程,則必須注意數據類型是否對應。 例如,如果聲明外部引用 Visual Basic 6.0 過程具有`Integer`參數(Visual Basic 6.0 中的`Short``Declare`16 位元),則必須標識 語句中的相應參數,因為這是 Visual Basic 中的 16 位元整數類型。 同樣,Visual `Long` Basic 6.0 中的數據寬`Date`度也不同 ,並且實現方式不同。

- **返回數據類型。** 如果外部過程為`Function``Option Strict``On`和 ,則必須指定返回給調用代碼的值的數據類型。 這可以是任何數據類型或枚舉、結構、類或介面的名稱。

  > [!NOTE]
  > Visual Basic 編譯器不驗證數據類型是否與外部過程的類型相容。 如果不匹配,則通用語言運行時會在運行時生成<xref:System.Runtime.InteropServices.MarshalDirectiveException>異常。

- **默認數據類型。** 如果`Option Strict``Off`與 沒有指定`parameterlist`參數的資料型態,則 Visual Basic 編譯器會對參數轉換為[物件資料型態](../../../visual-basic/language-reference/data-types/object-data-type.md)。 同樣,如果不指定`returntype`,編譯器將傳回資料類型`Object`為 。

  > [!NOTE]
  > 由於您正在處理可能已寫入其他平臺上的外部過程,因此對數據類型進行任何假設或允許它們預設是危險的。 指定每個參數的數據類型和返回值(如果有)要安全得多。 這也提高了代碼的可讀性。

## <a name="behavior"></a>行為

- **範圍。** 外部引用在其類、結構或模組中處於作用域中。

- **一生。** 外部引用的存留期與聲明外部引用的類、結構或模組的存留期相同。

- **調用外部過程。** 調用外部過程的方式與調用`Function``Sub`或 過程的方式相同—,如果在表達式中返回值時使用它,或者在[調用語句](../../../visual-basic/language-reference/statements/call-statement.md)中指定它(如果它不返回值)。

  將參數傳遞給外部過程,完全按照`parameterlist``Declare`語句中指定的方式進行。 不考慮參數最初在外部檔中聲明的方式。 同樣,如果存在返回值,則完全按照 語句`returntype``Declare`中 指定的方式使用它。

- **字元集。** 您可以指定`charsetmodifier`Visual Basic 在呼叫外部過程時應如何封送字串。 修改`Ansi`器指示 Visual Basic 將所有字串封送到`Unicode`ANSI 值,修改器指示它將將所有字串封送到 Unicode 值。 修改`Auto`器指示 Visual Basic`name`根據基於外部引用的 .NET Framework`aliasname`規則對字串進行 封送,或者如果指定。 預設值是 `Ansi`。

  `charsetmodifier`還指定 Visual Basic 應如何查找其外部檔中的外部過程。 `Ansi`和`Unicode`直接視覺基本查找它,而無需修改其名稱在搜索期間。 `Auto`指示 Visual Basic 確定執行時平臺的基本字元集,並可能修改外部過程名稱,如下所示:

  - 在 ANSI 平臺上(如 Windows 95、Windows 98 或 Windows 千年版)上,首先查找外部過程,無需修改名稱。 如果失敗,將「A」追加到外部過程名稱的末尾,然後再次查找它。

  - 在 Unicode 平臺上(如 Windows NT、Windows 2000 或 Windows XP)上,首先查找外部過程,無需修改名稱。 如果失敗,將「W」追加到外部過程名稱的末尾,然後再次查找它。

- **機制。** Visual Basic 使用 .NET 框架*平台呼叫*(PInvoke) 機制解析和存取外部過程。 語句`Declare`<xref:System.Runtime.InteropServices.DllImportAttribute>和 類都自動使用此機制,您不需要任何 PInvoke 的知識。 有關詳細資訊,請參閱[演練:調用 Windows API](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)。

> [!IMPORTANT]
> 如果外部過程在通用語言執行時 (CLR) 之外執行,則它是*非託管代碼*。 調用此類過程(例如 Windows API 函數或 COM 方法)時,可能會使應用程式面臨安全風險。 有關詳細資訊,請參閱[非託管代碼的安全編碼準則](https://docs.microsoft.com/previous-versions/dotnet/framework/security/secure-coding-guidelines-for-unmanaged-code)。

## <a name="example"></a>範例

以下範例聲明對返回當前使用者名`Function`的過程的外部引用。 然後,它將外部過程`GetUserNameA`稱為該過程的`getUser`一部分。

[!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]

## <a name="example"></a>範例

提供了<xref:System.Runtime.InteropServices.DllImportAttribute>在非託管代碼中使用函數的替代方法。 下面的範例宣告匯入的函式而不使用敘述`Declare`。

[!code-vb[VbVbalrStatements#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#16)]

[!code-vb[VbVbalrStatements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#1)]

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>
- [Imports 陳述式 (.NET 命名空間和類型)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [AddressOf 運算子](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)
- [參數清單](../../../visual-basic/language-reference/statements/parameter-list.md)
- [Call 陳述式](../../../visual-basic/language-reference/statements/call-statement.md)
- [逐步解說：呼叫 Windows API](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
