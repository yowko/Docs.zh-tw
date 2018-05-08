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
ms.openlocfilehash: e64b54b93463845dd9afd0c0efd0e39f20cab1ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="structures-and-classes-visual-basic"></a>結構和類別 (Visual Basic)
Visual Basic 統一的語法結構和類別，因為這兩個實體支援的大部分相同的功能。 不過，另外還有結構和類別之間的重要差異。  
  
 類別具有參考類型的優點，傳遞參考會比將它的資料結構變數傳遞更有效率。 相反地，結構不需要全域堆積上的記憶體配置。  
  
 您無法從結構繼承，因為結構應該只能用於不需要擴充的物件。 當您想要建立的物件有小型執行個體的大小，並考慮類別與結構的效能特性，請使用結構。  
  
## <a name="similarities"></a>相似之處  
 結構和類別是在下列方面類似：  
  
-   兩者都是*容器*類型，這表示它們包含為成員的其他類型。  
  
-   兩者都有建構函式、 方法、 屬性、 欄位、 常數、 列舉型別、 事件和事件處理常式可包含的成員。 不過，請勿混淆與宣告這些成員*元素*的結構。  
  
-   兩者的成員都有各自的存取層級。 例如，可以宣告一個成員`Public`和另一個`Private`。  
  
-   兩者都可以實作介面。  
  
-   同時可以有共用的建構函式，使用或不含參數。  
  
-   兩者都公開*預設屬性*，前提是屬性會使用至少一個參數。  
  
-   兩者都可以宣告和引發事件，而且兩者都可以宣告委派。  
  
## <a name="differences"></a>差異  
 結構和類別的差異如下：  
  
-   兩個結構*實值型別的*; 類別是*參考型別*。 結構類型的變數包含的結構資料，而不是未包含的資料做為類別類型的參考。  
  
-   結構會使用堆疊配置;類別會使用堆積配置。  
  
-   結構的所有項目是`Public`依預設，類別變數和常數是`Private`根據預設，其他類別成員時`Public`預設。 類別成員的這個行為可提供與 Visual Basic 6.0 系統的預設值的相容性。  
  
-   結構必須具有至少一個非共用變數或非共用，非自訂事件項目。類別可以完全空白。  
  
-   結構項目不能宣告為`Protected`; 可以類別成員。  
  
-   結構的程序可以處理事件，只有在[共用](../../../../visual-basic/language-reference/modifiers/shared.md)`Sub`程序，並只透過的方式[AddHandler 陳述式](../../../../visual-basic/language-reference/statements/addhandler-statement.md); 類別中的任何程序可以處理使用其中一個事件[處理](../../../../visual-basic/language-reference/statements/handles-clause.md)關鍵字或`AddHandler`陳述式。 如需詳細資訊，請參閱[事件](../../../../visual-basic/programming-guide/language-features/events/index.md)。  
  
-   結構變數宣告不能指定初始設定式或陣列; 的初始大小可以類別變數宣告。  
  
-   結構會隱含繼承自<xref:System.ValueType?displayProperty=nameWithType>類別，並無法繼承自任何其他類型; 不是類別繼承自任何類別或類別<xref:System.ValueType?displayProperty=nameWithType>。  
  
-   結構是無法繼承。類別是。  
  
-   結構會永遠不會終止，因此 common language runtime (CLR) 永遠不會呼叫<xref:System.Object.Finalize%2A>任何結構; 上的方法類別會在記憶體回收行程 (GC)，它會呼叫終止<xref:System.Object.Finalize%2A>上時偵測到沒有作用中參考的類別其餘的。  
  
-   結構不需要建構函式。類別會執行。  
  
-   結構可以具有非共用的建構函式才會顯示參數。類別可以讓他們具有或不含參數。  
  
 每個結構會有不含參數的隱含公用建構函式。 這個建構函式會初始化成為其預設值結構的所有資料元素。 您不能重新定義此行為。  
  
## <a name="instances-and-variables"></a>執行個體和變數  
 結構是實值類型，因為每個結構變數會永久繫結至個別結構執行個體。 類別是參考類型，但物件變數可以參考不同的類別執行個體在不同的時間。 區別這兩者會以下列方式影響結構和類別的使用方式：  
  
-   **初始化。** 結構變數隱含包含項目使用該結構的無參數建構函式的初始化。 因此，`Dim s As struct1`相當於`Dim s As struct1 = New struct1()`。  
  
-   **指派變數。** 當您將一個結構變數指派給另一個，或將結構執行個體傳遞至程序引數時，目前的值的所有變數的項目會複製到新的結構。 當您將一個物件變數指派給另一個，或傳遞至程序的物件變數時，只會複製參考指標。  
  
-   **指定執行任何動作。** 您可以將值指派[Nothing](../../../../visual-basic/language-reference/nothing.md)結構變數，但執行個體仍然能夠繼續與變數相關聯。 您仍可以呼叫其方法及存取其資料元素，但重新指派所初始化變數的項目。  
  
     相反地，如果您設定物件變數`Nothing`中斷與從任何類別執行個體，直到您將另一個執行個體指派給它，您無法透過變數存取的任何成員。  
  
-   **多個執行個體。** 物件變數可以有不同的類別執行個體指派給它，在不同的時間和數個物件變數可以參考相同的類別執行個體在相同的時間。 您對類別成員的值變更會影響存取透過指向相同的執行個體的另一個變數時，那些成員。  
  
     結構項目，不過，會隔離在自己的執行個體。 其值的變更不會反映在任何其他結構變數，即使是在相同的其他執行個體`Structure`宣告。  
  
-   **相等。** 與項目依項目測試必須執行的兩個結構相等測試。 可以使用比較兩個物件變數<xref:System.Object.Equals%2A>方法。 <xref:System.Object.Equals%2A> 指出兩個變數是否指向相同的執行個體。  
  
## <a name="see-also"></a>另請參閱  
 [資料類型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [複合資料類型](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [值類型和參考類型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [結構](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [資料類型的疑難排解](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [結構和其他程式設計項目](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)  
 [物件和類別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
