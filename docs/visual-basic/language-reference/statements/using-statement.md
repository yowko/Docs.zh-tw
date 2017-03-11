---
title: "Using Statement (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.using"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "resource disposal"
  - "Try...Catch...Finally statements, equivalent to Using statement"
  - "resources [Visual Basic], disposing"
  - "Using statement"
ms.assetid: 665d1580-dd54-4e96-a9a9-6be2a68948f1
caps.latest.revision: 36
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 36
---
# Using Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

宣告 `Using` 區塊的開頭，並選擇性地取得區塊所控制的系統資源。  
  
## 語法  
  
```  
Using { resourcelist | resourceexpression }  
    [ statements ]  
End Using  
```  
  
## 組件  
  
|||  
|-|-|  
|詞彙|定義|  
|`resourcelist`|如果未提供 `resourceexpression`，則為必要項。  一或多個系統資源清單 `Using` 方塊控制項，並以逗號分隔。|  
|`resourceexpression`|如果未提供 `resourcelist`，則為必要項。  參考此 `Using` 區塊控制之系統資源的參考變數或運算式。|  
|`statements`|選擇項。  `Using` 區塊執行的陳述式區塊。|  
|`End Using`|必要項。  結束 `Using` 區塊的定義，並處置 \(Dispose\) 它控制的所有資源。|  
  
 在 `resourcelist` 部分中的每個資源，都具備下列語法及參數：  
  
 `resourcename As New resourcetype [ ( [ arglist ] ) ]`  
  
 \-或\-  
  
 `resourcename As resourcetype = resourceexpression`  
  
## resourcelist 參數  
  
|||  
|-|-|  
|詞彙|定義|  
|`resourcename`|必要項。  參考變數，參考 `Using` 區塊控制的系統資源。|  
|`New`|如果 `Using` 陳述式會取得資源，則為必要項。  如果您已取得資源，請使用第二個語法代替。|  
|`resourcetype`|必要項。  資源的類別。  類別必須實作 <xref:System.IDisposable> 介面。|  
|`arglist`|選擇項。  您傳遞至建構函式 \(Constructor\)，以建立 `resourcetype` 執行個體的引數清單。  請參閱 [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md)。|  
|`resourceexpression`|必要項。  變數或運算式，參考滿足 `resourcetype` 之需求的系統資源。  如果您使用第二個語法代替，必須先取得資源，才能將控制傳遞至 `Using` 陳述式。|  
  
## 備註  
 有時候程式碼需要 Unmanaged 資源，例如，檔案控制代碼 \(File Handle\)、COM 包裝函式或 SQL 連接。  程式碼完成處理一或多個這類資源時，`Using` 區塊保證會處置它們，  讓其他程式碼也可以使用它們。  
  
 Managed 資源是由 .NET Framework 記憶體回收行程 \(GC\) 處置，而不需另行編碼。  您不需要 `Using` 區塊即可使用 Managed 資源。  但是您仍然可以使用 `Using` 區塊，強制處置 Managed 資源，而不是等待記憶體回收行程。  
  
 `Using` 區塊有三個參數：擷取、使用方式和處置。  
  
-   「*擷取*」\(Acquisition\) 表示建立變數，並將該變數初始設定為參考系統資源。  `Using` 陳述式可以取得一或多個資源，或者可以在輸入區塊之前確切取得一個資源，然後將此資源提供給 `Using` 陳述式。  如果您提供 `resourceexpression`，則必須先取得資源，才能將控制傳遞至 `Using` 陳述式。  
  
-   「*使用方式*」\(Usage\) 表示會存取資源並利用這些資源來執行動作。  `Using` 和 `End Using` 之間的陳述式代表資源的使用方式。  
  
-   「*處置*」\(Disposal\) 表示在 `resourcename` 中的物件上呼叫 <xref:System.IDisposable.Dispose%2A> 方法。  這可讓物件徹底終止其資源。  `End Using` 陳述式會在 `Using` 區塊的控制下處置資源。  
  
## 行為  
 `Using` 區塊的運作方式類似於 `Try`...`Finally` 語法結構，但 `Try` 區塊會使用資源，而 `Finally` 區塊則會處置這些資源。  因此，不論結束區塊的方式為何，`Using` 區塊都保證會處置資源。  即使是未處理的例外狀況 \(Exception\) 也一樣 \(但 <xref:System.StackOverflowException> 除外\)。  
  
 `Using` 陳述式可取得的每個資源變數範圍會受限於 `Using` 區塊。  
  
 如果您在 `Using` 陳述式中指定多個系統資源，效果就和將 `Using` 區塊彼此組成巢狀一樣。  
  
 如果 `resourcename` 是 `Nothing`，對 <xref:System.IDisposable.Dispose%2A> 的呼叫沒有開啟，然後，例外狀況不會被擲回。  
  
## Using 區塊內的結構化例外狀況處理  
 如果您需要處理可能是在 `Using` 區塊內發生的例外狀況，則可以在該區塊中新增完整的 `Try`...`Finally` 語法結構。  如果需要處理的狀況是 `Using` 陳述式未順利取得資源，則可以進行測試，以查看 `resourcename` 是否為 `Nothing`。  
  
## 取代 Using 區塊的結構化例外狀況處理  
 如果您需要在擷取資源時有更好的控制，或是在 `Finally` 區塊中需要其他程式碼，則可以將 `Using` 區塊重新撰寫為 `Try`...`Finally` 語法結構。  下列範例會顯示基本架構 `Try` 和 `Using` 語法結構，這兩個語法結構同等於擷取和處置 `resource`。  
  
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
>  `Using` 區塊內部的程式碼不應該將 `resourcename` 中的物件指派給其他變數。  結束 `Using` 區塊時會處置資源，而其他變數則無法存取它所指向的資源。  
  
## 範例  
 下列範例會建立名為 log.txt 和寫入兩行文字至檔案。  這個範例也會盡量讀取檔案並顯示文字行。  
  
 由於 <xref:System.IO.TextWriter> 和 <xref:System.IO.TextReader> 類別實作介面 <xref:System.IDisposable> ，程式碼可以使用 `Using` 陳述式確保檔案在寫入和讀取作業之後正常關閉。  
  
 [!code-vb[VbVbalrStatements#50](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/using-statement_1.vb)]  
  
## 請參閱  
 <xref:System.IDisposable>   
 [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)   
 [How to: Dispose of a System Resource](../../../visual-basic/programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md)