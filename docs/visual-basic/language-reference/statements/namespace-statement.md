---
title: Namespace 陳述式
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
ms.openlocfilehash: 0f1ba9a038fc604b6e4ede758891832e087fc096
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404430"
---
# <a name="namespace-statement"></a>Namespace 陳述式
宣告命名空間的名稱，並使宣告後面的原始程式碼在該命名空間內進行編譯。  
  
## <a name="syntax"></a>語法  
  
```vb  
Namespace [Global.] { name | name.name }  
    [ componenttypes ]  
End Namespace  
```  
  
## <a name="parts"></a>組件  
 全球  
 選擇性。 可讓您從專案的根命名空間定義命名空間。 請參閱[Visual Basic 中的命名空間](../../programming-guide/program-structure/namespaces.md)。  
  
 `name`  
 必要。 識別命名空間的唯一名稱。 必須是有效的 Visual Basic 識別碼。 如需詳細資訊，請參閱宣告的[元素名稱](../../programming-guide/language-features/declared-elements/declared-element-names.md)。  
  
 `componenttypes`  
 選擇性。 組成命名空間的元素。 這些包括（但不限於）列舉、結構、介面、類別、模組、委派和其他命名空間。  
  
 `End Namespace`  
 結束 `Namespace` 區塊。  
  
## <a name="remarks"></a>備註  
 命名空間是當做組織系統使用。 它們提供一種方式來分類和呈現公開給其他程式和應用程式的程式設計項目。 請注意，命名空間不是類別或結構所用的*型*別，您無法宣告程式設計專案以具有命名空間的資料型別。  
  
 在語句之後宣告的所有程式設計項目都 `Namespace` 屬於該命名空間。 Visual Basic 會繼續將專案編譯成最後一個已宣告的命名空間，直到遇到 `End Namespace` 語句或另一個 `Namespace` 語句為止。  
  
 如果已定義命名空間，甚至是在您的專案之外，您可以在其中加入程式設計項目。 若要這樣做，您可以使用 `Namespace` 語句來指示 Visual Basic 將元素編譯到該命名空間。  
  
 您 `Namespace` 只能在檔案或命名空間層級使用語句。 這表示命名空間的宣告*內容*必須是原始程式檔或其他命名空間，而且不能是類別、結構、模組、介面或程式。 如需詳細資訊，請參閱[宣告內容和預設存取層級](declaration-contexts-and-default-access-levels.md)。  
  
 您可以在另一個命名空間內宣告。 您可以宣告的嵌套層級沒有嚴格的限制，但請記住，當其他程式碼存取最內層命名空間中宣告的元素時，它必須使用包含在嵌套階層架構中所有命名空間名稱的限定性字串。  
  
## <a name="access-level"></a>存取層級  
 命名空間會被視為具有 `Public` 存取層級。 命名空間可以從相同專案中的程式碼、從參考專案的其他專案，以及從專案所建立的任何元件中存取。  
  
 在命名空間層級宣告的程式設計項目（表示在命名空間中，但不在任何其他專案內）可以擁有 `Public` 或 `Friend` 存取。 如果未指定，這類元素的存取層級 `Friend` 預設會使用。 您可以在命名空間層級宣告的元素包括類別、結構、模組、介面、列舉和委派。 如需詳細資訊，請參閱[宣告內容和預設存取層級](declaration-contexts-and-default-access-levels.md)。  
  
## <a name="root-namespace"></a>根命名空間  
 專案中的所有命名空間名稱都是以*根命名空間*為基礎。 Visual Studio 會針對專案中的所有程式碼，將專案名稱指派為預設根命名空間。 例如，如果專案已命名為 `Payroll`，其程式設計項目會屬於命名空間 `Payroll`。 如果您宣告 `Namespace funding` ，該命名空間的完整名稱會是 `Payroll.funding` 。  
  
 如果您想要在語句中指定現有的命名空間 `Namespace` ，例如在泛型清單類別範例中，您可以將根命名空間設定為 null 值。 若要這樣做，請從 [**專案**] 功能表中按一下 [**專案屬性**]，然後清除 [**根命名空間**] 專案，讓方塊空白。 如果您未在泛型清單類別範例中執行此動作，Visual Basic 編譯器會採用 `System.Collections.Generic` 專案內的新命名空間 `Payroll` ，其完整名稱為 `Payroll.System.Collections.Generic` 。  
  
 或者，您可以使用 `Global` 關鍵字來參考在專案外部定義的命名空間元素。 這麼做可讓您保留專案名稱做為根命名空間。 這可減少不小心將您的程式設計項目與現有命名空間的合併在一起的機會。 如需詳細資訊，請參閱[Visual Basic 的命名空間](../../programming-guide/program-structure/namespaces.md)中的「完整名稱中的全域關鍵字」一節。  
  
 `Global`關鍵字也可以在 Namespace 語句中使用。 這可讓您從專案的根命名空間定義一個命名空間。 如需詳細資訊，請參閱[Visual Basic 的命名](../../programming-guide/program-structure/namespaces.md)空間中的「命名空間語句中的全域關鍵字」一節。  
  
 **疑難排解.** 根命名空間可能會導致非預期的命名空間名稱串連。 如果您參考在專案外部定義的命名空間，Visual Basic 編譯器可以在根命名空間中將其 construe 為嵌套命名空間。 在這種情況下，編譯器無法辨識已在外部命名空間中定義的任何類型。 若要避免這個情況，請將根命名空間設定為 null 值（如「根命名空間」中所述），或使用 `Global` 關鍵字來存取外部命名空間的元素。  
  
## <a name="attributes-and-modifiers"></a>屬性和修飾詞  
 您無法將屬性套用至命名空間。 屬性會將資訊提供給元件的中繼資料，這對來源分類器（例如命名空間）沒有意義。  
  
 您不能將任何存取或程式修飾詞或任何其他修飾詞套用至命名空間。 因為這不是型別，所以這些修飾詞沒有意義。  
  
## <a name="example"></a>範例  
 下列範例會宣告兩個命名空間，其中一個是在另一個。  
  
 [!code-vb[VbVbalrStatements#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#43)]  
  
## <a name="example"></a>範例  
 下列範例會在單一程式列上宣告多個嵌套的命名空間，而且它相當於先前的範例。  
  
 [!code-vb[VbVbalrStatements#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#41)]  
  
## <a name="example"></a>範例  
 下列範例會存取先前範例中定義的類別。  
  
 [!code-vb[VbVbalrStatements#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#42)]  
  
## <a name="example"></a>範例  
 下列範例會定義新泛型清單類別的基本架構，並將其新增至 <xref:System.Collections.Generic?displayProperty=nameWithType> 命名空間。  
  
```vb  
Namespace System.Collections.Generic  
    Class specialSortedList(Of T)  
        Inherits List(Of T)  
        ' Insert code to define the special generic list class.  
    End Class  
End Namespace  
```  
  
## <a name="see-also"></a>另請參閱

- [Imports 陳述式 (.NET 命名空間和類型)](imports-statement-net-namespace-and-type.md)
- [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md)
- [Visual Basic 中的命名空間](../../programming-guide/program-structure/namespaces.md)
