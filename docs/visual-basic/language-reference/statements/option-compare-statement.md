---
title: "Option Compare 陳述式 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Compare
- vb.OptionCompare
dev_langs:
- VB
helpviewer_keywords:
- case sensitivity, Option Compare statement
- Compare keyword
- binary comparison
- strings [Visual Basic], returning from functions
- binary comparison, Option Compare statement
- strings [Visual Basic], comparing
- string comparison [Visual Basic], Option Compare statement
- Text keyword, Option Compare statement
- Binary keyword, Option Compare statement
- string comparison [Visual Basic], sorting data
- Option Compare statement
- text [Visual Basic], comparing
ms.assetid: 54e8eeeb-3b0d-4fb9-acce-fbfbd5975f6e
caps.latest.revision: 37
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 8b1b077a8818315e52ada6b08ff1e1ced9bbd17c
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

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
|`Binary`|選擇項。 字串比較是依據衍生自內部的二進位表示的字元的排序順序中的結果。<br /><br /> 這種類型是比較的很有用，特別是比較的如果字串可以包含不是比較的將解譯為文字的字元。 在此情況下，您不想要依字母順序排列其等效，例如不區分大小寫比較偏差。|  
|`Text`|選擇項。 字串比較是不區分大小寫文字排序順序取決於您的系統地區設定所依據的結果。<br /><br /> 如果字串包含所有文字字元，而且您想要考慮到帳戶密切相關的字母等不區分大小寫字母其等效相比較，這種比較很有用。 例如，您可能要考慮`A`和`a`視為相等，以及`Ä`和`ä`排在前面`B`和`b`。|  
  
## <a name="remarks"></a>備註  
 如果使用`Option Compare`陳述式必須出現在任何其他來源的程式碼陳述式之前的檔案。  
  
 `Option Compare`陳述式指定的字串比較方法 (`Binary`或`Text`)。  預設文字比較方法是`Binary`。  
  
 A`Binary`比較比較每個字串中的每個字元的數字 Unicode 值。 A`Text`比較比較根據其目前的文化特性中的語彙意義的每個 Unicode 字元。  
  
 Microsoft Windows 中的字碼頁會決定排序次序。 如需詳細資訊，請參閱[字碼頁](https://docs.microsoft.com/cpp/c-runtime-library/code-pages)。  
  
 在下列範例中，英文/歐語系字碼頁 (ANSI 1252) 中的字元是使用 `Option Compare Binary` 來排序，這會產生一般的二進位排序順序。  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 使用 `Option Compare Text` 排序相同字碼頁中的相同字元時，會產生下列的文字排序順序。  
  
 `(A=a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
## <a name="when-an-option-compare-statement-is-not-present"></a>Option Compare 陳述式不存在時  
 如果原始程式碼不包含`Option Compare`陳述式，**選項比較**上設定[編譯的頁面上，專案設計工具 (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic)用。 如果您使用命令列編譯器時，所指定的設定[/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)編譯器選項使用。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
#### <a name="to-set-option-compare-in-the-ide"></a>在 IDE 中設定選項比較  
  
1.  在**方案總管 中**，選取專案。 在**專案**] 功能表上，按一下 [**屬性**。 如需詳細資訊，請參閱[NIB︰ 使用專案設計工具管理專案屬性](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e)。  
  
2.  按一下 [編譯]**** 索引標籤。  
  
3.  在設定的值**選項比較**方塊。  
  
 當您建立專案，**選項比較**上設定**編譯** 索引標籤設為**選項比較**中設定**選項**對話方塊。 若要變更此設定，請在**工具**] 功能表上，按一下 [**選項**。 在**選項**對話方塊方塊中，展開**專案和方案**，然後按一下  **VB 預設值**。 中的初始預設設定**VB 預設值**是**二進位**。  
  
#### <a name="to-set-option-compare-on-the-command-line"></a>在命令列上設定選項比較  
  
-   包含[/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)編譯器選項，在**vbc**命令。  
  
## <a name="example"></a>範例  
 下列範例會使用 `Option Compare` 陳述式來將二進位比較設為預設字串比較方法。 若要使用這段程式碼，請取消註解 `Option Compare Binary` 陳述式，並將其放置在原始程式檔的頂端。  
  
 [!code-vb[VbVbalrStatements #&45;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-compare-statement_1.vb)]  
  
## <a name="example"></a>範例  
 下列範例會使用 `Option Compare` 陳述式，將不區分大小寫文字排序順序設定為預設字串比較方法。 若要使用這段程式碼，請取消註解 `Option Compare Text` 陳述式，並將其放置在原始程式檔的頂端。  
  
 [!code-vb[VbVbalrStatements #&46;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-compare-statement_2.vb)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.Strings.InStr%2A></xref:Microsoft.VisualBasic.Strings.InStr%2A>   
 <xref:Microsoft.VisualBasic.Strings.InStrRev%2A></xref:Microsoft.VisualBasic.Strings.InStrRev%2A>   
 <xref:Microsoft.VisualBasic.Strings.Replace%2A></xref:Microsoft.VisualBasic.Strings.Replace%2A>   
 <xref:Microsoft.VisualBasic.Strings.Split%2A></xref:Microsoft.VisualBasic.Strings.Split%2A>   
 <xref:Microsoft.VisualBasic.Strings.StrComp%2A></xref:Microsoft.VisualBasic.Strings.StrComp%2A>   
 [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)   
 [比較運算子](../../../visual-basic/language-reference/operators/comparison-operators.md)   
 [在 Visual Basic 中的比較運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)   
 [Like 運算子](../../../visual-basic/language-reference/operators/like-operator.md)   
 [字串函式](../../../visual-basic/language-reference/functions/string-functions.md)   
 [Option Explicit 陳述式](../../../visual-basic/language-reference/statements/option-explicit-statement.md)   
 [Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)
