---
title: "Default XAML Schema Context and WPF XAML Schema Context | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 04e06a15-09b3-4210-9bdf-9a64c2eccb83
caps.latest.revision: 7
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 7
---
# Default XAML Schema Context and WPF XAML Schema Context
XAML 結構描述內容是一種概念實體，可限定使用特定 XAML 詞彙的 XAML 產物與物件寫入行為互動的方式，包括如何解析型別對應、如何載入組件、如何解譯特定讀取器和寫入器設定。  本主題說明 .NET Framework XAML 服務的功能，以及以 CLR 型別系統為基礎的相關預設 XAML 結構描述內容。  本主題還說明用於 WPF 的 XAML 結構描述內容。  
  
## 預設 XAML 結構描述內容  
 .NET Framework XAML 服務會實作及使用預設 XAML 結構描述內容。  在 <xref:System.Xaml.XamlSchemaContext> 類別的 API 中，並非永遠完全看得見預設 XAML 結構描述內容行為。  但是，在許多情況下，可以透過 XAML 型別系統的通用 API \(如 <xref:System.Xaml.XamlMember> 或 <xref:System.Xaml.XamlType> 的成員\)，或透過在使用預設 XAML 結構描述內容的 XAML 讀取器和 XAML 寫入器上公開的 API，觀察到預設 XAML 結構描述內容所影響的行為。  
  
 您可以建立封裝預設行為的 <xref:System.Xaml.XamlSchemaContext>，方法是呼叫 <xref:System.Xaml.XamlSchemaContext> 建構函式。  這樣會明確建立預設 XAML 結構描述內容。  如果您使用未明確加上 <xref:System.Xaml.XamlSchemaContext> 輸入參數的 API 來初始化 XAML 讀取器或 XAML 寫入器，則會隱含地建立相同的預設 XAML 結構描述內容。  
  
 預設 XAML 結構描述內容依賴 CLR 反映機制進行其型別對應行為。  這包括檢查定義端 CLR <xref:System.Type> 和相關的 <xref:System.Reflection.PropertyInfo> 或 <xref:System.Reflection.MethodInfo>。  另外，當 XAML 型別與 XAML 成員資訊使用 CLR 支援型別時，會使用 CLR 屬性化在型別或成員上填入細節。  預設 XAML 結構描述內容不需要型別系統延伸技巧 \(例如 `Invoker` 模式\)，因為 CLR 型別系統會提供必要的資訊。  
  
 就組件載入邏輯而言，預設 XAML 結構描述內容主要依賴任何在 XAML 命名空間對應中提供的組件值。  另外，在載入內部型別之類的情節中，<xref:System.Xaml.XamlReaderSettings.LocalAssembly%2A> 可以暗示組件進行載入。  
  
## WPF XAML 結構描述內容  
 本主題之所以說明 WPF XAML 結構描述內容，是因為 WPF 實作展現了可以透過實作非預設 XAML 結構描述內容來提供的功能，頗值得注意。  另外，在解說 WPF XAML 的 WPF 文件中並未深入探討 XAML 結構描述內容概念；唯有與預設 XAML 結構描述內容運作方式一起整合討論，才可能完全了解 XAML 結構描述內容的行為。  WPF XAML 結構描述內容會實作下列行為。  
  
 **查閱覆寫：**WPF 有一些 XAML 內容模型，而這些模型中有不需 <xref:System.Windows.Markup.ContentPropertyAttribute> 屬性化即可運作的 XAML 內容屬性。  WPF 的 <xref:System.Xaml.XamlType.LookupContentProperty%2A> 覆寫會實作這個行為。  
  
 **WPF 運算式延遲：**WPF 有數個運算式類別會將值延到有執行階段內容可用時才導出。  另外，範本延伸是一項依賴延遲技巧的執行階段行為。  
  
 **型別系統查閱最佳化：**WPF 有一套廣泛的 XAML 詞彙和物件模型，其中包含的基底類別成員定義會繼承給 WPF 所定義的數百個類別。  另外，WPF 本身分散於數個組件。  WPF 使用查閱資料表和其他技巧來最佳化其型別查閱機制。  此舉可改善預設 XAML 結構描述內容和其以 CLR 為基礎之型別查閱的效能。  如果型別不存在於查閱資料表，其行為會使用與預設 XAML 結構描述內容類似的 XAML 結構描述內容技巧。  
  
 **XamlType 和 XamlMember 延伸：**WPF 會以相依性屬性延伸屬性概念，並以路由事件延伸事件概念。  為了提高這些概念在 XAML 處理作業中的能見度，WPF 會延伸 <xref:System.Xaml.XamlType> 和 <xref:System.Xaml.XamlMember>，在其中加入會報告相依性屬性和路由事件特性的內部屬性。  
  
### 存取 WPF XAML 結構描述內容  
 如果您使用以 WPF <xref:System.Windows.Markup.XamlReader?displayProperty=fullName> 或 <xref:System.Windows.Markup.XamlWriter?displayProperty=fullName> 為基礎的 XAML 技巧，則這些 XAML 讀取器和 XAML 寫入器實作已經在使用 WPF XAML 結構描述內容。  
  
 如果您使用其他未以 WPF XAML 結構描述內容初始化的 XAML 讀取器或 XAML 寫入器實作，或許可以從 <xref:System.Windows.Markup.XamlReader.GetWpfSchemaContext%2A?displayProperty=fullName> 取得正常可用的 WPF XAML 結構描述內容。  然後，您可以在初始化其他使用 <xref:System.Xaml.XamlSchemaContext> 的 API 時使用此值。  例如，您可以呼叫 <xref:System.Xaml.XamlXmlReader.%23ctor%2A> 進行初始化並傳遞 WPF XAML 結構描述內容。  或者，您可以將 WPF XAML 結構描述內容使用於 XAML 型別系統作業。  這可能包括 <xref:System.Xaml.XamlType> 或 <xref:System.Xaml.XamlMember> 的建構初始化，或呼叫 <xref:System.Xaml.XamlSchemaContext.GetXamlType%2A?displayProperty=fullName>。  
  
 請注意，如果您從純粹 XAML 節點資料流觀點存取 WPF XAML 的特定部分，某些 WPF 架構功能可能尚未執行。  例如，尚未套用控制項的 WPF 範本。  因此，如果您存取的屬性在執行階段可能會以完整視覺化樹狀結構填入，您可能只會看見參考範本的屬性值。  另外，在非執行階段的情況下提供給 WPF 標記延伸的服務內容可能會不正確，而且可能會在嘗試寫入物件圖形時導致例外狀況。  
  
## XAML 和組件載入  
 XAML 和 .NET Framework XAML 服務的組件載入機制已與 CLR 定義的 <xref:System.AppDomain> 概念整合。  XAML 結構描述內容會根據 <xref:System.AppDomain> 的用法以及其他因素，解讀出在執行階段或設計階段載入組件或尋找型別的方式。  根據 XAML 是 XAML 讀取器適用的鬆散 XAML、是由 `XamlBuildTask` 編譯成 DLL 的 XAML，或是由 WPF 的 `PresentationBuildTask` 所產生的 BAML，這個邏輯稍有不同。  
  
 WPF 的 XAML 結構描述內容與 WPF 應用程式模型整合，後者會使用 <xref:System.AppDomain> 以及其他屬於 WPF 實作細節的因素。  
  
#### XAML 讀取器輸入 \(鬆散 XAML\)  
  
1.  XAML 結構描述內容會在應用程式的 <xref:System.AppDomain> 中逐一查看，從最近載入的組件開始，尋找名稱所有層面皆符合的已載入組件。  如果找到符合的項目，該組件便會用於解析。  
  
2.  否則，下列其中一個以 CLR <xref:System.Reflection.Assembly> API 為基礎的技巧會用於載入組件：  
  
    -   如果在對應中是限定名稱，則在限定名稱上呼叫 <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=fullName>。  
  
    -   如果上一個步驟失敗，則使用簡短名稱 \(和公開金鑰語彙基元，如果有的話\) 來呼叫 <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=fullName>。  
  
    -   如果在對應中是未限定名稱，則呼叫 <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName>。  
  
#### XamlBuildTask  
 `XamlBuildTask` 是用於 [!INCLUDE[vsindigo](../../../includes/vsindigo-md.md)] 和 [!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)]。  
  
 請注意，透過 `XamlBuildTask` 的組件參考一律是完整限定的。  
  
1.  在限定名稱上呼叫 <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=fullName>。  
  
2.  如果上一個步驟失敗，則使用簡短名稱 \(和公開金鑰語彙基元，如果有的話\) 來呼叫 <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=fullName>。  
  
#### BAML \(PresentationBuildTask\)  
 BAML 的組件載入機制有兩個層面：載入含有 BAML \(做為元件\) 的初始組件，以及針對 BAML 產物所參考的任何型別載入型別支援組件。  
  
##### 初始標記的組件載入：  
 要載入標記的來源組件之參考一律未限定。  
  
1.  WPF XAML 結構描述內容會在 WPF 應用程式的 <xref:System.AppDomain> 中逐一查看，從最近載入的組件開始，尋找名稱所有層面皆符合的已載入組件。  如果找到符合的項目，該組件便會用於解析。  
  
2.  如果上一個步驟失敗，則使用簡短名稱 \(和公開金鑰語彙基元，如果有的話\) 來呼叫 <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=fullName>。  
  
##### BAML 型別的組件參考：  
 BAML 產物中所用型別的組件參考一律是完整限定的 \(做為建置工作的輸出\)。  
  
1.  WPF XAML 結構描述內容會在 WPF 應用程式的 <xref:System.AppDomain> 中逐一查看，從最近載入的組件開始，尋找名稱所有層面皆符合的已載入組件。  如果找到符合的項目，該組件便會用於解析。  
  
2.  否則，下列其中一個技巧會用於載入組件：  
  
    -   在限定名稱上呼叫 <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=fullName>。  
  
    -   如果簡短名稱 \+ 公開金鑰語彙基元的組合符合當初載入 BAML 的來源組件，則使用該組件。  
  
    -   使用簡短名稱 \+ 公開金鑰語彙基元來呼叫 <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=fullName>。  
  
## 請參閱  
 [Understanding XAML Node Stream Structures and Concepts](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md)