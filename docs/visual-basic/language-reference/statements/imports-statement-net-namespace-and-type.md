---
title: "Imports 陳述式 （.NET 命名空間和類型） |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Imports
- imports
dev_langs:
- VB
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
caps.latest.revision: 40
author: stevehoag
ms.author: shoag
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 393f3e9a264817d8658585267c954d973290530a
ms.lasthandoff: 03/13/2017

---
# <a name="imports-statement-net-namespace-and-type"></a>Imports 陳述式 (.NET 命名空間和類型)
啟用類型參考而不限定命名空間的名稱。  
  
## <a name="syntax"></a>語法  
  
```  
Imports [ aliasname = ] namespace  
-or-  
Imports [ aliasname = ] namespace.element  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`aliasname`|選擇項。 *匯入別名*或名稱的程式碼可以參考`namespace`而不是完整限定性條件字串。 請參閱[宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。|  
|`namespace`|必要項。 正在匯入的命名空間的完整的名稱。 可使用的命名空間字串巢狀任何層級。|  
|`element`|選擇項。 命名空間中宣告的程式設計項目名稱。 可以是任何容器項目。|  
  
## <a name="remarks"></a>備註  
 `Imports`陳述式可讓指定的命名空間，以直接參考中所包含的型別。  
  
 您可以提供單一命名空間名稱或巢狀命名空間的字串。 每個巢狀命名空間以句號分隔下一個較高的層級命名空間 (`.`)，如下列範例所示。  
  
 `Imports System.Collections.Generic`  
  
 每個原始程式檔可以包含任意數目的`Imports`陳述式。 這些必須遵循的任何選項宣告，例如`Option Strict`陳述式，而且前面必須加上任何程式設計項目宣告，例如`Module`或`Class`陳述式。  
  
 您可以使用`Imports`只能在檔案層級。 這表示匯入宣告內容必須是原始程式檔，且不能命名空間、 類別、 結構、 模組、 介面、 程序或區塊。  
  
 請注意，`Imports`陳述式不會從其他專案和組件的項目提供至您的專案。 匯入不會設定參考。 它只會移除已使用於專案的名稱進行限定的需要。 如需詳細資訊，請參閱 「 匯入包含項目 」 中[宣告之項目的參考](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)。  
  
> [!NOTE]
>  您可以定義隱含`Imports`陳述式使用[專案設計工具 (Visual Basic)、 參考頁](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic)。 如需詳細資訊，請參閱[How to︰ 加入或移除已匯入命名空間 (Visual Basic)](http://msdn.microsoft.com/library/44cebec3-0ea0-47c2-8406-4edeab6a997e)。  
  
## <a name="import-aliases"></a>匯入別名  
 *匯入別名*定義命名空間或類型的別名。 當您需要使用一或多個命名空間中宣告相同名稱的項目時，匯入別名會非常有用。 如需詳細資訊和範例，請參閱 「 合格的項目名稱 」 中[宣告之項目的參考](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)。  
  
 您應該不會宣告具有相同名稱的模組層級的成員`aliasname`。 如果您這樣做，Visual Basic 編譯器會使用`aliasname`只會針對宣告的成員，但不能將其辨識為匯入別名。  
  
 雖然用來宣告匯入別名的語法類似的用來匯入 XML 命名空間前置詞，結果就不同。 匯入別名可以用做您的程式碼中的運算式，而 XML 命名空間前置詞可用來在 XML 常值或 XML 軸屬性中當做前置詞限定的項目或屬性名稱。  
  
### <a name="element-names"></a>項目名稱  
 如果您提供`element`，它必須代表*容器項目*，也就是程式設計項目可以包含其他項目。 容器項目包括類別、 結構、 模組、 介面和列舉型別。  
  
 提供的項目範圍`Imports`陳述式，取決於您是否指定`element`。 如果您只有指定`namespace`、 所有唯一名為該命名空間，以及該命名空間內的容器項目的成員，都可供使用。 如果您同時指定`namespace`和`element`，只有該元素的成員都可供使用。  
  
## <a name="example"></a>範例  
 下列範例傳回 C:\ 目錄中的所有資料夾，使用<xref:System.IO.DirectoryInfo>類別。</xref:System.IO.DirectoryInfo>  
  
 程式碼沒有`Imports`陳述式，在檔案頂端。 因此， `DirectoryInfo`， <xref:System.Text.StringBuilder>，和<xref:Microsoft.VisualBasic.ControlChars.CrLf>是命名空間的所有完整的參考。</xref:Microsoft.VisualBasic.ControlChars.CrLf> </xref:System.Text.StringBuilder>  
  
 [!code-vb[VbVbalrStatements #&152;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_1.vb)]  
  
## <a name="example"></a>範例  
 下列範例會加入`Imports`陳述式的參考命名空間。 因此，型別不必是命名空間的完整名稱。  
  
 [!code-vb[VbVbalrStatements #&153;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_2.vb)]  
  
 [!code-vb[VbVbalrStatements #&154;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_3.vb)]  
  
## <a name="example"></a>範例  
 下列範例會加入`Imports`陳述式，建立參考的命名空間的別名。 型別是以別名限定。  
  
 [!code-vb[VbVbalrStatements #&155;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_4.vb)]  
  
 [!code-vb[VbVbalrStatements #&156;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_5.vb)]  
  
## <a name="example"></a>範例  
 下列範例會加入`Imports`陳述式建立參考類型的別名。 別名用來指定的型別。  
  
 [!code-vb[VbVbalrStatements #&157;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_6.vb)]  
  
 [!code-vb[VbVbalrStatements #&158;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_7.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [Namespace 陳述式](../../../visual-basic/language-reference/statements/namespace-statement.md)   
 [在 Visual Basic 中的命名空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)   
 [參考和 Imports 陳述式](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)   
 [Imports 陳述式 （XML 命名空間）](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)   
 [對已宣告項目的參考](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
