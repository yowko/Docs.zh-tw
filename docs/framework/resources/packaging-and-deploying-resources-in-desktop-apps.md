---
title: "在桌面應用程式中封裝和部署資源"
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
- deploying applications [.NET Framework], resources
- resource files, deploying
- hub-and-spoke resource deployment model
- resource files, packaging
- application resources, packaging
- single resource assembly
- satellite assemblies
- default culture for applications
- names [.NET Framework], resources
- fallback process for resources
- grouping cultures
- application resources, deploying
- application resources, naming conventions
- culture, packaging and deploying resources
- resource files, naming conventions
- packaging application resources
- application resources, fallback processes
- resource files, fallback processes
- localizing resources
- neutral cultures
ms.assetid: b224d7c0-35f8-4e82-a705-dd76795e8d16
caps.latest.revision: 26
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 5de456ff1a371a43241dba3b47be7dcd80bf8f70
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# 在桌面應用程式中封裝和部署資源
應用程式相依於 .NET Framework 資源管理員，以 <xref:System.Resources.ResourceManager> 類別，擷取當地語系化的資源。  資源管理員會假設， hub 和 spoke 模型可用來封裝和部署資源。  中樞為主要組件，包含無法當地語系化的可執行程式碼，和稱為中性或預設文化特性的單一文化特性的資源。  預設文化特性為應用程式的後援文化特性;如果找不到當地語系化的資源，它會使用此文化特性的資源。  各個輪輻都連接至含有單一文化特性資源 \(但不包含任何程式碼\) 的附屬組件。  
  
 這個模型有幾個優點：  
  
-   您可以在已部署應用程式之後，遞增地加入新文化特性的資源。  因為特定文化特性資源的後續開發可能需要非常大量的時間，這允許您先發行主應用程式，而在日後發行特定文化特性資源。  
  
-   您可以更新並變更應用程式的附屬組件，而不需重新編譯應用程式。  
  
-   應用程式只需載入那些包含特定文化特性所需資源的附屬組件。  這大幅降低系統資源的使用。  
  
 然而，這個模型也有缺點：  
  
-   您必須管理多個資源集合。  
  
-   測試應用程式的初期成本會增加，因為您必須測試數個組態。  注意，就長期而言，測試一個具有數個附屬組件的核心應用程式，較測試並維護數個平行的國際版本，要來得更容易並且更便宜。  
  
## 資源命名規範  
 當您封裝應用程式的資源時，您必須使用 Common Language Runtime 所要求的資源命名規範來命名它們。  執行階段會根據它的文化特性名稱識別資源。  每個文化特性都會被指定成唯一名稱，該名稱是由和語言關聯之兩個小寫字母的文化特性名稱，以及在必要時和國家或地區關聯之兩個大寫字母的子文化特性名稱所組合而成。  子文化特性名稱會以破折號 \(\-\) 分隔，接在文化特性名稱之後。  範例包括， ja\-JP 代表日本的所說的日文，英文的 en\-US代表美國的所說的英文，或德文的 de\-DE代表德國的所說的德文， de\-AT代表澳洲所說的在德文。  請在移至全域開發人員中心的 [國家語言支援 \(NLS\) \(NLS\) API 參考](http://go.microsoft.com/fwlink/?LinkId=200048) 參閱文化特性名稱的完整清單。  
  
> [!NOTE]
>  如需建立資源檔的詳細資訊，請參閱 MSDN Library 中的。 [建立資源檔](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md) 和 [建立附屬組件](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md) 。  
  
<a name="cpconpackagingdeployingresourcesanchor1"></a>   
## 資源回溯過程  
 封裝並部署資源的中樞和輪輻模型使用回溯過程來找出適當資源。  如果應用程式使用者的要求無法使用 ，Common Language Runtime 會在文化特性的階層架構中搜尋最接近使用者要求的適當後援資源，而引發例外狀況只是做為最後手段。  在階層架構的各個層級上，如果找到適當資源，Runtime 就使用它。  如果未找到資源，會在下一層級繼續搜尋。  
  
 若要改善查閱效能，請將 <xref:System.Resources.NeutralResourcesLanguageAttribute> 屬性套用至主要組件，並為它傳遞將與主要組件一起使用的中性語言名稱。  
  
> [!TIP]
>  您可以使用組態項目 [\<relativeBindForResources\>](../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md) 最佳化以執行階段為資源組件探查的資源後援處理序和處理序。  如需詳細資訊，請參閱[最佳化資源後援處理序](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md#Optimizing)章節。  
  
 資源後援處理序是包含下列步驟:  
  
1.  執行時首先會檢查符合應用程式所要求之文化特性組件的[全域組件快取](../../../docs/framework/app-domains/gac.md)。  
  
     全域組件快取可以儲存許多應用程式所共用的資源組件。  這讓您免於必須包含特定資源集合於您所建立的一切應用程式的目錄結構中。  如果執行階段找到組件的參考，它會在組件中搜尋所要求的資源。  如果它找到組件中的項目，它會使用要求的資源。  如果它沒找到項目，它將繼續搜尋。  
  
2.  接下來檢查目前執行中組件的目錄，找出符合所要求文化特性的目錄。  如果它找到目錄，它會在那目錄中搜尋所要求文化特性的有效附屬組件。  Runtime 接著在附屬組件中搜尋要求的資源。  如果在組件中找到資源，即使用它。  如果它未找到資源，則繼續搜尋。  
  
3.  接下來查詢來判斷的 Windows Installer 附屬組件是否要在要求時安裝。  如果是，它會處理安裝，載入組件，並在其中搜尋或要求的資源。  如果在組件中找到資源，即使用它。  如果它未找到資源，則繼續搜尋。  
  
4.  執行階段引發事件 <xref:System.AppDomain.AssemblyResolve?displayProperty=fullName> 表示無法找到附屬組件。  如果您選擇要處理事件，則事件處理常式可以傳回至資源查閱時使用的附屬組件的參考。  如果沒有，事件處理常式會傳回 `null` ，而且搜尋作業會繼續進行。  
  
5.  接下來於全域組件快取中再度搜尋，此時要找出所要求資源的父組件。  如果父組件存在於全域組件快取，Runtime 則在組件中搜尋要求的資源。  
  
     父組件被定義為適當的回溯文化特性。  將父組件視為最適候選者，因為提供任何資源要比擲回例外狀況更合適。  這個過程也允許您重複使用資源。  只要子文化特性不需要當地語系化所要求的資源，您必須包括特定資源在父層級。  例如，如果您提供附屬組件給 en \(中性英文\)、en\-GB \(在英國所說的英文\) 和 en\-US \(在美國所說的英文\)，則 en 附屬組件會包含共通的專門用語，而 en\-GB 和 en\-US 附屬組件可能只對那些不同的詞彙進行覆寫。  
  
6.  Runtime 接下來檢查目前執行中組件的目錄，看看它是否包含父目錄。  如果父目錄存在，Runtime 在目錄中搜尋父文化特性的有效附屬組件。  如果它找到組件，Runtime 在組件中搜尋要求的資源。  如果找到資源，即使用它。  如果它未找到資源，則繼續搜尋。  
  
7.  接下來查詢來判斷的 Windows Installer 父附屬組件是否要在要求時安裝。  如果是，它會處理安裝，載入組件，並在其中搜尋或要求的資源。  如果在組件中找到資源，即使用它。  如果它未找到資源，則繼續搜尋。  
  
8.  執行階段會引發事件 <xref:System.AppDomain.AssemblyResolve?displayProperty=fullName> 表示找不到適當後援資源。  如果您選擇要處理事件，則事件處理常式可以傳回至資源查閱時使用的附屬組件的參考。  如果沒有，事件處理常式會傳回 `null` ，而且搜尋作業會繼續進行。  
  
9. 接下來在許多可能層級中全面搜尋父組件 \(如先前步驟\)。  每個文化特性只有一個父 <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=fullName> ，是由屬性所定義的，不過，父代可能具有自己的父代。  目前文化特性的 <xref:System.Globalization.CultureInfo.Parent%2A> 屬性傳回 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>，搜尋父文化停止;如需資源後援，不因文化特性不會被視為一個父項目可以有資源的文化特性或特定文化特性。  
  
10. 如果已經搜尋原先指定的文化特性和所有父文化特性卻仍未找到資源，則會使用預設 \(回溯\) 文化特性的資源。  通常，預設文化特性的資源置於主應用程式組件中。  不過，您可以在 <xref:System.Resources.NeutralResourcesLanguageAttribute> 屬性的 <xref:System.Resources.NeutralResourcesLanguageAttribute.Location%2A> 屬性指定 <xref:System.Resources.UltimateResourceFallbackLocation> 的值表示資源的最終後援位置為附屬組件，而不是主要組件。  
  
    > [!NOTE]
    >  預設資源是唯一與主要組件一起編譯的資源。  除非您利用 <xref:System.Resources.NeutralResourcesLanguageAttribute> 指定附屬組件，否則它便是最終後援 \(最終父代\)。  因此，我們建議您在您的主要組件永遠包含預設資源集合。  這有助於防止擲回例外狀況。  藉著包含預設資源檔，您可替所有資源提供回溯，並確保至少有一個資源一直為使用者存在著，即使它不是特定文化特性的。  
  
11. 最後，如果執行階段沒有找到預設 \(回溯\) 文化特性的資源，將會擲回<xref:System.Resources.MissingManifestResourceException>或<xref:System.Resources.MissingSatelliteAssemblyException>例外狀況以表示資源無法找到。  
  
 例如，假設應用程式要求墨西哥西班牙文的資源 \(es\-MX 當地語系化文化特性\)。  執行階段會先在全域組件快取中搜尋符合 es\-MX 的組件，但找不到。  若找到它，接著在目前執行中組件的目錄搜尋 "es\-MX" 目錄。  若失敗，Runtime 再度於全域組件快取中搜尋反映適當回溯文化特性的父組件 \- 在這個案例中為 "es" \(西班牙文\)。  如果沒有找到父組件，在父組件的所有可能層級上搜尋 "es\-MX" 文化特性，直到尋獲對應的資源為止。  如果未找到資源，Runtime 使用預設文化特性的資源。  
  
<a name="Optimizing"></a>   
### 最佳化資源後援處理序  
 在下列情況下，可以提高執行階段搜尋在附屬組件中的資源的處理序。  
  
-   附屬組件中部署位置和程式碼組件相同。  如果程式碼組件安裝在 [全域組件快取](../../../docs/framework/app-domains/gac.md)，附屬組件安裝在全域組件快取安裝代理程式。  如果程式碼組件目錄中安裝，附屬組件在該目錄中文化特性資料夾安裝。  
  
-   附屬組件在未要求時安裝。  
  
-   應用程式程式碼不會處理 <xref:System.AppDomain.AssemblyResolve?displayProperty=fullName> 事件。  
  
 如下列範例所示，您可以藉由 [\<relativeBindForResources\>](../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md) 項目來最佳化附屬組件，並在應用程式組態檔設定其屬性 `enabled` 為 `true` 。  
  
```  
  
<configuration>  
   <runtime>  
      <relativeBindForResources enabled="true" />  
   </runtime>  
</configuration>  
  
```  
  
 附屬組件的最佳化探查是選取功能。  也就是執行階段遵循  [資源回溯過程](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md#cpconpackagingdeployingresourcesanchor1) 中說明的步驟，除非 [\<relativeBindForResources\>](../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md)項目存在於應用程式的組態檔，而且其 `enabled` 屬性設定為`true`。  如果是這種情況，附屬組件的探查修改程序如下所示:  
  
-   執行階段會使用父程式碼組件的位置指定附屬組件的探查。  如果父組件位於全域組件快取中安裝，執行階段會探查在快取中，而不是在應用程式的目錄。  如果父組件在應用程式目錄中安裝， Runtime 會檢查應用程式目錄中，但不在全域組件快取。  
  
-   執行階段不會查詢附屬組件的隨選安裝的 Windows Installer。  
  
-   如果特定資源組件的探查失敗，執行階段不會引發事件。 <xref:System.AppDomain.AssemblyResolve?displayProperty=fullName>  
  
### 附屬組件的最終後援  
 您可以從主要組件中選擇性地移除資源和指定執行階段，從對應至特定文化特性的附屬組件載入最終後援資源。  若要控制後援處理序，您可以使用 <xref:System.Resources.NeutralResourcesLanguageAttribute.%23ctor%28System.String%2CSystem.Resources.UltimateResourceFallbackLocation%29?displayProperty=fullName> 建構函式並提供指定的 <xref:System.Resources.UltimateResourceFallbackLocation> 參數值設定資源管理員是否應從主要組件或附屬組件中抽取後援資源。  
  
 下列範例會在法文 \(fr\) 語言的附屬組件使用 <xref:System.Resources.NeutralResourcesLanguageAttribute> 屬性儲存應用程式的後援資源。這個範例會定義名為的 `Greeting`單一字串資源的兩個文字基礎的資源檔。  第一， resources.fr.txt，含有法文資源。  
  
```  
Greeting=Bon jour!  
```  
  
 第二，資源 ru.txt，包含俄文資源。  
  
```  
Greeting=Добрый день  
```  
  
 這兩個檔案編譯為 .resources 檔來執行 [資源檔產生器 \(Resgen.exe\)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) 從命令列。對於法文資源，這個命令是:  
  
 **resgen.exe resources.fr.txt**  
  
 對於俄文資源，這個命令是:  
  
 **resgen.exe resources.ru.txt**  
  
 將 .resources 檔案內嵌至動態連結程式庫 \(DLL\) 透過執行 [組件連結器 \(Al.exe\)](../../../docs/framework/tools/al-exe-assembly-linker.md) 從法文資源的命令列如下所示:  
  
 **al \/t:lib \/embed:resources.fr.resources \/culture:fr \/out:fr\\Example1.resources.dll**  
  
 對於俄文資源如下所示:  
  
 **al \/t:lib \/embed:resources.ru.resources \/culture:ru \/out:ru\\Example1.resources.dll**  
  
 應用程式原始程式碼中尋找名為 Example1.cs 或 Example1.vb 的檔案。  它包含 <xref:System.Resources.NeutralResourcesLanguageAttribute> 屬性表示預設應用程式資源在 fr 子目錄。  執行個體化資源管理員，擷取 `Greeting` 資源的值，並將它顯示至主控台。  
  
 [!code-csharp[Conceptual.Resources.Packaging#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.packaging/cs/example1.cs#1)]
 [!code-vb[Conceptual.Resources.Packaging#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.packaging/vb/example1.vb#1)]  
  
 您可以從命令列編譯 C\# 原始程式碼如下所示:  
  
 **csc Example1.cs**  
  
 Visual Basic 編譯器的命令非常類似:  
  
 **vbc Example1.vb**  
  
 因為沒有在主要組件中內嵌的資源，您可以使用 `/resource` 參數，您不需要編譯。  
  
 當您從刪除俄文之外的其他語言，會顯示下列輸出:  
  
```  
Bon jour!  
```  
  
## 建議的封裝替代方式  
 時間或經費限制可能會讓您無法建立一組您應用程式所支援的各個子文化特性的資源。  相反地，您可以建立所有相關子文化特性可以使用的父文化特性的單一附屬組件。  例如，您可以提供單一英文附屬組件 \(en\) 給要求地區特性英文資源的使用者擷取，和單一德文附屬組件 \(de\) 給要求地區特性德文資源的使用者。  例如，對於德國德文 \(de\-DE\)、奧地利德文 \(de\-AT\) 和瑞士德文 \(de\-CH\) 的要求將會回溯至德文附屬組件 \(de\)。  預設資源為最終回溯，並因此應該是您應用程式的大多數使用者所將要求的資源。  雖然這個方案會部署比較不是特定文化特性的資源，但它可以大幅降低您應用程式的當地語系化成本。  
  
## 請參閱  
 [桌面應用程式中的資源](../../../docs/framework/resources/index.md)   
 [全域組件快取](../../../docs/framework/app-domains/gac.md)   
 [建立資源檔](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md)   
 [建立附屬組件](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md)