---
title: 組件載入的最佳作法
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies,binding
- LoadFrom method
- default load context
- TypeLoadException class,causes
- assembly loading errors
- load contexts
- assemblies,loading
- LoadWithPartialName method
- load-from context
ms.assetid: 68d1c539-6a47-4614-ab59-4b071c9d4b4c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a95679f659f13956fd230f07e9401af9097a043c
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182476"
---
# <a name="best-practices-for-assembly-loading"></a>組件載入的最佳作法
本文討論如何避免發生可能造成 <xref:System.InvalidCastException>、<xref:System.MissingMethodException> 和其他錯誤之類型身分識別的問題。 本文討論下列建議：  
  
- [了解載入內容的優缺點](#load_contexts)  
  
- [避免部分組件名稱上的繫結](#avoid_partial_names)  
  
- [避免將組件載入多個內容](#avoid_loading_into_multiple_contexts)  
  
- [避免將多個版本的組件載入相同的內容](#avoid_loading_multiple_versions)  
  
- [考慮切換成預設載入內容](#switch_to_default)  
  
 第一個建議 ([了解載入內容的優缺點](#load_contexts)) 提供其他建議的背景資訊，因為它們都取決於載入內容的知識。  
  
<a name="load_contexts"></a>   
## <a name="understand-the-advantages-and-disadvantages-of-load-contexts"></a>了解載入內容的優缺點  
 在應用程式定義域內，可以將組件載入三個內容之一，或是載入時沒有內容：  
  
- 預設載入內容包含探查全域組件快取時所找到的組件、裝載執行階段時的主機組件存放區 (例如，在 SQL Server 中)，以及應用程式定義域的 <xref:System.AppDomainSetup.ApplicationBase%2A> 和 <xref:System.AppDomainSetup.PrivateBinPath%2A>。 <xref:System.Reflection.Assembly.Load%2A> 方法的大部分多載都會將組件載入此內容中。  
  
- 載入來源內容包含從載入器未搜尋的位置中載入的組件。 例如，增益集可能安裝在不在應用程式路徑下的目錄。 <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>、<xref:System.AppDomain.CreateInstanceFrom%2A?displayProperty=nameWithType> 和 <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType> 是依路徑載入之方法的範例。  
  
- 僅限反映的內容包含使用 <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> 和 <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> 方法所載入的組件。 無法執行此內容中的程式碼，因此此處不予討論。 如需詳細資訊，請參閱[如何：將組件載入僅限反映的內容](../reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)。  
  
- 如果您已使用反映發出來產生暫時性動態組件，則組件不會在任何內容中。 此外，使用 <xref:System.Reflection.Assembly.LoadFile%2A> 方法所載入的大部分組件在載入時都沒有內容，而且從位元組陣列載入的組件在載入時沒有內容，除非它們在套件原則之後所建立的身分識別位於全域組件快取中。  
  
 執行內容具有優缺點，如下列各節所討論。  
  
### <a name="default-load-context"></a>預設載入內容  
 將組件載入預設載入內容時，會自動載入其相依性。 針對預設載入內容或載入來源內容中的組件，自動找到載入到預設載入內容的相依性。 藉由確保未使用未知版本的組件，依組件身分識別載入可增加應用程式的穩定性 (請參閱[避免部分組件名稱上的繫結](#avoid_partial_names)節)。  
  
 使用預設載入內容的缺點如下：  
  
- 無法使用載入至其他內容的相依性。  
  
- 您無法將組件從探查路徑外部的位置載入預設載入內容。  
  
### <a name="load-from-context"></a>載入來源內容  
 載入來源內容可讓您從不在應用程式路徑下的路徑中載入組件，因此不會納入探查。 它可以從該路徑尋找和載入相依性，因為是透過內容來維護路徑資訊。 此外，此內容中的組件可以使用載入預設載入內容的相依性。  
  
 使用 <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> 方法或依路徑載入的其他一個方法來載入組件，其缺點如下：  
  
- 如果已載入具有相同身分識別的組件，<xref:System.Reflection.Assembly.LoadFrom%2A> 會傳回載入的組件，即使指定不同的路徑也是一樣。  
  
- 如果使用 <xref:System.Reflection.Assembly.LoadFrom%2A> 載入組件，之後預設載入內容中的組件卻嘗試依顯示名稱載入相同組件，則載入嘗試會失敗。 還原序列化組件時，也可能發生這種情況。  
  
- 如果使用 <xref:System.Reflection.Assembly.LoadFrom%2A> 載入組件，而且探查路徑包括具有相同身分識別但在不同位置的組件，則可能會發生 <xref:System.InvalidCastException>、<xref:System.MissingMethodException> 或其他非預期的行為。  
  
- <xref:System.Reflection.Assembly.LoadFrom%2A> 要求所指定路徑上的 <xref:System.Security.Permissions.FileIOPermissionAccess.Read?displayProperty=nameWithType> 和 <xref:System.Security.Permissions.FileIOPermissionAccess.PathDiscovery?displayProperty=nameWithType> 或 <xref:System.Net.WebPermission>。  
  
- 如果組件有原生映像，則不會使用它。  
  
- 組件無法以定義域中性方式載入。  
  
- 在 .NET Framework 1.0 和 1.1 版中，不會套用原則。  
  
### <a name="no-context"></a>沒有內容  
 沒有內容的載入是使用反映發出所產生之暫時性組件的唯一選項。 沒有內容的載入是將多個具有相同身分識別的組件載入到一個應用程式定義域的唯一方法。 會避免發生探查成本。  
  
 從位元組陣列載入的組件在載入時沒有內容，除非在套用規則時所建立之組件的身分識別符合全域組件快取中組件的身分識別；在該情況下，會從全域組件快取中載入組件。  
  
 載入沒有內容之組件的缺點如下：  
  
- 除非您處理 <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> 事件，否則其他組件無法繫結至載入時沒有內容的組件。  
  
- 不會自動載入相依性。 您可以預先載入它們但沒有內容、將它們預先載入至預設載入內容，或者處理 <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> 事件來載入它們。  
  
- 載入具有相同身分識別但沒有內容的多個組件可能會造成類型身分識別問題，而這些問題與將具有相同身分識別的組件載入多個內容所造成的問題類似。 請參閱[避免將組件載入多個內容](#avoid_loading_into_multiple_contexts)。  
  
- 如果組件有原生映像，則不會使用它。  
  
- 組件無法以定義域中性方式載入。  
  
- 在 .NET Framework 1.0 和 1.1 版中，不會套用原則。  
  
<a name="avoid_partial_names"></a>   
## <a name="avoid-binding-on-partial-assembly-names"></a>避免部分組件名稱上的繫結  
 如果您在載入組件時指定組件顯示名稱的唯一部分，就會發生部分名稱繫結 (<xref:System.Reflection.Assembly.FullName%2A>)。 例如，您可能會呼叫只具有組件簡單名稱的 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> 方法，並省略版本、文化特性和公開金鑰權杖。 或者，您可能會呼叫 <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> 方法，此方法會先呼叫 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> 方法，並在找不到組件時搜尋全域組件快取，並載入組件的最新可用版本。  
  
 部分名稱繫結會造成許多問題，包括下列：  
  
- <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> 方法可能會載入具有相同簡單名稱的不同組件。 例如，兩個應用程式可能會將兩個具有簡單名稱 `GraphicsLibrary` 的完全不同組件安裝到全域組件快取中。  
  
- 實際載入的組件可能無法與舊版相容。 例如，未指定版本可能會導致載入的版本，比一開始撰寫成使用之程式的版本還會新。 更新版本中的變更可能導致應用程式發生錯誤。  
  
- 實際載入的組件可能不正向相容。 例如，您可能已使用最新版本的組件來建置並測試應用程式，但部分繫結可能會載入缺乏應用程式所使用功能的更早版本。  
  
- 安裝新的應用程式可能會中斷現有應用程式。 安裝更新且不相容版本的共用組件，可能會中斷使用 <xref:System.Reflection.Assembly.LoadWithPartialName%2A> 方法的應用程式。  
  
- 可能會載入非預期的相依性。 如果您載入兩個共用相依性的組件，則使用部分繫結載入它們可能會導致一個組件，而此組件使用未用來建置或測試它的元件。  
  
 <xref:System.Reflection.Assembly.LoadWithPartialName%2A> 方法可能會導致問題，因此已標示為過時。 建議您改用 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> 方法，並指定完整組件顯示名稱。 請參閱[了解載入內容的優缺點](#load_contexts)和[考慮切換成預設載入內容](#switch_to_default)。  
  
 如果您因可以更輕鬆地載入組件而想要使用 <xref:System.Reflection.Assembly.LoadWithPartialName%2A> 方法，請考慮讓應用程式失敗時具有識別遺漏組件的錯誤訊息，而其提供的使用者體驗可能優於自動使用未知版本的組件，這可能會造成無法預期的行為和安全性漏洞。  
  
<a name="avoid_loading_into_multiple_contexts"></a>   
## <a name="avoid-loading-an-assembly-into-multiple-contexts"></a>避免將組件載入多個內容  
 將載入組件多個內容，可能會造成類型身分識別問題。 如果將相同類型從相同的組件載入兩個不同的內容，就像已載入具有相同名稱的兩個不同類型一樣。 如果您嘗試將某種類型轉換為另一種類型，則會擲回 <xref:System.InvalidCastException>，以及讓人混淆的訊息：無法將 `MyType` 類型轉換為 `MyType` 類型。  
  
 例如，假設在名為 `Utility` 的組件中宣告 `ICommunicate` 介面，而您的程式和您程式所載入的其他組件都參考此組件。 這些其他組件包含實作 `ICommunicate` 介面的類型，讓您的程式可以使用它們。  
  
 現在，請考慮您的程式執行時會發生什麼事。 您程式所參考的組件會載入預設載入內容。 如果您是依身分識別來載入目標組件，並使用 <xref:System.Reflection.Assembly.Load%2A> 方法，則該組件和其相依性都會在預設載入內容中。 您的程式和目標組件都會使用相同 `Utility` 組件。  
  
 不過，假設您依檔案路徑載入目標組件，並使用 <xref:System.Reflection.Assembly.LoadFile%2A> 方法。 組件在載入時沒有任何內容，因此不會自動載入其相依性。 您可能有 <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> 事件的處理常式來提供相依性，而且它可能會使用 <xref:System.Reflection.Assembly.LoadFile%2A> 方法載入沒有內容的 `Utility` 組件。 現在，如果您建立目標組件中所含類型的執行個體，並嘗試將它指派給 `ICommunicate` 類型的變數，則會擲回 <xref:System.InvalidCastException>，因為執行階段會將 `Utility` 組件之兩個複本中的 `ICommunicate` 介面視為不同類型。  
  
 有許多其他情況可以將組件載入多個內容。 最佳方式是將目標組件重新放置在應用程式路徑中，並搭配使用 <xref:System.Reflection.Assembly.Load%2A> 方法與完整顯示名稱，以避免衝突。 組件接著會載入預設載入內容，而且兩個組件都使用相同 `Utility` 組件。  
  
 如果目標組件必須保留在應用程式路徑外部，您可以使用 <xref:System.Reflection.Assembly.LoadFrom%2A> 方法，以將它載入到載入來源內容。 如果目標組件編譯成具有應用程式 `Utility` 組件的參考，則會使用應用程式已載入預設載入內容的 `Utility` 組件。 請注意，如果目標組件相依於位在應用程式路徑外部之 `Utility` 組件的複本，則可能會發生問題。 如果在應用程式載入 `Utility` 組件之前將該組件載入到載入來源內容，您應用程式的載入將會失敗。  
  
 [考慮切換成預設載入內容](#switch_to_default)一節討論使用 <xref:System.Reflection.Assembly.LoadFile%2A> 和 <xref:System.Reflection.Assembly.LoadFrom%2A> 這類檔案路徑載入的替代方式。  
  
<a name="avoid_loading_multiple_versions"></a>   
## <a name="avoid-loading-multiple-versions-of-an-assembly-into-the-same-context"></a>避免將多個版本的組件載入相同的內容  
 將組件的多個版本載入一個載入內容可能會造成類型身分識別問題。 如果從相同組件的兩個版本載入相同類型，就像已載入具有相同名稱的兩個不同類型一樣。 如果您嘗試將某種類型轉換為另一種類型，則會擲回 <xref:System.InvalidCastException>，以及讓人混淆的訊息：無法將 `MyType` 類型轉換為 `MyType` 類型。  
  
 例如，您的程式可能會直接載入 `Utility` 組件的一個版本，之後可能會載入另一個載入 `Utility` 組件之不同版本的組件。 或者，程式碼錯誤可能會在應用程式中產生兩個不同的程式碼路徑，以載入組件的不同版本。  
  
 在預設載入內容中，如果您使用 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> 方法，並指定包括不同版本號碼的完整組件顯示名稱，則會發生此問題。 針對載入時沒有內容的組件，使用 <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> 方法以從不同路徑載入相同組件時可能會發生問題。 執行階段會將兩個從不同路徑載入的組件視為不同組件，即使其身分識別相同也是一樣。  
  
 除了類型身分識別問題之外，如果將從某個版本的組件載入的類型傳遞給預期來自不同版本之該類型的程式碼，則組件的多個版本可能還會導致 <xref:System.MissingMethodException>。 例如，程式碼可能預期已新增至較新版本的方法。  
  
 如果版本之間的類型行為變更，可能會發生更細微的錯誤。 例如，方法可能會擲回未預期的例外狀況，或傳回未預期的值。  
  
 請仔細檢閱您的程式碼，確保只載入組件的一個版本。 您可以使用 <xref:System.AppDomain.GetAssemblies%2A?displayProperty=nameWithType> 方法，判斷在任何指定時間載入的組件。  
  
<a name="switch_to_default"></a>   
## <a name="consider-switching-to-the-default-load-context"></a>考慮切換成預設載入內容  
 檢查您應用程式的組件載入和部署模式。 您可以排除從位元組陣列載入的組件嗎？ 您可以將組件移到探查路徑嗎？ 如果組件位在全域組件快取或應用程式定義域的探查路徑中 (即其 <xref:System.AppDomainSetup.ApplicationBase%2A> 和 <xref:System.AppDomainSetup.PrivateBinPath%2A>)，您可以依其身分識別來載入組件。  
  
 如果不可能將您的所有組件放在探查路徑中，請考慮使用替代項目，例如使用 .NET Framework 增益集模型、將組件放入全域組件快取中，或建立應用程式定義域。  
  
### <a name="consider-using-the-net-framework-add-in-model"></a>考慮使用 .NET Framework 增益集模型  
 如果您使用載入來源內容來實作通常不會安裝在應用程式基底中的增益集，請使用 .NET Framework 增益集模型。 此模型會提供應用程式定義域或處理序層級的隔離，而不需要您自行管理應用程式定義域。 如需增益集模型的資訊，請參閱[增益集和擴充性](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))。  
  
### <a name="consider-using-the-global-assembly-cache"></a>考慮使用全域組件快取  
 將組件放入全域組件快取以受益於應用程式基底外部的共用組件路徑，而不會遺失預設載入內容的優點或造成其他內容的缺點。  
  
### <a name="consider-using-application-domains"></a>考慮使用應用程式定義域  
 如果您判斷無法在應用程式的探查路徑中部署部分組件，請考慮針對這些組件建立新的應用程式定義域。 使用 <xref:System.AppDomainSetup> 建立新的應用程式定義域，並使用 <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> 屬性指定包含您想要載入之組件的路徑。 如果您有多個要探查的目錄，則可以將 <xref:System.AppDomainSetup.ApplicationBase%2A> 設定為根目錄，並使用 <xref:System.AppDomainSetup.PrivateBinPath%2A?displayProperty=nameWithType> 屬性來識別要探查的子目錄。 或者，您可以建立多個應用程式定義域，並將每個應用程式定義域的 <xref:System.AppDomainSetup.ApplicationBase%2A> 設定為其組件的適當路徑。  
  
 請注意，您可以使用 <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> 方法來載入這些組件。 因為它們現在是在探查路徑中，所以會將其載入到預設載入內容，而非載入來源內容。 不過，建議您切換成 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> 方法，並提供完整組件顯示名稱，確保一律使用正確版本。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType>
- <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>
