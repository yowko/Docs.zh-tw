---
title: ".NET 原生和編譯 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e38ae4f3-3e3d-42c3-a4b8-db1aa9d84f85
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 5
---
# .NET 原生和編譯
以 .NET Framework 為目標的 Windows 8.1 應用程式及 Windows 桌面應用程式，會以特定的程式設計語言撰寫，並會編譯成中繼語言 \(IL\)。  在執行階段，Just\-In\-Time \(JIT\) 編譯器在第一次執行方法之前，才會負責編譯 IL 為本機電腦的原生程式碼。  相較之下，.NET 原生工具鏈會在編譯時期轉換原始碼為原生程式碼。  本主題比較 .NET 原生與其他適用於 .NET Framework 應用程式的編譯技術，並提供 .NET 原生如何產生原生程式碼的實用概觀，可協助您了解為什麼在以 .NET 原生編譯的程式碼中發生的例外狀況不會發生在 JIT 編譯程式碼中。  
  
## .NET 原生：產生原生二進位檔  
 目標為 .NET Framework 且不使用 .NET 原生工具鏈編譯的應用程式，可由您的應用程式組件組成，其中包含下列項目：  
  
-   描述組件、相依性、包含的類型和描述成員的中繼資料。  中繼資料用於反映和晚期繫結存取，以及在某些情況下也由編譯器及建置工具所使用。  
  
-   實作程式碼。  這包含中繼語言 \(IL\) Opcode。  在執行階段，Just\-In\-Time \(JIT\) 編譯器將其轉譯成目標平台的原生程式碼。  
  
 除了主要應用程式組件，應用程式會要求下列項目必須存在：  
  
-   任何您應用程式所需的其他類別庫或協力廠商組件。  這些組件同樣包含描述組件、類型及成員的中繼資料，以及實作所有類型成員的 IL。  
  
-   .NET Framework 類別庫  這是在安裝 .NET Framework 時安裝在本機系統的組件集合。  包含在 .NET Framework 類別庫中的組件含有一組完整的中繼資料和實作的程式碼。  
  
-   Common Language Runtime。  這是做為組件載入的動態連結程式庫集合，會執行這類服務如：記憶體管理和記憶體回收、例外狀況處理、Just\-In\-Time 編譯、遠端處理和 Interop。  就像類別庫，執行階段會安裝在本機系統上，做為安裝 .NET Framework 的一部分。  
  
 請注意必須有整個 Common Language Runtime 以及應用程式特有的組件、協力廠商組件和系統組件中所有類型的中繼資料和 IL，才能讓應用程式順利執行。  
  
## .NET 原生和 Just\-In\-Time 編譯  
 .NET 原生工具鏈的輸入，是 C\# 或 Visual Basic 編譯器所建置的 Windows 市集應用程式。  換句話說，當語言編譯器完成 Windows 市集應用程式的編譯時，.NET 原生工具鏈就會開始執行。  
  
> [!TIP]
>  因為 .NET 原生的輸入是寫入至 Managed 組件中的 IL 和中繼資料，您仍然可以使用建置前或建置後事件，或修改 MSBuild 專案檔，來執行自訂程式碼產生或其他自訂作業。  
>   
>  不過，不支援會修改 IL，並藉此防止 .NET 工具鏈分析應用程式 IL 的類別。  模糊化是這種類型最值得注意的工具。  
  
 在應用程式從 IL 轉換成原生程式碼的過程中，.NET 原生工具鏈會執行如下所示的作業：  
  
-   對於某些程式碼路徑，它會取代依賴反映和中繼資料的程式碼為靜態機器碼。  例如，如果實值類型不覆寫 <xref:System.ValueType.Equals%2A?displayProperty=fullName> 方法，則測試是否相等的預設測試會使用反映來擷取 <xref:System.Reflection.FieldInfo> 物件，此物件表示值類型的欄位，然後會比較兩個執行個體的欄位值。  當編譯為機器碼時，.NET 原生工具鏈會取代反映程式碼和中繼資料為欄位值的靜態比較。  
  
-   如果可行的話，它會嘗試排除所有中繼資料。  
  
-   在最終的應用程式組件中只包含應用程式所實際叫用的實作程式碼。  這尤其會影響協力廠商程式庫和 .NET Framework 類別庫中的程式碼。  如此一來，應用程式不再依賴協力廠商程式庫或完整 .NET Framework 類別庫；相反地，現在協力廠商和 .NET Framework 類別庫中的程式碼對於應用程式而言是本機的。  
  
-   它會取代完整的 CLR 為重構的執行階段，主要包含記憶體回收行程。  重構的執行階段會在名為 mrt100\_app.dll 的程式庫中找到，對於應用程式而言是本機的，而且也只有數百 KB 大小。  這可能是因為靜態連結不需要許多由 Common Language Runtime 所執行的服務。  
  
    > [!NOTE]
    >  .NET 原生使用相同的記憶體回收行程，如同標準的 Common Language Runtime 。  在 .NET 原生記憶體回收行程中，預設會啟用背景記憶體回收。  如需記憶體回收的詳細資訊，請參閱[Fundamentals of Garbage Collection](../../../docs/standard/garbage-collection/fundamentals.md)。  
  
> [!IMPORTANT]
>  .NET 原生會編譯整個應用程式為原生應用程式。  它不允許您編譯包含類別程式庫的單一組件為原生程式碼，如此一來才可單獨從 Managed 程式碼中呼叫它。  
  
 由 .NET 原生工具鏈所產生的應用程式會寫入名為 ilc.out 的目錄，位於您專案目錄的偵錯或發行目錄中。  它包含下列檔案：  
  
-   *\<appName\>*.exe 為虛設常式可執行檔，只會把控制項傳輸至特殊的 `Main` \(在 *\<appName\>*.dll 中匯出\)。  
  
-   *\<appName\>*.dll 為 Windows 動態連結程式庫，其中包含您應用程式的程式碼，以及來自 .NET Framework 類別庫的程式碼，和任何有相依性的協力廠商程式庫的程式碼。  它也包含支援程式碼，例如應用程式中與 Windows 交互操作及序列化物件所必需的程式碼。  
  
-   mrt100\_app.dll 為重構的執行階段，會提供執行階段服務，例如記憶體回收。  
  
 應用程式的 APPX 資訊清單會擷取所有相依性。  除了直接組合在 appx 封裝中的應用程式 exe、dll 和 mrt100\_app.dll 之外，這還包含另外兩個檔案：  
  
-   msvcr140\_app.dll，其為 mrt100\_app.dll 所使用的 C 執行階段 \(CRT\) 程式庫。  它會包含在封裝中的 Framework 參考。  
  
-   mrt100.dll。  此程式庫包含可改善 mrt100\_app.dll 效能的函式，儘管沒有它也不會造成 mrt100\_app.dll 無法正常運作。  如果有的話，會從本機電腦的 System32 目錄載入它。  
  
 因為 .NET 原生工具鏈只會在當它知道您的應用程式會實際叫用該程式碼時才會連結實作程式碼到應用程式中，所以下列案例所需的中繼資料或實作程式碼可能未必包含於您的應用程式中：  
  
-   反映。  
  
-   動態或晚期繫結引動過程。  
  
-   序列化與還原序列化。  
  
-   COM Interop。  
  
 如果在執行階段沒有必要的中繼資料或實作程式碼，則 .NET 原生執行階段會擲回例外狀況。  您可以防止這些例外狀況發生，並確認 .NET 原生工具鏈中包含必要的中繼資料和實作程式碼，這可藉由使用[執行階段指示詞檔案](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)達成，此為會指定程式項目的 XML 檔案，其中繼資料或實作程式碼必須是在執行階段可用的，且會指派執行階段原則給程式項目。  以下是加入由 .NET 原生工具鏈所編譯的 Windows 市集專案之預設執行階段指示詞檔案：  
  
```  
  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
    <Assembly Name="*Application*" Dynamic="Required All" />  
  </Application>  
</Directives>  
  
```  
  
 這會在應用程式封裝中的所有組件裡啟用所有類型及其所有成員，供反映和動態引動過程之用。  不過，它不會啟用 .NET Framework 類別庫組件中類型的反映或動態啟動。  在許多情況下，這樣已足夠。  
  
## .NET 原生和 NGEN  
 [原生映像產生器](../../../docs/framework/tools/ngen-exe-native-image-generator.md) \(NGEN\) 會編譯組件成機器碼，並在本機電腦上的原生映像快取安裝它們。  不過，儘管 NGEN 如同 .NET 原生會產生機器碼，仍有幾個不同於 .NET 原生的顯著區別：  
  
-   如果沒有原生映像能用於特定的方法，NGEN 會轉而使用 JIT 編譯的程式碼。  這表示在 NGEN 需要轉而使用 JIT 編譯的情況下，原生映像必須繼續包含中繼資料和 IL。  相反地，.NET 原生只會產生原生映像，並不會轉而產生 JIT 編譯。  如此一來，您只需保留一些反映、序列化和 Interop 案例所需的中繼資料。  
  
-   NGEN 繼續依賴完整 Common Language Runtime 的服務，例如組件載入、遠端處理、Interop、記憶體管理、記憶體回收，若有需要的話，也依賴 JIT 編譯。  在 .NET 原生中，這些服務有許多都不必要 \(JIT 編譯\) 或會在建置階段解決，並且併入應用程式組件中。  其中最重要的剩餘服務是記憶體回收，會包含在較小、重構的執行階段，名為 mrt100\_app.dll。  
  
-   NGEN 映像通常易於損壞。  例如，修補檔案或相依性的變更通常要求使用它的組件也是由原生映像所產生的。  特別在 .NET Framework 類別庫中的系統組件更是如此。  相反地，.NET 原生允許獨立地服務彼此的應用程式。  
  
## 請參閱  
 [探索 .NET 原生 \(Channel 9 影片\)](http://channel9.msdn.com/Shows/Going+Deep/Inside-NET-Native)   
 [反映和 .NET 原生](../../../docs/framework/net-native/reflection-and-net-native.md)   
 [.NET 原生一般疑難排解](../../../docs/framework/net-native/net-native-general-troubleshooting.md)