---
title: "如何：接收第一個可能發生的例外狀況通知"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- first-chance exception notifications
- exceptions, first chance notifications
ms.assetid: 66f002b8-a97d-4a6e-a503-2cec01689113
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d8c98f8a1f09488bb2d93c4fda531f695354059a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-receive-first-chance-exception-notifications"></a>如何：接收第一個可能發生的例外狀況通知
<xref:System.AppDomain> 類別的 <xref:System.AppDomain.FirstChanceException> 事件可讓您在 Common Language Runtime 開始搜尋例外狀況處理常式之前，收到已擲回例外狀況的通知。  
  
 這個事件是在應用程式定義域層級引發。 執行的執行緒可以通過多個應用程式定義域；因此，在另一個應用程式定義域中無法處理某個應用程式定義域中未處理的例外狀況。 在應用程式定義域處理例外狀況之前，通知都會發生在每個已新增事件之處理常式的應用程式定義域中。  
  
 本文中的程序和範例示範如何接收具有一個應用程式定義域的簡單程式中以及您所建立之應用程式定義域中第一個可能發生傳回型別的例外狀況通知。  
  
 如需跨數個應用程式定義域的更複雜範例，請參閱 <xref:System.AppDomain.FirstChanceException> 事件的範例。  
  
## <a name="receiving-first-chance-exception-notifications-in-the-default-application-domain"></a>接收預設應用程式定義域中第一個可能發生傳回型別的例外狀況通知  
 在下列程序中，應用程式的進入點 (`Main()` 方法) 會在預設應用程式定義域中執行。  
  
#### <a name="to-demonstrate-first-chance-exception-notifications-in-the-default-application-domain"></a>示範預設應用程式定義域中第一個可能發生傳回型別的例外狀況通知  
  
1.  使用 Lambda 函式定義 <xref:System.AppDomain.FirstChanceException> 事件的事件處理常式，並將它附加至事件。 在此範例中，事件處理常式會列印已處理事件之應用程式定義域的名稱以及例外狀況的 <xref:System.Exception.Message%2A> 屬性。  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#2)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#2)]  
  
2.  擲回並攔截例外狀況。 執行階段找到例外狀況處理常式之前，會引發 <xref:System.AppDomain.FirstChanceException> 事件，並顯示訊息。 此訊息接在例外狀況處理常式所顯示的訊息後面。  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#3)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#3)]  
  
3.  擲回但不會攔截例外狀況。 執行階段尋找例外狀況處理常式之前，會引發 <xref:System.AppDomain.FirstChanceException> 事件，並顯示訊息。 沒有任何例外狀況處理常式，因此應用程式會終止。  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#4)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#4)]  
  
     此程序的前三個步驟所示的程式碼會形成完整主控台應用程式。 應用程式的輸出會根據 .exe 檔案的名稱而不同，因為預設應用程式定義域的名稱包含 .exe 檔案的名稱和副檔名。 請參閱下面以取得範例輸出。  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#5)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#5)]  
  
## <a name="receiving-first-chance-exception-notifications-in-another-application-domain"></a>接收另一個應用程式定義域中第一個可能發生傳回型別的例外狀況通知  
 如果您的程式包含多個應用程式定義域，您可以選擇哪些應用程式網域會收到通知。  
  
#### <a name="to-receive-first-chance-exception-notifications-in-an-application-domain-that-you-create"></a>接收您所建立之應用程式定義域中第一個可能發生傳回型別的例外狀況通知  
  
1.  定義 <xref:System.AppDomain.FirstChanceException> 事件的事件處理常式。 此範例使用 `static` 方法 (在 Visual Basic 中為 `Shared` 方法)，這個方法會列印已處理事件之應用程式定義域的名稱以及例外狀況的 <xref:System.Exception.Message%2A> 屬性。  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#3)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#3)]  
  
2.  建立應用程式定義域，並將事件處理常式新增至該應用程式定義域的 <xref:System.AppDomain.FirstChanceException> 事件。 在此範例中，應用程式定義域命名為 `AD1`。  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#2)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#2)]  
  
     您可以使用相同的方式在預設應用程式定義域中處理此事件。 在 `Main()` 中使用 `static` (在 Visual Basic 中為 `Shared`) <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> 屬性，以取得預設應用程式定義域的參考。  
  
#### <a name="to-demonstrate-first-chance-exception-notifications-in-the-application-domain"></a>示範應用程式定義域中第一個可能發生傳回型別的例外狀況通知  
  
1.  在您於上一個程序建立的應用程式定義域中建立 `Worker` 物件。 `Worker` 類別必須是公用，而且必須衍生自 <xref:System.MarshalByRefObject>，如本文結尾的完整範例所示。  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#4)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#4)]  
  
2.  呼叫可擲回例外狀況之 `Worker` 物件的方法。 在此範例中，會呼叫 `Thrower` 方法兩次。 第一次，方法引數是 `true`，可讓方法攔截它自己的例外狀況。 第二次，引數是 `false`，而 `Main()` 方法會攔截預設應用程式定義域中的例外狀況。  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#6)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#6)]  
  
3.  將程式碼放在 `Thrower` 方法中，以控制方法是否處理它自己的例外狀況。  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#5)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#5)]  
  
## <a name="example"></a>範例  
 下列範例會建立名為 `AD1` 的應用程式定義域，並將事件處理常式新增至應用程式定義域的 <xref:System.AppDomain.FirstChanceException> 事件。 此範例會在應用程式定義域中建立 `Worker` 類別的執行個體，並呼叫名為 `Thrower` 且擲回 <xref:System.ArgumentException> 的方法。 根據其引數的值，方法會攔截例外狀況或無法處理它。  
  
 每次 `Thrower` 方法在 `AD1` 中擲回例外狀況時，都會在 `AD1` 中引發 <xref:System.AppDomain.FirstChanceException> 事件，而且事件處理常式會顯示訊息。 執行階段接著會尋找例外狀況處理常式。 在第一個案例中，例外狀況處理常式位於 `AD1` 中。 在第二個案例中，此例外狀況未在 `AD1` 中處理，而是改為在預設應用程式定義域中攔截。  
  
> [!NOTE]
>  預設應用程式定義域的名稱與可執行檔的名稱相同。  
  
 如果您將 <xref:System.AppDomain.FirstChanceException> 事件的處理常式新增至預設應用程式定義域，則會引發事件，並在預設應用程式定義域處理例外狀況之前處理事件。 若要查看其運作，請在 `Main()` 開頭新增 C# 程式碼 `AppDomain.CurrentDomain.FirstChanceException += FirstChanceException;` (在 Visual Basic 中，為 `AddHandler AppDomain.CurrentDomain.FirstChanceException, FirstChanceException`)。  
  
 [!code-csharp[System.AppDomain.FirstChanceException_howto#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#1)]
 [!code-vb[System.AppDomain.FirstChanceException_howto#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
  
-   這個範例是命令列應用程式。 若要在 [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)] 中編譯和執行此程式碼，請在 `Main()` 結尾新增 C# 程式碼 `Console.ReadLine();` (在 Visual Basic 中，為 `Console.ReadLine()`)，防止在您讀取輸出之前關閉命令視窗。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.AppDomain.FirstChanceException>
