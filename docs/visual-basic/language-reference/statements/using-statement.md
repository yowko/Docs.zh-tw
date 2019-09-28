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
ms.openlocfilehash: 819af63acb6a1f038300bcb999dcfb904eb8a457
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592081"
---
# <a name="using-statement-visual-basic"></a>Using 陳述式 (Visual Basic)

宣告 @no__t 0 區塊的開頭，並選擇性地取得區塊所控制的系統資源。

## <a name="syntax"></a>語法

```vb
Using { resourcelist | resourceexpression }
    [ statements ]
End Using
```

## <a name="parts"></a>組件

|詞彙|定義|  
|---|---|  
|`resourcelist`|如果您未提供 `resourceexpression`，則為必要。 這個 `Using` 區塊控制項的一或多個系統資源清單，並以逗號分隔。|  
|`resourceexpression`|如果您未提供 `resourcelist`，則為必要。 參考要由此 @no__t 0 區塊控制之系統資源的參考變數或運算式。|  
|`statements`|選擇性。 @No__t 0 區塊執行的語句區塊。|  
|`End Using`|必要項。 結束 @no__t 0 區塊的定義，並處置它所控制的所有資源。|  

 @No__t 0 部分中的每個資源都有下列語法和部分：

 `resourcename As New resourcetype [ ( [ arglist ] ) ]`

 -或-

 `resourcename As resourcetype = resourceexpression`

## <a name="resourcelist-parts"></a>resourcelist 元件

|詞彙|定義|  
|---|---|  
|`resourcename`|必要項。 參考變數，參照 @no__t 0 區塊所控制的系統資源。|  
|`New`|如果 `Using` 語句取得資源，則為必要。 如果您已經取得資源，請使用第二個替代語法。|  
|`resourcetype`|必要項。 資源的類別。 類別必須執行 0 @no__t 介面。|  
|`arglist`|選擇性。 您要傳遞至函式的引數清單，以建立 `resourcetype` 的實例。 請參閱[參數清單](parameter-list.md)。|  
|`resourceexpression`|必要項。 參考系統資源的變數或運算式，滿足 `resourcetype` 的需求。 如果您使用第二個語法替代，則必須先取得資源，然後再將控制權傳遞給 `Using` 語句。|  
  
## <a name="remarks"></a>備註

 有時候，您的程式碼需要非受控資源，例如檔案控制代碼、COM 包裝函式或 SQL 連接。 當您的程式碼完成時，@no__t 0 區塊可保證一或多個這類資源的處置。 這讓它們可供其他程式碼使用。

 受控資源會由 .NET Framework 垃圾收集行程（GC）處置，而不需要您進行任何額外的程式碼撰寫。 您不需要受控資源的 `Using` 區塊。 不過，您仍然可以使用 `Using` 區塊來強制處置受管理的資源，而不是等候垃圾收集行程。

 @No__t-0 區塊有三個部分：取得、使用和處置。

- 取得*表示建立*變數，並將它初始化以參考系統資源。 @No__t-0 語句可以取得一或多個資源，或者您可以在輸入區塊並將它提供給 `Using` 語句之前，只取得一個資源。 如果您提供 `resourceexpression`，則必須先取得資源，然後再將控制權傳遞給 `Using` 語句。

- *使用*方式表示存取資源，並對它們執行動作。 @No__t-0 和 `End Using` 之間的語句代表資源的使用。

- *處置*表示在 `resourcename` 中的物件上呼叫 <xref:System.IDisposable.Dispose%2A> 方法。 這可讓物件完全終止其資源。 @No__t-0 語句會處置 `Using` 區塊控制項下的資源。

## <a name="behavior"></a>行為

 @No__t 0 區塊的行為就像是 `Try` ... `Finally` 結構，其中 `Try` 區塊會使用資源，而 `Finally` 區塊則會處置它們。 因此，不論您如何結束區塊，@no__t 0 區塊都會保證資源的處置。 即使在未處理的例外狀況中，也是如此，但 <xref:System.StackOverflowException> 除外。

 @No__t-0 語句所取得之每個資源變數的範圍僅限於 `Using` 區塊。

 如果您在 `Using` 語句中指定多個系統資源，效果會與您在另一個中嵌套 `Using` 個區塊相同。

 如果 `resourcename` 是 `Nothing`，則不會呼叫 <xref:System.IDisposable.Dispose%2A>，也不會擲回任何例外狀況。

## <a name="structured-exception-handling-within-a-using-block"></a>Using 區塊內的結構化例外狀況處理

 如果您需要處理可能發生在 `Using` 區塊中的例外狀況，您可以在其中加入完整的 `Try` ... `Finally` 的結構。 如果您需要處理 `Using` 語句無法成功取得資源的情況，您可以測試以查看 `resourcename` 是否 `Nothing`。

## <a name="structured-exception-handling-instead-of-a-using-block"></a>結構化例外狀況處理，而不是 Using 區塊

 如果您需要更精確地控制資源的取得，或在 `Finally` 區塊中需要額外的程式碼，您可以將 @no__t 1 區塊重寫為 `Try` ... `Finally` 結構。 下列範例會顯示在 `resource` 的取得與處置中，對等的基本架構 `Try` 和 @no__t 1 的結構。

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
> @No__t-0 區塊內的程式碼不應該將 `resourcename` 中的物件指派給另一個變數。 當您結束 `Using` 區塊時，系統會處置資源，而另一個變數無法存取其指向的資源。

## <a name="example"></a>範例

 下列範例會建立名為 log .txt 的檔案，並將兩行文字寫入檔案。 此範例也會讀取相同的檔案，並顯示文字行：

 因為 <xref:System.IO.TextWriter> 和 @no__t 1 類別會執行 @no__t 2 介面，所以程式碼可以使用 `Using` 語句，以確保檔案在寫入和讀取作業之後會正確地關閉。

 [!code-vb[VbVbalrStatements#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#50)]

## <a name="see-also"></a>另請參閱

- <xref:System.IDisposable>
- [Try...Catch...Finally 陳述式](try-catch-finally-statement.md)
- [如何：處置系統資源 @ no__t-0
