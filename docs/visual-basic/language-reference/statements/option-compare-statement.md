---
title: Option Compare 陳述式
ms.date: 07/20/2015
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
ms.openlocfilehash: 396770a2fc6996475d408cf8023a4eafdf6d3011
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90869646"
---
# <a name="option-compare-statement"></a>Option Compare 陳述式

宣告比較字串資料時要使用的預設比較方法。  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Option Compare { Binary | Text }  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`Binary`|選擇性。 根據從字元的內部二進位標記法衍生的排序次序，產生字串比較。<br /><br /> 這種比較很有用，尤其是當字串可以包含不會被解釋為文字的字元時。 在此情況下，您不會想要以字母順序 equivalences 進行偏差比較，例如不區分大小寫。|  
|`Text`|選擇性。 根據您系統的地區設定所決定的不區分大小寫文字排序次序，來產生字串比較。<br /><br /> 如果您的字串包含所有文字字元，而且您想要將它們納入考慮不區分大小寫和緊密相關字母的字母 equivalences 中，這種比較就很有用。 例如，您可能想要將 `A` 和視為 `a` 相等，以及 `Ä` `ä` 在 `B` 和之前 `b` 。|  
  
## <a name="remarks"></a>備註  

 如果使用的話， `Option Compare` 語句必須出現在檔案中的任何其他原始程式碼語句之前。  
  
 `Option Compare`語句會指定 (或) 的字串比較方法 `Binary` `Text` 。  預設的文字比較方法是 `Binary` 。  
  
 `Binary`比較會比較每個字串中每個字元的數位 Unicode 值。 `Text`比較會根據其在目前文化特性中的詞法表示來比較每個 Unicode 字元。  
  
 在 Microsoft Windows 中，排序次序是由字碼頁所決定。 如需詳細資訊，請參閱[字碼頁](/cpp/c-runtime-library/code-pages)。  
  
 在下列範例中，英文/歐語系字碼頁 (ANSI 1252) 中的字元是使用 `Option Compare Binary` 來排序，這會產生一般的二進位排序順序。  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 使用 `Option Compare Text` 排序相同字碼頁中的相同字元時，會產生下列的文字排序順序。  
  
 `(A=a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
## <a name="when-an-option-compare-statement-is-not-present"></a>Option Compare 陳述式不存在時  

 如果原始程式碼不包含 `Option Compare` 語句，則會使用 [編譯] 頁面上的 [ **選項比較** ] 設定 [、[專案設計工具] (Visual Basic) ](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) 。 如果您使用命令列編譯器，則會使用 [-optioncompare](../../reference/command-line-compiler/optioncompare.md) 編譯器選項所指定的設定。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
#### <a name="to-set-option-compare-in-the-ide"></a>在 IDE 中設定選項比較  
  
1. 在 **方案總管**中，選取專案。 按一下 [專案] 功能表上的 [屬性]。  
  
2. 按一下 [編譯]**** 索引標籤。  
  
3. 在 [ **選項比較** ] 方塊中設定值。  
  
 當您建立專案時，[**編譯**] 索引標籤上的 [**選項比較**] 設定會設定為 [**選項**] 對話方塊中的 [**選項比較**] 設定。 若要變更此設定，請按一下 [ **工具** ] 功能表上的 [ **選項**]。 在 [選項]**** 對話方塊中，展開 [專案和方案]****，然後按一下 [VB 預設值]****。 **VB 預設值**中的初始預設設定為**Binary**。  
  
#### <a name="to-set-option-compare-on-the-command-line"></a>在命令列上設定選項比較  
  
- 在**vbc**命令中包含[-optioncompare](../../reference/command-line-compiler/optioncompare.md)編譯器選項。  
  
## <a name="example"></a>範例  

 下列範例會使用 `Option Compare` 陳述式來將二進位比較設為預設字串比較方法。 若要使用這段程式碼，請取消註解 `Option Compare Binary` 陳述式，並將其放置在原始程式檔的頂端。  
  
 [!code-vb[VbVbalrStatements#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#45)]  
  
## <a name="example"></a>範例  

 下列範例會使用 `Option Compare` 陳述式，將不區分大小寫文字排序順序設定為預設字串比較方法。 若要使用這段程式碼，請取消註解 `Option Compare Text` 陳述式，並將其放置在原始程式檔的頂端。  
  
 [!code-vb[VbVbalrStatements#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#46)]  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.InStrRev%2A>
- <xref:Microsoft.VisualBasic.Strings.Replace%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [-optioncompare](../../reference/command-line-compiler/optioncompare.md)
- [比較運算子](../operators/comparison-operators.md)
- [Comparison Operators in Visual Basic](../../programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Like 運算子](../operators/like-operator.md)
- [字串函式](../functions/string-functions.md)
- [Option Explicit 陳述式](option-explicit-statement.md)
- [Long](option-strict-statement.md)
