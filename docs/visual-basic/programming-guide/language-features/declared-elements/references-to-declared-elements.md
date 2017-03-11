---
title: "已宣告之項目的參考 (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "宣告項目"
  - "參考宣告項目"
  - "完整名稱"
ms.assetid: d6301709-f4cc-4b7a-b8ba-80898f14ab46
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# 已宣告之項目的參考 (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

在程式碼參考宣告的項目， [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 編譯器對應至適當的宣告該名稱的參考中的名稱。 如果多個項目宣告具有相同名稱時，您可以控制的項目所參考 *合格* 它的名稱。  
  
 編譯器會嘗試比對的名稱宣告的名稱參考 *最小範圍*。 這表示它參考的程式碼的開頭，而且包含項目的連續層級向外運作。  
  
 下列範例顯示兩個變數具有相同名稱的參考。 此範例會宣告兩個變數，每個命名為 `totalCount`, ，範圍在模組中的不同層級 `container`。 當程序 `showCount` 顯示 `totalCount` 無限制， [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 編譯器會具有最小的範圍，也就是在本機宣告的宣告將參考解析 `showCount`。 當它符合 `totalCount` 所包含的模組與 `container`, ，編譯器會解析具有更廣泛的範圍宣告的參考。  
  
```vb  
' Assume these two modules are both in the same assembly.  
Module container  
    Public totalCount As Integer = 1  
    Public Sub showCount()  
        Dim totalCount As Integer = 6000  
        ' The following statement displays the local totalCount (6000).  
        MsgBox("Unqualified totalCount is " & CStr(totalCount))  
        ' The following statement displays the module's totalCount (1).  
        MsgBox("container.totalCount is " & CStr(container.totalCount))  
    End Sub  
End Module  
Module callingModule  
    Public Sub displayCount()  
        container.showCount()  
        ' The following statement displays the containing module's totalCount (1).  
        MsgBox("container.totalCount is " & CStr(container.totalCount))  
    End Sub  
End Module  
```  
  
## <a name="qualifying-an-element-name"></a>限定項目名稱  
 如果您想要覆寫這個搜尋程序並指定名稱宣告在更廣泛的範圍內，您必須 *限定* 與更廣泛的範圍的包含項目名稱。 在某些情況下，您可能也必須限定包含項目。  
  
 限定名稱表示可識別目標項目定義的位置資訊的來源陳述式中在它前面。 這項資訊稱為 *限定性條件字串*。 它可以包含一個或多個命名空間或模組類別或結構。  
  
 模組、 類別或結構，其中包含目標項目，應該明確地指定限定性條件字串。 容器接著可能位於另一個包含項目，通常是命名空間。 您可能需要限定性條件字串中包含數個內含項目。  
  
#### <a name="to-access-a-declared-element-by-qualifying-its-name"></a>若要存取宣告的項目來限定其名稱  
  
1.  判斷在其中定義之項目的位置。 這可能包括命名空間或甚至是命名空間的階層。 最低層級命名空間內的項目必須包含在模組、 類別或結構。  
  
    ```vb  
    ' Assume the following hierarchy exists outside your code.  
    Namespace outerSpace  
        Namespace innerSpace  
            Module holdsTotals  
                Public Structure totals  
                    Public thisTotal As Integer  
                    Public Shared grandTotal As Long  
                End Structure  
            End Module  
        End Namespace  
    End Namespace  
    ```  
  
2.  判斷目標項目位置為基礎的限定性條件路徑。 最高層級的命名空間，繼續在最低層級命名空間，以開頭和結束模組、 類別或結構，其中包含目標項目。 在路徑中的每個項目必須包含在它後面的項目。  
  
     `outerSpace` → `innerSpace` → `holdsTotals` → `totals`  
  
3.  準備目標項目的限定性條件字串。 將一個句點 (`.`) 的路徑中每個項目之後。 應用程式必須具有限定性條件字串中的每個項目的存取權。  
  
    ```vb  
    outerSpace.innerSpace.holdsTotals.totals.  
    ```  
  
4.  撰寫運算式或指派陳述式以一般方式參考的目標項目。  
  
    ```vb  
    grandTotal = 9000  
    ```  
  
5.  目標項目名稱前加限定性條件字串。 名稱應該立即接在句號 (`.`)，跟模組、 類別或結構，其中包含項目。  
  
    ```vb  
    ' Assume the following module is part of your code.  
    Module accessGrandTotal  
        Public Sub setGrandTotal()  
            outerSpace.innerSpace.holdsTotals.totals.grandTotal = 9000  
        End Sub  
    End Module  
    ```  
  
6.  編譯器會用來尋找清楚、 明確宣告，它可以比對的目標項目參考的限定性條件字串。  
  
 您也可能會限定名稱參考，如果您的應用程式可以存取多個具有相同名稱的程式設計項目。 例如， <xref:System.Windows.Forms> 和 <xref:System.Web.UI.WebControls> 這兩個的命名空間包含的 `Label` 類別 (<xref:System.Windows.Forms.Label?displayProperty=fullName> 和 <xref:System.Web.UI.WebControls.Label?displayProperty=fullName>)。 如果您的應用程式同時使用兩者，或者它會定義它自己 `Label` 類別中，您必須區分不同 `Label` 物件。 在變數宣告中包含的命名空間或匯入別名。 下列範例會使用匯入別名。  
  
```vb  
' The following statement must precede all your declarations.  
Imports win = System.Windows.Forms, web = System.Web.UI.WebControls  
' The following statement references the Windows.Forms.Label class.  
Dim winLabel As New win.Label()  
```  
  
## <a name="members-of-other-containing-elements"></a>成員的其他包含的項目  
 當您使用另一個類別或結構的非共用的成員時，您必須先限定成員名稱的變數或運算式，以指向類別或結構的執行個體。 在下列範例中， `demoClass` 是名為的類別執行個體 `class1`。  
  
```vb  
Dim demoClass As class1 = New class1()  
demoClass.someSub[(argumentlist)]  
```  
  
 您無法使用本身的類別名稱限定成員不是 [共用](../../../../visual-basic/language-reference/modifiers/shared.md)。 您必須先建立執行個體的物件變數中 (在此情況下 `demoClass`)，然後以變數名稱參考它。  
  
 如果類別或結構 `Shared` 成員，您可以限定該成員的類別或結構名稱或變數或運算式，以指向執行個體。  
  
 模組沒有任何不同的執行個體和其所有成員都是 `Shared` 預設。 因此，您可以限定模組名稱的模組成員。  
  
 下列範例顯示模組成員程序的完整的參考。 此範例會宣告兩個 `Sub` 程序，名為 `perform`, ，在專案中的不同模組中。 每一個可以指定無限制地在自己的模組內，但若從其他地方參考必須為完整名稱。 因為最後一個參考中 `module3` 不限定 `perform`, ，編譯器無法解析的參考。  
  
```vb  
' Assume these three modules are all in the same assembly.  
Module module1  
    Public Sub perform()  
        MsgBox("module1.perform() now returning")  
    End Sub  
End Module  
Module module2  
    Public Sub perform()  
        MsgBox("module2.perform() now returning")  
    End Sub  
    Public Sub doSomething()  
        ' The following statement calls perform in module2, the active module.  
        perform()  
        ' The following statement calls perform in module1.  
        module1.perform()  
    End Sub  
End Module  
Module module3  
    Public Sub callPerform()  
        ' The following statement calls perform in module1.  
        module1.perform()  
        ' The following statement makes an unresolvable name reference  
        ' and therefore generates a COMPILER ERROR.  
        perform() ' INVALID statement  
    End Sub  
End Module  
```  
  
## <a name="references-to-projects"></a>專案的參考  
 若要使用 [公用](../../../../visual-basic/language-reference/modifiers/public.md) 另一個專案中定義的項目，您必須先設定 *參考* 至該專案的組件或類型程式庫。 若要設定的參考，按一下 [ **加入參考** 上 **專案** ] 功能表上或使用 [/reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) 命令列編譯器選項。  
  
 例如，您可以使用 XML 物件模型的 [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)]。 如果將參考設定至 <xref:System.Xml> 命名空間，您可以宣告和使用任何其類別，例如 <xref:System.Xml.XmlDocument>。 下列範例會使用 <xref:System.Xml.XmlDocument>。  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As System.Xml.XmlDocument  
```  
  
## <a name="importing-containing-elements"></a>匯入包含項目  
 您可以使用 [Imports 陳述式 （.NET 命名空間和類型）](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) 至 *匯入* 命名空間包含的模組或您想要使用的類別。 這可讓您匯入的命名空間中定義，而不需要完整名稱的項目參考。 下列範例重寫匯入上例 <xref:System.Xml> 命名空間。  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As XmlDocument  
```  
  
 此外， `Imports` 陳述式可定義 *匯入別名* 每個匯入命名空間。 這可讓更短而且更容易讀取的原始程式碼。 下列範例重寫前一個範例中使用 `xD` 做為別名 <xref:System.Xml> 命名空間。  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports xD = System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As xD.XmlDocument  
```  
  
  `Imports` 陳述式不會從其他專案項目提供您的應用程式。 也就是說，它不會設定參考的位置。 只匯入命名空間中移除的需求來限定該命名空間中定義的名稱。  
  
 您也可以使用 `Imports` 陳述式來匯入模組、 類別、 結構和列舉型別。 然後，您可以使用這類匯入的項目，但是不限定的成員。 不過，您必須一律限定類別和結構的變數或運算式評估為類別或結構的執行個體的非共用的的成員。  
  
## <a name="naming-guidelines"></a>命名方針  
 當您定義兩個以上的程式設計項目具有相同的名稱， *名稱模稜兩可* 可能會造成當編譯器嘗試解析該名稱的參考。 如果多個定義在範圍內，或如果沒有定義位於範圍內時，會無法解析的參考。 如需範例，請參閱這個說明網頁的限定參考 「 範例 」。  
  
 您可以為每一個項目指定唯一的名稱，以避免名稱模稜兩可。 則您可以讓任何項目的參考，而不需限定的命名空間、 模組或類別名稱。 您也會減少意外的錯誤項目參考的機會。  
  
## <a name="shadowing"></a>遮蔽  
 當兩個程式設計項目共用相同的名稱時，其中可以隱藏它，或 *陰影*, ，另一個。 遮蔽的項目不能用於參考;相反地，當您的程式碼會使用遮蔽的項目名稱， [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 編譯器解析遮蔽的項目。 範例與更詳細的說明，請參閱 [在 Visual Basic 中，以遮蔽](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)。  
  
## <a name="see-also"></a>另請參閱  
 [宣告項目名稱](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [宣告項目特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)   
 [NIB 如何︰ 修改專案屬性和組態設定](http://msdn.microsoft.com/zh-tw/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [變數](../../../../visual-basic/programming-guide/language-features/variables/index.md)   
 [Imports 陳述式 （.NET 命名空間和類型）](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [New 運算子](../../../../visual-basic/language-reference/operators/new-operator.md)   
 [公用](../../../../visual-basic/language-reference/modifiers/public.md)