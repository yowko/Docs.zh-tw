---
title: "例外狀況階層架構 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "例外狀況類型"
  - "執行階段例外狀況"
  - "基底例外狀況"
  - "ApplicationException 類別"
  - "common language runtime 例外狀況"
  - "COM interop，例外狀況"
  - "例外狀況階層"
ms.assetid: f7d68675-be06-40fb-a555-05f0c5a6f66b
caps.latest.revision: 14
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 14
---
# 例外狀況階層架構
例外狀況的類型有兩種：正在執行之程式所產生的例外狀況，以及 Common Language Runtime 所產生的例外狀況。 此外，還有例外狀況的階層架構，可以為應用程式或者執行階段所擲回。  
  
 <xref:System.Exception?displayProperty=fullName>類別是例外狀況的基底類別。 數個例外狀況類別直接繼承自<xref:System.Exception>，包括<xref:System.ApplicationException>和<xref:System.SystemException>。 這兩個類別幾乎組成所有執行階段例外狀況的基礎。  
  
 大部分的例外狀況，直接衍生自<xref:System.Exception>將任何功能和新的成員。 例如， <xref:System.InvalidCastException>類別階層架構如下︰  
  
 <xref:System.Object><xref:System.Exception> <xref:System.SystemException> <xref:System.InvalidCastException>  
  
 執行階段會擲回適當的衍生的類別的<xref:System.SystemException>發生錯誤時。 這些錯誤起因於失敗的執行階段檢查 (例如陣列超出界限的錯誤)，並且會在執行任一方法時發生。 如果您要設計的應用程式，建立新的例外狀況，您應該衍生這些例外狀況從<xref:System.Exception>類別。 不建議您攔截<xref:System.SystemException>，也不是良好的程式設計作法，會擲回<xref:System.SystemException>應用程式中。  
  
 最嚴重的例外狀況，所擲回執行階段，或在無法復原的情況 — 包括<xref:System.ExecutionEngineException>， <xref:System.StackOverflowException>，和<xref:System.OutOfMemoryException>。  
  
 互通性的例外狀況衍生自<xref:System.SystemException> ，可以進一步擴充<xref:System.Runtime.InteropServices.ExternalException>。 例如， <xref:System.Runtime.InteropServices.COMException> COM interop 作業期間擲回的例外狀況，並衍生自<xref:System.Runtime.InteropServices.ExternalException>。 <xref:System.ComponentModel.Win32Exception>和<xref:System.Runtime.InteropServices.SEHException>也衍生自<xref:System.Runtime.InteropServices.ExternalException>。  
  
## <a name="hierarchy-of-runtime-exceptions"></a>執行階段例外狀況的階層架構  
 執行階段有一組基本的例外狀況衍生自<xref:System.SystemException> ，它就會擲回執行個別的指示。 下表階層式列出執行階段提供的標準例外狀況，和在哪些情況下您應該建立衍生類別。  
  
|例外狀況類型|基底類型|描述|範例|  
|--------------------|---------------|-----------------|-------------|  
|[例外狀況](../../../docs/standard/exceptions/exception-class-and-properties.md)|<xref:System.Object>|適用於所有例外狀況的基底類別。|無 (使用這個例外狀況的衍生類別)。|  
|<xref:System.SystemException>|<xref:System.Exception>|適用於所有執行階段所產生錯誤的基底類別。|無 (使用這個例外狀況的衍生類別)。|  
|<xref:System.IndexOutOfRangeException>|<xref:System.SystemException>|只有當陣列索引不正確時，才由執行階段擲回。|在陣列有效範圍之外對它進行索引：<br /><br /> `var i = arr[arr.Length + 1];`<br /><br /> `Dim i = arr(arr.Length + 1)`|  
|<xref:System.NullReferenceException>|<xref:System.SystemException>|只有當參考 Null 物件時，才由執行階段擲回。|`object o = null; string s = o.ToString();`<br /><br /> `Dim o As Object = Nothing Dim s As String = o.ToString()`|  
|<xref:System.AccessViolationException>|<xref:System.SystemException>|只有在存取無效的記憶體時，才由執行階段擲回。|當與 Unmanaged 程式碼或不安全的 Managed 程式碼交互操作，且使用無效的指標時發生。|  
|<xref:System.InvalidOperationException>|<xref:System.SystemException>|當處於無效狀態時，由方法擲回。|呼叫列舉值的`GetNext`方法之後從基礎集合中移除項目。|  
|<xref:System.ArgumentException>|<xref:System.SystemException>|適用於所有引數例外狀況的基底類別。|無 (使用這個例外狀況的衍生類別)。|  
|<xref:System.ArgumentNullException>|<xref:System.ArgumentException>|由不允許引數為 Null 的方法擲回。|`String s = null; int i = "Calculate".IndexOf(s);`<br /><br /> `Dim s As String = Nothing Dim i As Integer = "Calculate".IndexOf(s)`|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.ArgumentException>|由驗證引數是在指定範圍內的方法擲回。|`String s = "string"; s = s.Substring(s.Length + 1);`<br /><br /> `Dim s As String = "string" s = s.Substring(s.Length + 1)`|  
|<xref:System.Runtime.InteropServices.ExternalException>|<xref:System.SystemException>|發生的或以執行階段外部環境為目標的例外狀況的基底類別。|無 (使用這個例外狀況的衍生類別)。|  
|<xref:System.Runtime.InteropServices.COMException>|<xref:System.Runtime.InteropServices.ExternalException>|封裝 COM HRESULT 資訊的例外狀況。|用於 COM Interop。|  
|<xref:System.Runtime.InteropServices.SEHException>|<xref:System.Runtime.InteropServices.ExternalException>|封裝 Win32 結構化例外處理資訊的例外狀況。|用於 Unmanaged 程式碼 Interop。|  
  
## <a name="see-also"></a>另請參閱  
 [Exception 類別和屬性](../../../docs/standard/exceptions/exception-class-and-properties.md)   
 [例外狀況處理基礎觀念](../../../docs/standard/exceptions/exception-handling-fundamentals.md)   
 [例外狀況的最佳作法](../../../docs/standard/exceptions/best-practices-for-exceptions.md)   
 [例外狀況](../../../docs/standard/exceptions/index.md)