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
ms.openlocfilehash: e7ca5b9d55611eafad88517e71f9807fe2aa4416
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91086214"
---
# <a name="structures-and-classes-visual-basic"></a>結構和類別 (Visual Basic)

Visual Basic 統一結構和類別的語法，結果是兩個實體都支援大部分相同的功能。 不過，結構和類別之間也有重要的差異。  
  
 類別具有參考型別的優點：傳遞參考比傳遞結構變數及其所有資料更有效率。 另一方面，結構不需要在全域堆積上配置記憶體。  
  
 因為您無法從結構繼承，所以結構應該僅用於不需要擴充的物件。 當您想要建立的物件具有小型實例大小時，請使用結構，並考慮類別與結構的效能特性。  
  
## <a name="similarities"></a>相似 之 處  

 結構和類別在下列方面很類似：  
  
- 兩者都是 *容器* 類型，表示它們包含其他類型作為成員。  
  
- 兩者都具有成員，這些成員可以包含函式、方法、屬性、欄位、常數、列舉、事件和事件處理常式。 不過，請勿將這些成員與結構的宣告 *元素* 混淆。  
  
- 兩者的成員都可以有個別的存取層級。 例如，您可以宣告一個成員 `Public` 和另一個成員 `Private` 。  
  
- 兩者都可以執行介面。  
  
- 兩者都可以有共用的函式，其中包含或不含參數。  
  
- 兩者都可以公開 *預設屬性*，前提是該屬性至少接受一個參數。  
  
- 兩者都可以宣告和引發事件，而且兩者都可以宣告委派。  
  
## <a name="differences"></a>差異  

 結構和類別在下列細節中有不同：  
  
- 結構是實 *數值型別*;類別是 *參考型別*。 結構類型的變數包含結構的資料，而不是包含資料的參考做為類別類型。  
  
- 結構使用堆疊配置;類別使用堆積配置。  
  
- 依預設，所有結構專案都是 `Public` ; 類別變數和常數預設為 `Private` ，其他類別成員則 `Public` 預設為。 類別成員的這個行為會提供與預設 Visual Basic 6.0 系統的相容性。  
  
- 結構至少必須有一個非共用變數或非共用的 noncustom 事件元素;類別可以完全空白。  
  
- 結構元素不能宣告為 `Protected` ; 類別成員可以。  
  
- 結構程式只有在它是[共用](../../../language-reference/modifiers/shared.md)的程式時才能處理事件 `Sub` ，而只有透過[AddHandler 語句](../../../language-reference/statements/addhandler-statement.md)才能處理事件; 任何類別程式都可以使用[Handles](../../../language-reference/statements/handles-clause.md)關鍵字或語句來處理事件 `AddHandler` 。 如需詳細資訊，請參閱[事件](../events/index.md)。  
  
- 結構變數宣告不能指定初始化運算式或陣列的初始大小;類別變數宣告可以。  
  
- 結構隱含繼承自 <xref:System.ValueType?displayProperty=nameWithType> 類別，無法繼承自任何其他類型; 類別可以繼承自以外的任何類別或類別 <xref:System.ValueType?displayProperty=nameWithType> 。  
  
- 結構無法繼承;類別為。  
  
- 結構永遠不會終止，因此 common language runtime (CLR) 永遠不會 <xref:System.Object.Finalize%2A> 在任何結構上呼叫方法; 類別會由垃圾收集行程終止 (GC) ， <xref:System.Object.Finalize%2A> 當偵測到沒有任何作用中的參考時，就會在類別上呼叫。  
  
- 結構不需要函式;類別會執行。  
  
- 結構只有在使用參數時，才可以有非共用的函式;類別可以有或不使用參數。  
  
 每個結構都有不含參數的隱含公用函數。 這個函式會將所有結構的資料元素初始化為其預設值。 您無法重新定義此行為。  
  
## <a name="instances-and-variables"></a>實例和變數  

 因為結構是實值型別，所以每個結構變數都會永久系結至個別的結構實例。 但是類別是參考型別，而物件變數可以在不同的時間參考不同的類別實例。 這項差異會以下列方式影響結構和類別的使用方式：  
  
- **初始 化。** 結構變數會使用結構的無參數函式，以隱含的方式包含元素的初始化。 因此， `Dim s As struct1` 相當於 `Dim s As struct1 = New struct1()` 。  
  
- **指派變數。** 當您將某個結構變數指派給另一個結構變數，或是將結構實例傳遞至程式引數時，所有變數元素的目前值都會複製到新的結構。 當您將某個物件變數指派給另一個物件變數，或將物件變數傳遞至程式時，只會複製參考指標。  
  
- **不指派任何專案。** 您可以將值 [Nothing](../../../language-reference/nothing.md) 指派給結構變數，但實例會繼續與變數相關聯。 您仍然可以呼叫其方法並存取其資料元素，但變數元素會由指派重新初始化。  
  
     相反地，如果您將物件變數設定為 `Nothing` ，就會將它與任何類別實例解除關聯，而您將無法透過變數來存取任何成員，除非您指派另一個實例給它。  
  
- **多個實例。** 物件變數可以在不同的時間指派不同的類別實例，而且有數個物件變數可以同時參考相同的類別實例。 您對類別成員的值所做的變更，會在透過指向相同實例的另一個變數存取時影響這些成員。  
  
     不過，結構專案會在自己的實例中隔離。 值的變更不會反映在任何其他結構變數中，即使在相同宣告的其他實例中也一樣 `Structure` 。  
  
- **平等。** 兩個結構的等號比較測試必須以元素元素測試來執行。 您可以使用方法來比較兩個物件變數 <xref:System.Object.Equals%2A> 。 <xref:System.Object.Equals%2A> 指出兩個變數是否指向相同的實例。  
  
## <a name="see-also"></a>另請參閱

- [Data types (資料類型)](index.md)
- [複合資料類型](composite-data-types.md)
- [Value Types and Reference Types](value-types-and-reference-types.md)
- [結構](structures.md)
- [疑難排解資料類型的問題](troubleshooting-data-types.md)
- [結構與其他程式設計項目](structures-and-other-programming-elements.md)
- [物件和類別](../objects-and-classes/index.md)
