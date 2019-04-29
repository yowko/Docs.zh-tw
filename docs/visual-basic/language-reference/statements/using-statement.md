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
ms.openlocfilehash: fe53ea58dc98a4de793fe9dad1c3ceeac71622fc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698651"
---
# <a name="using-statement-visual-basic"></a>Using 陳述式 (Visual Basic)
宣告的開頭`Using`封鎖，並選擇性地取得區塊所控制的系統資源。  
  
## <a name="syntax"></a>語法  
  
```  
Using { resourcelist | resourceexpression }  
    [ statements ]  
End Using  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`resourcelist`|如果您未提供所需`resourceexpression`。 這個清單的一或多個系統資源`Using`封鎖控制項，並以逗號分隔。|  
|`resourceexpression`|如果您未提供所需`resourcelist`。 參考變數或運算式，指的系統資源，來控制這個`Using`區塊。|  
|`statements`|選擇性。 陳述式區塊，`Using`封鎖執行。|  
|`End Using`|必要項。 結束的定義`Using`區塊，並處置它所控制的所有資源。|  
  
 在每個資源`resourcelist`組件具有下列語法和組成部分：  
  
 `resourcename As New resourcetype [ ( [ arglist ] ) ]`  
  
 -或-  
  
 `resourcename As resourcetype = resourceexpression`  
  
## <a name="resourcelist-parts"></a>resourcelist 組件  
  
|詞彙|定義|  
|---|---|  
|`resourcename`|必要項。 指的是系統資源的參考變數，`Using`封鎖控制權。|  
|`New`|需要`Using`陳述式會取得資源。 如果您已經取得資源，請使用第二個語法替代方案。|  
|`resourcetype`|必要項。 資源的類別。 此類別必須實作<xref:System.IDisposable>介面。|  
|`arglist`|選擇性。 您要傳遞至要建立的執行個體建構函式的引數清單的`resourcetype`。 請參閱[參數清單](../../../visual-basic/language-reference/statements/parameter-list.md)。|  
|`resourceexpression`|必要項。 變數或運算式指滿足需求的系統資源`resourcetype`。 如果您使用第二個語法替代方案，您必須先取得資源，將控制項傳遞至`Using`陳述式。|  
  
## <a name="remarks"></a>備註  
 有時候您的程式碼需要 unmanaged 的資源，例如檔案控制代碼、 COM 包裝函式或 SQL 連接。 A`Using`區塊與他們完成您的程式碼時，保證一或多個這類資源的處置。 這使其可供其他程式碼使用。  
  
 受管理的資源處置掉.NET Framework 記憶體回收行程 (GC) 而不需要任何額外的程式碼，就在您的組件。 您不需要`Using`區塊的 managed 資源。 不過，您仍然可以使用`Using`區塊，以強制受管理的資源，而不是等待記憶體回收行程的處置。  
  
 A`Using`區塊有三個部分︰ 取得、 使用量以及各種可供使用。  
  
- *取得*表示建立變數，並初始化參考的系統資源。 `Using`陳述式可以取得一或多個資源，或您可以輸入區塊之前，先取得一個資源，並提供它`Using`陳述式。 如果您提供`resourceexpression`，您必須先取得資源，將控制項傳遞至`Using`陳述式。  
  
- *使用量*表示的資源存取和使用它們執行動作。 之間的陳述式`Using`和`End Using`代表資源的使用量。  
  
- *處置*方法呼叫<xref:System.IDisposable.Dispose%2A>方法中的物件上`resourcename`。 這可讓物件完全終止其資源。 `End Using`陳述式處置的資源下`Using`區塊的控制項。  
  
## <a name="behavior"></a>行為  
 A`Using`區塊的行為類似`Try`...`Finally`所在的建構`Try`區塊中使用的資源和`Finally`區塊處置它們。 因為這個緣故，`Using`區塊都保證會處置的資源，無論您如何結束區塊。 即使發生例外狀況，則為 true，這是除了<xref:System.StackOverflowException>。  
  
 取得每個資源變數的範圍`Using`陳述式僅限於`Using`區塊。  
  
 如果您指定一個以上的系統資源，在`Using`陳述式，效果會相同，如同您巢狀`Using`封鎖其中一個在另一個。  
  
 如果`resourcename`是`Nothing`，不需要呼叫<xref:System.IDisposable.Dispose%2A>進行，而且會擲回任何例外狀況。  
  
## <a name="structured-exception-handling-within-a-using-block"></a>處理使用的區塊內的結構化例外狀況  
 如果您需要處理中可能發生的例外狀況`Using`區塊中，您可以新增完整`Try`...`Finally`給它的建構。 如果您要處理的情況所在`Using`陳述式不成功取得資源，您可以測試是否`resourcename`是`Nothing`。  
  
## <a name="structured-exception-handling-instead-of-a-using-block"></a>結構化例外狀況，而不使用區塊處理  
 如果您需要更精細地控制擷取的資源，或您需要額外的程式碼中`Finally`區塊中，您可以重新撰寫`Using`封鎖`Try`...`Finally`建構。 下列範例示範基本架構`Try`並`Using`建構，而且相當於取得和處置`resource`。  
  
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
>  內的程式碼`Using`區塊不應該指派中的物件`resourcename`給另一個變數。 當您結束`Using`區塊中，資源處置，而另一個變數無法存取它所指向的資源。  
  
## <a name="example"></a>範例  
 下列範例會建立名為 log.txt，並將兩行文字寫入檔案的檔案。 範例也會讀取該相同的檔案，並顯示的文字行。  
  
 因為<xref:System.IO.TextWriter>並<xref:System.IO.TextReader>類別會實作<xref:System.IDisposable>介面，可以使用程式碼`Using`陳述式來確認檔案正確關閉之後寫入和讀取作業。  
  
 [!code-vb[VbVbalrStatements#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#50)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.IDisposable>
- [Try...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [如何：處置系統資源](../../../visual-basic/programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md)
