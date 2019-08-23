---
title: Using 陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.using
helpviewer_keywords:
- resource disposal
- Try...Catch...Finally statements, equivalent to Using statement
- resources [Visual Basic], disposing
- Using statement [Visual Basic]
ms.assetid: 665d1580-dd54-4e96-a9a9-6be2a68948f1
ms.openlocfilehash: 346a26ad5751599831d8b0d3e0497e4d488eb76c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957537"
---
# <a name="using-statement-visual-basic"></a>Using 陳述式 (Visual Basic)
宣告`Using`區塊的開頭, 並選擇性地取得區塊所控制的系統資源。  
  
## <a name="syntax"></a>語法  
  
```  
Using { resourcelist | resourceexpression }  
    [ statements ]  
End Using  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`resourcelist`|如果您沒有提供`resourceexpression`, 則為必要。 這個`Using`區塊所控制的一或多個系統資源清單, 並以逗號分隔。|  
|`resourceexpression`|如果您沒有提供`resourcelist`, 則為必要。 參考要由這個`Using`區塊控制之系統資源的參考變數或運算式。|  
|`statements`|選擇性。 `Using`區塊執行的語句區塊。|  
|`End Using`|必要項。 結束`Using`區塊的定義, 並處置它所控制的所有資源。|  
  
 `resourcelist`元件中的每個資源都有下列語法和部分:  
  
 `resourcename As New resourcetype [ ( [ arglist ] ) ]`  
  
 -或-  
  
 `resourcename As resourcetype = resourceexpression`  
  
## <a name="resourcelist-parts"></a>resourcelist 元件  
  
|詞彙|定義|  
|---|---|  
|`resourcename`|必要項。 參考`Using`區塊所控制之系統資源的參考變數。|  
|`New`|如果語句取得`Using`資源, 則為必要。 如果您已經取得資源, 請使用第二個替代語法。|  
|`resourcetype`|必要項。 資源的類別。 類別必須執行<xref:System.IDisposable>介面。|  
|`arglist`|選擇性。 您要傳遞至函式的引數清單, 以建立的`resourcetype`實例。 請參閱[參數清單](../../../visual-basic/language-reference/statements/parameter-list.md)。|  
|`resourceexpression`|必要項。 參考滿足需求之`resourcetype`系統資源的變數或運算式。 如果您使用第二個語法替代, 則必須先取得資源, 然後再將`Using`控制權傳遞給語句。|  
  
## <a name="remarks"></a>備註  
 有時候, 您的程式碼需要非受控資源, 例如檔案控制代碼、COM 包裝函式或 SQL 連接。 當您的程式碼完成時,區塊會保證一或多個這類資源的處置。`Using` 這讓它們可供其他程式碼使用。  
  
 受控資源會由 .NET Framework 垃圾收集行程 (GC) 處置, 而不需要您進行任何額外的程式碼撰寫。 您不需要受控資源`Using`的區塊。 不過, 您仍然可以使用`Using`區塊來強制處置受管理的資源, 而不是等候垃圾收集行程。  
  
 `Using`區塊有三個部分: [取得]、[使用方式] 和 [處置]。  
  
- 取得表示建立變數, 並將它初始化以參考系統資源。 語句可以取得一或多個資源, 您也可以在進入區塊並將它提供`Using`給語句之前, 取得剛好一個資源。 `Using` 如果您提供`resourceexpression`, 則必須先取得資源, 然後再將控制權`Using`傳遞給語句。  
  
- *使用*方式表示存取資源, 並對它們執行動作。 `Using` 和`End Using`之間的語句代表資源的使用。  
  
- *處置*表示在中<xref:System.IDisposable.Dispose%2A> `resourcename`的物件上呼叫方法。 這可讓物件完全終止其資源。 語句會處置`Using`區塊控制項底下的資源。 `End Using`  
  
## <a name="behavior"></a>行為  
 區塊的行為`Try`就像 ... `Using`區塊會使用資源, 而區塊會處置它們的結構。`Finally` `Finally` `Try` 因此, `Using`不論您如何結束區塊, 區塊都會保證資源的處置。 即使是未處理的例外狀況 (除外<xref:System.StackOverflowException>), 也是如此。  
  
 `Using`語句所取得之每個資源變數的範圍會限制`Using`為區塊。  
  
 如果您在`Using`語句中指定多個系統資源, 其效果會與您在另一個中嵌套`Using`區塊的結果相同。  
  
 如果`resourcename` <xref:System.IDisposable.Dispose%2A>為`Nothing`, 則不會呼叫, 而且不會擲回任何例外狀況。  
  
## <a name="structured-exception-handling-within-a-using-block"></a>Using 區塊內的結構化例外狀況處理  
 如果您需要處理區塊內可能發生的例外狀況, `Using`您可以新增 [完成`Try`...]`Finally`對它進行結構。 如果您需要處理`Using`語句無法成功取得資源的情況, 您可以測試以`resourcename`查看是否為`Nothing`。  
  
## <a name="structured-exception-handling-instead-of-a-using-block"></a>結構化例外狀況處理, 而不是 Using 區塊  
 如果您需要更精確地控制資源的取得, 或在`Finally`區塊中需要額外的程式碼, 您可以將`Using`區塊重寫為`Try`.。。`Finally`結構。 下列範例會顯示`Try`在`resource`的`Using`取得與處置中, 對等的基本架構和結構。  
  
```vb  
Using resource As New resourceType   
    ' Insert code to work with resource.  
End Using  
  
' For the acquisition and disposal of resource, the following  
' Try construction is equivalent to the Using block.  
Dim resource As New resourceType  
Try   
    ' Insert code to work with resource.  
Finally   
    If resource IsNot Nothing Then  
        resource.Dispose()   
    End If  
End Try   
```  
  
> [!NOTE]
> `Using`區塊內的程式碼不應該將中`resourcename`的物件指派給另一個變數。 當您`Using`結束區塊時, 系統會處置資源, 而另一個變數無法存取其指向的資源。  
  
## <a name="example"></a>範例  
 下列範例會建立名為 log .txt 的檔案, 並將兩行文字寫入檔案。 此範例也會讀取相同的檔案, 並顯示文字行。  
  
 <xref:System.IDisposable> `Using`由於和類別<xref:System.IO.TextReader>會實作為介面, 因此程式碼可以使用語句來確保檔案在寫入和讀取作業之後會正確地關閉。 <xref:System.IO.TextWriter>  
  
 [!code-vb[VbVbalrStatements#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#50)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.IDisposable>
- [Try...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [如何：處置系統資源](../../../visual-basic/programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md)
