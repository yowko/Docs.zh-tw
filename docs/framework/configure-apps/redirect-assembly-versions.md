---
title: 重新導向組件版本
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- assembly binding, redirection
- redirecting assembly binding to earlier version
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], binding redirection
ms.assetid: 88fb1a17-6ac9-4b57-8028-193aec1f727c
caps.latest.revision: 26
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: 24343e1ee2e95cbeb7613d3b22dd7cdac848903b
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="redirecting-assembly-versions"></a>重新導向組件版本
您可以將編譯時間繫結參考重新導向至 .NET Framework 組件、協力廠商組件或您自己的應用程式組件。 您可以用多種方式將應用程式重新導向為使用其他版本的組件：透過發行者原則、透過應用程式設定檔或透過電腦設定檔。 本文討論 .NET Framework 中的組件繫結如何運作，以及其設定方式。  
  
<a name="BKMK_Assemblyunificationanddefaultbinding"></a>   
## <a name="assembly-unification-and-default-binding"></a>組件統一和預設繫結  
 .NET Framework 組件的繫結有時會透過名為 *「組件統一」*(assembly unification) 的處理序進行重新導向。 .NET Framework 包含某個版本的通用語言執行平台，以及大約二十多個組成類型程式庫的 .NET Framework 組件。 執行階段將這些 .NET Framework 組件視為單一單位。 根據預設，應用程式啟動時，任何類型參考只要位於執行階段所執行的程式碼中，都會導向至 .NET Framework 組件；且該組建將與載入處理序的執行階段具有相同的版本號碼。 與此模型同時發生的重新導向，皆為執行階段的預設行為。  
  
 例如，如果您的應用程式參考 System.XML 命名空間中的類型，而且是使用 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]所建立，則會包含隨附於執行階段 4.5 版之 System.XML 組件的靜態參考。 如果您要將點的繫結參考重新導向至隨附於 .NET Framework 4 的 System.XML 組件，可以將重新導向資訊放在應用程式設定檔中。 統一的 .NET Framework 組件之設定檔中的繫結重新導向會取消統一該組件。  
  
 此外，如果有多個可用版本，您可能會想要以手動方式將協力廠商組件的組件繫結重新導向。  
  
<a name="BKMK_Redirectingassemblyversionsbyusingpublisherpolicy"></a>   
## <a name="redirecting-assembly-versions-by-using-publisher-policy"></a>使用發行者原則將組件版本重新導向  
 組件的廠商可以加入具有新組件的發行者原則檔，藉此將應用程式導向至較新版的組件。 發行者原則檔位於全域組件快取，其中包含組件重新導向設定。  
  
 組件的每個主要 .次要 版本都有自己的發行者原則檔。 例如，從 2.0.2.222 版重新導向至 2.0.3.000 版，以及從 2.0.2.321 版重新導向至 2.0.3.000 版，兩者的目標檔案皆相同，因為已透過 2.0 版建立了關係。 然而，從 3.0.0.999 版重新導向至 4.0.0.000 版則會傳入 3.0.999 版的檔案。 .NET Framework 的每個主要版本都有自己的發行者原則檔。  
  
 如果組件有發行者原則檔，則執行階段會在檢查組件的資訊清單和應用程式設定檔後，檢查此檔案。 廠商必須只在新組件與重新導向的舊版組件相容時，才使用發行者原則檔。  
  
 您可以指定應用程式設定檔中的設定，藉此略過應用程式的發行者原則，方法詳述於 [略過發行者原則章節](#bypass_PP)。  
  
<a name="BKMK_Redirectingassemblyversionsattheapplevel"></a>   
## <a name="redirecting-assembly-versions-at-the-app-level"></a>將應用程式層級的組件版本重新導向  
 有數種不同技術可透過應用程式設定檔變更應用程式的繫結行為：您可以手動編輯應用程式設定檔、可以依賴自動繫結重新導向，也可以略過發行者原則以指定繫結行為。  
  
### <a name="manually-editing-the-app-config-file"></a>手動編輯應用程式設定檔  
 您可以手動編輯應用程式設定檔以解決組件問題。 例如，如果廠商可能發行您應用程式所使用的組件較新版本，但因為不保證與舊版相容而未提供發行者原則，則可以將組件繫結資訊放在應用程式的設定檔中 (如下所示)，藉此將應用程式重新導向為使用較新版的組件。  
  
```xml  
<dependentAssembly>  
  <assemblyIdentity name="someAssembly"  
    publicKeyToken="32ab4ba45e0a69a1"  
    culture="en-us" />  
  <bindingRedirect oldVersion="7.0.0.0" newVersion="8.0.0.0" />  
</dependentAssembly>  
```  
  
### <a name="relying-on-automatic-binding-redirection"></a>依賴自動繫結重新導向  
 從 [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)]開始，以 [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] 為目標的新桌面應用程式會使用自動繫結重新導向。 這表示如果兩個元件參考了同一個強式名稱組件的不同版本，則執行階段會自動將繫結重新導向加入較新版組件的輸出應用程式設定檔 (app.config)。 此重新導向會覆寫可能執行的組件統一。 來源 app.config 檔案則不會加以修改。 例如，假設您的應用程式直接參考頻外 .NET Framework 元件，但使用以相同元件較舊版本為目標的協力廠商程式庫。 當您編譯應用程式時，輸出應用程式設定檔已修改為包含較新版元件的繫結重新導向。 如果您建立的是 Web 應用程式，則會收到有關繫結衝突的建置警告，從而提供您選項將必要的繫結重新導向加入來源 Web 設定檔中。  
  
 如果您在編譯期間以手動方式將繫結重新導向加入來源 app.config 檔案中， [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)] 會嘗試依據您加入的繫結重新導向來統一組件。 例如，假設您為組件插入下列繫結重新導向：  
  
 `<bindingRedirect oldVersion="3.0.0.0" newVersion="2.0.0.0" />`  
  
 如果應用程式中另一個專案參考同一個組件的 1.0.0.0 版，自動繫結重新導向會將下列項目加入輸出 app.config 檔案，使得應用程式在此組件的 2.0.0.0 版上統一：  
  
 `<bindingRedirect oldVersion="1.0.0.0" newVersion="2.0.0.0" />`  
  
 如果您的應用程式以 [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)]中的舊版 .NET Framework 為目標，您可以啟用自動繫結重新導向。 您可以為任何組件提供 app.config 檔中的繫結重新導向資訊，藉此覆寫此預設行為，或關閉繫結重新導向功能。 如需如何開啟或關閉這項功能的資訊，請參閱[How to： 啟用和停用自動繫結重新導向](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)。  
  
<a name="bypass_PP"></a>   
### <a name="bypassing-publisher-policy"></a>略過發行者原則  
 您可以在必要時覆寫應用程式設定檔中的發行者原則。 例如，宣告與舊版相容的新版組件仍可能中斷應用程式。 如果您想略過發行者原則，新增[ \<p >](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md)元素[ \<dependentAssembly >](../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md)組與應用程式組態檔中的項目**套用**屬性**沒有**，它會覆寫任何先前**是**設定。  
  
 `<publisherPolicy apply="no" />`  
  
 略過發行者原則可讓應用程式持續為使用者執行，但請務必將您的問題回報給組件的廠商。 如果組件有發行者原則檔，廠商應確保該組件與舊版相容，並確保用戶端使用新版時受到最少的限制。  
  
<a name="BKMK_Redirectingassemblyversionsatthemachinelevel"></a>   
## <a name="redirecting-assembly-versions-at-the-machine-level"></a>將電腦層級的組件版本重新導向  
 電腦系統管理員要讓電腦上所有應用程式都使用特定版本組件的案例很少見。 例如，因為特定的組件版本可修正安全性漏洞，所以系統管理員可能會想讓所有應用程式都使用該版本。 如果在電腦的設定檔中將組件重新導向，則該電腦上所有使用舊版的應用程式都會重新導向為使用新版。 電腦設定檔會覆寫應用程式設定檔和發行者原則檔。 這個檔案位於 %*runtime install path*%\Config 目錄中。 .NET Framework 通常會安裝在 %drive%\Windows\Microsoft.NET\Framework 目錄中。  
  
<a name="BKMK_Specifyingassemblybindinginconfigurationfiles"></a>   
## <a name="specifying-assembly-binding-in-configuration-files"></a>指定設定檔中的組件繫結  
 無論繫結重新導向位於應用程式設定檔、電腦設定檔或發行者原則檔，您都可以使用相同的 XML 格式加以指定。 若要將一個組件版本重新導向至另一個，使用[ \<bindingRedirect >](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)項目。 **oldVersion** 屬性可指定單一或一個範圍的組件版本。 `newVersion` 屬性應指定單一版本。  例如， `<bindingRedirect oldVersion="1.1.0.0-1.2.0.0" newVersion="2.0.0.0"/>` 可指定執行階段使用 2.0.0.0 版，而非指定介於 1.1.0.0 和 1.2.0.0 之間的組件版本。  
  
 下列程式碼範例示範多種繫結重新導向情節。 此範例為一個範圍的 `myAssembly`版本指定重新導向，並為 `mySecondAssembly`指定單一繫結重新導向。 範例同時指定發行者原則檔不會覆寫 `myThirdAssembly`的繫結重新導向。  
  
 要繫結組件，您必須指定字串"描述 urn:-microsoft-: asm.v1"與**xmlns**屬性[ \<assemblyBinding >](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md)標記。  
  
```xml  
<configuration>  
  <runtime>  
    <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
      <dependentAssembly>  
        <assemblyIdentity name="myAssembly"  
          publicKeyToken="32ab4ba45e0a69a1"  
          culture="en-us" />  
        <!-- Assembly versions can be redirected in app,   
          publisher policy, or machine configuration files. -->  
        <bindingRedirect oldVersion="1.0.0.0-2.0.0.0" newVersion="3.0.0.0" />  
      </dependentAssembly>  
  <dependentAssembly>  
        <assemblyIdentity name="mySecondAssembly"  
          publicKeyToken="32ab4ba45e0a69a1"  
          culture="en-us" />  
             <bindingRedirect oldVersion="1.0.0.0" newVersion="2.0.0.0" />  
      </dependentAssembly>  
      <dependentAssembly>  
      <assemblyIdentity name="myThirdAssembly"  
        publicKeyToken="32ab4ba45e0a69a1"  
        culture="en-us" />  
        <!-- Publisher policy can be set only in the app   
          configuration file. -->  
        <publisherPolicy apply="no" />  
      </dependentAssembly>  
    </assemblyBinding>  
  </runtime>  
</configuration>  
```  
  
### <a name="limiting-assembly--bindings-to-a-specific-version"></a>將組件繫結限制在特定版本  
 您可以使用**appliesTo**屬性[ \<assemblyBinding >](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md)重新導向組件繫結參考至特定版本的.NET 應用程式組態檔中的項目架構。 這個選擇性屬性會使用 .NET Framework 版本號碼，以表示它適用於哪一個版本。 如果未指定 **appliesTo** 屬性，則 [\<assemblyBinding>](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) 項目會套用至所有的 .NET Framework 版本。  
  
 例如，若要將 .NET Framework 3.5 組件的組件繫結重新導向，您會將下列 XML 程式碼加入您的應用程式設定檔中。  
  
```xml  
<runtime>  
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1"   
    appliesTo="v3.5">  
    <dependentAssembly>   
      <!-- assembly information goes here -->  
    </dependentAssembly>  
  </assemblyBinding>  
</runtime>  
```  
  
 您必須依版本順序輸入重新導向資訊。 例如，請先輸入 .NET Framework 3.5 組件的組件繫結重新導向資訊，接著再輸入 .NET Framework 4.5 組件的資訊。 最後，請輸入不使用 **appliesTo** 屬性的任何 .NET Framework 組件重新導向之組件繫結重新導向資訊，如此一來會適用於所有版本的 .NET Framework。 如果重新導向發生衝突，會使用設定檔中第一筆相符的重新導向陳述式。  
  
 例如，若要將一個參考重新導向至 .NET Framework 3.5 組件，並將另一個參考重新導向至 .NET Framework 4 組件，則您可以使用下列虛擬程式碼所示的模式。  
  
```xml  
<assemblyBinding xmlns="..." appliesTo="v3.5 ">   
  <!—.NET Framework version 3.5 redirects here -->   
</assemblyBinding>   
  
<assemblyBinding xmlns="..." appliesTo="v4.0.30319">   
  <!—.NET Framework version 4.0 redirects here -->   
</assemblyBinding>   
  
<assemblyBinding xmlns="...">   
  <!-- redirects meant for all versions of the runtime -->   
</assemblyBinding>  
```  
  
## <a name="see-also"></a>另請參閱  
 [如何：啟用和停用自動繫結重新導向](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)  
 [\<bindingRedirect > 項目](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)  
 [組件繫結重新導向安全性使用權限](../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md)  
 [Common Language Runtime 中的組件](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 [使用組件設計程式](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 [執行階段如何找出組件](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [設定應用程式](../../../docs/framework/configure-apps/index.md)  
 [設定.NET Framework 應用程式](http://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)  
 [執行階段設定結構描述](../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [組態檔結構描述](../../../docs/framework/configure-apps/file-schema/index.md)  
 [如何：建立發行者原則](../../../docs/framework/configure-apps/how-to-create-a-publisher-policy.md)
