---
title: "處理和擲回例外狀況 | Microsoft Docs"
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
  - "Common Language Runtime, 例外狀況"
  - "錯誤 [.NET Framework], 例外狀況"
  - "例外狀況 [.NET Framework]"
  - "例外狀況 [.NET Framework], 處理"
  - "例外狀況 [.NET Framework], 擲回"
  - "篩選例外狀況"
  - "執行階段, 例外狀況"
ms.assetid: f99a1d29-a2a8-47af-9707-9909f9010735
caps.latest.revision: 16
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 16
---
# 處理和擲回例外狀況
<a name="top"></a> 應用程式必須能以一致的方式處理執行期間發生的錯誤。 Common Language Runtime 提供模型，可以統一的方式通知應用程式的錯誤。 .NET Framework 的所有作業都會藉由擲回例外狀況指出失敗。  
  
 此主題包括下列章節：  
  
-   [.NET Framework 中的例外狀況](#exceptions_in_the_net_framework)  
  
-   [例外狀況與傳統錯誤處理方法的比較](#exceptions_vs_traditional_errorhandling_methods)  
  
-   [Common Language Runtime 如何管理例外狀況](#how_the_runtime_manages_exceptions)  
  
-   [篩選執行期間的例外狀況](#filtering_runtime_exceptions)  
  
-   [相關主題](#related_topics)  
  
-   [參考資料](#reference)  
  
<a name="exceptions_in_the_net_framework"></a>   
## .NET Framework 中的例外狀況  
 例外狀況是執行程式所遇到的錯誤狀況或未預期的行為。 若是程式碼或您呼叫 \(例如共用程式庫\) 的程式碼中有錯誤、無法使用作業系統資源、Common Language Runtime 遇到非預期的狀況 \(例如無法驗證程式碼\) 等等，就可能引發例外狀況。 您的應用程式可從一些狀況中復原，但有些狀況就無法復原。 雖然您可以從應用程式的大部分例外狀況中復原，但卻無法從執行階段的大部分例外狀況中復原。  
  
 在 .NET Framework 中，例外狀況是從 <xref:System.Exception?displayProperty=fullName> 類別繼承的物件。 從發生問題的程式碼區域擲回例外狀況。 例外狀況會向上傳遞堆疊，直到應用程式處理或程式終止它。  
  
 [回到頁首](#top)  
  
<a name="exceptions_vs_traditional_errorhandling_methods"></a>   
## 例外狀況與傳統錯誤處理方法的比較  
 傳統上，一種語言的錯誤處理模型不是依賴語言唯一偵測錯誤的方式與尋找處理常式，就是依賴作業系統所提供的錯誤處理機制。 執行階段實作例外狀況可處理下列功能：  
  
-   在不管會產生例外狀況的語言，或處理例外狀況的語言下處理例外狀況。  
  
-   要處理例外狀況不需要任何特定語言的語法，但可讓每一種語言定義自己的語法。  
  
-   可讓例外狀況跨程序，甚至是跨電腦界限擲回。  
  
 例外狀況提供了許多優於其他錯誤通知的方法，例如傳回碼。 不會發生未通知失敗的情況。 無效的值不會透過系統繼續散佈。 您不見得需要檢查傳回碼。 可以輕鬆地新增例外狀況處理程式碼，以增加程式可靠性。 最後一點，執行階段的例外狀況處理速度比 Windows 架構的 C\+\+ 錯誤處理還快。  
  
 因為執行緒會定期周遊 Managed 和 Unmanaged 程式碼區塊，此執行階段可從Managed 或 Unmanaged 程式碼中擲回或攔截例外狀況。 Unmanaged 程式碼可包含 C\+\+ 樣式 SEH 例外狀況以及 COM 架構的 HRESULT。  
  
<a name="how_the_runtime_manages_exceptions"></a>   
## Common Language Runtime 如何管理例外狀況  
 執行階段會依據例外狀況物件，以及受保護的程式碼區塊來使用例外狀況處理模型。 當例外狀況發生時，會建立一個 <xref:System.Exception> 物件來表示例外狀況。  
  
 執行階段會為每個可執行檔建立例外狀況資訊資料表。 在例外狀況資訊資料表中，每個可執行檔的方法都有個例外狀況的處理資訊關聯陣列 \(可為空白\)。 陣列中的每個項目描述了受保護的指令碼區塊、與此程式碼相關聯的任何例外狀況，以及例外狀況的任何處理常式 \(`catch` 陳述式\)。 這個例外狀況資料表效率極高，而且在例外狀況未發生時，不會在處理器時間或記憶體使用上對效能產生任何負面影響。 只有在例外狀況發生時，您才會使用到資源。  
  
 例外狀況資訊表代表了受保護類型區塊中的四種例外狀況處理常式：  
  
-   不論是正常的程式控制流程，或是未處理的例外狀況，每當區塊結束時，`finally` 處理常式就會執行。  
  
-   如果發生例外狀況，就必須執行錯誤處理常式，但不會在正常控制流程完成時執行。  
  
-   一種篩選類型處理常式，可處理指定類別的任何例外狀況或因其衍生的任何類別。  
  
-   一種使用者篩選處理常式，可執行使用者指定的程式碼，以判斷是否應該由相關聯的處理常式處理例外狀況，或是應該傳遞至下一個受保護區塊。  
  
 每種語言會根據語言的規格實作這些例外狀況處理常式。 例如，Visual Basic 透過 \(使用 `When` 關鍵字\) 比較變數，來提供存取使用者篩選的處理常式，在 `catch` 陳述式中，C\# 不會實作使用者篩選的處理常式。  
  
 當例外狀況發生時，執行階段就會開始兩個步驟的程序：  
  
1.  執行階段會替第一個受保護區塊搜尋陣列，該區塊會執行下列項目：  
  
    -   保護包含目前執行指示的區域。  
  
    -   包含例外狀況處理常式，或包含處理例外狀況的篩選條件。  
  
2.  如果相符，執行階段就會建立描述例外狀況的 <xref:System.Exception> 物件。 執行階段接著會執行所有 `finally` 或介於處理例外狀況與發生例外狀況的陳述式間的錯誤陳述式。 請注意例外狀況處理常式的順序非常重要 ；最內層的例外狀況處理常式會先評估。 另請注意，例外狀況處理常式可存取區域變數和攔截到例外狀況的本機記憶體常式，但是在擲回例外狀況時的任何中繼值時都會遺失。  
  
     如果目前的方法沒有相符項目，執行階段就會搜尋目前方法的各個呼叫端，並且在繼續重複此路徑直到堆疊。 如果呼叫端不相符，執行階段會讓偵錯工具存取此例外狀況。 如果偵錯工具未附加至例外狀況，執行階段就會引發 <xref:System.AppDomain.UnhandledException?displayProperty=fullName> 事件。 如果沒有針對此事件的接聽程式，執行階段會傾印堆疊追蹤，並結束應用程式。  
  
 [回到頁首](#top)  
  
<a name="filtering_runtime_exceptions"></a>   
## 篩選執行期間的例外狀況  
 您可以篩選您攔截到的例外狀況，並依據類型或是部分使用者定義的準則處理。  
  
 類型篩選處理常式可管理特定類型的例外狀況 \(或是從其衍生的類別\)。 下列範例顯示出一種設計用來攔截特定例外狀況類型篩選處理常式，在此情況下，即為 <xref:System.IO.FileNotFoundException>。  
  
 [!code-cpp[CatchException#5](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception3.cpp#5)]
 [!code-csharp[CatchException#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception3.cs#5)]
 [!code-vb[CatchException#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception3.vb#5)]  
  
 使用者篩選例外狀況處理常式會依據您定義的例外狀況需求，攔截和處理例外狀況。 如需以這種方式篩選例外狀況的詳細資訊，請參閱 [在 Catch 區塊中使用特定例外狀況](../../../docs/standard/exceptions/how-to-use-specific-exceptions-in-a-catch-block.md)。  
  
 [回到頁首](#top)  
  
<a name="related_topics"></a>   
## 相關主題  
  
|標題|描述|  
|--------|--------|  
|[Exception 類別和屬性](../../../docs/standard/exceptions/exception-class-and-properties.md)|說明例外狀況物件的項目。|  
|[例外狀況階層架構](../../../docs/standard/exceptions/exception-hierarchy.md)|描述大部分例外狀況衍生出的例外狀況。|  
|[例外狀況處理基礎觀念](../../../docs/standard/exceptions/exception-handling-fundamentals.md)|說明如何使用 Catch、擲回，以及最終的陳述式處理例外狀況。|  
|[例外狀況的最佳作法](../../../docs/standard/exceptions/best-practices-for-exceptions.md)|描述處理例外狀況的建議方法。|  
|[處理 COM Interop 例外狀況](../../../docs/standard/exceptions/handling-com-interop-exceptions.md)|描述如何在擲回並攔截的 Unmanaged 程式碼中處理例外狀況。|  
|[如何：對應 HRESULT 和例外狀況](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md)|描述例外狀況 Managed 和 Unmanaged 程式碼之間的對應。|  
  
<a name="reference"></a>   
## 參考資料  
 <xref:System.Exception?displayProperty=fullName>  
  
 <xref:System.ApplicationException?displayProperty=fullName>  
  
 <xref:System.SystemException?displayProperty=fullName>