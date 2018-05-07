---
title: Visual Basic 中的範圍
ms.date: 07/20/2015
helpviewer_keywords:
- module scope [Visual Basic]
- scope [Visual Basic], levels
- module level
- procedures [Visual Basic], scope
- declared elements [Visual Basic], scope
- namespaces [Visual Basic], scope
- scope [Visual Basic], declared elements
- scope [Visual Basic], about scope
- levels of scope [Visual Basic]
- block scope [Visual Basic]
- scope [Visual Basic], Visual Basic
- procedure scope [Visual Basic]
ms.assetid: 208106fe-79c9-4eec-93c6-55f08548895f
ms.openlocfilehash: d6692379626d787b728d6e92bd447c4a96e6680e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="scope-in-visual-basic"></a>Visual Basic 中的範圍
*範圍*的宣告的項目是 所有程式碼，而不需要限定其名稱，或透過參考一組[Imports 陳述式 （.NET 命名空間和類型）](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)。 元素可以有範圍，在下列層級的其中一個：  
  
|層級|描述|  
|-----------|-----------------|  
|區塊範圍|只有在程式碼內的可用區塊內宣告|  
|程序範圍|適用於在宣告它的程序中的所有程式碼|  
|模組範圍|提供給內模組、 類別或結構宣告它的所有程式碼|  
|命名空間範圍|提供給所有的程式碼會宣告命名空間中|  
  
 這些範圍的層級的最少的 （區塊） 從在寬 （命名空間），其中*最小範圍*表示無限制的項目可以參考程式碼的最小集。 如需詳細資訊，請參閱此頁面上的 「 範圍層級 」。  
  
## <a name="specifying-scope-and-defining-variables"></a>指定範圍，以及定義變數  
 當您宣告它時，您可以指定項目的範圍。 範圍可能會相依於下列因素：  
  
-   您可以在其中宣告項目區域 （區塊、 程序、 模組、 類別或結構）  
  
-   包含的項目宣告的命名空間  
  
-   您宣告的項目存取層級  
  
 注意當您定義使用變數具有相同名稱但不同的範圍，因為這樣做可能會造成非預期的結果。 如需詳細資訊，請參閱 [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)。  
  
## <a name="levels-of-scope"></a>範圍層級  
 整個區域宣告它使用的程式設計項目。 相同區域中的所有程式碼可以參考的項目中，而不需要限定其名稱。  
  
### <a name="block-scope"></a>區塊範圍  
 一個區塊是一組陳述式括住初始和終止宣告陳述式，如下所示：  
  
-   `Do` 和 `Loop`  
  
-   `For` [`Each`] 和 `Next`  
  
-   `If` 和 `End If`  
  
-   `Select` 和 `End Select`  
  
-   `SyncLock` 和 `End SyncLock`  
  
-   `Try` 和 `End Try`  
  
-   `While` 和 `End While`  
  
-   `With` 和 `End With`  
  
 如果您宣告的變數在區塊內，您可以使用它只在該區塊內。 在下列範例中，整數變數的範圍`cube`之間區塊`If`和`End If`，而且您可以不再參考`cube`當執行會通過區塊之外。  
  
```  
If n < 1291 Then  
    Dim cube As Integer  
    cube = n ^ 3  
End If  
```  
  
> [!NOTE]
>  即使變數的範圍僅限於一個區塊，其存留期仍然是整個程序。 如果在程序中多次進入區塊時，每個區塊變數會保留先前的值。 若要避免非預期的結果，在這種情況下，最好將初始化的區塊開頭的區塊變數。  
  
### <a name="procedure-scope"></a>程序範圍  
 無法使用該程序之外宣告程序內的項目。 包含宣告的程序可以使用它。 在此層級的變數是也稱為*區域變數*。 您將其與宣告[Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)、 含[靜態](../../../../visual-basic/language-reference/modifiers/static.md)關鍵字。  
  
 密切相關程序和區塊的範圍。 如果您宣告的變數，該程序內任何區塊內的程序之外，您可以將此變數視為具有區塊範圍，其中區塊是整個程序。  
  
> [!NOTE]
>  所有本機元素，即使它們是`Static`變數，都是私用程序以其出現。 您無法宣告任何項目使用[公用](../../../../visual-basic/language-reference/modifiers/public.md)程序內的關鍵字。  
  
### <a name="module-scope"></a>模組範圍  
 為了方便起見，單一詞彙*模組層級*同樣適用於模組、 類別和結構。 您可以宣告此層級的項目放入任何程序或區塊外部，但模組、 類別或結構內宣告陳述式。  
  
 當您在模組層級的宣告時，您所選擇的存取層級會決定的範圍。 包含模組、 類別或結構的命名空間也會影響範圍。  
  
 在您宣告的項目[私人](../../../../visual-basic/language-reference/modifiers/private.md)存取層級可用每個程序，在該模組中，但是不能在不同的模組中的任何程式碼。 `Dim`陳述式在模組層級預設為`Private`如果您未使用任何存取層級的關鍵字。 不過，您可以建立將領域和存取層級更明顯使用`Private`關鍵字`Dim`陳述式。  
  
 下列範例中，在模組中定義的所有程序可以參考的字串變數`strMsg`。 第二個程序呼叫時，它會顯示字串變數的內容`strMsg`對話方塊中。  
  
```  
' Put the following declaration at module level (not in any procedure).  
Private strMsg As String  
' Put the following Sub procedure in the same module.  
Sub initializePrivateVariable()  
    strMsg = "This variable cannot be used outside this module."  
End Sub  
' Put the following Sub procedure in the same module.  
Sub usePrivateVariable()  
    MsgBox(strMsg)  
End Sub  
```  
  
### <a name="namespace-scope"></a>命名空間範圍  
 如果您宣告的項目，在模組層級使用[Friend](../../../../visual-basic/language-reference/modifiers/friend.md)或[公用](../../../../visual-basic/language-reference/modifiers/public.md)關鍵字，它就會變成可用至整個宣告項目所在的命名空間的所有程序。 與上述範例中，字串變數將`strMsg`可以參考其宣告的命名空間中的程式碼。  
  
```  
' Include this declaration at module level (not inside any procedure).  
Public strMsg As String  
```  
  
 命名空間範圍包括巢狀命名空間。 命名空間內可用的項目也會提供任何巢狀方式置於該命名空間的命名空間內。  
  
 如果您的專案不包含任何[命名空間陳述式](../../../../visual-basic/language-reference/statements/namespace-statement.md)s，專案中的所有項目是在相同的命名空間中。 在此情況下，命名空間範圍可以視為專案範圍。 `Public` 模組、 類別或結構中的項目也可用來參考其專案的任何專案。  
  
## <a name="choice-of-scope"></a>選擇範圍  
 當您宣告變數時，您應該記住下列幾點選擇其範圍時。  
  
### <a name="advantages-of-local-variables"></a>本機變數的優點  
 本機變數是不錯的選擇對於任何類型的暫存計算，原因如下：  
  
-   **避免名稱衝突。** 本機變數名稱不容易發生衝突。 例如，您可以建立數個不同的程序包含名為`intTemp`。 只要每個`intTemp`宣告為區域變數，每個程序能夠辨識只有自己版本的`intTemp`。 任何一個程序可以改變在其區域變數值`intTemp`而不會影響`intTemp`其他程序中的變數。  
  
-   **記憶體耗用量。** 僅執行其程序時，本機變數會耗用記憶體。 程序傳回呼叫程式碼時，會釋放其記憶體。 相反地，[共用](../../../../visual-basic/language-reference/modifiers/shared.md)和[靜態](../../../../visual-basic/language-reference/modifiers/static.md)變數耗用的記憶體資源，直到您的應用程式停止執行，因此，它們只在必要時使用。 *執行個體變數*耗用的記憶體時，其執行個體會持續存在，使其成為較有效率的區域變數，但可能更有效率`Shared`或`Static`變數。  
  
### <a name="minimizing-scope"></a>最小化範圍  
 一般情況下，宣告任何變數或常數，它是良好的程式設計作法進行範圍愈小愈好 （區塊範圍最小）。 這有助於節省記憶體，並將程式碼誤用錯誤變數的機會降到最低。 同樣地，您應該在其中宣告變數為[靜態](../../../../visual-basic/language-reference/modifiers/static.md)只會在必要時要保留其程序呼叫的間隔值。  
  
## <a name="see-also"></a>另請參閱  
 [宣告項目特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [如何：控制變數的範圍](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)  
 [在 Visual Basic 中的存留期](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [在 Visual Basic 中的存取層級](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [對已宣告項目的參考](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [變數宣告](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
