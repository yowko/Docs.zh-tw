---
title: "追蹤和稽核應用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "追蹤 [.NET Framework]"
  - "偵錯 [.NET Framework]、 檢測"
  - "效能監視檢測"
  - "檢測，關於檢測"
  - "關於追蹤的追蹤 [.NET Framework]"
  - "效能監視，追蹤程式碼"
  - "Trace 類別，.NET 應用程式的檢測"
ms.assetid: 773b6fc4-9013-4322-b728-5dec7a72e743
caps.latest.revision: 21
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 21
---
# 追蹤和稽核應用程式
追蹤可讓您在應用程式執行時，監視應用程式的執行。 您可以在開發 .NET Framework 應用程式時，加入追蹤和偵錯檢測，當您在開發應用程式時，以及將其部署之後，都可以使用該檢測。 您可以使用<xref:System.Diagnostics.Trace?displayProperty=fullName>， <xref:System.Diagnostics.Debug?displayProperty=fullName>，和<xref:System.Diagnostics.TraceSource?displayProperty=fullName>類別，以記錄錯誤和記錄檔、 文字檔案，或其他裝置，以便稍後進行分析的應用程式執行的相關資訊。  
  
 這個詞彙*檢測*是指監視或測量產品效能層級，以及診斷錯誤的能力。 在程式設計中，這表示應用程式納入下列項目的能力：  
  
-   **程式碼追蹤**-接收有關執行的應用程式在執行階段參考訊息。  
  
-   **偵錯**-追蹤並修正在開發的應用程式的程式設計錯誤。 如需詳細資訊，請參閱[偵錯](../Topic/Debugging%20in%20Visual%20Studio.md)。  
  
-   **效能計數器**-元件可讓您追蹤應用程式的效能。 如需詳細資訊，請參閱[效能計數器](../../../docs/framework/debug-trace-profile/performance-counters.md)。  
  
-   **事件記錄檔**-元件可讓您接收和追蹤應用程式的執行中的主要事件。 如需詳細資訊，請參閱<xref:System.Diagnostics.EventLog>類別。  
  
 在程式碼的策略性位置上放置追蹤陳述式來檢測應用程式，特別適用於分散式應用程式。 使用追蹤陳述式可讓您檢測應用程式，不僅可以在發生錯誤時顯示資訊，還可以監視應用程式執行的效能。  
  
 <xref:System.Diagnostics.TraceSource>類別提供增強的追蹤功能，並可用來代替較舊的靜態方法<xref:System.Diagnostics.Trace>和<xref:System.Diagnostics.Debug>追蹤類別。 熟悉<xref:System.Diagnostics.Trace>和<xref:System.Diagnostics.Debug>類別仍廣為使用，但<xref:System.Diagnostics.TraceSource>類別建議用於新的追蹤命令，例如<xref:System.Diagnostics.TraceSource.TraceEvent%2A>和<xref:System.Diagnostics.TraceSource.TraceData%2A>。  
  
 <xref:System.Diagnostics.Trace>和<xref:System.Diagnostics.Debug>類別是完全相同，除了該程序和函式的<xref:System.Diagnostics.Trace>編譯成發行組建，而的預設類別<xref:System.Diagnostics.Debug>類別不是。  
  
 <xref:System.Diagnostics.Trace>和<xref:System.Diagnostics.Debug>類別提供方法來監視及檢查開發期間或部署後的應用程式效能。 例如，您可以使用<xref:System.Diagnostics.Trace>類別來追蹤的特定部署的應用程式中的動作類型發生 （例如，建立新的資料庫連接），並藉此監視應用程式的效率。  
  
## <a name="code-tracing-and-debugging"></a>程式碼追蹤和偵錯  
 在開發期間，您可以使用的輸出方法<xref:System.Diagnostics.Debug>類別，以在 Visual Studio 整合式的開發環境 (IDE) 的 [輸出] 視窗中顯示訊息。 例如:   
  
```vb  
Trace.WriteLine("Hello World!")  
Debug.WriteLine("Hello World!")  
  
```  
  
```csharp  
System.Diagnostics.Trace.WriteLine("Hello World!");  
System.Diagnostics.Debug.WriteLine("Hello World!");  
  
```  
  
 每個範例會顯示"Hello World ！" 在 [輸出] 視窗中偵錯工具執行應用程式時。  
  
 這可讓您偵錯應用程式，並依據其於測試環境中的的行為，將其效能最佳化。 您可以偵錯應用程式偵錯組建中<xref:System.Diagnostics.Debug>開啟，如此您會收到所有的偵錯輸出的條件屬性。 準備發行您的應用程式時，您可以編譯發行組建，無需開啟 <xref:System.Diagnostics.Debug>條件屬性，使編譯器將會包含偵錯程式碼中的最後一個可執行檔。 如需詳細資訊，請參閱[How to︰ 使用追蹤和偵錯進行條件式編譯](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)。 如需有關不同組建組態的應用程式的詳細資訊，請參閱[編譯和建置](../Topic/Compiling%20and%20Building%20in%20Visual%20Studio.md)。  
  
 您也可以追蹤程式碼執行安裝的應用程式中使用的方法<xref:System.Diagnostics.Trace>類別。 藉由放置[追蹤參數](../../../docs/framework/debug-trace-profile/trace-switches.md)在您的程式碼中，您可以控制是否進行追蹤，而且廣泛程度。 這可讓您監視應用程式在生產環境中的狀態。 這很重要，特別是在有多個元件在多部電腦上執行的商務應用程式中。 您可以透過組態檔來控制部署之後如何使用參數。 如需詳細資訊，請參閱[How to︰ 建立、 初始化和設定追蹤參數](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)。  
  
 在開發要使用追蹤的應用程式時，您通常會將追蹤和偵錯訊息都包含在應用程式程式碼中。 當您準備好要部署應用程式時，您可以編譯發行組建，無需開啟 **偵錯**條件屬性。 不過，您可以開啟**追蹤**條件屬性，使編譯器可執行檔中包含您的追蹤程式碼。 如需詳細資訊，請參閱[How to︰ 使用追蹤和偵錯進行條件式編譯](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)。  
  
### <a name="phases-of-code-tracing"></a>程式碼追蹤的階段  
 程式碼追蹤分為三個階段：  
  
1.  **檢測**— 追蹤程式碼加入應用程式。  
  
2.  **追蹤**— 追蹤程式碼會將資訊寫入至指定的目標。  
  
3.  **分析**— 您評估追蹤資訊，以識別並了解應用程式的問題。  
  
 根據預設，在開發期間，所有偵錯和追蹤輸出方法都會將資訊寫入 Visual Studio 中的 [輸出] 視窗。 在已部署的應用程式中，這些方法會將追蹤資訊寫入您指定的目標。 如需有關如何指定追蹤或偵錯的輸出目標的詳細資訊，請參閱[追蹤接聽項](../../../docs/framework/debug-trace-profile/trace-listeners.md)。  
  
 以下是在已部署的應用程式中，使用追蹤來分析及更正潛在問題時，常用的主要步驟整體概觀。 如需有關如何執行這些步驟的詳細資訊，請參閱適當的連結。  
  
##### <a name="to-use-tracing-in-an-application"></a>若要在應用程式中使用追蹤  
  
1.  請考慮您在部署應用程式之後，會想要在現場接收哪些追蹤輸出。  
  
2.  建立一組參數。 如需詳細資訊，請參閱[How to︰ 設定追蹤參數](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)。  
  
3.  將追蹤陳述式加入應用程式程式碼  
  
4.  決定您想要讓追蹤輸出出現在哪裡，並加入適當的接聽程式。 如需詳細資訊，請參閱[建立和初始化追蹤接聽程式](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-listeners.md)。  
  
5.  測試和偵錯您的應用程式，以及其包含的追蹤程式碼。  
  
6.  使用下列其中一個程序，將應用程式編譯為可執行的程式碼：  
  
    -   使用**建置**功能表，以及**偵錯**頁面**屬性頁**對話方塊中的 [**方案總管] 中**。 在 Visual Studio 中進行編譯時，請使用此選項。  
  
         \-或-  
  
    -   使用**追蹤**和**偵錯**編譯的命令列方法的編譯器指示詞。 如需詳細資訊，請參閱[使用追蹤和偵錯進行條件式編譯](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)。 從命令列編譯時，請使用此選項。  
  
7.  如果在執行階段期間發生問題，請開啟適當的追蹤參數。 如需詳細資訊，請參閱[設定追蹤參數](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)。  
  
     追蹤程式碼會將追蹤訊息寫入指定的目標，例如畫面、文字檔或事件記錄檔。 包含在接聽項的類型**Trace.Listeners**集合決定目標。  
  
8.  分析追蹤訊息，以識別並了解應用程式中的問題。  
  
## <a name="trace-instrumentation-and-distributed-applications"></a>追蹤檢測和分散式應用程式  
 當您建立分散式應用程式時，可能會發現很難以將要使用應用程式的方式來測試應用程式。 很少有開發小組能夠測試所有可能的作業系統或 Web 瀏覽器的組合 (包括所有當地語系化的語言選項)，或是模擬將會同時存取應用程式的大量使用者。 在這些情況下，您無法測試分散式應用程式將如何回應龐大的數量、不同的設定，以及獨特的使用者行為。 此外，分散式應用程式的許多部分都沒有使用者介面可讓您直接互動或檢視的那些部分的活動。  
  
 不過，您可以為了彌補這一點來描述系統管理員，尤其是出差錯的事情感興趣的特定事件的分散式應用程式，進而*檢測*應用程式 — 也就是由您的程式碼的策略性位置上放置追蹤陳述式。 然後如果在執行階段時發生非預期的事件 (例如，回應時間極慢)，您就可以判斷可能的原因。  
  
 利用追蹤陳述式，您可以避免掉一些困難的工作，例如，檢查原始來源程式碼、加以修改、重新編譯，以及嘗試在偵錯環境內產生執行階段錯誤。 請記住，檢測應用程式不但可以顯示錯誤，還能監視效能。  
  
## <a name="strategic-placement-of-trace-statements"></a>追蹤陳述式的策略位置  
 在放置追蹤陳述式，以在執行階段使用時，您必須特別小心。 您必須考量，在所部署的應用程式中，可能會需要哪些追蹤資訊，以充分涵蓋所有可能的追蹤案例。 使用追蹤的應用程式差異甚大，但是並沒有追蹤策略位置的一般方針。 如需有關放置追蹤陳述式的詳細資訊，請參閱[How to︰ 將追蹤陳述式加入應用程式程式碼](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)。  
  
## <a name="output-from-tracing"></a>追蹤的輸出  
 追蹤輸出由稱為物件收集*接聽程式*。 接聽程式是會接收追蹤輸出，並將其寫入輸出裝置 (通常是視窗、記錄檔或文字檔) 的物件。 建立追蹤接聽程式時，它通常會新增至<xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=fullName>集合，讓接聽程式接收所有追蹤輸出。  
  
 追蹤資訊一定會寫入至少為預設值<xref:System.Diagnostics.Trace>輸出目標<xref:System.Diagnostics.DefaultTraceListener>。 如果基於某些原因已刪除<xref:System.Diagnostics.DefaultTraceListener>而不加入任何其他接聽程式，<xref:System.Diagnostics.Trace.Listeners%2A>集合中，您將不會收到任何追蹤訊息。 如需詳細資訊，請參閱[追蹤接聽項](../../../docs/framework/debug-trace-profile/trace-listeners.md)。  
  
 六個<xref:System.Diagnostics.Debug>成員和<xref:System.Diagnostics.Trace>下表列出寫入追蹤資訊的方法。  
  
|方法|輸出|  
|------------|------------|  
|**判斷提示**|指定的文字；或者如果未指定，則為呼叫堆疊。 輸出才會寫入做為引數中指定的條件**Assert**陳述式是**false**。|  
|**失敗**|指定的文字；或者如果未指定，則為呼叫堆疊。|  
|**寫入**|指定的文字。|  
|**WriteIf**|指定的文字，如果做為引數中指定的條件**WriteIf**符合陳述式。|  
|**WriteLine**|指定的文字和歸位字元。|  
|**WriteLineIf**|指定的文字和歸位字元傳回時，如果做為引數中指定的條件**WriteLineIf**符合陳述式。|  
  
 中的所有接聽程式<xref:System.Diagnostics.Trace.Listeners%2A>集合接收上表中，所述的訊息，但是所採取的動作而有所不同的接聽程式種類接收訊息。 例如， <xref:System.Diagnostics.DefaultTraceListener>收到時，會顯示判斷提示對話方塊**失敗**或失敗**Assert**通知，但<xref:System.Diagnostics.TextWriterTraceListener>只是將輸出寫入資料流。  
  
 您可以實作自己的接聽程式來產生自訂結果。 比方說，自訂追蹤接聽程式可能會將訊息顯示在訊息方塊，或連接至資料庫，以將訊息加入資料表。 所有自訂接聽程式應該都會支援上述六種方法。 如需建立開發人員定義之接聽程式的詳細資訊，請參閱<xref:System.Diagnostics.TraceListener> .NET Framework 參考中。  
  
> [!NOTE]
>  在[!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)]、 **Debug.Write**， **Debug.WriteIf**， **Debug.WriteLine**，和**Debug.WriteLineIf**方法，已經取代**Debug.Print**較早版本的 Visual Basic 中可用的方法。  
  
 **撰寫**和**WriteLine**方法一律會寫入您指定文字。 **判斷提示**， **WriteIf**，和**WriteLineIf**需要控制它們寫入指定的文字是否為布林值引數，寫入指定之的文字的運算式是否**true** (如**WriteIf**和**WriteLineIf**)，或**false** (如**Assert**)。 **失敗**方法一律會寫入指定的文字。 如需詳細資訊，請參閱[How to︰ 將追蹤陳述式加入應用程式程式碼](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)和.NET Framework 參考。  
  
## <a name="security-concerns"></a>安全性考量  
 如果您在部署 ASP.NET 應用程式之前，沒有先停用追蹤和偵錯，您的應用程式可能會顯示其本身會遭惡意程式利用的相關資訊。 如需詳細資訊，請參閱[How to︰ 使用追蹤和偵錯進行條件式編譯](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)，[編譯和建置](../Topic/Compiling%20and%20Building%20in%20Visual%20Studio.md)，和[How to︰ 建立、 初始化和設定追蹤參數](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)。 偵錯也可以透過 Internet Information Services (IIS) 來設定。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Diagnostics.Trace>   
 <xref:System.Diagnostics.TraceSource>   
 [程式碼合約](../../../docs/framework/debug-trace-profile/code-contracts.md)   
 [C#、 F # 和 Visual Basic 專案類型](../Topic/Debugging%20Preparation:%20C%23,%20F%23,%20and%20Visual%20Basic%20Project%20Types.md)   
 [如何︰ 將追蹤陳述式加入至應用程式程式碼](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)   
 [如何︰ 使用追蹤和偵錯進行條件式編譯](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)   
 [如何︰ 建立、 初始化和設定追蹤參數](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)   
 [如何︰ 建立和初始化追蹤來源](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-sources.md)   
 [如何︰ 使用 TraceSource 和篩選器含有追蹤接聽項](../../../docs/framework/debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners.md)   
 [追蹤接聽程式](../../../docs/framework/debug-trace-profile/trace-listeners.md)   
 [追蹤參數](../../../docs/framework/debug-trace-profile/trace-switches.md)