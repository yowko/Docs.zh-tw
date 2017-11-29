---
title: "追蹤接聽項"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Listener object types
- listeners
- Trace class, listeners
- trace listeners, about trace listeners
- Listeners collection
- trace listeners
- tracing [.NET Framework], trace listeners
- logs, trace listeners
ms.assetid: 444b0d33-67ea-4c36-9e94-79c50f839025
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 56cbde16eff89d25960e510e7eec2424f15e51b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="trace-listeners"></a>追蹤接聽項
使用 **Trace**、**Debug** 和 <xref:System.Diagnostics.TraceSource> 時，您必須具有收集和記錄所傳送訊息的機制。 追蹤訊息由「接聽程式」負責接收。 接聽項的用途是收集、儲存和傳送追蹤訊息。 接聽項會將追蹤輸出導向至適當的目標，例如記錄檔、視窗或文字檔。  
  
 接聽程式可供 **Debug**、**Trace** 和 <xref:System.Diagnostics.TraceSource> 類別使用，其中每一項都可以將輸出傳送至各種不同的接聽程式物件。 以下是常用的預先定義接聽程式：  
  
-   <xref:System.Diagnostics.TextWriterTraceListener> 會將輸出重新導向至 <xref:System.IO.TextWriter> 類別的執行個體，或重新導向至任何 <xref:System.IO.Stream> 類別。 因為這些是 <xref:System.IO.Stream> 類別，所以還可寫入至主控台或檔案。  
  
-   <xref:System.Diagnostics.EventLogTraceListener>會將輸出重新導向至事件記錄檔。  
  
-   <xref:System.Diagnostics.DefaultTraceListener> 會發出 **Write** 和 **WriteLine** 訊息至 **OutputDebugString** 和 **Debugger.Log** 方法。 在 Visual Studio 中，這會造成 [輸出] 視窗中出現偵錯訊息。 **Fail** 和失敗的 **Assert** 訊息也會發送至 **OutputDebugString** Windows API 和 **Debugger.Log** 方法，這也造成會顯示訊息方塊。 因為 **DefaultTraceListener** 會被自動納入所有的 `Listeners` 集合，並且這是唯一被自動納入的接聽項，所以這種行為是 **Debug** 和 **Trace** 訊息的預設行為。  
  
-   <xref:System.Diagnostics.ConsoleTraceListener> 會將追蹤或偵錯輸出導向至標準輸出或標準錯誤資料流。  
  
-   <xref:System.Diagnostics.DelimitedListTraceListener> 會將追蹤或偵錯輸出導向文字寫入器，例如資料流寫入器，或是導向資料流，例如檔案資料流。 此追蹤輸出使用分隔的文字格式，該格式使用由 <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> 屬性指定的分隔符號。  
  
-   <xref:System.Diagnostics.XmlWriterTraceListener> 會將追蹤或偵錯輸出當成 XML 編碼資料導向至 <xref:System.IO.TextWriter> 或 <xref:System.IO.Stream>，例如 <xref:System.IO.FileStream>。  
  
 如果您要 <xref:System.Diagnostics.DefaultTraceListener> 以外的接聽程式接收 **Debug**、**Trace** 和 <xref:System.Diagnostics.TraceSource> 輸出，則您必須將該接聽程式新增到 `Listeners` 集合。 如需詳細資訊，請參閱[如何：建立和初始設定追蹤接聽項](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-listeners.md)與[如何：使用 TraceSource 和含有追蹤接聽項的篩選條件](../../../docs/framework/debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners.md)。 **Listeners** 集合中的任何接聽程式都會自追蹤輸出方法取得相同的訊息。 例如，假設您設定兩個接聽項：**TextWriterTraceListener** 和 **EventLogTraceListener**。 則每個接聽項都會收到相同的訊息。 **TextWriterTraceListener** 會將其輸出導向至資料流，而 **EventLogTraceListener** 則會將其輸出導向至事件記錄檔。  
  
 下列範例顯示如何將輸出傳送至 **Listeners** 集合。  
  
```vb  
' Use this example when debugging.  
Debug.WriteLine("Error in Widget 42")  
' Use this example when tracing.  
Trace.WriteLine("Error in Widget 42")  
```  
  
```csharp  
// Use this example when debugging.  
System.Diagnostics.Debug.WriteLine("Error in Widget 42");  
// Use this example when tracing.  
System.Diagnostics.Trace.WriteLine("Error in Widget 42");  
```  
  
 偵錯和追蹤共用同一個 **Listeners** 集合，因此如果您在應用程式中，將接聽程式物件新增到 **Debug.Listeners** 集合，則也會將它新增到 **Trace.Listeners** 集合。  
  
 下列範例顯示如何使用接聽程式將追蹤資訊傳送至主控台：  
  
```vb  
Trace.Listeners.Clear()  
Trace.Listeners.Add(New TextWriterTraceListener(Console.Out))  
```  
  
```csharp  
System.Diagnostics.Trace.Listeners.Clear();  
System.Diagnostics.Trace.Listeners.Add(  
   new System.Diagnostics.TextWriterTraceListener(Console.Out));  
```  
  
## <a name="developer-defined-listeners"></a>開發人員定義的接聽程式  
 您可繼承自 **TraceListener** 基底類別並用自訂方法來覆寫其方法，定義自己的接聽程式。 如需有關如何建立開發人員定義之接聽程式的詳細資訊，請參閱 .NET Framework 參考中的 <xref:System.Diagnostics.TraceListener>。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 <xref:System.Diagnostics.DefaultTraceListener>  
 <xref:System.Diagnostics.TraceListener>  
 [追蹤和檢測應用程式](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)  
 [追蹤參數](../../../docs/framework/debug-trace-profile/trace-switches.md)
