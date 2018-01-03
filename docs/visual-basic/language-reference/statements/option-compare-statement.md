---
title: "Option Compare 陳述式"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Compare
- vb.OptionCompare
helpviewer_keywords:
- case sensitivity, Option Compare statement
- Compare keyword [Visual Basic]
- binary comparison [Visual Basic]
- strings [Visual Basic], returning from functions
- binary comparison [Visual Basic], Option Compare statement
- strings [Visual Basic], comparing
- string comparison [Visual Basic], Option Compare statement
- Text keyword [Visual Basic], Option Compare statement
- Binary keyword [Visual Basic], Option Compare statement
- string comparison [Visual Basic], sorting data
- Option Compare statement [Visual Basic]
- text [Visual Basic], comparing
ms.assetid: 54e8eeeb-3b0d-4fb9-acce-fbfbd5975f6e
caps.latest.revision: "37"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 00753eddb641c07ef9c6e6282fe00c5e8d00547a
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="option-compare-statement"></a>Option Compare 陳述式
宣告比較字串資料時要使用的預設比較方法。  
  
## <a name="syntax"></a>語法  
  
```  
Option Compare { Binary | Text }  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`Binary`|選擇項。 字串比較是依據排序次序會導致衍生自內部的二進位表示法的字元。<br /><br /> 這種類型是比較的很有用，特別是比較的當字串可以包含要解譯為文字的字元。 在此情況下，您不想要依字母順序排列其等效，例如不區分大小寫比較偏差。|  
|`Text`|選擇項。 字串比較是依據您的系統地區設定所決定的不區分大小寫文字排序順序中的結果。<br /><br /> 如果字串包含所有文字字元，而且您想要納入帳戶字母其等效例如不區分大小寫和密切相關的字母比較它們，這種比較很有用。 例如，您可能要考慮`A`和`a`視為相等，和`Ä`和`ä`是之前`B`和`b`。|  
  
## <a name="remarks"></a>備註  
 如果單獨使用，`Option Compare`陳述式必須出現在任何其他來源的程式碼陳述式之前的檔案。  
  
 `Option Compare`陳述式指定的字串比較方法 (`Binary`或`Text`)。  預設文字比較方法是`Binary`。  
  
 A`Binary`比較比較每個字串中的每個字元的數字 Unicode 值。 A`Text`比較比較根據目前文化特性中其語彙意義的每個 Unicode 字元。  
  
 在 Microsoft Windows 中，依字碼頁會決定排序次序。 如需詳細資訊，請參閱[字碼頁](/cpp/c-runtime-library/code-pages)。  
  
 在下列範例中，英文/歐語系字碼頁 (ANSI 1252) 中的字元是使用 `Option Compare Binary` 來排序，這會產生一般的二進位排序順序。  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 使用 `Option Compare Text` 排序相同字碼頁中的相同字元時，會產生下列的文字排序順序。  
  
 `(A=a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
## <a name="when-an-option-compare-statement-is-not-present"></a>Option Compare 陳述式不存在時  
 如果不包含原始碼`Option Compare`陳述式， **Option Compare**上設定[編譯的頁面上，專案設計工具 (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)用。 如果您使用命令列編譯器時，所指定的設定[/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)編譯器選項使用。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
#### <a name="to-set-option-compare-in-the-ide"></a>在 IDE 中設定選項比較  
  
1.  在方案總管中選取專案。 在 [專案] 功能表上，按一下 [屬性]。  
  
2.  按一下 [編譯] 索引標籤。  
  
3.  設定中的值**Option Compare**方塊。  
  
 當您建立專案， **Option Compare**上設定**編譯** 索引標籤設為**Option Compare**中設定**選項**對話方塊。 若要變更這項設定，在**工具**功能表上，按一下 **選項**。 在 [選項] 對話方塊中，展開 [專案和方案]，然後按一下 [VB 預設值]。 中的初始預設設定**VB 預設值**是**二進位**。  
  
#### <a name="to-set-option-compare-on-the-command-line"></a>在命令列上設定選項比較  
  
-   包含[/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)編譯器選項在**vbc**命令。  
  
## <a name="example"></a>範例  
 下列範例會使用 `Option Compare` 陳述式來將二進位比較設為預設字串比較方法。 若要使用這段程式碼，請取消註解 `Option Compare Binary` 陳述式，並將其放置在原始程式檔的頂端。  
  
 [!code-vb[VbVbalrStatements#45](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-compare-statement_1.vb)]  
  
## <a name="example"></a>範例  
 下列範例會使用 `Option Compare` 陳述式，將不區分大小寫文字排序順序設定為預設字串比較方法。 若要使用這段程式碼，請取消註解 `Option Compare Text` 陳述式，並將其放置在原始程式檔的頂端。  
  
 [!code-vb[VbVbalrStatements#46](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-compare-statement_2.vb)]  
  
## <a name="see-also"></a>請參閱  
 <xref:Microsoft.VisualBasic.Strings.InStr%2A>  
 <xref:Microsoft.VisualBasic.Strings.InStrRev%2A>  
 <xref:Microsoft.VisualBasic.Strings.Replace%2A>  
 <xref:Microsoft.VisualBasic.Strings.Split%2A>  
 <xref:Microsoft.VisualBasic.Strings.StrComp%2A>  
 [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [比較運算子](../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [在 Visual Basic 中的比較運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [Like 運算子](../../../visual-basic/language-reference/operators/like-operator.md)  
 [字串函式](../../../visual-basic/language-reference/functions/string-functions.md)  
 [Option Explicit 陳述式](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)
