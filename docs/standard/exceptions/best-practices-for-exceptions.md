---
title: "例外狀況的最佳作法 | Microsoft Docs"
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
  - "例外狀況, 最佳作法"
ms.assetid: f06da765-235b-427a-bfb6-47cd219af539
caps.latest.revision: 28
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 28
---
# 例外狀況的最佳作法
設計良好的應用程式可處理例外狀況和錯誤，防止應用程式損毀。  本文將說明處理和建立例外狀況的最佳實務作法。  
  
## 處理例外狀況  
 下列清單中包含處理應用程式中例外狀況的一般方針。  
  
-   適時使用例外狀況處理程式碼 \(`try`\/`catch` 區塊\)。  您也可以利用程式設計方式檢查可能發生的情況，而不需使用例外狀況處理。  
  
     **以程式設計方式檢查**。  下列範例使用 `if` 陳述式來檢查連接是否關閉。  如果連接未關閉，範例中會關閉連接，而不是擲回例外狀況。  
  
     [!code-cpp[Conceptual.Exception.Handling#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#2)]
     [!code-csharp[Conceptual.Exception.Handling#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#2)]
     [!code-vb[Conceptual.Exception.Handling#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#2)]  
  
     **例外狀況處理**。  下列範例會使用 `try`\/`catch` 區塊檢查連接，並且於連接未關閉時擲回例外狀況。  
  
     [!code-cpp[Conceptual.Exception.Handling#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#3)]
     [!code-csharp[Conceptual.Exception.Handling#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#3)]
     [!code-vb[Conceptual.Exception.Handling#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#3)]  
  
     您選擇的方法取決於您預期事件會發生的頻率。  
  
    -   如果事件不常發生，也就是說事件真的是例外並且表示錯誤 \(例如未預期的檔案結尾\)，則使用例外狀況處理。  當您使用例外狀況處理時，在正常情況下會執行較少的程式碼。  
  
    -   如果事件定期發生而且可視為正常執行的一部分，請使用程式設計方式檢查是否有錯誤。  當您以程式設計方式檢查錯誤時，如果發生例外狀況，則會執行較多程式碼。  
  
-   在可能產生例外狀況的程式碼周圍使用 `try`\/`catch` 區塊，並視需要使用 `finally` 區塊清除資源。  這樣一來，`try` 陳述式會產生例外狀況、`catch` 陳述式會處理例外狀況，而 `finally` 陳述式則不論是否發生例外狀況都會關閉或取消配置資源。  
  
-   在 `catch` 區塊中，一律將例外狀況從最特殊的排列到最不特殊的。  這項技術會在特定例外狀況傳遞至較為一般的 `catch` 區塊之前進行處理。  
  
## 建立及引發例外狀況  
 下列清單包含建立自己的例外狀況及何時應引發例外狀況的方針。  如需詳細資訊，請參閱 [例外狀況的設計指導方針](../../../docs/standard/design-guidelines/exceptions.md)。  
  
-   設計類別以讓例外狀況在正常使用時絕不會擲回。  例如，<xref:System.IO.FileStream> 類別會提供方法，協助判斷是否已經抵達檔案結尾。  這避免萬一您讀取超過檔案結尾時，會擲回例外狀況。  下列範例示範如何讀取至檔案結尾。  
  
     [!code-cpp[Conceptual.Exception.Handling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#5)]
     [!code-csharp[Conceptual.Exception.Handling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#5)]
     [!code-vb[Conceptual.Exception.Handling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#5)]  
  
-   擲回例外狀況來代替傳回錯誤碼或 HRESULT。  
  
-   對於相當普片的錯誤案例傳回 null，而不會擲回例外狀況。  相當普遍的錯誤案例可視為一般控制流程。  針對這些案例傳回 null，就能盡量降低對應用程式效能的影響。  
  
-   在大部分情況下，使用預先定義的 .NET Framework 例外狀況類型。  只有在預先定義的類型不適用時，才引進新的例外狀況類別。  
  
-   如果屬性集或方法呼叫對於物件的目前狀態而言並不適當，就會擲回 <xref:System.InvalidOperationException> 例外狀況。  
  
-   如果傳遞無效的參數，就會擲回 <xref:System.ArgumentException> 例外狀況或是衍生自 <xref:System.ArgumentException> 的類別。  
  
-   對於大多數應用程式，請從 <xref:System.Exception> 類別衍生自訂例外狀況。  衍生自 <xref:System.ApplicationException> 類別並不會加入重要的值。  
  
-   以文字 "Exception" 做為例外狀況類別名稱的結尾。  例如：  
  
     [!code-cpp[Conceptual.Exception.Handling#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#4)]
     [!code-csharp[Conceptual.Exception.Handling#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#4)]
     [!code-vb[Conceptual.Exception.Handling#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#4)]  
  
-   在 C\# 和 C\+\+ 中，當您建立自己的例外狀況類別時，請使用至少三種常見的建構函式：預設建構函式、採用字串訊息的建構函式，以及採用字串訊息和內部例外狀況的建構函式。  如需範例，請參閱 [如何：建立使用者定義的例外狀況](../../../docs/standard/exceptions/how-to-create-user-defined-exceptions.md)。  
  
    1.  <xref:System.Exception.%23ctor>，它會使用預設值。  
  
    2.  <xref:System.Exception.%23ctor%28System.String%29>，它會接受字串訊息。  
  
    3.  <xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>，它會接受字串訊息和內部例外狀況。  
  
-   當您建立使用者定義的例外狀況時，必須確保例外狀況的中繼資料可供程式碼作遠端執行，包括當例外狀況跨應用程式定義域發生時。  例如，假定應用程式定義域 A 建立應用程式定義域 B，它會執行擲回例外狀況的程式碼。  為了讓應用程式定義域 A 正確攔截並處理例外狀況，它必須能夠尋找含有應用程式定義域 B 所擲回之例外狀況的組件。  如果應用程式定義域 B 擲回例外狀況，但此例外狀況包含位於其應用程式基底之下，而不是在應用程式定義域 A 的應用程式基底之下的組件，應用程式定義域 A 將無法尋找例外狀況，而通用語言執行平台將擲回 <xref:System.IO.FileNotFoundException>。  若要避免這個情形，您可以透過兩種方式部署含有例外狀況資訊的組件：  
  
    -   將組件放入這兩個應用程式定義域共用的通用應用程式基底。  
  
         \-或\-  
  
    -   如果定義域不共用通用應用程式基底，則以強式名稱簽署含有例外狀況資訊的組件，並將組件部署到全域組件快取中。  
  
-   將當地語系化的說明字串包含於一切例外狀況中。  使用者看到的錯誤訊息是衍生自擲回的例外狀況描述字串，而不是衍生自例外狀況類別。  
  
-   使用文法正確的錯誤訊息，包括結束的標點符號。  例外狀況說明字串中的每一句應該以句號結束。  例如「記錄表溢位」就是適當的描述字串。  
  
-   提供 <xref:System.Exception> 屬性以供程式設計方式存取。  只有在額外資訊對某個程式設計案例有用時，才提供例外狀況的額外屬性 \(以及描述字串\)。  例如，<xref:System.IO.FileNotFoundException> 提供 <xref:System.IO.FileNotFoundException.FileName%2A> 屬性。  
  
-   堆疊追蹤會從擲回例外狀況所在的陳述式開始，並在攔截例外狀況的 `catch` 陳述式結束。  在決定要放置 `throw` 陳述式的放置時，請留意這個情況。  
  
-   使用例外狀況產生器方法。  類別在它的實作中從不同的地方擲回相同的例外狀況是很常見的。  若要避免過多的程式碼，請使用 Helper 方法，以建立例外狀況並將它傳回。  例如：  
  
     [!code-cpp[Conceptual.Exception.Handling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#6)]
     [!code-csharp[Conceptual.Exception.Handling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#6)]
     [!code-vb[Conceptual.Exception.Handling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#6)]  
  
     此外，使用例外狀況的建構函式來建置例外狀況。  這對全域例外狀況類別而言更為適當，例如 <xref:System.ArgumentException>。  
  
-   在擲回例外狀況時清除中繼結果。  呼叫端應該能夠假設，從方法擲回例外狀況時不會產生副作用。  
  
## 請參閱  
 [例外狀況](../../../docs/standard/exceptions/index.md)