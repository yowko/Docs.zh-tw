---
title: 程式碼中的特殊字元
ms.date: 07/20/2015
f1_keywords:
- vb.)
- vb.(
- vb.colon
- vb.!
- vb..
- 'vb.:'
helpviewer_keywords:
- special characters [Visual Basic], in code
- parentheses [Visual Basic], using in code
- colons (:)
- period character in code
- dot operator (.)
- dictionary access operator [Visual Basic]
- concatenation operators [Visual Basic], special characters in code
- concatenation operators [Visual Basic], vs. addition operator
- '! operator'
- separators [Visual Basic], using in code
- operators [Visual Basic], dictionary access
- ': separator character'
- member access operator [Visual Basic]
- addition operator [Visual Basic]
- operators [Visual Basic], member access
- . operator
- exclamation points
- separators
- exclamation point operator (!)
- Visual Basic code, special characters
ms.assetid: 310dce0c-45b5-4e0d-83e9-32df258d2a3e
ms.openlocfilehash: 60f815f0d30fa785f4a2166db5a041d3851aa954
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097822"
---
# <a name="special-characters-in-code-visual-basic"></a>程式碼中的特殊字元 (Visual Basic)

有時您必須在程式碼中使用特殊字元，也就是不是字母或數位的字元。 Visual Basic 字元集中的標點符號和特殊字元具有各種用途，從組織程式文字到定義編譯器或編譯器所執行的工作。 這些字元不指定要執行的作業。  
  
## <a name="parentheses"></a>括號  

 當您定義程式時（例如或），請使用括弧 `Sub` `Function` 。 您必須將所有程式引數清單括在括弧中。 您也可以使用括弧將變數或引數放入邏輯群組，特別是在複雜運算式中覆寫運算子優先順序的預設順序。 下列範例將說明這點。  
  
 [!code-vb[VbVbcnConventions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#11)]  
  
 執行先前的程式碼之後，的值 `d` 為8.225，而的值 `e` 為3。 的計算 `d` 使用的預設優先順序 `/` `+` ，相當於 `d = b + (c / a)` 。 計算中的括弧會覆 `e` 寫預設優先順序。  
  
## <a name="separators"></a>分隔符號  

 分隔符號可做為其名稱的建議：它們可分隔程式碼區段。 在 Visual Basic 中，分隔符號是 () 的冒號 `:` 。 當您想要將多個語句包含在同一行，而不是個別行時，請使用分隔符號。 這樣可以節省空間並提高程式碼的可讀性。 下列範例顯示三個以冒號分隔的語句。  
  
 [!code-vb[VbVbcnConventions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#12)]  
  
 如需詳細資訊，請參閱 [如何：在程式碼中中斷和合併語句](how-to-break-and-combine-statements-in-code.md)。  
  
 冒號 (`:`) 字元也用來識別語句標籤。 如需詳細資訊，請參閱 [如何：標記語句](how-to-label-statements.md)。  
  
## <a name="concatenation"></a>串連  

 使用 `&` 運算子進行 *串連*，或將字串連結在一起。 請勿將它與運算子混淆 `+` ，以將數值相加。 如果您在 `+` 運算元值時使用運算子串連，則可以取得不正確的結果。 下列範例示範此作業。  
  
 [!code-vb[VbVbcnConventions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#13)]  
  
 執行先前的程式碼之後，的值 `resultA` 為21.01，而的值 `resultB` 為 "10.0111"。  
  
## <a name="member-access-operators"></a>成員存取運算子  

 若要存取類型的成員，請在 `.` `!` 類型名稱和成員名稱之間使用點 () 或驚嘆號 () 運算子。  
  
### <a name="dot--operator"></a>點 (. ) 運算子  

 `.`在類別、結構、介面或列舉上使用運算子作為成員存取運算子。 成員可以是欄位、屬性、事件或方法。 下列範例將說明這點。  
  
 [!code-vb[VbVbcnConventions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#14)]  
  
### <a name="exclamation-point--operator"></a>驚嘆號 (！ ) 運算子  

 請 `!` 只在類別或介面上使用運算子作為字典存取運算子。 類別或介面必須有接受單一引數的 default 屬性 `String` 。 緊接在運算子之後的識別碼 `!` 會變成以字串形式傳遞至預設屬性的引數值。 下列範例示範此作業。  
  
 [!code-vb[VbVbcnConventions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#15)]  
  
 的三個輸出行會 `MsgBox` 顯示值 `32856` 。 第一行使用屬性的傳統存取 `index` ，第二行則 `index` 是使用類別的預設屬性的事實 `hasDefault` ，而第三行則使用類別的字典存取。  
  
 請注意，運算子的第二個運算元 `!` 必須是未以雙引號括住的有效 Visual Basic 識別碼 (`" "`) 。 換句話說，您不能使用字串常值或字串變數。 下列對呼叫最後一行所做的變更 `MsgBox` 會產生錯誤，因為 `"X"` 是包含的字串常值。  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
> 預設集合的參考必須是明確的。 尤其是，您不能 `!` 在晚期繫結變數上使用運算子。  
  
 `!`字元也會用來做為 `Single` 類型字元。  
  
## <a name="see-also"></a>另請參閱

- [程式結構和程式碼慣例](program-structure-and-code-conventions.md)
- [類型字元](../language-features/data-types/type-characters.md)
