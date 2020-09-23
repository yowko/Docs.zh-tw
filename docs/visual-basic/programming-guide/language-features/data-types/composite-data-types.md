---
title: 複合資料類型
ms.date: 04/25/2017
helpviewer_keywords:
- classes [Visual Basic], composite data types
- composite types [Visual Basic]
- composite data types [Visual Basic]
- data types [Visual Basic], composite
- arrays [Visual Basic], composite data types
- structures [Visual Basic], composite data types
- classes [Visual Basic], composite types
- types [Visual Basic], composite
ms.assetid: 62970f2e-52c0-4369-8963-613820f1f434
ms.openlocfilehash: 842b74aa7cc99c8196fdfb1eb6c976d9e72a4fa4
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077159"
---
# <a name="composite-data-types-visual-basic"></a>複合資料類型 (Visual Basic)

除了 Visual Basic 提供的基本資料類型之外，您還可以組合不同類型的專案來建立 *複合資料型別* ，例如結構、陣列和類別。 您可以從基本類型和其他複合類型建立複合資料型別。 例如，您可以定義結構專案的陣列，或具有陣列成員的結構。  
  
## <a name="data-types"></a>資料類型  

 複合類型與其任何元件的資料類型不同。 例如，元素的陣列 `Integer` 不是 `Integer` 資料類型。  
  
 陣列資料類型通常會在必要時使用元素類型、括弧和逗號來表示。 例如，一維 `String` 元素陣列以表示 `String()` ，而一維元素的二維陣列 `Boolean` 則表示為 `Boolean(,)` 。  
  
## <a name="structure-types"></a>結構類型  

 沒有任何單一資料類型組成所有結構。 相反地，結構的每個定義都代表一個唯一的資料類型，即使兩個結構以相同順序定義相同的專案也是一樣。 但是，如果您建立兩個或多個相同結構的實例，Visual Basic 會將它們視為相同的資料類型。  
  
## <a name="tuples"></a>Tuple

元組是輕量結構，其中包含兩個或多個已預先定義類型的欄位。 從 Visual Basic 2017 開始支援元組。 元組最常用來從單一方法呼叫傳回多個值，而不需要以傳址方式傳遞引數，或將傳回的欄位封裝在更高的權數類別或結構中。 如需有關元組的詳細資訊，請參閱「 [元組](tuples.md) 」主題。

## <a name="array-types"></a>陣列類型  

 沒有任何單一資料類型組成所有陣列。 陣列的特定實例的資料類型取決於下列各項：  
  
- 成為陣列的事實  
  
- 陣列) 維度的排名 (數目  
  
- 陣列的元素類型  
  
 尤其是，給定維度的長度不是實例之資料類型的一部分。 下列範例將說明這點。  
  
```vb  
Dim arrayA( ) As Byte = New Byte(12) {}  
Dim arrayB( ) As Byte = New Byte(100) {}  
Dim arrayC( ) As Short = New Short(100) {}  
Dim arrayD( , ) As Short  
Dim arrayE( , ) As Short = New Short(4, 10) {}  
```  
  
 在上述範例中，陣列變數 `arrayA` 和 `arrayB` 都會被視為相同的資料類型， `Byte()` 即使它們已初始化為不同的長度也一樣。 變數 `arrayB` 和 `arrayC` 不是相同的類型，因為它們的元素類型不同。 變數 `arrayC` 和 `arrayD` 不屬於相同類型，因為它們的排名不同。 變數 `arrayD` 和 `arrayE` 具有相同的類型（ `Short(,)` ），因為它們的排名和元素類型都相同，即使尚未 `arrayD` 初始化。  
  
 如需陣列的詳細資訊，請參閱 [陣列](../arrays/index.md)。  
  
## <a name="class-types"></a>類別類型  

 沒有包含所有類別的單一資料類型。 雖然一個類別可以繼承自另一個類別，但每個類別都是個別的資料類型。 相同類別的多個實例屬於相同的資料類型。 如果您將一個類別執行個體變數指派給另一個類別執行個體變數，則不僅它們具有相同的資料類型，也會指向記憶體中的相同類別實例。  
  
 如需類別的詳細資訊，請參閱 [物件和類別](../objects-and-classes/index.md)。  
  
## <a name="see-also"></a>另請參閱

- [Data types (資料類型)](index.md)
- [基礎資料類型](elementary-data-types.md)
- [Generic Types in Visual Basic](generic-types.md)
- [Value Types and Reference Types](value-types-and-reference-types.md)
- [Visual Basic 中的類型轉換](type-conversions.md)
- [結構](structures.md)
- [疑難排解資料類型的問題](troubleshooting-data-types.md)
- [作法：在變數中存放多個值](how-to-hold-more-than-one-value-in-a-variable.md)
