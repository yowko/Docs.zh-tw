---
title: 命名空間陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Namespace
helpviewer_keywords:
- namespaces [Visual Basic], root
- Namespace statement [Visual Basic]
- namespaces [Visual Basic], nested
- declaring namespaces [Visual Basic], syntax
- namespaces [Visual Basic], declaring
- root namespaces
- declarations [Visual Basic], namespaces
ms.assetid: a31fbd95-9ace-4c3d-bbb1-51222a2272b2
ms.openlocfilehash: 1e7fb55cac1de747c620ea44f320ec9185bfbd3b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54612147"
---
# <a name="namespace-statement"></a>Namespace 陳述式
宣告命名空間的名稱，並造成接在宣告該命名空間內進行編譯的原始程式碼。  
  
## <a name="syntax"></a>語法  
  
```vb  
Namespace [Global.] { name | name.name }  
    [ componenttypes ]  
End Namespace  
```  
  
## <a name="parts"></a>組件  
 Global  
 選擇性。 可讓您定義的命名空間從您的專案的根命名空間。 請參閱[在 Visual Basic 中的命名空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)。  
  
 `name`  
 必要項。 唯一的名稱識別命名空間。 必須是有效的 Visual Basic 識別項。 如需詳細資訊，請參閱 <<c0> [ 宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。  
  
 `componenttypes`  
 選擇性。 命名空間所組成的項目。 這些包括但不限於列舉、 結構、 介面、 類別、 模組、 委派及其他命名空間。  
  
 `End Namespace`  
 終止`Namespace`區塊。  
  
## <a name="remarks"></a>備註  
 命名空間會作為組織的系統。 它們提供分類，並提供程式設計的項目公開給其他程式和應用程式的方式。 請注意，命名空間不是*型別*意思是類別或結構，您不能宣告為具有資料類型的命名空間的程式設計項目。  
  
 所有的程式設計項目宣告之後`Namespace`陳述式屬於該命名空間。 Visual Basic 會繼續編譯成最後一個宣告的命名空間的項目，直到它遇到其中`End Namespace`陳述式或另一個`Namespace`陳述式。  
  
 如果已經定義命名空間，甚至是外部專案中，您可以新增給它的程式設計項目。 若要這樣做，您使用`Namespace`直接編譯項目至該命名空間的 Visual Basic 的陳述式。  
  
 您可以使用`Namespace`只能在檔案或命名空間層級的陳述式。 這表示*宣告內容*命名空間必須是原始程式檔或另一個命名空間，並不是類別、 結構、 模組、 介面或程序。 如需詳細資訊，請參閱[宣告內容和預設存取層級](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。  
  
 您可以宣告在另一個命名空間。 您可以宣告，但請記住，當其他程式碼存取最內層的命名空間中宣告的項目時，它必須使用限定性條件字串，包含巢狀階層中的所有命名空間名稱的巢狀層級沒有嚴格限制。  
  
## <a name="access-level"></a>存取層級  
 命名空間會視為它們有`Public`存取層級。 從相同的專案中的任何位置的程式碼、 其他參考該專案的專案和專案所建立的任何組件，就可以存取命名空間。  
  
 在命名空間層級，這表示命名空間中，但不是能在任何其他項目，宣告的程式設計項目可以有`Public`或`Friend`存取。 如果未指定，這類的存取層級項目使用`Friend`預設。 您可以在命名空間層級宣告的項目包括類別、 結構、 模組、 介面、 列舉和委派。 如需詳細資訊，請參閱[宣告內容和預設存取層級](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。  
  
## <a name="root-namespace"></a>根命名空間  
 在您的專案中的所有命名空間名稱為基礎*根命名空間*。 Visual Studio 會針對專案中的所有程式碼，將專案名稱指派為預設根命名空間。 例如，如果專案已命名為 `Payroll`，其程式設計項目會屬於命名空間 `Payroll`。 如果您宣告`Namespace funding`，該命名空間的完整名稱是`Payroll.funding`。  
  
 如果您想要指定現有的命名空間中`Namespace`陳述式，例如在泛型清單類別範例中，您可以設定您的根命名空間為 null 值。 若要這樣做，請按一下**專案屬性**從**專案**功能表，然後清除**根命名空間**項目以便方塊是空的。 如果您未這麼做在泛型清單類別的範例中，採取 Visual Basic 編譯器`System.Collections.Generic`專案中的新命名空間`Payroll`，以完整名稱`Payroll.System.Collections.Generic`。  
  
 或者，您可以使用`Global`關鍵字來參考您的專案以外定義的命名空間的項目。 如此一來，可讓您保留您的專案名稱，當做根命名空間。 這可減少意外合併您的程式設計項目，以及現有的命名空間的機會。 如需詳細資訊，請參閱中的 「 全域關鍵字中完整限定名稱 」 一節[在 Visual Basic 中的命名空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)。  
  
 `Global`關鍵字也可以用於命名空間陳述式。 這可讓您從專案的根命名空間定義一個命名空間。 如需詳細資訊，請參閱中的 < 全域關鍵字在命名空間陳述式 > 一節[在 Visual Basic 中的命名空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)。  
  
 **疑難排解。** 根命名空間可能會導致非預期的命名空間名稱的串連。 若要在專案以外定義的命名空間的參考，Visual Basic 編譯器可以將它們當做是根命名空間中的巢狀命名空間。 在此情況下，編譯器無法辨識已經定義外部命名空間中的任何型別。 若要避免這個問題，請將您的根命名空間設定為 「 根命名空間 」 中所述的 null 值，或使用`Global`關鍵字來存取的外部命名空間的項目。  
  
## <a name="attributes-and-modifiers"></a>屬性和修飾詞  
 您無法將屬性套用至命名空間。 屬性會提供資訊給組件的中繼資料，這不是有意義的來源分類器，例如命名空間。  
  
 您無法將任何存取或程序修飾詞或任何其他修飾詞，套用至命名空間中。 由於不是類型，這些修飾詞不是有意義的。  
  
## <a name="example"></a>範例  
 下列範例會宣告兩個命名空間，巢狀方式置於另一個。  
  
 [!code-vb[VbVbalrStatements#43](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/namespace-statement_1.vb)]  
  
## <a name="example"></a>範例  
 下列範例會宣告多個巢狀命名空間以單行，並相當於先前的範例。  
  
 [!code-vb[VbVbalrStatements#41](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/namespace-statement_2.vb)]  
  
## <a name="example"></a>範例  
 下列範例會存取先前的範例中定義的類別。  
  
 [!code-vb[VbVbalrStatements#42](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/namespace-statement_3.vb)]  
  
## <a name="example"></a>範例  
 下列範例會定義新的泛型清單類別的基本架構，並將它加入<xref:System.Collections.Generic?displayProperty=nameWithType>命名空間。  
  
```vb  
Namespace System.Collections.Generic  
    Class specialSortedList(Of T)  
        Inherits List(Of T)  
        ' Insert code to define the special generic list class.  
    End Class  
End Namespace  
```  
  
## <a name="see-also"></a>另請參閱
- [Imports 陳述式 (.NET 命名空間和類型)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [在 Visual Basic 中的命名空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)
