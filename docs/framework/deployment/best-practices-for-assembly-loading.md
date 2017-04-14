---
title: "組件載入的最佳作法 | Microsoft Docs"
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
  - "組件, 繫結"
  - "組件, 載入"
  - "組件載入錯誤"
  - "預設載入內容"
  - "載入內容"
  - "載入來源內容"
  - "LoadFrom 方法"
  - "LoadWithPartialName 方法"
  - "TypeLoadException 類別, 原因"
ms.assetid: 68d1c539-6a47-4614-ab59-4b071c9d4b4c
caps.latest.revision: 10
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 10
---
# 組件載入的最佳作法
本文將討論避免出現可造成 <xref:System.InvalidCastException>、<xref:System.MissingMethodException> 和其他錯誤之型別識別問題的方法。  本文會討論下列建議：  
  
-   [了解載入內容的優缺點](#load_contexts)  
  
-   [避免部分組件名稱繫結](#avoid_partial_names)  
  
-   [避免將組件載入多個內容中](#avoid_loading_into_multiple_contexts)  
  
-   [避免將組件的多個版本載入相同的內容中](#avoid_loading_multiple_versions)  
  
-   [考量切換至預設載入內容](#switch_to_default)  
  
 第一個建議 \([了解載入內容的優缺點](#load_contexts)\) 會為其他建議提供背景資訊，原因是所有其他建議都取決於對載入內容的了解。  
  
<a name="load_contexts"></a>   
## 了解載入內容的優缺點  
 在應用程式定義域內，可以將組件載入三個內容的其中一個中，也可以在沒有內容的情況下載入：  
  
-   預設載入內容包含探查全域組件快取時找到的組件：執行階段已裝載時的主機組件存放區 \(例如，在 SQL Server 中\)，以及應用程式定義域的 <xref:System.AppDomainSetup.ApplicationBase%2A> 和 <xref:System.AppDomainSetup.PrivateBinPath%2A>。  大多數的 <xref:System.Reflection.Assembly.Load%2A> 方法多載會將組件載入到這個內容中。  
  
-   載入來源內容包含一些組件，這些組件是從未經載入器搜尋的位置載入的。  例如，增益集可能會安裝在非應用程式路徑下的目錄中。  <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName>、<xref:System.AppDomain.CreateInstanceFrom%2A?displayProperty=fullName> 和 <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=fullName> 都是根據路徑所載入之方法的範例。  
  
-   僅限反映內容包含利用 <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> 與 <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> 方法載入的組件。  由於無法執行此內容中的程式碼，因此在此先不做討論。  如需詳細資訊，請參閱 [如何：將組件載入僅限反映的內容](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)。  
  
-   如果您透過使用反映發出產生暫時性動態組件，則該組件不在任何內容中。  此外，透過使用 <xref:System.Reflection.Assembly.LoadFile%2A> 方法載入的大部分組件都是在沒有內容的狀況下載入的，從位元組陣列中載入的組件也是在沒有內容的狀況下載入的，除非其身分識別 \(套用原則之後\) 表明它們位於全域組件快取中。  
  
 執行內容具有其優缺點，如下列各節中所述。  
  
### 預設載入內容  
 將組件載入預設載入內容中時，會自動載入其相依性。  對於預設載入內容或載入來源內容中的組件，會自動尋找已載入預設載入內容的相依性。  透過組件識別進行的載入可確保不會使用未知版本的組件，從而增加應用程式的穩定性 \(請參閱[避免部分組件名稱繫結](#avoid_partial_names)一節\)。  
  
 使用預設載入內容具有下列優點：  
  
-   無法使用載入其他內容中的相依性。  
  
-   無法將組件從探查路徑外的位置載入預設載入內容。  
  
### 載入來源內容  
 載入來源內容可讓您從非應用程式路徑下的路徑中載入組件，因而其未包含在探查中。  因為路徑資訊由內容來維護，所以可從該路徑尋找和載入相依性。  此外，此內容中的組件可以使用載入預設載入內容中的相依性。  
  
 透過使用 <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName> 方法或按路徑載入的其中一種其他方法載入的組件具有下列缺點：  
  
-   如果已經載入具有相同識別的組件，則即使指定不同的路徑，<xref:System.Reflection.Assembly.LoadFrom%2A> 也會傳回載入的組件。  
  
-   如果使用 <xref:System.Reflection.Assembly.LoadFrom%2A> 載入了組件，然後預設載入內容中的組件嘗試根據顯示名稱載入相同的組件時，載入嘗試會失敗。  當組件已還原序列化時，就會發生這種情形。  
  
-   如果使用 <xref:System.Reflection.Assembly.LoadFrom%2A> 載入了組件，而探查路徑包括具有相同識別但不同位置的組件，則可能會發生 <xref:System.InvalidCastException>、<xref:System.MissingMethodException> 或其他無法預期的行為。  
  
-   <xref:System.Reflection.Assembly.LoadFrom%2A> 會針對指定的路徑要求 <xref:System.Security.Permissions.FileIOPermissionAccess?displayProperty=fullName> 和 <xref:System.Security.Permissions.FileIOPermissionAccess?displayProperty=fullName> 或 <xref:System.Net.WebPermission>。  
  
-   如果存在組件的原生映像，則不會使用它。  
  
-   組件無法當做定義域中性載入。  
  
-   在 .NET Framework 1.0 和 1.1 版中，不會套用原則。  
  
### 無內容  
 無內容載入是利用反映發出所產生暫時性組件的唯一選項。  無內容載入是將具有相同識別的多個組件載入一個應用程式定義域的唯一方法。  這可避免探查成本。  
  
 除非在套用原則時建立的組件識別與全域組件快取中的組件識別相符 \(在該情況下，組件載入自全域組件快取\)，否則從位元組陣列載入的組件將採用無內容形式載入。  
  
 無內容載入組件具有下列缺點：  
  
-   除非您處理 <xref:System.AppDomain.AssemblyResolve?displayProperty=fullName> 事件，否則無法將其他組件繫結至無內容載入的組件。  
  
-   不會自動載入相依性。  您可以採用無內容形式預先載入它們、將其預先載入至預設載入內容，或者透過處理 <xref:System.AppDomain.AssemblyResolve?displayProperty=fullName> 事件載入它們。  
  
-   無內容載入具有相同識別的多個組件可能會造成型別識別問題，該問題與將具有相同識別的組件載入多個內容而造成的問題類似。  請參閱[避免將組件載入多個內容中](#avoid_loading_into_multiple_contexts)。  
  
-   如果存在組件的原生映像，則不會使用它。  
  
-   組件無法當做定義域中性載入。  
  
-   在 .NET Framework 1.0 和 1.1 版中，不會套用原則。  
  
<a name="avoid_partial_names"></a>   
## 避免部分組件名稱繫結  
 載入組件期間，當您僅指定部分組件顯示名稱 \(<xref:System.Reflection.Assembly.FullName%2A>\) 時，會發生部分名稱繫結。  例如，您可能會僅利用組件的簡單名稱來呼叫 <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> 方法，而省略組件的版本、文化特性及公開金鑰語彙基元。  或者您可能會呼叫 <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName> 方法：首先呼叫 <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> 方法，如果找不到組件，則會搜尋全域組件快取並載入組件的最新可用版本。  
  
 部分名稱繫結可能會造成許多問題，包括：  
  
-   <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName> 方法可能會載入具有相同簡單名稱的不同組件。  例如，兩個應用程式可能會將具有簡單名稱 `GraphicsLibrary` 的兩個完全不同組件安裝至全域組件快取中。  
  
-   實際載入的組件可能不具有回溯相容性。  例如，如果未指定版本，則可能會導致載入比原本撰寫程式所使用的版本更新的版本。  更新版本中的變更可能會造成應用程式發生錯誤。  
  
-   實際載入的組件可能不具有向前相容性。  例如，您可能已利用最新版本的組件建置並測試您的應用程式，但是部分繫結可能會載入缺少應用程式所使用功能的更早版本。  
  
-   安裝新的應用程式可能會中斷現有的應用程式。  安裝更新且不相容版本的共用組件可能會中斷使用 <xref:System.Reflection.Assembly.LoadWithPartialName%2A> 方法的應用程式。  
  
-   可能會發生非預期的相依性載入問題。  如果您載入共用相依性的兩個組件，則利用部分繫結載入它們可能會導致一個組件使用非建置或測試時所使用的元件。  
  
 由於 <xref:System.Reflection.Assembly.LoadWithPartialName%2A> 方法可能造成問題，因此已將該方法標記為過時。  我們建議您改為使用 <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> 方法，並指定完整的組件顯示名稱。  請參閱[了解載入內容的優缺點](#load_contexts)與[考量切換至預設載入內容](#switch_to_default)。  
  
 如果您想要使用易於載入組件的 <xref:System.Reflection.Assembly.LoadWithPartialName%2A> 方法，請考量在應用程式失敗時顯示錯誤訊息，用於確定遺漏組件可能會提供比自動使用未知版本組件更佳的使用者體驗，但可能會造成無法預期的行為與安全性漏洞。  
  
<a name="avoid_loading_into_multiple_contexts"></a>   
## 避免將組件載入多個內容中  
 將組件載入多個內容可能會造成型別識別問題。  如果將相同的型別從相同的組件載入兩個不同的內容中，就好像載入了具有相同名稱的兩個不同型別。  如果您嘗試將一種型別轉換成另一種型別，則會擲回 <xref:System.InvalidCastException>，並會顯示無法將型別 `MyType` 轉換成型別 `MyType` 的混淆訊息。  
  
 例如，假設 `ICommunicate` 介面在名為 `Utility` 的組件中進行宣告，該組件由您的程式同時也由程式所載入的其他組件參考。  其他這些組件包含會實作 `ICommunicate` 介面的型別，可讓您的程式使用這些組件。  
  
 現在請考量執行程式時會發生哪些狀況。  程式參考的組件會載入預設載入內容中。  如果您使用 <xref:System.Reflection.Assembly.Load%2A> 方法依識別載入目標組件，則該目標組件及其相依性都會位於預設載入內容中。  您的程式與目標組件將會使用相同的 `Utility` 組件。  
  
 然而，假設您使用 <xref:System.Reflection.Assembly.LoadFile%2A> 方法依檔案路徑載入目標組件。  這時會在無內容的情況下載入組件，因此不會自動載入其相依性。  您可能會使用 <xref:System.AppDomain.AssemblyResolve?displayProperty=fullName> 事件的處理常式來提供相依性，該處理常式會使用 <xref:System.Reflection.Assembly.LoadFile%2A> 方法在沒有內容的情況下載入 `Utility` 組件。  現在，當您建立目標組件中所含型別的執行個體並嘗試將其指派給型別為 `ICommunicate` 的變數時，會擲回 <xref:System.InvalidCastException>，原因是執行階段將 `Utility` 組件兩個複本中的 `ICommunicate` 介面視為不同的型別。  
  
 還有許多其他情節，可以將組件載入多個內容中。  最佳方法是在應用程式路徑中重新尋找目標組件並使用 <xref:System.Reflection.Assembly.Load%2A> 方法與完整顯示名稱，來避免衝突。  然後組件會載入預設載入內容中，且兩個組件會使用相同的 `Utility` 組件。  
  
 如果目標組件必須保留在您的應用程式路徑之外，則您可以使用 <xref:System.Reflection.Assembly.LoadFrom%2A> 方法將其載入至載入來源內容中。  如果目標組件是利用您應用程式 `Utility` 組件的參考進行編譯的，則其會使用應用程式已載入預設載入內容中的 `Utility` 組件。  請注意，如果目標組件對應用程式路徑之外的 `Utility` 組件複本具有相依性，則可能會發生問題。  如果在您的應用程式載入 `Utility` 組件之前該組件已載入至載入來源內容中，則您應用程式的載入會失敗。  
  
 [考量切換至預設載入內容](#switch_to_default)一節會討論使用檔案路徑載入的替代方法，例如 <xref:System.Reflection.Assembly.LoadFile%2A> 與 <xref:System.Reflection.Assembly.LoadFrom%2A>。  
  
<a name="avoid_loading_multiple_versions"></a>   
## 避免將組件的多個版本載入相同的內容中  
 將組件的多個版本載入一個載入內容中可能會造成型別識別問題。  如果從相同組件的兩個版本載入相同的型別，就好像載入了具有相同名稱的兩個不同型別。  如果您嘗試將一種型別轉換成另一種型別，則會擲回 <xref:System.InvalidCastException>，並會顯示無法將型別 `MyType` 轉換成型別 `MyType` 的混淆訊息。  
  
 例如，您的程式可能會直接載入一個版本的 `Utility` 組件，且稍後可能會載入另一個組件，該組件載入不同版本的 `Utility` 組件。  或者，程式碼錯誤可能會造成您應用程式中兩個不同的程式碼路徑載入不同版本的組件。  
  
 在預設載入內容中，當您使用 <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> 方法並指定包括不同版本號碼的完整組件顯示名稱時，可能會發生此問題。  若為無內容載入的組件，使用 <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=fullName> 方法從不同路徑載入相同組件可能會造成問題。  執行階段會將從不同路徑載入的兩個組件視為不同的組件，無論其識別是否相同。  
  
 除了型別識別問題之外，如果將從一個組件版本載入的型別傳遞給預期從其他版本載入型別的程式碼時，多個組件版本會造成 <xref:System.MissingMethodException>。  例如，該程式碼可能預期已新增至更新版本的方法。  
  
 如果版本之間的型別行為變更，則可能會發生更多不明顯的錯誤。  例如，方法可能會擲回非預期的例外狀況或者傳回非預期的值。  
  
 仔細檢閱程式碼，以確定僅載入一個版本的組件。  您隨時可以使用 <xref:System.AppDomain.GetAssemblies%2A?displayProperty=fullName> 方法判斷載入哪些組件。  
  
<a name="switch_to_default"></a>   
## 考量切換至預設載入內容  
 請檢查應用程式的組件載入與部署模式。  您可以去除從位元組陣列載入的組件嗎？  您可以將組件移至探查路徑嗎？  如果組件位於全域組件快取或應用程式定義域的路徑中 \(也就是其 <xref:System.AppDomainSetup.ApplicationBase%2A> 與 <xref:System.AppDomainSetup.PrivateBinPath%2A>\)，則您可以依其識別載入組件。  
  
 如果無法將所有組件放置到探查路徑中，請考量替代方法，例如使用 .NET Framework 增益集模型，將組件放置在全域組件快取中或者建立應用程式定義域。  
  
### 考量使用 .NET Framework 增益集模型  
 如果您使用載入來源內容實作通常未安裝在應用程式基底中的增益集，請使用 .NET Framework 增益集模型。  此模型會隔離應用程式定義域或處理程序等級，而不需要您自行管理應用程式定義域。  如需增益集模型的詳細資訊，請參閱[增益集和擴充性](../../../ml/index.xml)。  
  
### 考量使用全域組件快取  
 將組件放置在全域組件快取中，可以獲得應用程式基底之外共用組件路徑的優勢，同時不會失去預設載入內容的優勢也不會有其他內容的缺點。  
  
### 考量使用應用程式定義域  
 如果您判斷部分組件無法在應用程式探查路徑中進行部署，請考量為那些組件建立新的應用程式定義域。  使用 <xref:System.AppDomainSetup> 來建立新的應用程式定義域，並使用 <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=fullName> 屬性來指定包含您想要載入之組件的路徑。  如果您有多個要探查的目錄，則可以將 <xref:System.AppDomainSetup.ApplicationBase%2A> 設定為根目錄，並使用 <xref:System.AppDomainSetup.PrivateBinPath%2A?displayProperty=fullName> 屬性來識別要探查的子目錄。  此外，您也可以建立多個應用程式定義域，並將每一個應用程式定義域的 <xref:System.AppDomainSetup.ApplicationBase%2A> 設定為組件的適當路徑。  
  
 請注意，您可以使用 <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName> 方法來載入這些組件。  由於現在它們位於探查路徑中，因此它們會載入預設載入內容而非載入來源內容。  然而，我們建議您切換至 <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> 方法並提供完整的組件顯示名稱，以確定始終使用正確的版本。  
  
## 請參閱  
 <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName>   
 <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName>   
 <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=fullName>   
 <xref:System.AppDomain.AssemblyResolve?displayProperty=fullName>   
 [增益集和擴充性](../../../ml/index.xml)