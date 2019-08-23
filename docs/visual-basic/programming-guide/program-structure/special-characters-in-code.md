---
title: 程式碼中的特殊字元 (Visual Basic)
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
ms.openlocfilehash: 95bef937912e35cd828bf0090b4cf48ccb3290cc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962470"
---
# <a name="special-characters-in-code-visual-basic"></a>程式碼中的特殊字元 (Visual Basic)
有時候您必須在程式碼中使用特殊字元, 也就是不是字母或數位的字元。 Visual Basic 字元集中的標點符號和特殊字元具有各種用途, 從組織程式文字到定義編譯器或編譯器所執行的工作。 這些字元不指定要執行的作業。  
  
## <a name="parentheses"></a>後  
 當您定義程式時, 請使用括弧, 例如`Sub`或`Function`。 您必須將所有程式引數清單括在括弧中。 您也可以使用括弧將變數或引數放入邏輯群組, 特別是在複雜運算式中覆寫運算子優先順序的預設順序。 下列範例將說明這點。  
  
 [!code-vb[VbVbcnConventions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#11)]  
  
 執行先前的`d`程式碼之後, 的值為 8.225, 且的`e`值為3。 的計算`d`會使用的預設`/`優先順序`d = b + (c / a)`over `+` , 而相當於。 計算中的括弧會覆`e`寫預設優先順序。  
  
## <a name="separators"></a>分隔符號  
 分隔符號會執行其名稱的建議: 它們會分隔程式碼區段。 在 Visual Basic 中, 分隔字元是冒號 (`:`)。 當您想要在單一行上包含多個語句, 而不是個別行時, 請使用分隔符號。 這可節省空間並改善程式碼的可讀性。 下列範例顯示三個以冒號分隔的語句。  
  
 [!code-vb[VbVbcnConventions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#12)]  
  
 如需詳細資訊，請參閱[如何：在程式碼](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)中中斷和合併語句。  
  
 冒號 (`:`) 字元也會用來識別語句標籤。 如需詳細資訊，請參閱[如何：標籤](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)語句。  
  
## <a name="concatenation"></a>串連  
 使用運算子進行串連, 或將字串連結在一起。 `&` 請勿將它與`+`運算子混淆, 這會將數值相加。 如果您在操作`+`數值時使用運算子來串連, 您可以取得不正確的結果。 下列範例為其示範。  
  
 [!code-vb[VbVbcnConventions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#13)]  
  
 執行先前的`resultA`程式碼之後, 的值為 21.01, 且的`resultB`值為 "10.0111"。  
  
## <a name="member-access-operators"></a>成員存取運算子  
 若要存取類型的成員, 請在類型名稱和成員`.`名稱之間使用點 (`!`) 或驚嘆號 () 運算子。  
  
### <a name="dot--operator"></a>點 (.)運算子  
 在類別、結構、介面或列舉上使用運算子做為成員存取運算子。`.` 成員可以是欄位、屬性、事件或方法。 下列範例將說明這點。  
  
 [!code-vb[VbVbcnConventions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#14)]  
  
### <a name="exclamation-point--operator"></a>驚嘆號 (!)運算子  
 只在類別或介面上使用運算子做為字典存取運算子。`!` 類別或介面必須具有接受單一`String`引數的預設屬性。 緊接在`!`運算子後面的識別碼會變成當做字串傳遞至預設屬性的引數值。 下列範例為其示範。  
  
 [!code-vb[VbVbcnConventions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#15)]  
  
 的三個輸出行會`MsgBox`顯示值。 `32856` 第一行使用傳統的存取屬性`index`, 第二行使用的`index`事實是類別`hasDefault`的預設屬性, 而第三個使用類別的字典存取。  
  
 請注意, `!`運算子的第二個運算元必須是不以雙引號 (`" "`) 括住的有效 Visual Basic 識別碼。 換句話說, 您不能使用字串常值或字串變數。 `MsgBox`呼叫最後一行的下列變更會產生錯誤, 因為`"X"`是括住的字串常值。  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
> 預設集合的參考必須是明確的。 特別的`!`是, 您無法在晚期繫結變數上使用運算子。  
  
 字元也會用來`Single`做為類型字元。 `!`  
  
## <a name="see-also"></a>另請參閱

- [程式結構和程式碼慣例](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [類型字元](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
