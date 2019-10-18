---
title: 已宣告之項目的參考 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic]
- references [Visual Basic], declared elements
- qualified names [Visual Basic]
ms.assetid: d6301709-f4cc-4b7a-b8ba-80898f14ab46
ms.openlocfilehash: de4d42803be48a87f4dfd37a92b1b22fa2d5c554
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524549"
---
# <a name="references-to-declared-elements-visual-basic"></a>已宣告之項目的參考 (Visual Basic)
當您的程式碼參考宣告的元素時，Visual Basic 編譯器會將參考中的名稱與該名稱的適當宣告相符。 如果以相同的名稱宣告多個專案，您可以藉由*限定*其名稱來控制要參考哪些元素。  
  
 編譯器會嘗試將名稱參考與最小*範圍*的名稱宣告進行比對。 這表示它會從進行參考的程式碼開始，並透過包含專案的後續層級向外運作。  
  
 下列範例會顯示兩個名稱相同的變數參考。 此範例會宣告兩個變數，分別命名為 `totalCount`，位於模組 `container` 中不同的範圍層級。 當程式 `showCount` 顯示沒有限定的 `totalCount` 時，Visual Basic 編譯器會以最窄的範圍（亦即 `showCount` 內的區域宣告）解析宣告的參考。 當它符合包含模組 `container` 的 `totalCount` 資格時，編譯器會將參考解析為範圍較廣的宣告。  
  
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
  
## <a name="qualifying-an-element-name"></a>限定元素名稱  
 如果您想要覆寫此搜尋程式，並指定在更廣泛範圍中宣告的名稱，您必須使用更廣泛範圍的包含元素*來限定*名稱。 在某些情況下，您可能也必須限定包含元素。  
  
 限定名稱表示在您的 source 語句中的前面加上可識別目標元素定義位置的資訊。 這種資訊稱為*限定性字串*。 它可以包含一或多個命名空間和模組、類別或結構。  
  
 限定性字串應該明確地指定包含目標元素的模組、類別或結構。 容器可能會轉而位於另一個包含元素中，通常是命名空間。 您可能需要在限定性字串中包含數個包含元素。  
  
#### <a name="to-access-a-declared-element-by-qualifying-its-name"></a>藉由限定名稱來存取宣告的元素  
  
1. 判斷定義元素的位置。 這可能包括命名空間，甚至是命名空間的階層。 在最低層級的命名空間中，元素必須包含在模組、類別或結構中。  
  
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
  
2. 根據目標元素的位置判斷限定性路徑。 從最高層級的命名空間開始，繼續進行最低層級的命名空間，並以包含目標元素的模組、類別或結構做為結尾。 路徑中的每個元素都必須包含其後的元素。  
  
     `outerSpace` → `innerSpace` → `holdsTotals` → `totals`  
  
3. 準備目標元素的限定性字串。 在路徑中的每個元素之後放置句點（`.`）。 您的應用程式必須能夠存取您的限定性字串中的每個元素。  
  
    ```vb  
    outerSpace.innerSpace.holdsTotals.totals.  
    ```  
  
4. 撰寫以一般方式參考目標元素的運算式或指派語句。  
  
    ```vb  
    grandTotal = 9000  
    ```  
  
5. 在目標元素名稱前面加上限定性字串。 名稱應該緊接在包含元素的模組、類別或結構後面的句點（`.`）後面。  
  
    ```vb  
    ' Assume the following module is part of your code.  
    Module accessGrandTotal  
        Public Sub setGrandTotal()  
            outerSpace.innerSpace.holdsTotals.totals.grandTotal = 9000  
        End Sub  
    End Module  
    ```  
  
6. 編譯器會使用限定性字串來尋找清楚且明確的宣告，使其可以符合目標專案參考。  
  
 如果您的應用程式可以存取多個具有相同名稱的程式設計項目，您可能也必須限定名稱參考。 例如，<xref:System.Windows.Forms> 和 <xref:System.Web.UI.WebControls> 命名空間都包含 `Label` 類別（<xref:System.Windows.Forms.Label?displayProperty=nameWithType> 和 <xref:System.Web.UI.WebControls.Label?displayProperty=nameWithType>）。 如果您的應用程式同時使用，或如果它定義自己的 `Label` 類別，您就必須區分不同的 `Label` 物件。 在變數宣告中包含命名空間或匯入別名。 下列範例會使用匯入別名。  
  
```vb  
' The following statement must precede all your declarations.  
Imports win = System.Windows.Forms, web = System.Web.UI.WebControls  
' The following statement references the Windows.Forms.Label class.  
Dim winLabel As New win.Label()  
```  
  
## <a name="members-of-other-containing-elements"></a>其他包含元素的成員  
 當您使用另一個類別或結構的非共用成員時，必須先使用指向類別或結構實例的變數或運算式來限定成員名稱。 在下列範例中，`demoClass` 是名為 `class1` 之類別的實例。  
  
```vb  
Dim demoClass As class1 = New class1()  
demoClass.someSub[(argumentlist)]  
```  
  
 您不能使用類別名稱本身來限定未[共用](../../../../visual-basic/language-reference/modifiers/shared.md)的成員。 您必須先在物件變數中建立實例（在此案例中為 `demoClass`），然後再以變數名稱加以參考。  
  
 如果類別或結構具有 `Shared` 的成員，您可以使用類別或結構名稱或指向實例的變數或運算式來限定該成員。  
  
 模組沒有任何個別的實例，而且其所有成員預設都會 `Shared`。 因此，您可以使用模組名稱來限定模組成員。  
  
 下列範例會顯示模組成員程式的限定參考。 此範例會在專案的不同模組中，宣告兩個 `Sub` 程式，兩個都有名稱 `perform`。 您可以指定每個模組，而不限定其本身的模組，但如果從任何其他位置參考，則必須限定。 因為 `module3` 中的最後一個參考不符合 `perform`，所以編譯器無法解析該參考。  
  
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
 若要使用另一個專案中定義的[公用](../../../../visual-basic/language-reference/modifiers/public.md)元素，您必須先設定該專案元件或類型程式庫的*參考*。 若要設定參考，請按一下 [**專案**] 功能表上的 [**加入參考**]，或使用[-reference （Visual Basic）](../../../../visual-basic/reference/command-line-compiler/reference.md)命令列編譯器選項。  
  
 例如，您可以使用 .NET Framework 的 XML 物件模型。 如果您設定 <xref:System.Xml> 命名空間的參考，您可以宣告並使用它的任何類別，例如 <xref:System.Xml.XmlDocument>。 下列範例會使用 <xref:System.Xml.XmlDocument>。  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As System.Xml.XmlDocument  
```  
  
## <a name="importing-containing-elements"></a>匯入包含元素  
 您可以使用[Imports 語句（.Net 命名空間和類型）](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)匯*入*包含您要使用之模組或類別的命名空間。 這可讓您參考已匯入之命名空間中定義的元素，而不需完整限定其名稱。 下列範例會重寫前一個範例，以匯入 <xref:System.Xml> 命名空間。  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As XmlDocument  
```  
  
 此外，`Imports` 語句可以為每個匯入的命名空間定義匯*入別名*。 這可讓原始程式碼變得更短且更容易閱讀。 下列範例會重寫上一個範例，以使用 `xD` 做為 <xref:System.Xml> 命名空間的別名。  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports xD = System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As xD.XmlDocument  
```  
  
 @No__t_0 語句不會將其他專案中的元素提供給您的應用程式。 也就是說，它不會取代設定參考。 匯入命名空間只會移除限定該命名空間中所定義名稱的需求。  
  
 您也可以使用 `Imports` 語句來匯入模組、類別、結構和列舉。 然後您可以使用這類匯入專案的成員，而不需要限定。 不過，您一律必須使用評估為類別或結構實例的變數或運算式，來限定類別和結構的非共用成員。  
  
## <a name="naming-guidelines"></a>命名方針  
 當您定義兩個或多個名稱相同的程式設計專案時，當編譯器嘗試解析該名稱的參考時，可能會造成*名稱不明確*的問題。 如果範圍內有一個以上的定義，或如果沒有定義在範圍內，則參考會是兩難。 如需範例，請參閱此說明頁面上的「限定參考範例」。  
  
 您可以提供所有元素的唯一名稱，以避免名稱不明確。 然後您可以參考任何專案，而不需要以命名空間、模組或類別來限定其名稱。 您也可以減少意外參考錯誤元素的機會。  
  
## <a name="shadowing"></a>遮蔽  
 當兩個程式設計項目共用相同名稱時，其中一個專案可以隱藏或*遮蔽*另一個。 有陰影的元素無法供參考;相反地，當您的程式碼使用陰影專案名稱時，Visual Basic 編譯器會將它解析成遮蔽元素。 如需範例的詳細說明，請參閱[Visual Basic 中的陰影](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)。  
  
## <a name="see-also"></a>請參閱

- [宣告項目名稱](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [宣告項目特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)
- [變數](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [Imports 陳述式 (.NET 命名空間和類型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [New 運算子](../../../../visual-basic/language-reference/operators/new-operator.md)
- [Public](../../../../visual-basic/language-reference/modifiers/public.md)
