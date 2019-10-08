---
title: 疑難排解程式（Visual Basic）
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting Visual Basic, procedures
- procedures [Visual Basic], troubleshooting
- Visual Basic code, procedures
- troubleshooting procedures
- procedures [Visual Basic], about procedures
ms.assetid: 525721e8-2e02-4f75-b5d8-6b893462cf2b
ms.openlocfilehash: c74947e21de8ba26ffde01f6f28aea67346c2071
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002071"
---
# <a name="troubleshooting-procedures-visual-basic"></a>疑難排解程式（Visual Basic）

此頁面會列出使用程式時可能發生的一些常見問題。  
  
## <a name="returning-an-array-type-from-a-function-procedure"></a>從函數程式傳回陣列型別

如果 `Function` 程式傳回陣列資料類型，您就不能使用 `Function` 名稱來儲存陣列元素中的值。 如果您嘗試這麼做，編譯器會將它解釋為 `Function` 的呼叫。 下列範例會產生編譯器錯誤：
  
```vb
Function AllOnes(n As Integer) As Integer()
   For i As Integer = 1 To n - 1  
      ' The following statement generates a COMPILER ERROR.  
      AllOnes(i) = 1  
   Next  

   ' The following statement generates a COMPILER ERROR.  
   Return AllOnes()  
End Function
```

語句 `AllOnes(i) = 1` 會產生編譯器錯誤，因為它似乎是以錯誤資料類型的引數呼叫 `AllOnes` （純量 `Integer`，而不是 `Integer` 陣列）。 @No__t-0 的語句會產生編譯器錯誤，因為它似乎沒有引數呼叫 `AllOnes`。  
  
 **正確的方法：** 若要能夠修改要傳回之陣列的元素，請將內部陣列定義為本機變數。 下列範例會編譯而不會發生錯誤：

 [!code-vb[VbVbcnProcedures#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#66)]

## <a name="argument-not-modified-by-procedure-call"></a>程序呼叫未修改引數

如果您想要允許程式變更呼叫程式碼中引數基礎的程式設計項目，您必須以傳址方式傳遞它。 但是，即使您以傳值方式傳遞參考型別引數的專案，程式也可以存取這些元素。

- **基礎變數**。 若要允許程式取代基礎變數元素本身的值，程式必須宣告參數[ByRef](../../../language-reference/modifiers/byref.md)。 此外，呼叫程式碼不能將引數括在括弧中，因為這會覆寫 `ByRef` 傳遞機制。

- **參考型別元素**。 如果您宣告了參數[ByVal](../../../language-reference/modifiers/byval.md)，程式就無法修改基礎變數元素本身。 不過，如果引數是參考型別，則程式可以修改它所指向之物件的成員，即使它無法取代變數的值也一樣。 例如，如果引數是陣列變數，則程式無法指派新的陣列給它，但它可以變更一個或多個其元素。 已變更的元素會反映在呼叫程式碼的基礎陣列變數中。

下列範例會定義兩個程式，以傳值方式使用陣列變數，並在其元素上操作。 程式 `increase` 只會將其中一個專案新增至每個元素。 程式 `replace` 會將新陣列指派給參數 `a()`，然後將其中一個新增至每個元素。 不過，重新指派並不會影響呼叫程式碼中的基礎陣列變數，因為 `a()` 會宣告 `ByVal`。

[!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]

[!code-vb[VbVbcnProcedures#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#38)]

下列範例會呼叫 `increase` 並 `replace`：

[!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]
  
第一個 `MsgBox` 呼叫會在增加（n）之後顯示 "：11，21，31，41 "。 因為 `n` 是參考型別，所以 `increase` 可以變更其成員，即使是傳遞 `ByVal` 也一樣。

第二個 `MsgBox` 呼叫會顯示 "replace （n）：11，21，31，41 "。 因為 `n` 傳遞 `ByVal`，`replace` 無法藉由指派新的陣列來修改變數 `n`。 當 `replace` 會建立新的陣列實例 `k`，並將它指派給本機變數 `a`，它會失去呼叫程式碼傳入之 `n` 的參考。 當它遞增 `a` 的成員時，只有 `k` 的本機陣列會受到影響。

**正確的方法：** 若要能夠修改基礎變數元素本身，請以傳址方式傳遞它。 下列範例顯示 `replace` 的宣告中的變更，讓它能夠以呼叫程式碼中的另一個陣列取代其中一個陣列：

[!code-vb[VbVbcnProcedures#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#64)]

## <a name="unable-to-define-an-overload"></a>無法定義多載

如果您想要定義程式的多載版本，您必須使用相同的名稱，但不能有不同的簽章。 如果編譯器無法區分您的宣告與具有相同簽章的多載，則會產生錯誤。

程式*的簽章取決於過程*名稱和參數清單。 每個多載都必須與所有其他多載具有相同的名稱，但在簽章的其他其中一個元件中，必須與它們的全部相同。 如需詳細資訊，請參閱 [Procedure Overloading](./procedure-overloading.md)。

下列專案雖然與參數清單有關，但並不是程式簽章的元件：

- 程式修飾詞關鍵字，例如 `Public`、`Shared` 和 `Static`。
- 參數名稱。
- 參數修飾詞關鍵字，例如 `ByRef` 和 `Optional`。
- 傳回值的資料類型（轉換運算子除外）。

您無法藉由只改變一或多個先前的專案來多載程式。

**正確的方法：** 若要能夠定義程式多載，您必須變更簽章。 因為您必須使用相同的名稱，所以您必須變更參數的數目、順序或資料類型。 在泛型程式中，您可以改變型別參數的數目。 在轉換運算子（[CType 函數](../../../language-reference/functions/ctype-function.md)）中，您可以改變傳回型別。

### <a name="overload-resolution-with-optional-and-paramarray-arguments"></a>具有選擇性和 ParamArray 引數的多載解析

如果您要多載具有一或多個[選擇性](../../../language-reference/modifiers/optional.md)參數或[ParamArray](../../../language-reference/modifiers/paramarray.md)參數的程式，您必須避免複製任何*隱含*的多載。 如需詳細資訊，請參閱多載[程式的考慮](./considerations-in-overloading-procedures.md)。

## <a name="calling-the-wrong-version-of-an-overloaded-procedure"></a>呼叫錯誤的多載程式版本

如果程式有數個多載版本，您應該熟悉其所有的參數清單，並瞭解 Visual Basic 如何解析多載之間的呼叫。 否則，您可以呼叫非預期的多載。

當您決定要呼叫的多載時，請小心觀察下列規則：

- 請以正確的順序提供正確的引數數目。  
- 在理想的情況下，您的引數應該具有與對應參數完全相同的資料類型。 在任何情況下，每個引數的資料型別都必須擴展為其對應參數的資料類型。 即使[Option Strict 語句](../../../language-reference/statements/option-strict-statement.md)設定為 `Off` 也是如此。 如果多載需要引數清單的任何縮小轉換，該多載就不符合呼叫的資格。
- 如果您提供需要擴展的引數，請將其資料類型盡可能靠近對應的參數資料類型。 如果有兩個以上的多載接受您的引數資料類型，則編譯器會解析呼叫最少量擴展的多載呼叫。

準備引數時，您可以使用[CType 函數](../../../language-reference/functions/ctype-function.md)轉換關鍵字，來減少資料類型不符的機會。

### <a name="overload-resolution-failure"></a>多載解析失敗

當您呼叫多載的程式時，編譯器會嘗試排除其中一個多載。 如果成功，它會解析對該多載的呼叫。 如果它排除所有多載，或如果無法將合格的多載縮減為單一候選，則會產生錯誤。

下列範例說明多載解析程式：

[!code-vb[VbVbcnProcedures#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#62)]

[!code-vb[VbVbcnProcedures#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#63)]
  
在第一次呼叫中，編譯器會排除第一個多載，因為第一個引數（`Short`）的類型會縮小為對應參數的類型（`Byte`）。 然後，它會排除第三個多載，因為第二個多載中的每個引數類型（`Short` 和 `Single`）會擴展到第三個多載中的對應類型（`Integer` 和 `Single`）。 第二個多載需要較少的擴展，因此編譯器會使用它來進行呼叫。

在第二次呼叫中，編譯器無法以縮小的基礎來排除任何多載。 它會在第一次呼叫時排除第三個多載，因為它可以呼叫具有較少引數類型的第二個多載。 不過，編譯器無法解析第一個和第二個多載。 每個都有一個已定義的參數類型，可擴大至另一個中的對應類型（`Byte` 到 `Short`，但 `Single` 到 `Double`）。 因此，編譯器會產生多載解析錯誤。

**正確的方法：** 若要能夠呼叫多載程式而不明確，請使用[CType 函數](../../../language-reference/functions/ctype-function.md)來比對引數資料類型與參數類型。 下列範例示範對 `z` 的呼叫，它會強制解決第二個多載。

[!code-vb[VbVbcnProcedures#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#65)]

### <a name="overload-resolution-with-optional-and-paramarray-arguments"></a>具有選擇性和 ParamArray 引數的多載解析

如果程式的兩個多載具有相同的簽章，但最後一個參數在其中一個和[ParamArray](../../../language-reference/modifiers/paramarray.md)中宣告為[選擇性](../../../language-reference/modifiers/optional.md)，則編譯器會根據最接近的相符項來解析該程式的呼叫。 如需詳細資訊，請參閱 [Overload Resolution](./overload-resolution.md)。

## <a name="see-also"></a>另請參閱

- [程序](index.md)
- [Sub 程序](sub-procedures.md)
- [函式程序](function-procedures.md)
- [屬性程序](property-procedures.md)
- [運算子程序](operator-procedures.md)
- [程序參數和引數](procedure-parameters-and-arguments.md)
- [程序多載化](procedure-overloading.md)
- [多載化程序的考慮因素](considerations-in-overloading-procedures.md)
- [多載解析](overload-resolution.md)
