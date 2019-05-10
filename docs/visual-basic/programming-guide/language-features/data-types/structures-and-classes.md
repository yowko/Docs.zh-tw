---
title: 結構和類別 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], vs. structures
- structures [Visual Basic]
- classes [Visual Basic]
- structures [Visual Basic], compared to classes
- structures [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: a221e74a-ffcf-4bdc-a0f6-a088a9bf26cc
ms.openlocfilehash: b947109f99d94b0ecb1d798835c311f2374e96fc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64601016"
---
# <a name="structures-and-classes-visual-basic"></a>結構和類別 (Visual Basic)
Visual Basic 統一的語法結構和類別，因為這兩個實體支援的大部分相同的功能。 不過，還有結構和類別的重要差異。  
  
 類別具有的優點是參考型別，將參考傳遞的效率高於傳遞結構的變數，它的所有資料。 相反地，結構不需要全域堆積上的記憶體配置。  
  
 因為您無法從結構繼承，所以結構應該僅適用於不需要擴充的物件。 當您想要建立的物件具有小型執行個體的大小，並考慮類別與結構的效能特性，請使用結構。  
  
## <a name="similarities"></a>相似之處  
 結構和類別是在下列方面類似：  
  
- 兩者都*容器*類型，這表示它們包含為成員的其他型別。  
  
- 兩者都有建構函式、 方法、 屬性、 欄位、 常數、 列舉型別、 事件和事件處理常式可以包含的成員。 不過，不會混淆與宣告這些成員*項目*的結構。  
  
- 兩者的成員都有各自的存取層級。 例如，可以宣告一個成員`Public`是另一個`Private`。  
  
- 兩者都可以實作介面。  
  
- 兩者都可以有共用的建構函式，使用或不含參數。  
  
- 兩者都可以公開*屬性預設*，前提是屬性會採用至少一個參數。  
  
- 兩者都可以宣告和引發事件，而兩者都可以宣告委派。  
  
## <a name="differences"></a>差異  
 結構和類別的差異如下：  
  
- 結構*實值型別*; 類別是*參考型別*。 結構類型的變數包含的結構資料，而不是未包含的資料做為類別類型的參考。  
  
- 結構會使用堆疊配置;類別會使用堆積配置。  
  
- 所有的結構項目都`Public`根據預設，類別變數和常數`Private`根據預設，其他類別成員時`Public`預設。 類別成員的此行為可提供與 Visual Basic 6.0 系統的預設值的相容性。  
  
- 結構必須有至少一個非共用變數，或將非共用，非自訂事件項目;類別可以是完全空白的。  
  
- 結構項目不可以宣告為`Protected`; 類別的成員可以。  
  
- 結構的程序可以處理事件時才[Shared](../../../../visual-basic/language-reference/modifiers/shared.md) `Sub`程序，並只利用[AddHandler 陳述式](../../../../visual-basic/language-reference/statements/addhandler-statement.md); 類別中的任何程序可以處理事件，使用任一[會處理](../../../../visual-basic/language-reference/statements/handles-clause.md)關鍵字或`AddHandler`陳述式。 如需詳細資訊，請參閱[事件](../../../../visual-basic/programming-guide/language-features/events/index.md)。  
  
- 結構變數宣告不能指定初始設定式或陣列; 的初始大小可以類別變數的宣告。  
  
- 結構會隱含地繼承自<xref:System.ValueType?displayProperty=nameWithType>類別，並無法繼承自任何其他型別，而非類別繼承自任何類別或類別<xref:System.ValueType?displayProperty=nameWithType>。  
  
- 結構是無法繼承;類別是。  
  
- 結構永遠不會終止，因此 common language runtime (CLR) 永遠不會呼叫<xref:System.Object.Finalize%2A>上的任何結構; 方法類別會由記憶體回收行程 (GC)，它會呼叫終止<xref:System.Object.Finalize%2A>上時偵測到沒有作用中參考的類別剩餘的。  
  
- 結構不需要建構函式類別會執行。  
  
- 結構可以具有非共用的建構函式才會顯示參數;類別可以讓它們使用或不加任何參數。  
  
 每個結構會有不含參數的隱含公用建構函式。 這個建構函式會初始化為其預設值的所有結構的資料元素。 您無法重新定義此行為。  
  
## <a name="instances-and-variables"></a>執行個體與變數  
 因為結構是實值型別，則每個結構變數是永久繫結至個別的結構執行個體中。 類別是參考型別，但物件變數時，可以參考到各種不同的類別執行個體上，在不同的時間。 這項區別會以下列方式影響結構和類別的使用方式：  
  
- **初始化。** 結構變數隱含包含項目使用該結構的無參數建構函式的初始化。 因此，`Dim s As struct1`相當於`Dim s As struct1 = New struct1()`。  
  
- **指派變數。** 當您將一個結構變數指派給另一個，或結構執行個體傳遞給程序引數時，就會將目前值的所有變數的項目複製到新的結構。 當您將一個物件變數指派給另一個，或傳遞至程序的物件變數時，只會複製參考指標。  
  
- **指派執行任何動作。** 您可以將值指派[Nothing](../../../../visual-basic/language-reference/nothing.md)結構變數，但執行個體將繼續與變數相關聯。 您仍然可以呼叫其方法，並存取其資料元素，但變數的項目會藉由指派而重新初始化。  
  
     相反地，如果您設定物件變數`Nothing`中斷任何類別執行個體中，且您無法透過變數存取的任何成員，直到您指派給它的另一個執行個體。  
  
- **多個執行個體。** 物件變數可以有不同的類別執行個體指派給它，在不同的時間和數個物件變數時，可以參考相同的類別執行個體上，在相同的時間。 您對類別成員的值變更會影響時透過指向相同的執行個體的另一個變數來存取這些成員。  
  
     不過，結構項目，都隔離在自己的執行個體。 其值的變更不會反映在任何其他結構變數，即使是在相同的其他執行個體`Structure`宣告。  
  
- **相等。** 與項目依項目測試必須執行兩個結構的等號比較測試。 可以比較兩個物件變數，使用<xref:System.Object.Equals%2A>方法。 <xref:System.Object.Equals%2A> 指出兩個變數是否指向相同的執行個體。  
  
## <a name="see-also"></a>另請參閱

- [資料類型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [複合資料類型](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [結構](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [資料類型的疑難排解](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [結構和其他程式設計項目](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)
- [物件和類別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
