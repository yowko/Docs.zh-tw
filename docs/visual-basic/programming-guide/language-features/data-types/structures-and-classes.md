---
title: 結構與類別
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], vs. structures
- structures [Visual Basic]
- classes [Visual Basic]
- structures [Visual Basic], compared to classes
- structures [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: a221e74a-ffcf-4bdc-a0f6-a088a9bf26cc
ms.openlocfilehash: 3353935a74bb77fa4a630e706aa425063c7a610a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346321"
---
# <a name="structures-and-classes-visual-basic"></a>結構和類別 (Visual Basic)
Visual Basic 會將結構和類別的語法統一，而且這兩個實體都支援相同的大部分功能。 不過，結構與類別之間也有重要的差異。  
  
 類別的優點是參考型別，傳遞參考比傳遞結構變數及其所有資料更有效率。 另一方面，結構不需要在全域堆積上配置記憶體。  
  
 因為您無法從結構繼承，所以結構應該僅用於不需要擴充的物件。 當您想要建立的物件具有小型實例大小時，請使用結構，並將類別與結構的效能特性納入考慮。  
  
## <a name="similarities"></a>相似  
 結構和類別在下列方面很類似：  
  
- 兩者都是*容器*類型，這表示它們包含其他類型做為成員。  
  
- 兩者都有成員，其中可以包含函數、方法、屬性、欄位、常數、列舉、事件和事件處理常式。 不過，請不要將這些成員與結構的宣告*元素*混淆。  
  
- 兩者的成員可以具有個人化的存取層級。 例如，一個成員可以 `Public` 宣告，另一個 `Private`。  
  
- 兩者都可以執行介面。  
  
- 兩者都可以有共用的處理函式，以及或不含參數。  
  
- 這兩者都可以公開*預設屬性*，前提是該屬性至少接受一個參數。  
  
- 兩者都可以宣告和引發事件，而且兩者都可以宣告委派。  
  
## <a name="differences"></a>差異  
 結構和類別在下列細節方面有所不同：  
  
- 結構是實*數值型別*;類別是*參考型別*。 結構類型的變數包含結構的資料，而不是包含資料的參考做為類別類型。  
  
- 結構使用堆疊配置;類別會使用堆積配置。  
  
- 預設會 `Public` 所有結構元素;預設會 `Private` 類別變數和常數，而其他類別成員則 `Public` 預設。 類別成員的這個行為會提供與 Visual Basic 6.0 系統預設值的相容性。  
  
- 結構必須至少有一個非共用的變數或非共用的 noncustom 事件元素;類別可以完全空白。  
  
- 結構元素不可以宣告為 `Protected`;類別成員可以。  
  
- 結構程式只能處理事件（如果它是[共用](../../../../visual-basic/language-reference/modifiers/shared.md)的`Sub` 程式），而且只能使用[AddHandler 語句](../../../../visual-basic/language-reference/statements/addhandler-statement.md);任何類別程式都可以使用[Handles](../../../../visual-basic/language-reference/statements/handles-clause.md)關鍵字或 `AddHandler` 語句來處理事件。 如需詳細資訊，請參閱 [事件](../../../../visual-basic/programming-guide/language-features/events/index.md)中定義的介面的私用 C++ 專屬實作。  
  
- 結構變數宣告不能指定陣列的初始化運算式或初始大小;類別變數宣告可以。  
  
- 結構會隱含繼承自 <xref:System.ValueType?displayProperty=nameWithType> 類別，而且無法繼承自任何其他類型;類別可以繼承自 <xref:System.ValueType?displayProperty=nameWithType>以外的任何類別或類別。  
  
- 結構不可繼承;類別為。  
  
- 結構永遠不會終止，因此 common language runtime （CLR）永遠不會在任何結構上呼叫 <xref:System.Object.Finalize%2A> 方法。類別會由垃圾收集行程（GC）終止，當偵測不到任何使用中的參考時，會呼叫類別上的 <xref:System.Object.Finalize%2A>。  
  
- 結構不需要使用函數，類別會執行。  
  
- 結構只有在接受參數時，才可以有非共用的函式;類別可以有或不使用參數。  
  
 每個結構都有一個不含參數的隱含公用函數。 此函式會將所有結構的資料元素初始化為其預設值。 您無法重新定義此行為。  
  
## <a name="instances-and-variables"></a>實例和變數  
 因為結構是實值型別，所以每個結構變數都會永久系結至個別的結構實例。 但是類別是參考型別，而物件變數可以在不同的時間參考各種類別實例。 這項區別會以下列方式影響您對結構和類別的使用：  
  
- **初始.** 結構變數會使用結構的無參數的函式，隱含地包含初始化元素。 因此，`Dim s As struct1` 相當於 `Dim s As struct1 = New struct1()`。  
  
- **指派變數。** 當您將某個結構變數指派給另一個，或將結構實例傳遞給程式引數時，所有變數元素的目前值都會複製到新的結構。 當您將某個物件變數指派給另一個，或將物件變數傳遞至程式時，只會複製參考指標。  
  
- **不指派任何內容。** 您可以將值 [[無](../../../../visual-basic/language-reference/nothing.md)] 指派給結構變數，但是實例會繼續與變數相關聯。 您仍然可以呼叫其方法並存取其資料元素，雖然指派會重新初始化變數元素。  
  
     相反地，如果您將物件變數設定為 `Nothing`，就會將它與任何類別實例中斷關聯，而且您無法透過變數存取任何成員，直到您將另一個實例指派給它為止。  
  
- **多個實例。** 物件變數可以在不同時間指派不同的類別實例，而且有數個物件變數可以同時參考相同的類別實例。 當您對類別成員的值所做的變更，會在透過指向相同實例的另一個變數存取時，影響這些成員。  
  
     不過，結構專案會隔離在自己的實例中。 對其值所做的變更不會反映在其他任何結構變數中，即使在相同 `Structure` 宣告的其他實例中也一樣。  
  
- **等效.** 兩個結構的相等測試必須以元素 by 元素測試來執行。 您可以使用 <xref:System.Object.Equals%2A> 方法來比較兩個物件變數。 <xref:System.Object.Equals%2A> 指出兩個變數是否指向相同的實例。  
  
## <a name="see-also"></a>請參閱

- [資料類型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [複合資料類型](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [值類型和參考類型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [結構](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [資料類型的疑難排解](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [結構和其他程式設計項目](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)
- [物件和類別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
