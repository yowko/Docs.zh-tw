---
title: Namespace 陳述式
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 39
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 90eb33bdbc01afc983869c919f9d7b2feab44037
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="namespace-statement"></a>Namespace 陳述式
宣告命名空間的名稱，並遵循編譯該命名空間中宣告的原始程式碼。  
  
## <a name="syntax"></a>語法  
  
```vb  
Namespace [Global.] { name | name.name }  
    [ componenttypes ]  
End Namespace  
```  
  
## <a name="parts"></a>組件  
 Global  
 選擇性。 可讓您定義超出您的專案的根命名空間的命名空間。 請參閱[Visual Basic 中的命名空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)。  
  
 `name`  
 必要。 唯一名稱識別命名空間。 必須是有效的 Visual Basic 識別項。 如需詳細資訊，請參閱[宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。  
  
 `componenttypes`  
 選擇性。 命名空間所組成的項目。 這些包括但不限於列舉、 結構、 介面、 類別、 模組、 委派，以及其他命名空間。  
  
 `End Namespace`  
 終止`Namespace`區塊。  
  
## <a name="remarks"></a>備註  
 命名空間會作為組織的系統。 提供的方式來分類和呈現公開給其他程式和應用程式的程式設計項目。 請注意，命名空間不是*類型*類別或結構會在概念上，您無法宣告具有命名空間的資料類型的程式設計項目。  
  
 所有的程式設計項目宣告之後`Namespace`陳述式屬於該命名空間。 若要編譯至最後一個宣告的命名空間的項目，直到它遇到任何的 Visual Basic 會繼續`End Namespace`陳述式或另一個`Namespace`陳述式。  
  
 如果已定義命名空間，即使超出您的專案，您可以新增程式設計項目。 若要這樣做，您使用`Namespace`陳述式來直接 Visual Basic 編譯該命名空間中的項目。  
  
 您可以使用`Namespace`陳述式只能在檔案或命名空間層級。 這表示*宣告內容*命名空間必須是原始程式檔或另一個命名空間，而且不可為類別、 結構、 模組、 介面或程序。 如需詳細資訊，請參閱[宣告內容和預設存取層級](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。  
  
 您可以宣告在另一個命名空間。 您可以宣告，但是請記住，當其他程式碼存取的最內層的命名空間中宣告的項目時，它必須使用限定性條件字串，包含巢狀階層中的所有命名空間名稱的巢狀層級沒有嚴格限制。  
  
## <a name="access-level"></a>存取層級  
 命名空間會視為它們有`Public`存取層級。 從程式碼在同一個專案中的任何位置、 其他參考該專案的專案和專案所建立的任何組件，就可以存取命名空間。  
  
 命名空間層級，這表示命名空間中，但不是能在任何其他項目，在宣告的程式設計項目可以有`Public`或`Friend`存取。 如果未指定，這類的存取層級項目使用`Friend`預設。 您可以在命名空間層級宣告的項目包括類別、 結構、 模組、 介面、 列舉和委派。 如需詳細資訊，請參閱[宣告內容和預設存取層級](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。  
  
## <a name="root-namespace"></a>根命名空間  
 您的專案中的所有命名空間名稱根據*根命名空間*。 Visual Studio 會針對專案中的所有程式碼，將專案名稱指派為預設根命名空間。 例如，如果專案已命名為 `Payroll`，其程式設計項目會屬於命名空間 `Payroll`。 如果您宣告`Namespace funding`，該命名空間的完整名稱是`Payroll.funding`。  
  
 如果您想要指定現有的命名空間中`Namespace`陳述式，例如在泛型清單類別範例中，您可以設定您的根命名空間為 null 值。 若要這樣做，請按一下**專案屬性**從**專案**功能表，然後取消核取**根命名空間**項目以便方塊是空的。 如果您沒有這麼做在泛型清單類別範例中，Visual Basic 編譯器會採用`System.Collections.Generic`做為新專案中的命名空間`Payroll`，使用的完整名稱`Payroll.System.Collections.Generic`。  
  
 或者，您可以使用`Global`關鍵字來參考您的專案之外定義的命名空間的項目。 這樣可讓您保留您的專案名稱做為根命名空間。 這可減少意外合併程式設計項目與現有的命名空間的機會。 如需詳細資訊，請參閱中的 「 全域關鍵字中完整限定名稱 」 一節[在 Visual Basic 中的命名空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)。  
  
 `Global`關鍵字也可以用於命名空間陳述式。 這可讓您從專案的根命名空間定義一個命名空間。 如需詳細資訊，請參閱中的 「 全域關鍵字在命名空間陳述式 」 一節[在 Visual Basic 中的命名空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)。  
  
 **疑難排解。** 根命名空間可能會導致非預期的命名空間名稱的串連。 若要在專案外部定義的命名空間的參考，Visual Basic 編譯器會將它們是做為根命名空間中的巢狀命名空間。 在這種情況下，編譯器無法辨識已經定義外部命名空間中的任何型別。 若要避免這個問題，請將您的根命名空間設定為 「 根命名空間 」 中所述的 null 值，或使用`Global`關鍵字來存取的外部命名空間的項目。  
  
## <a name="attributes-and-modifiers"></a>屬性和修飾詞  
 您無法將屬性套用至命名空間。 屬性會提供資訊給組件的中繼資料，不是有意義的來源分類器，例如命名空間。  
  
 您無法將任何存取或程序修飾詞或任何其他修飾詞，套用至命名空間。 因為它不是型別，這些修飾詞並沒有意義。  
  
## <a name="example"></a>範例  
 下列範例會宣告兩個命名空間，其中巢狀方式置於另一個。  
  
 [!code-vb[VbVbalrStatements#43](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/namespace-statement_1.vb)]  
  
## <a name="example"></a>範例  
 下列範例會宣告多個巢狀命名空間在單一行中，它相當於先前的範例。  
  
 [!code-vb[VbVbalrStatements#41](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/namespace-statement_2.vb)]  
  
## <a name="example"></a>範例  
 下列範例會存取先前範例中定義的類別。  
  
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
 [Imports 陳述式 (.NET 命名空間和類型)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [在 Visual Basic 中的命名空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)
