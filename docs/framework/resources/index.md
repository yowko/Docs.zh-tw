---
title: "桌面應用程式中的資源 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "應用程式資源"
  - "部署應用程式 [.NET Framework], 資源"
  - "當地語系化"
  - "當地語系化資源"
  - "封裝應用程式資源"
  - "資源檔"
  - "附屬組件"
ms.assetid: 8ad495d4-2941-40cf-bf64-e82e85825890
caps.latest.revision: 19
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 19
---
# 桌面應用程式中的資源
幾乎一切產品品質應用程式必須使用資源。  資源是使用應用程式部署在本機的任何不可執行的資料。  資源可能在應用程式中顯示作錯誤訊息，或做為使用者介面的一部分。  資源可以含有一些表單中的資料，包括字串、影像和永續性物件。請注意，為了將永續性物件寫入資源檔，該物件必須可序列化。若資料儲存於資源檔中，即允許您變更資料，而不需重新編譯整個應用程式。  它也可讓您在單一位置儲存資料，而不需倚賴在多個位置中的硬式編碼資料。  
  
 .NET Framework 對傳統型應用程式中資源的建立和當地語系化提供廣泛的支援。  此外，.NET Framework 還支援在傳統型應用程式中封裝 \(Package\) 和部署這些當地語系化資源的簡單模型。  
  
 如需 ASP.NET 資源的詳細資訊，請參閱 [ASP.NET Web Page Resources Overview](../Topic/ASP.NET%20Web%20Page%20Resources%20Overview.md) 在 Internet Explorer 開發人員中心。  
  
 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式從傳統型應用程式使用不同的來源模型並將其資源儲存在單一資源索引檔案中。  如需 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式中資源的詳細資訊，請參閱Windows 開發人員中心的 [建立和擷取 Windows 市集應用程式的資源](http://go.microsoft.com/fwlink/p/?LinkId=241674) 。  
  
## 建立和當地語系化資源  
 在非當地語系化的應用程式，您可以使用資源檔做為儲存機制的應用程式資料，特別是針對可能會在多個位置原始程式碼硬式編碼的字串。  通常，您會建立資源，或文字 \(.txt\) 或 XML \(.resx\) 檔案和使用 [Resgen.exe \(Resource File Generator\)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) 將它們編譯成二進位 .resources 檔案。  這些檔案位於應用程式的可執行檔可以由語言編譯器內嵌。  如需有關資源的詳細資訊，請參閱[建立資源檔](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md)。  
  
 您可以針對特定文化特性來當地語系化您的應用程式資源。  這可讓您建置應用程式的當地語系化 \(轉譯\) 版本。  當您開發應用程式時使用當地語系化資源，如果適當的資源無法使用，您會指定做為中性或後援文化特性的資源的文化特性。  通常，中性文化特性的資源儲存在應用程式的可執行檔中。  個別當地語系化文化特性的剩餘資源儲存在個別附屬組件中。  如需詳細資訊，請參閱[建立附屬組件](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md)。  
  
## 封裝和部署資源  
 您在 [附屬組件。](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)的當地語系化的應用程式資源。  附屬組件包含單一文化特性的資源，它不包含任何應用程式程式碼。  在附屬組件部署模型中，您建立的應用程式 \(通常是主要組件\) 的預設組件以及應用程式支援的所有文化特性的附屬組件。  因為附屬組件不是主要組件的一部分，您可以輕易取代或更新對應特定文化特性的資源，而不需取代應用程式的主要組件。  
  
 小心決定哪些資源要構成您應用程式的預設資源組件。  因為它是主要組件的一部分，它若有任何的變更，都將需要您取代主要組件。  如果您不提供預設資源，就會在[資源回溯過程](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)嘗試尋找它時，擲回例外狀況。  在設計良好的應用程式中，資源的使用應該從來不會擲回例外狀況。  
  
 如需詳細資訊，請參閱[封裝和部署資源](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)。  
  
## 擷取資源  
 在執行階段，應用程式會在個別執行緒在資料載入適當的當地語系化資源，根據文化特性所指定 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> 屬性。  這個屬性值衍生如下所示:  
  
-   透過直接指派代表當地語系化的文化特性設定為 <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=fullName> 屬性的 <xref:System.Globalization.CultureInfo> 物件。  
  
-   如果文化特性沒有明確指派，藉由 <xref:System.Globalization.CultureInfo.DefaultThreadCurrentUICulture%2A?displayProperty=fullName> 屬性擷取預設執行緒 UI 文化特性。  
  
-   如果預設執行緒 UI 文化特性沒有明確指派，使用來擷取目前使用者文化特性的本機電腦上透過呼叫 Windows `GetUserDefaultUILanguage` 函式。  
  
 如需目前 UI 文化特性如何設定屬性的詳細資訊，請參閱 <xref:System.Globalization.CultureInfo> 和 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> 參考頁面。  
  
 您可以使用 <xref:System.Resources.ResourceManager?displayProperty=fullName> 類別，擷取資源的目前 UI 文化特性或特定文化特性。  雖然 <xref:System.Resources.ResourceManager> 類別用於擷取在傳統型應用程式的資源， 最常用的是<xref:System.Resources?displayProperty=fullName> 命名空間包含可用於擷取資源的其他類型。  這些需求包括：  
  
-   <xref:System.Resources.ResourceReader> 類別，讓您能夠列舉資源在獨立的二進位 .resources 檔案內嵌在組件或儲存。  在您不知道可在執行階段資源時的正確名稱時很有用。  
  
-   <xref:System.Resources.ResXResourceReader> 類別，可讓您從 XML \(.resx\) 檔中擷取資源。  
  
-   <xref:System.Resources.ResourceSet> 類別，可讓您擷取特定文化特性資源，而不需遵守回溯原則。  資源可以儲存在組件或獨立的二進位 .resources 檔案中。  您也可以開發可讓您使用 <xref:System.Resources.ResourceSet> 類別從其他來源擷取資源的 <xref:System.Resources.IResourceReader> 實作。  
  
-   <xref:System.Resources.ResXResourceSet> 類別，可讓您擷取 XML 資源檔的所有項目至記憶體。  
  
## 請參閱  
 <xref:System.Globalization.CultureInfo>   
 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>   
 [應用程式基本概念](../../../docs/standard/application-essentials.md)   
 [建立資源檔](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md)   
 [封裝和部署資源](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)   
 [建立附屬組件](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md)   
 [擷取資源](../../../docs/framework/resources/retrieving-resources-in-desktop-apps.md)