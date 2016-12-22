---
title: "Scope in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "module scope"
  - "scope, levels"
  - "module level"
  - "procedures, scope"
  - "declared elements, scope"
  - "namespaces, scope"
  - "scope, declared elements"
  - "scope, about scope"
  - "levels of scope"
  - "block scope"
  - "scope, Visual Basic"
  - "procedure scope"
ms.assetid: 208106fe-79c9-4eec-93c6-55f08548895f
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Scope in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

宣告項目的「*範圍*」\(Scope\) 是一組不需完整名稱或透過 [Imports Statement \(.NET Namespace and Type\)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)即可使用的程式碼。  項目的範圍可以是下列層級之一：  
  
|層級|描述|  
|--------|--------|  
|區塊範圍|只能在宣告的程式碼區塊內使用|  
|程序範圍|在程序內宣告的所有程式皆可使用|  
|模組範圍|宣告的模組、類別或結構內所有程式碼皆可使用|  
|命名空間範圍|在命名空間內宣告的所有程式碼皆可使用|  
  
 這些範圍的層級由最窄的 \(區塊\) 至最寬的 \(命名空間\)，其中「*最窄範圍*」\(Narrowest Scope\) 表示不需完整名稱項目的最小程式碼組合。  如需詳細資訊，請參閱本頁的＜範圍層級＞。  
  
## 指定範圍並定義變數  
 當您宣告項目時，請指定它的範圍。  範圍端視下列因素而定：  
  
-   您宣告該項目的區域 \(區塊、程序、模組、類別或結構\)  
  
-   包含該項目的宣告之命名空間  
  
-   您為該項目宣告的存取層級  
  
 當您定義相同名稱但不同範圍的變數時請小心使用，因為這麼做可能會導致未預期的結果。  如需詳細資訊，請參閱 [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)。  
  
## 範圍層級  
 程式項目可在您宣告它的整個區域中使用。  相同區域中的所有程式碼都可代表該項目，而不需完整描述其名稱。  
  
### 區塊範圍  
 區塊是一組陳述式，包含在初始及結束宣告的陳述式中，如下所示：  
  
-   `Do` 和 `Loop`  
  
-   `For` \[`Each`\] 和 `Next`  
  
-   `If` 和 `End If`  
  
-   `Select` 和 `End Select`  
  
-   `SyncLock` 和 `End SyncLock`  
  
-   `Try` 和 `End Try`  
  
-   `While` 和 `End While`  
  
-   `With` 和 `End With`  
  
 如果您在區塊內宣告變數，則該變數只能區塊中使用。  在下列範例中，整數變數 `cube` 的範圍是介於 `If` 和 `End If` 之間的區塊，而當程序執傳遞到區塊以外時，就不能再參考 `cube`：  
  
```  
If n < 1291 Then  
    Dim cube As Integer  
    cube = n ^ 3  
End If  
```  
  
> [!NOTE]
>  即使變數的範圍限制在一個區塊內，其存留期 \(Lifetime\) 仍然是整個程序的存留期。  如果您在程序執行期間進入該區塊多次，每個區塊變數會保留其之前的值。  如果要避免在這種情況下產生無法預期的結果，最好在區塊開頭即初始化區塊變數。  
  
### 程序範圍  
 在程序內宣告的項目無法在該程序外使用。  只有包含宣告的程序可使用它。  這個層級的變數亦稱為「*區域變數*」\(Local Variable\)。  您可以使用 [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) 來宣告這些變數，也可以使用或不使用 [Static](../../../../visual-basic/language-reference/modifiers/static.md) 關鍵字。  
  
 程序和區塊範圍的關係十分密切。  如果在程序內的任何區塊外宣告變數，可將此變數視為擁有區塊範圍，而該區塊就是整個程序。  
  
> [!NOTE]
>  所有的區域項目，在其出現的程序中都是私用的 \(Private\)，即使是 `Static` 變數也一樣。  您無法使用程序內的 [Public](../../../../visual-basic/language-reference/modifiers/public.md) 關鍵字來宣告任何項目。  
  
### 模組範圍  
 為了方便起見，「*模組層級*」\(Module Level\) 這個詞彙也可套用在模組、類別和結構。  可以將宣告陳述式 \(Declaration Statement\) 放置在模組、類別或結構內的任何程序或區塊之外，以宣告這個層次的項目。  
  
 在這個模組層級宣告時，所選擇的存取層級將決定宣告範圍。  包含模組、類別或結構的命名空間也會影響範圍。  
  
 宣告的 [Private](../../../../visual-basic/language-reference/modifiers/private.md) 存取層級項目，可在該模組的每一個程序中使用，但是無法在不同模組的任何程式碼中使用。  如果沒有使用任何存取層級的關鍵字，模組層級的 `Dim` 陳述式會依預設值為 `Private`。  但是，您可以在 `Dim` 陳述式中使用 `Private` 關鍵字，以更明確地設定範圍及存取層級。  
  
 在下列範例中，模組內定義的所有程序都視為字串變數 `strMsg`。  呼叫第二個程序時，會在對話方塊中顯示字串變數 `strMsg` 的內容。  
  
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
  
### 命名空間範圍  
 如果您用 [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) 或 [Public](../../../../visual-basic/language-reference/modifiers/public.md) 關鍵字宣告模組層級的項目，透過在命名空間中宣告該項目，所有程序都可使用該項目。  將上個範例做了如下修改後，在宣告字串變數 `strMsg` 的命名空間內之任意位置的程式碼就可參考該變數。  
  
```  
' Include this declaration at module level (not inside any procedure).  
Public strMsg As String  
```  
  
 命名空間範圍包括巢狀的命名空間。  命名空間內可用的項目也可在該命名空間內的任何巢狀命名空間使用。  
  
 如果您的專案不包含任何 [Namespace Statement](../../../../visual-basic/language-reference/statements/namespace-statement.md)陳述式，則專案中的一切都屬於相同的命名空間中。  在這種情況下，命名空間範圍可視為專案範圍。  模組、類別或結構中的 `Public` 項目也可供參考此專案的任何專案使用。  
  
## 選擇範圍  
 在宣告變數和選擇其範圍時，請留意下列數點。  
  
### 區域變數的優點  
 區域變數適合任何類型的暫存計算，原因如下：  
  
-   **避免名稱衝突**： 區域變數不受名稱衝突影響。  例如，您可以建立數個含 `intTemp` 變數的不同程序。  只要每一個 `intTemp` 都被宣告為區域變數，每一個程序就只會辨識自己的 `intTemp`。  任何一個程序都可以在不影響其他程序的 `intTemp` 變數的情況下，變更其區域 `intTemp` 的值。  
  
-   **記憶體消耗量**： 區域變數只會在程序執行時才會耗用記憶體。  當程序回到呼叫程式碼時，記憶體就會被釋放。  相反地，[Shared](../../../../visual-basic/language-reference/modifiers/shared.md) 和 [Static](../../../../visual-basic/language-reference/modifiers/static.md) 變數只有在應用程式停止執行時才會停止耗用記憶體資源，所以請在必要時才使用這兩個變數。  當執行個體存在時，「*執行個體變數*」\(Instance Variable\) 會持續消耗記憶體，因而其效率比區域變數的效率低，但可能比 `Shared` 或 `Static` 變數更有效率。  
  
### 最小化範圍  
 一般而言，在宣告任何變數或常數時，良好的程式設計方式是將範圍設定得愈小愈好 \(區塊範圍是最小的\)。  這麼做有助於節省記憶體，並將程式碼誤用錯誤變數的機會降到最低。  同樣地，僅在必須於程序呼叫之間保留其值時，您才需要將變數宣告為 [Static](../../../../visual-basic/language-reference/modifiers/static.md)。  
  
## 請參閱  
 [Declared Element Characteristics](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)   
 [How to: Control the Scope of a Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)   
 [Lifetime in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)   
 [Access Levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)   
 [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [變數宣告](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)