---
title: Imports 語句-.NET 命名空間和類型 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Imports
- imports
helpviewer_keywords:
- declared element names [Visual Basic], qualification
- imports [Visual Basic]
- Imports statement [Visual Basic]
- aliases [Visual Basic], Imports statement
- container elements [Visual Basic]
- namespaces [Visual Basic], importing
- Imports statement [Visual Basic], syntax
- import aliases [Visual Basic]
- aliases [Visual Basic], import
- declared elements [Visual Basic], container elements
ms.assetid: 7062f8aa-d890-4232-9eed-92836e13fb6e
ms.openlocfilehash: a0b7a6a5fd16dc0daa620e6b490ddfdeb0e7c80e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912380"
---
# <a name="imports-statement-net-namespace-and-type"></a>Imports 陳述式 (.NET 命名空間和類型)
在不限定命名空間的情況下, 允許參考型別名稱。  
  
## <a name="syntax"></a>語法  
  
```  
Imports [ aliasname = ] namespace  
-or-  
Imports [ aliasname = ] namespace.element  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`aliasname`|選擇性。 可供程式碼參考`namespace`的匯*入別名*或名稱, 而不是完整的限定性字串。 請參閱 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。|  
|`namespace`|必要項。 要匯入之命名空間的完整名稱。 可以是嵌套于任何層級的命名空間字串。|  
|`element`|選擇性。 命名空間中宣告的程式設計項目名稱。 可以是任何容器元素。|  
  
## <a name="remarks"></a>備註  
 `Imports`語句可讓您直接參考指定命名空間中包含的類型。  
  
 您可以提供單一命名空間名稱或一個嵌套命名空間的字串。 每個嵌套的命名空間都是以句點 (`.`) 與下一個較高層級的命名空間分隔, 如下列範例所示。  
  
 `Imports System.Collections.Generic`  
  
 每個來源檔案可以包含任意數目`Imports`的語句。 這些必須遵循任何選項宣告 (例如`Option Strict`語句), 而且必須在任何程式設計專案宣告之前, `Module`例如或`Class`語句。  
  
 您只能在`Imports`檔案層級使用。 這表示匯入的宣告內容必須是原始程式檔, 而且不能是命名空間、類別、結構、模組、介面、程式或區塊。  
  
 請注意, `Imports`語句不會將其他專案和元件中的元素提供給您的專案。 匯入不會取代設定參考。 這只是不需要限定已可用於您專案的名稱。 如需詳細資訊, 請參閱宣告專案[參考](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)中的「匯入包含元素」。  
  
> [!NOTE]
> 您可以使用 [ `Imports`專案設計工具] 的 [[參考] 頁面 (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)來定義隱含的語句。 如需詳細資訊，請參閱[如何：新增或移除匯入的命名空間](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic)(Visual Basic)。  
  
## <a name="import-aliases"></a>匯入別名  
 匯*入別名*會定義命名空間或類型的別名。 當您需要使用與一個或多個命名空間中宣告的相同名稱的專案時, 匯入別名會很有用。 如需詳細資訊和範例, 請參閱宣告[元素的參考](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)中的「限定專案名稱」。  
  
 您不應該使用與相同的名稱`aliasname`來宣告模組層級的成員。 如果您這樣做, Visual Basic 編譯器只`aliasname`會針對宣告的成員使用, 而不會再將它辨識為匯入別名。  
  
 雖然用來宣告匯入別名的語法就像是用來匯入 XML 命名空間前置詞, 但結果並不相同。 匯入別名可以當做程式碼中的運算式使用, 而 XML 命名空間前置詞只能用在 XML 常值或 XML 軸屬性中, 做為限定專案或屬性名稱的前置詞。  
  
### <a name="element-names"></a>項目名稱  
 如果您提供`element`, 它必須代表*容器元素*, 也就是可以包含其他元素的程式設計項目。 容器元素包括類別、結構、模組、介面和列舉。  
  
 `Imports`語句所提供的元素範圍取決於您是否指定`element`。 如果您只`namespace`指定, 就可以使用該命名空間的所有唯一名稱成員, 以及該命名空間內的容器元素成員, 而不需要限定。 如果您同時`namespace`指定和`element`, 則只有該元素的成員可以使用, 而不需要限定。  
  
## <a name="example"></a>範例  
 下列範例會傳回 C:\ 中的所有資料夾目錄, 方法是<xref:System.IO.DirectoryInfo>使用類別。  
  
 此程式碼在`Imports`檔案的頂端沒有任何語句。 因此,、和<xref:Microsoft.VisualBasic.ControlChars.CrLf>參考都是完整的命名空間。 `DirectoryInfo` <xref:System.Text.StringBuilder>  
  
 [!code-vb[VbVbalrStatements#152](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#152)]  
  
## <a name="example"></a>範例  
 下列範例包含`Imports`所參考之命名空間的語句。 因此, 類型不一定要使用命名空間來完整限定。  
  
 [!code-vb[VbVbalrStatements#153](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#153)]  
  
 [!code-vb[VbVbalrStatements#154](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#154)]  
  
## <a name="example"></a>範例  
 下列範例包含`Imports`的語句會建立所參考之命名空間的別名。 類型是以別名限定。  
  
 [!code-vb[VbVbalrStatements#155](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#155)]  
  
 [!code-vb[VbVbalrStatements#156](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#156)]  
  
## <a name="example"></a>範例  
 下列範例包含`Imports`的語句會建立參考型別的別名。 別名是用來指定類型。  
  
 [!code-vb[VbVbalrStatements#157](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#157)]  
  
 [!code-vb[VbVbalrStatements#158](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#158)]  
  
## <a name="see-also"></a>另請參閱

- [Namespace 陳述式](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [Visual Basic 中的命名空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [參考和 Imports 陳述式](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)
- [Imports 陳述式 (XML 命名空間)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
- [對已宣告項目的參考](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
