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
ms.openlocfilehash: 725eeb42dc5462022ac1a021c537d701929398ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604961"
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
|`resourcelist`|如果您未提供所需`resourceexpression`。 此清單的一或多個系統資源`Using`封鎖控制項，並以逗號分隔。|  
|`resourceexpression`|如果您未提供所需`resourcelist`。 參考變數或運算式參考之系統資源，這會由`Using`區塊。|  
|`statements`|選擇性。 陳述式區塊，`Using`封鎖執行。|  
|`End Using`|必要。 結束的定義`Using`區塊，並處置它所控制的所有資源。|  
  
 在每個資源`resourcelist`組件具有下列語法和組件：  
  
 `resourcename As New resourcetype [ ( [ arglist ] ) ]`  
  
 -或-  
  
 `resourcename As resourcetype = resourceexpression`  
  
## <a name="resourcelist-parts"></a>resourcelist 組件  
  
|詞彙|定義|  
|---|---|  
|`resourcename`|必要。 指的是系統資源的參考變數，`Using`封鎖控制項。|  
|`New`|若`Using`陳述式會取得資源。 如果您已取得資源，請使用第二個語法替代方案。|  
|`resourcetype`|必要。 資源的類別。 此類別必須實作<xref:System.IDisposable>介面。|  
|`arglist`|選擇性。 您要傳遞給要建立的執行個體建構函式的引數清單`resourcetype`。 請參閱[參數清單](../../../visual-basic/language-reference/statements/parameter-list.md)。|  
|`resourceexpression`|必要。 變數或運算式參考到滿足需求的系統資源`resourcetype`。 如果您使用第二個語法替代方案，您必須先取得資源，控制項傳遞至`Using`陳述式。|  
  
## <a name="remarks"></a>備註  
 有時候您的程式碼需要 unmanaged 的資源，例如檔案控制代碼、 COM 包裝函式或 SQL 連接。 A`Using`區塊保證會處置的一或多個這類資源與其完成您的程式碼時。 這可讓它們使用其他程式碼。  
  
 受管理的資源處置的.NET Framework 記憶體回收行程 (GC) 沒有任何額外撰寫程式碼。 您不需要`Using`managed 資源的區塊。 不過，您仍然可以使用`Using`區塊，以強制執行的受管理的資源，而不是等待記憶體回收行程處置。  
  
 A`Using`區塊都具有三個部分： 擷取、 使用量及處置。  
  
-   *擷取*表示建立的變數，並初始化參考系統資源。 `Using`陳述式可以取得一或多個資源，或者您可以取得輸入區塊之前的一個資源，其提供給`Using`陳述式。 如果您提供`resourceexpression`，您必須先取得資源，控制項傳遞至`Using`陳述式。  
  
-   *使用量*表示存取的資源，並使用它們執行動作。 陳述式之間`Using`和`End Using`代表資源的使用量。  
  
-   *處置*方法呼叫<xref:System.IDisposable.Dispose%2A>方法中的物件上`resourcename`。 這可讓物件正常終止其資源。 `End Using`陳述式下的資源處置`Using`區塊的控制項。  
  
## <a name="behavior"></a>行為  
 A`Using`區塊的行為類似`Try`...`Finally`所在建構`Try`區塊中使用的資源和`Finally`區塊處置它們。 因為這個緣故，`Using`區塊保證會處置資源，不論您如何結束區塊。 即使有未處理的例外狀況，則為 true，這是除了<xref:System.StackOverflowException>。  
  
 來取得每個資源變數的範圍`Using`陳述式僅限於`Using`區塊。  
  
 如果您指定一個以上的系統資源中`Using`陳述式，效果會相同，如同您巢狀`Using`封鎖另一個。  
  
 如果`resourcename`是`Nothing`，不需要呼叫<xref:System.IDisposable.Dispose%2A>進行時，並擲回任何例外狀況。  
  
## <a name="structured-exception-handling-within-a-using-block"></a>使用的區塊中處理結構化例外狀況  
 如果您要處理的例外狀況可能會發生在`Using`區塊中，您可以加入完整`Try`...`Finally`建構它。 如果您要處理的情況其中`Using`陳述式不成功取得資源，您可以測試以查看`resourcename`是`Nothing`。  
  
## <a name="structured-exception-handling-instead-of-a-using-block"></a>結構化例外狀況，而不使用區塊處理  
 如果您需要更細微地控制的資源擷取，或需要額外的程式碼中`Finally`區塊中，您可以重新撰寫`Using`為封鎖`Try`...`Finally`建構。 下列範例顯示基本架構`Try`和`Using`語法結構，而且相當於擷取及處置`resource`。  
  
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
>  內部的程式碼`Using`區塊不應該指派中的物件`resourcename`給另一個變數。 當您結束`Using`處置資源的區塊，以及其他變數無法存取它所指向的資源。  
  
## <a name="example"></a>範例  
 下列範例會建立名為.log.txt，並將兩行文字寫入檔案的檔案。 此範例也會讀取該檔案，並且顯示的文字行。  
  
 因為<xref:System.IO.TextWriter>和<xref:System.IO.TextReader>類別會實作<xref:System.IDisposable>介面，可以使用程式碼`Using`陳述式，以確保檔案正確關閉之後寫入和讀取作業。  
  
 [!code-vb[VbVbalrStatements#50](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/using-statement_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IDisposable>  
 [Try...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [如何：處置系統資源](../../../visual-basic/programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md)
