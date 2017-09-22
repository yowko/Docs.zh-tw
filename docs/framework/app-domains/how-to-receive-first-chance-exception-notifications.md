---
title: "如何：接收第一個可能發生的例外狀況通知"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- first-chance exception notifications
- exceptions, first chance notifications
ms.assetid: 66f002b8-a97d-4a6e-a503-2cec01689113
caps.latest.revision: 10
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: dd906fa2d45331082b9dc86c972e5630361e2653
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# 如何：接收第一個可能發生的例外狀況通知
<xref:System.AppDomain> 類別的 <xref:System.AppDomain.FirstChanceException> 事件可讓您在 Common Language Runtime 開始搜尋例外處理常式之前，接收擲回例外狀況的通知。  
  
 這個事件會在應用程式定義域層級中引發。  一個例外狀況的執行緒可以通過多個應用程式定義域，所以在一個應用程式定義域中未處理的例外狀況可以在另一個應用程式定義域中處理。  在加入事件處理常式的每個應用程式定義域中，都會發生通知，直到應用程式定義域處理例外狀況為止。  
  
 本文中的程序和範例顯示如何在具有一個應用程式定義域的簡單程式，以及在您所建立應用程式定義域中接收第一個可能發生的例外狀況通知。  
  
 如需深入了解較複雜之跨多個應用程式定義域的範例，請參閱 <xref:System.AppDomain.FirstChanceException> 事件的範例。  
  
## 在預設應用程式定義域中接收第一個可能發生的例外狀況通知  
 在下列程序中，應用程式的進入點 \(`Main()` 方法\) 會在預設應用程式定義域中執行。  
  
#### 若要在預設應用程式定義域中示範第一個可能發生的例外狀況通知  
  
1.  使用 Lambda 函式定義 <xref:System.AppDomain.FirstChanceException> 事件的事件處理常式，然後將該處理常式附加至事件。  在這個範例中，事件處理常式會列印用以處理事件的應用程式定義域的名稱以及例外狀況的 <xref:System.Exception.Message%2A> 屬性。  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#2)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#2)]  
  
2.  擲回例外狀況並攔截例外狀況。  在執行階段尋找例外狀況處理常式之前，會引發 <xref:System.AppDomain.FirstChanceException> 事件並會顯示訊息。  此訊息之後為例外狀況處理常式顯示的訊息。  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#3)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#3)]  
  
3.  擲回例外狀況但不攔截例外狀況。  在執行階段尋找例外狀況處理常式之前，會引發 <xref:System.AppDomain.FirstChanceException> 事件並會顯示訊息。  因為沒有例外狀況處理常式，所以應用程式會終止。  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#4)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#4)]  
  
     這個程序前三個步驟顯示的程式碼可共同形成完整的主控台應用程式。  應用程式的輸出會隨 .exe 檔案的名稱而有所不同，這是因為預設應用程式定義域的名稱是由 .exe 檔案的檔名和副檔名所組成。  請參閱下列的範例輸出。  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#5)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#5)]  
  
## 在另一個應用程式定義域中接收第一個可能發生的例外狀況通知  
 如果程式包含多個應用程式定義域，則可以選擇哪些應用程式定義域來接收通知。  
  
#### 若要在您建立的應用程式定義域中接收第一個可能發生的例外狀況通知  
  
1.  為 <xref:System.AppDomain.FirstChanceException> 事件定義事件處理常式。  此範例使用 `static` 方法 \(在 Visual Basic 中為 `Shared` 方法\)，其會列印處理事件的應用程式定義域的名稱和例外狀況的 <xref:System.Exception.Message%2A> 屬性。  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#3)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#3)]  
  
2.  建立應用程式定義域，並將事件處理常式加入至該應用程式定義域的 <xref:System.AppDomain.FirstChanceException> 事件中。  在此範例中，應用程式定義域命名為 `AD1`。  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#2)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#2)]  
  
     您可以使用相同的方式在預設應用程式定義域中處理這個事件。  在 `Main()` 中使用 `static` \(在 Visual Basic 中為 `Shared`\) <xref:System.AppDomain.CurrentDomain%2A?displayProperty=fullName> 屬性，以取得預設應用程式定義域的參考。  
  
#### 若要在應用程式定義域中示範第一個可能發生的例外狀況通知  
  
1.  在您於先前的程序建立的應用程式定義域中建立 `Worker` 物件。  `Worker` 類別必須是公開的，且必須衍生自 <xref:System.MarshalByRefObject>，如本文結尾的完整範例所示。  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#4)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#4)]  
  
2.  呼叫會擲回例外狀況的 `Worker` 物件的方法。  在這個範例中，會呼叫 `Thrower` 方法兩次。  第一次，方法引數為 `true`，這會導致方法攔截它自己的例外狀況。  第二次引數為 `false`，且 `Main()` 方法會攔截預設應用程式定義域的例外狀況。  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#6)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#6)]  
  
3.  請將程式碼放置在 `Thrower` 方法中，以控制方法是否處理它自己的例外狀況。  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#5)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#5)]  
  
## 範例  
 下列程式碼會建立名為 `AD1` 的應用程式定義域，並將事件處理常式加入至應用程式定義域的 <xref:System.AppDomain.FirstChanceException> 事件。  這個範例會在應用程式定義域中建立 `Worker` 類別的執行個體，然後呼叫名為 `Thrower` 的方法，其會擲出 <xref:System.ArgumentException>。  視引數的值而定，這個方法會攔截例外狀況或無法處理該例外狀況。  
  
 每次 `Thrower` 方法在 `AD1` 中擲出例外狀況時，都會在 `AD1` 中引發 <xref:System.AppDomain.FirstChanceException> 事件，並且事件處理常式會顯示訊息。  然後執行階段會搜尋例外狀況處理常式。  在第一種情況下，會在 `AD1` 中找到例外狀況處理常式。  在第二種情況下，不會在 `AD1` 中處理例外狀況，而是在預設應用程式定義域中攔截例外狀況。  
  
> [!NOTE]
>  預設應用程式定義域的名稱與可執行檔的名稱相同。  
  
 如果您將 <xref:System.AppDomain.FirstChanceException> 事件的處理常式新增至預設應用程式定義域，則會引發事件，並在預設應用程式定義域處理例外狀況之前處理事件。 若要查看其運作，請在 `Main()` 開頭新增 C# 程式碼 `AppDomain.CurrentDomain.FirstChanceException += FirstChanceException;` (在 Visual Basic 中，為 `AddHandler AppDomain.CurrentDomain.FirstChanceException, FirstChanceException`)。  
  
 [!code-csharp[System.AppDomain.FirstChanceException_howto#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#1)]
 [!code-vb[System.AppDomain.FirstChanceException_howto#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#1)]  
  
## 編譯程式碼  
  
-   這個範例是命令列應用程式。  若要在 [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)] 中編譯和執行此程式碼，請將 C\# 程式碼 `Console.ReadLine();` \(在 Visual Basic 中為 `Console.ReadLine()`\) 加入至 `Main()` 的結尾，以阻止在您還沒有閱讀輸出之前，命令視窗即關閉。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.AppDomain.FirstChanceException>

