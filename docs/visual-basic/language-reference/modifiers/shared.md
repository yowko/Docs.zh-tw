---
title: "Shared (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Shared"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Shared keyword"
  - "members, shared"
  - "shared members"
  - "nonshared"
  - "shared elements"
  - "elements, shared"
ms.assetid: 2bf7cf2c-b0dd-485e-8749-b5d674dab4cd
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# Shared (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

指定一個或多個宣告的程式設計項目會與整個類別或結構產生關聯，而不是與類別或結構的特定執行個體 \(Instance\) 產生關聯。  
  
## 備註  
  
## 使用共用的時機  
 若共用類別或結構的成員，可讓每一個執行個體都能使用該成員，而不是每個執行個體各自保留一份成員複本的「*非共用*」情況。  在某些情況下 \(例如，當變數的值套用至整個應用程式時\)，這種做法會很有用。  如果您將該變數宣告為 `Shared`，那麼所有的執行個體都會存取相同的儲存位置，而且若某個執行個體變更了變數的值，則所有的執行個體都會存取更新後的值。  
  
 共用並不會改變成員的存取層級。  例如，類別成員可以是共用且私用的 \(只能從類別中存取\)，或是非共用且公用的。  如需詳細資訊，請參閱 [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
## 規則  
  
-   **宣告內容：** 只能在模組層級使用 `Shared`。  這表示 `Shared` 項目的宣告內容必須是類別或結構，不可以是原始程式檔 \(Source File\)、命名空間 \(Namespace\) 或程序。  
  
-   **組合的修飾詞：** 您無法在同一個宣告中，同時指定 `Shared` 與 [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)、[Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)、[NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)、[MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md) 或 [Static](../../../visual-basic/language-reference/modifiers/static.md)。  
  
-   **存取** ：您可以使用其類別或結構名稱進行限定 \(而非使用其類別或結構之特定執行個體的變數名稱\)，藉以存取共用項目。  您甚至不須建立類別或結構的執行個體，即可存取其共用成員。  
  
     下列範例會呼叫 <xref:System.Double> 結構所公開 \(Expose\) 的共用程序 <xref:System.Double.IsNaN%2A>。  
  
     `If Double.IsNaN(result) Then MsgBox("Result is mathematically undefined.")`  
  
-   **隱含共用：** 您無法在 [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md) 中使用 `Shared` 修飾詞，但常數會被隱含共用。  同樣地，您無法將模組或介面的成員宣告為 `Shared`，但是成員會被隱含共用。  
  
## 行為  
  
-   **儲存：** 不論您為類別或結構建立多少個執行個體，共用變數或事件都只會在記憶體中儲存一次。  同樣地，共用程序或屬性只會保留一組區域變數。  
  
-   **透過執行個體變數存取：** 有可能使用包含其類別或結構之特定執行個體的變數名稱來進行限定，以存取共用項目。  雖然通常會如預期運作，但編譯器 \(Compiler\) 仍會產生警告訊息，並改為透過類別或結構名稱進行存取，而不是透過變數進行存取。  
  
-   **透過執行個體運算式存取：** 如果您是透過運算式存取共用項目，而且這個運算式會傳回其類別或結構的執行個體，則編譯器會改為透過類別或結構名稱進行存取，而不會評估運算式。  如果您想要運算式不但會傳回執行個體，還會執行其他動作，則會產生未預期的結果。  下列範例將說明這點。  
  
    ```  
    Sub main()  
        shareTotal.total = 10  
        ' The preceding line is the preferred way to access total.  
        Dim instanceVar As New shareTotal  
        instanceVar.total += 100  
        ' The preceding line generates a compiler warning message and  
        ' accesses total through class shareTotal instead of through  
        ' the variable instanceVar. This works as expected and adds  
        ' 100 to total.  
        returnClass().total += 1000  
        ' The preceding line generates a compiler warning message and  
        ' accesses total through class shareTotal instead of calling  
        ' returnClass(). This adds 1000 to total but does not work as  
        ' expected, because the MsgBox in returnClass() does not run.  
        MsgBox("Value of total is " & CStr(shareTotal.total))  
    End Sub  
    Public Function returnClass() As shareTotal  
        MsgBox("Function returnClass() called")  
        Return New shareTotal  
    End Function  
    Public Class shareTotal  
        Public Shared total As Integer  
    End Class  
    ```  
  
     在上述範例中，程式碼會透過執行個體存取共用變數 `total` 兩次，每一次編譯器都會產生警告訊息。  每次編譯器都會直接透過類別 `shareTotal` 進行存取，而不利用任何的執行個體。  對於想要執行的程序 `returnClass` 呼叫而言，這表示甚至連 `returnClass` 呼叫都不會產生，因此也不會執行顯示 "Function returnClass\(\) called" 的額外動作。  
  
 `Shared` 修飾詞可用於以下內容中：  
  
 [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Operator 陳述式](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## 請參閱  
 [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)   
 [Static](../../../visual-basic/language-reference/modifiers/static.md)   
 [Lifetime in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)   
 [Procedures](../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Structures](../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)