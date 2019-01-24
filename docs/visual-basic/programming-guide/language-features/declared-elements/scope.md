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
ms.openlocfilehash: 38dd9d6d40780c25f06a35cf1ffbe4743b7da4a4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54537230"
---
# <a name="scope-in-visual-basic"></a>Visual Basic 中的範圍
*領域*的宣告的項目是 所有程式碼都可以參考它，而不需要限定其名稱，或使其能透過一組[Imports 陳述式 （.NET 命名空間和類型）](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)。 元素可能具有其中一個下列層級的範圍：  
  
|層級|描述|  
|-----------|-----------------|  
|區塊範圍|只有在程式碼內的可用區塊中宣告它|  
|程序範圍|提供給所有的程式碼中宣告它的程序|  
|模組範圍|提供給內模組、 類別或結構宣告它的所有程式碼|  
|命名空間範圍|提供給所有的程式碼中宣告它的命名空間|  
  
 這些層級的範圍進行最少 （區塊） 中最寬 （命名空間中），其中*最小範圍*表示的最小的集合，但是不限定的項目可以參考的程式碼。 如需詳細資訊，請參閱此頁面上的 「 層級的範圍 」。  
  
## <a name="specifying-scope-and-defining-variables"></a>指定範圍，以及定義變數  
 當您在宣告時，您會指定項目的範圍。 範圍可能取決於下列因素：  
  
-   您可以在其中宣告之項目的區域 （區塊、 程序、 模組、 類別或結構）  
  
-   包含的項目宣告的命名空間  
  
-   您宣告的項目之存取層級  
  
 小心，因為如此一來，定義具有相同名稱但不同的範圍變數時，可能會導致非預期的結果。 如需詳細資訊，請參閱 [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)。  
  
## <a name="levels-of-scope"></a>範圍層級  
 在宣告它的區域使用的程式設計項目。 項目可以參考相同的區域中的所有程式碼未限定其名稱。  
  
### <a name="block-scope"></a>區塊範圍  
 區塊是一組陳述式括住起始並終止陳述式的宣告，如下所示：  
  
-   `Do` 和 `Loop`  
  
-   `For` [`Each`] 與 `Next`  
  
-   `If` 和 `End If`  
  
-   `Select` 和 `End Select`  
  
-   `SyncLock` 和 `End SyncLock`  
  
-   `Try` 和 `End Try`  
  
-   `While` 和 `End While`  
  
-   `With` 和 `End With`  
  
 如果您宣告的變數在區塊內，您可以只在該區塊內使用它。 在下列範例中，整數變數的範圍`cube`之間區塊`If`並`End If`，而且您可以不再參考`cube`當執行會通過區塊之外。  
  
```  
If n < 1291 Then  
    Dim cube As Integer  
    cube = n ^ 3  
End If  
```  
  
> [!NOTE]
>  即使變數的範圍僅限於一個區塊，其存留期內仍然是整個程序。 如果程序期間中一次進入區塊時，每個區塊的變數會保留先前的值。 若要避免非預期的結果，在此情況下，最好是初始化在區塊開頭的區塊變數。  
  
### <a name="procedure-scope"></a>程序範圍  
 無法使用該程序之外宣告程序內的項目。 包含宣告的程序可以使用它。 在此層級的變數是也稱為*區域變數*。 您將它們與宣告[Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)、 包含或不含[靜態](../../../../visual-basic/language-reference/modifiers/static.md)關鍵字。  
  
 密切相關程序和區塊的範圍。 如果您宣告變數的程序內，但該程序內的任何區塊外，您可以將此變數視為具有區塊範圍，而區塊就是整個程序。  
  
> [!NOTE]
>  所有本機元素，即使它們是`Static`變數，都是以其出現的程序私用。 您無法宣告任何項目使用[公開](../../../../visual-basic/language-reference/modifiers/public.md)程序內的關鍵字。  
  
### <a name="module-scope"></a>模組範圍  
 為了方便起見，單一詞彙*模組層級*同樣適用於模組、 類別和結構。 您可以藉由將放在宣告陳述式之外的任何程序或區塊，但在模組、 類別或結構宣告在此層級的項目。  
  
 當您在模組層級的宣告時，您所選擇的存取層級會決定範圍。 包含模組、 類別或結構的命名空間也會影響範圍。  
  
 在您宣告的項目[私人](../../../../visual-basic/language-reference/modifiers/private.md)存取層級可在該模組中，每個程序但不是能在不同的模組中的任何程式碼。 `Dim`陳述式在模組層級預設為`Private`如果您未使用任何存取層級的關鍵字。 不過，您可以進行的範圍和存取層級更明顯利用`Private`中的關鍵字`Dim`陳述式。  
  
 在下列範例中，模組中定義的所有程序可以參考的字串變數`strMsg`。 呼叫第二個程序時，它會顯示字串變數的內容`strMsg`在對話方塊中。  
  
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
 如果您宣告在模組層級使用的項目[Friend](../../../../visual-basic/language-reference/modifiers/friend.md)或是[公用](../../../../visual-basic/language-reference/modifiers/public.md)關鍵字，均可使用整個項目宣告所在的命名空間的所有程序。 使用上述範例中，字串變數將`strMsg`可以由其宣告的命名空間中的任何位置的程式碼加以參考。  
  
```  
' Include this declaration at module level (not inside any procedure).  
Public strMsg As String  
```  
  
 命名空間範圍包含巢狀命名空間。 命名空間內可用的項目也會提供任何巢狀方式置於該命名空間的命名空間內。  
  
 如果您的專案不包含任何[命名空間陳述式](../../../../visual-basic/language-reference/statements/namespace-statement.md)s，在專案中的所有項目是在相同的命名空間中。 在此情況下，命名空間範圍可以視為專案範圍。 `Public` 模組、 類別或結構中的項目也可用於任何參考此專案的專案。  
  
## <a name="choice-of-scope"></a>選擇的範圍  
 當您宣告變數時，您應該記住下列幾點選擇其範圍時。  
  
### <a name="advantages-of-local-variables"></a>本機變數的優點  
 本機變數會是不錯的選擇，為任何種類的暫存計算，原因如下：  
  
-   **避免名稱衝突。** 本機變數名稱不容易發生衝突。 例如，您可以建立數個不同的程序包含名為`intTemp`。 只要每個`intTemp`宣告為區域變數，每個程序可辨識自己的版本的`intTemp`。 任何一個程序可以改變其區域變數中的值`intTemp`而不會影響`intTemp`其他程序中的變數。  
  
-   **記憶體耗用量。** 只會執行其程序時，本機變數會消耗記憶體。 程序傳回給呼叫程式碼時，會釋放其記憶體。 相反地， [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)並[靜態](../../../../visual-basic/language-reference/modifiers/static.md)變數耗用的記憶體資源，直到您的應用程式停止執行，因此，它們只在必要時使用。 *執行個體變數*耗用記憶體而其執行個體會持續存在，使其成為較不有效比本機變數，但可能更有效率，比`Shared`或`Static`變數。  
  
### <a name="minimizing-scope"></a>最小化範圍  
 一般情況下，宣告時的任何變數或常數，是良好的程式設計做法範圍愈小愈好 （區塊範圍內最小的）。 這有助於節省記憶體，並將程式碼誤用錯誤變數的機會降到最低。 同樣地，您應該將變數宣告[靜態](../../../../visual-basic/language-reference/modifiers/static.md)只會在必要時要保留其程序呼叫的間隔值。  
  
## <a name="see-also"></a>另請參閱
- [宣告項目特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [如何：控制變數的範圍](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)
- [在 Visual Basic 中的存留期](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [在 Visual Basic 中的存取層級](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [對已宣告項目的參考](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [變數宣告](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
