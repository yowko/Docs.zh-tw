---
title: .NET 應用程式中的資源
ms.date: 07/25/2018
helpviewer_keywords:
- deploying applications [.NET Framework], resources
- deploying applications [.NET Core], resources
- application resources
- resource files
- satellite assemblies
- localization
- packaging application resources
- localizing resources
ms.assetid: 8ad495d4-2941-40cf-bf64-e82e85825890
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 86efc3a9d9eab5c1529804769af413dd88e71f1c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59220483"
---
# <a name="resources-in-net-apps"></a>.NET 應用程式中的資源
幾乎每個實際執行品質應用程式都必須使用資源。 資源是任何使用應用程式以邏輯方式部署的非執行檔資料。 資源可能在應用程式中顯示作錯誤訊息，或做為使用者介面的一部分。 資源可以含有一些表單中的資料，包括字串、影像和永續性物件。 (若要將保留物件寫入資源檔，物件必須是可序列化的)。將資料儲存在資源檔中，可讓您不需要重新編譯整個應用程式即可變更資料。 也可讓您將資料儲存在單一位置，不需要依賴儲存在多個位置的硬式編碼資料。  
  
 .NET Framework 與 .NET Core 提供桌建立和當地語系化資源的完整支援。 此外，.NET 也支援簡單的模型以封裝及部署當地語系化資源。  
  
 如需 ASP.NET 中資源的詳細資訊，請參閱 [ASP.NET 網頁資源概觀](https://docs.microsoft.com/previous-versions/aspnet/ms227427(v=vs.100))。  
  
## <a name="creating-and-localizing-resources"></a>建立和當地語系化資源  

在非當地語系化的應用程式中，您可以使用資源檔做為應用程式資料的存放庫，特別是針對原始程式碼中多個位置的硬式編碼字串。 大多數情況下，您建立的資源是文字 (.txt) 或 XML (.resx) 檔案，並且使用 [Resgen.exe (資源檔產生器)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) 將它們編譯成二進位 .resources 檔。 然後這些檔案會由語言編譯器內嵌在應用程式的可執行檔。 如需有關建立資源檔的詳細資訊，請參閱[建立資源檔](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md)。  

您也可以針對特定文化特性當地語系化應用程式的資源。 這可讓您建置應用程式的當地語系化 (轉譯) 版本。 當您開發使用當地語系化資源的應用程式時，如果沒有適當的資源可供使用，您會指定文化特性做為其資源使用的中性或後援文化特性。 一般而言，中性文化特性的資源是儲存在應用程式的可執行檔中。 個別當地語系化文化特性的其餘資源會儲存在獨立的附屬組件。 如需詳細資訊，請參閱[建立附屬組件](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md)。  
  
## <a name="packaging-and-deploying-resources"></a>封裝和部署資源  
 您在[附屬組件](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)中部署當地語系化應用程式資源。 附屬組件包含單一文化特性的資源。它不包含任何應用程式程式碼。 在附屬組件部署模型中，您會建立應用程式，具有一個預設組件 (通常是主要組件) 和應用程式支援之每個文化特性的一個附屬組件。 因為附屬組件不是主要組件的一部分，您可以輕鬆地取代或更新對應至特定文化特性的資源，而不需要取代應用程式的主要組件。  
  
 謹慎地決定哪些資源將組成應用程式的預設資源組件。 因為它是主要組件的一部分，它的任何變更需要您取代主要組件。 如果您未提供預設資源，當[資源後援處理序](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)嘗試尋找它時，將會擲回例外狀況。 在設計良好的應用程式中，使用資源應該永遠不會擲回例外狀況。  
  
 如需詳細資訊，請參閱[封裝和部署資源](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)文章。  
  
## <a name="retrieving-resources"></a>擷取資源  
 在執行階段，應用程式會根據 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> 屬性所指定的文化特性，針對每個執行緒載入適當的當地語系化資源。 這個屬性值被衍生，如下所示︰  
  
-   藉由直接將代表當地語系化文化特性的 <xref:System.Globalization.CultureInfo> 物件指派至 <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> 屬性。  
  
-   如果未明確指派文化特性，則會從 <xref:System.Globalization.CultureInfo.DefaultThreadCurrentUICulture%2A?displayProperty=nameWithType> 屬性擷取預設執行緒 UI 文化特性。  
  
-   如果未明確指派預設執行緒 UI 文化特性 (透過在本機電腦上擷取目前使用者的文化特性)。 在 Windows 上執行的 .NET 實作透過呼叫 Windows [`GetUserDefaultUILanguage`](/windows/desktop/api/winnls/nf-winnls-getuserdefaultuilanguage) 函式來執行此動作。  
  
 如需如何設定目前 UI 文化特性的詳細資訊，請參閱 <xref:System.Globalization.CultureInfo> 和 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> 參考頁面。  
  
 然後，您可以使用 <xref:System.Resources.ResourceManager?displayProperty=nameWithType> 類別，針對目前 UI 文化特性或特定文化特性擷取資源。 雖然 <xref:System.Resources.ResourceManager> 類別最常用於擷取資源，<xref:System.Resources?displayProperty=nameWithType> 命名空間包含您可以用來擷取資源的額外類型。 它們包括：  
  
-   <xref:System.Resources.ResourceReader> 類別，可讓您列舉內嵌在組件中，或儲存在獨立二進位 .resources 檔中的資源。 當您不知道資源在執行階段可用的確切名稱時，這個項目很有用。  
  
-   <xref:System.Resources.ResXResourceReader> 類別，可讓您從 XML (.resx) 檔擷取資源。  
  
-   <xref:System.Resources.ResourceSet> 類別，可讓您擷取特定文化特性的資源，而不需要觀察後援規則。 資源可以儲存在組件或獨立二進位 .resources 檔中。 您也可以開發 <xref:System.Resources.IResourceReader> 實作，以使用 <xref:System.Resources.ResourceSet> 類別從其他來源擷取資源。  
  
-   <xref:System.Resources.ResXResourceSet> 類別，可讓您將 XML 資源檔中的所有項目擷取至記憶體。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Globalization.CultureInfo>
- <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType>
- [應用程式基本概念](../../../docs/standard/application-essentials.md)
- [建立資源檔](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md)
- [封裝和部署資源](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [建立附屬組件](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
- [擷取資源](../../../docs/framework/resources/retrieving-resources-in-desktop-apps.md)
