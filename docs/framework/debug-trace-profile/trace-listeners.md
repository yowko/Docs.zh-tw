---
title: 追蹤接聽項
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 457310fbf12ef2d6143586116f76df1720b59a6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33391750"
---
# <a name="trace-listeners"></a><span data-ttu-id="8a013-102">追蹤接聽項</span><span class="sxs-lookup"><span data-stu-id="8a013-102">Trace Listeners</span></span>
<span data-ttu-id="8a013-103">使用 **Trace**、**Debug** 和 <xref:System.Diagnostics.TraceSource> 時，您必須具有收集和記錄所傳送訊息的機制。</span><span class="sxs-lookup"><span data-stu-id="8a013-103">When using **Trace**, **Debug** and <xref:System.Diagnostics.TraceSource>, you must have a mechanism for collecting and recording the messages that are sent.</span></span> <span data-ttu-id="8a013-104">追蹤訊息由「接聽程式」負責接收。</span><span class="sxs-lookup"><span data-stu-id="8a013-104">Trace messages are received by *listeners*.</span></span> <span data-ttu-id="8a013-105">接聽項的用途是收集、儲存和傳送追蹤訊息。</span><span class="sxs-lookup"><span data-stu-id="8a013-105">The purpose of a listener is to collect, store, and route tracing messages.</span></span> <span data-ttu-id="8a013-106">接聽項會將追蹤輸出導向至適當的目標，例如記錄檔、視窗或文字檔。</span><span class="sxs-lookup"><span data-stu-id="8a013-106">Listeners direct the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
 <span data-ttu-id="8a013-107">接聽程式可供 **Debug**、**Trace** 和 <xref:System.Diagnostics.TraceSource> 類別使用，其中每一項都可以將輸出傳送至各種不同的接聽程式物件。</span><span class="sxs-lookup"><span data-stu-id="8a013-107">Listeners are available to the **Debug**, **Trace**, and <xref:System.Diagnostics.TraceSource> classes, each of which can send its output to a variety of listener objects.</span></span> <span data-ttu-id="8a013-108">以下是常用的預先定義接聽程式：</span><span class="sxs-lookup"><span data-stu-id="8a013-108">The following are the commonly used predefined listeners:</span></span>  
  
-   <span data-ttu-id="8a013-109"><xref:System.Diagnostics.TextWriterTraceListener> 會將輸出重新導向至 <xref:System.IO.TextWriter> 類別的執行個體，或重新導向至任何 <xref:System.IO.Stream> 類別。</span><span class="sxs-lookup"><span data-stu-id="8a013-109">A <xref:System.Diagnostics.TextWriterTraceListener> redirects output to an instance of the <xref:System.IO.TextWriter> class or to anything that is a <xref:System.IO.Stream> class.</span></span> <span data-ttu-id="8a013-110">因為這些是 <xref:System.IO.Stream> 類別，所以還可寫入至主控台或檔案。</span><span class="sxs-lookup"><span data-stu-id="8a013-110">It can also write to the console or to a file, because these are <xref:System.IO.Stream> classes.</span></span>  
  
-   <span data-ttu-id="8a013-111"><xref:System.Diagnostics.EventLogTraceListener>會將輸出重新導向至事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="8a013-111">An <xref:System.Diagnostics.EventLogTraceListener> redirects output to an event log.</span></span>  
  
-   <span data-ttu-id="8a013-112"><xref:System.Diagnostics.DefaultTraceListener> 會發出 **Write** 和 **WriteLine** 訊息至 **OutputDebugString** 和 **Debugger.Log** 方法。</span><span class="sxs-lookup"><span data-stu-id="8a013-112">A <xref:System.Diagnostics.DefaultTraceListener> emits **Write** and **WriteLine** messages to the **OutputDebugString** and to the **Debugger.Log** method.</span></span> <span data-ttu-id="8a013-113">在 Visual Studio 中，這會造成 [輸出] 視窗中出現偵錯訊息。</span><span class="sxs-lookup"><span data-stu-id="8a013-113">In Visual Studio, this causes the debugging messages to appear in the Output window.</span></span> <span data-ttu-id="8a013-114">**Fail** 和失敗的 **Assert** 訊息也會發送至 **OutputDebugString** Windows API 和 **Debugger.Log** 方法，這也造成會顯示訊息方塊。</span><span class="sxs-lookup"><span data-stu-id="8a013-114">**Fail** and failed **Assert** messages also emit to the **OutputDebugString** Windows API and the **Debugger.Log** method, and also cause a message box to be displayed.</span></span> <span data-ttu-id="8a013-115">因為 **DefaultTraceListener** 會被自動納入所有的 `Listeners` 集合，並且這是唯一被自動納入的接聽項，所以這種行為是 **Debug** 和 **Trace** 訊息的預設行為。</span><span class="sxs-lookup"><span data-stu-id="8a013-115">This behavior is the default behavior for **Debug** and **Trace** messages, because **DefaultTraceListener** is automatically included in every `Listeners` collection and is the only listener automatically included.</span></span>  
  
-   <span data-ttu-id="8a013-116"><xref:System.Diagnostics.ConsoleTraceListener> 會將追蹤或偵錯輸出導向至標準輸出或標準錯誤資料流。</span><span class="sxs-lookup"><span data-stu-id="8a013-116">A <xref:System.Diagnostics.ConsoleTraceListener> directs tracing or debugging output to either the standard output or the standard error stream.</span></span>  
  
-   <span data-ttu-id="8a013-117"><xref:System.Diagnostics.DelimitedListTraceListener> 會將追蹤或偵錯輸出導向文字寫入器，例如資料流寫入器，或是導向資料流，例如檔案資料流。</span><span class="sxs-lookup"><span data-stu-id="8a013-117">A <xref:System.Diagnostics.DelimitedListTraceListener> directs tracing or debugging output to a text writer, such as a stream writer, or to a stream, such as a file stream.</span></span> <span data-ttu-id="8a013-118">此追蹤輸出使用分隔的文字格式，該格式使用由 <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> 屬性指定的分隔符號。</span><span class="sxs-lookup"><span data-stu-id="8a013-118">The trace output is in a delimited text format that uses the delimiter specified by the <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> property.</span></span>  
  
-   <span data-ttu-id="8a013-119"><xref:System.Diagnostics.XmlWriterTraceListener> 會將追蹤或偵錯輸出當成 XML 編碼資料導向至 <xref:System.IO.TextWriter> 或 <xref:System.IO.Stream>，例如 <xref:System.IO.FileStream>。</span><span class="sxs-lookup"><span data-stu-id="8a013-119">An <xref:System.Diagnostics.XmlWriterTraceListener> directs tracing or debugging output as XML-encoded data to a <xref:System.IO.TextWriter> or to a <xref:System.IO.Stream>, such as a <xref:System.IO.FileStream>.</span></span>  
  
 <span data-ttu-id="8a013-120">如果您要 <xref:System.Diagnostics.DefaultTraceListener> 以外的接聽程式接收 **Debug**、**Trace** 和 <xref:System.Diagnostics.TraceSource> 輸出，則您必須將該接聽程式新增到 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="8a013-120">If you want any listener besides the <xref:System.Diagnostics.DefaultTraceListener> to receive **Debug**, **Trace** and <xref:System.Diagnostics.TraceSource> output, you must add it to the `Listeners` collection.</span></span> <span data-ttu-id="8a013-121">如需詳細資訊，請參閱[如何：建立和初始設定追蹤接聽項](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-listeners.md)與[如何：使用 TraceSource 和含有追蹤接聽項的篩選條件](../../../docs/framework/debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners.md)。</span><span class="sxs-lookup"><span data-stu-id="8a013-121">For more information, see [How to: Create and Initialize Trace Listeners](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-listeners.md) and [How to: Use TraceSource and Filters with Trace Listeners](../../../docs/framework/debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners.md).</span></span> <span data-ttu-id="8a013-122">**Listeners** 集合中的任何接聽程式都會自追蹤輸出方法取得相同的訊息。</span><span class="sxs-lookup"><span data-stu-id="8a013-122">Any listener in the **Listeners** collection gets the same messages from the trace output methods.</span></span> <span data-ttu-id="8a013-123">例如，假設您設定兩個接聽項：**TextWriterTraceListener** 和 **EventLogTraceListener**。</span><span class="sxs-lookup"><span data-stu-id="8a013-123">For example, suppose you set up two listeners: a **TextWriterTraceListener** and an **EventLogTraceListener**.</span></span> <span data-ttu-id="8a013-124">則每個接聽項都會收到相同的訊息。</span><span class="sxs-lookup"><span data-stu-id="8a013-124">Each listener receives the same message.</span></span> <span data-ttu-id="8a013-125">**TextWriterTraceListener** 會將其輸出導向至資料流，而 **EventLogTraceListener** 則會將其輸出導向至事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="8a013-125">The **TextWriterTraceListener** would direct its output to a stream, and the **EventLogTraceListener** would direct its output to an event log.</span></span>  
  
 <span data-ttu-id="8a013-126">下列範例顯示如何將輸出傳送至 **Listeners** 集合。</span><span class="sxs-lookup"><span data-stu-id="8a013-126">The following example shows how to send output to the **Listeners** collection.</span></span>  
  
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
  
 <span data-ttu-id="8a013-127">偵錯和追蹤共用同一個 **Listeners** 集合，因此如果您在應用程式中，將接聽程式物件新增到 **Debug.Listeners** 集合，則也會將它新增到 **Trace.Listeners** 集合。</span><span class="sxs-lookup"><span data-stu-id="8a013-127">Debug and trace share the same **Listeners** collection, so if you add a listener object to a **Debug.Listeners** collection in your application, it gets added to the **Trace.Listeners** collection as well.</span></span>  
  
 <span data-ttu-id="8a013-128">下列範例顯示如何使用接聽程式將追蹤資訊傳送至主控台：</span><span class="sxs-lookup"><span data-stu-id="8a013-128">The following example shows how to use a listener to send tracing information to a console:</span></span>  
  
```vb  
Trace.Listeners.Clear()  
Trace.Listeners.Add(New TextWriterTraceListener(Console.Out))  
```  
  
```csharp  
System.Diagnostics.Trace.Listeners.Clear();  
System.Diagnostics.Trace.Listeners.Add(  
   new System.Diagnostics.TextWriterTraceListener(Console.Out));  
```  
  
## <a name="developer-defined-listeners"></a><span data-ttu-id="8a013-129">開發人員定義的接聽程式</span><span class="sxs-lookup"><span data-stu-id="8a013-129">Developer-Defined Listeners</span></span>  
 <span data-ttu-id="8a013-130">您可繼承自 **TraceListener** 基底類別並用自訂方法來覆寫其方法，定義自己的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="8a013-130">You can define your own listeners by inheriting from the **TraceListener** base class and overriding its methods with your customized methods.</span></span> <span data-ttu-id="8a013-131">如需有關如何建立開發人員定義之接聽程式的詳細資訊，請參閱 .NET Framework 參考中的 <xref:System.Diagnostics.TraceListener>。</span><span class="sxs-lookup"><span data-stu-id="8a013-131">For more information on creating developer-defined listeners, see <xref:System.Diagnostics.TraceListener> in the .NET Framework reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a013-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a013-132">See Also</span></span>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 <xref:System.Diagnostics.DefaultTraceListener>  
 <xref:System.Diagnostics.TraceListener>  
 [<span data-ttu-id="8a013-133">追蹤和檢測應用程式</span><span class="sxs-lookup"><span data-stu-id="8a013-133">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)  
 [<span data-ttu-id="8a013-134">追蹤參數</span><span class="sxs-lookup"><span data-stu-id="8a013-134">Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/trace-switches.md)
