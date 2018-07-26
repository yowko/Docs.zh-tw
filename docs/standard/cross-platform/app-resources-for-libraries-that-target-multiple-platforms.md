---
title: 以多平台為目標之函式庫的應用程式資源
ms.date: 07/18/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- multiple platforms, resources for
- resources [.NET Framework]
- .NET Framework, resources when targeting multiple platforms
- resources, for multiple platforms
- targeting multiple platforms, resources for
ms.assetid: 72c76f0b-7255-4576-9261-3587f949669c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 11b9bde41e2209a88a042eb6c61de37def9da787
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/25/2018
ms.locfileid: "39245489"
---
# <a name="app-resources-for-libraries-that-target-multiple-platforms"></a>以多平台為目標之函式庫的應用程式資源
您可以使用.NET Framework[可攜式類別庫](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)專案類型，以確保您類別庫中的資源，可從多個平台。 這個專案類型會在 [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)] 中提供，並且以 .NET Framework 類別庫的可攜式子集為目標。 使用[!INCLUDE[net_portable](../../../includes/net-portable-md.md)]可確保能夠從桌面應用程式、Silverlight 應用程式、Windows Phone 應用程式和 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式存取您的程式庫。  

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]
  
 [!INCLUDE[net_portable](../../../includes/net-portable-md.md)]專案只會將 <xref:System.Resources> 命名空間中非常有限的類型子集提供給您的應用程式，但確實可讓您使用 <xref:System.Resources.ResourceManager> 類別擷取資源。 不過，如果您要使用 Visual Studio 建立應用程式，則應該使用 Visual Studio 所建立的強類型包裝函式，而不要直接使用 <xref:System.Resources.ResourceManager> 類別。  
  
 若要在 Visual Studio 中建立的強型別包裝函式，設定主要資源檔的**存取修飾詞**Visual Studio 資源設計工具中**公用**。 這樣會建立包含強類型 ResourceManager 包裝函式的 [resourceFileName].designer.cs 或 [resourceFileName].designer.vb 檔。 如需使用的強類型的資源包裝函式的詳細資訊，請參閱 「 產生強類型資源類別 > 一節[Resgen.exe （資源檔產生器）](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)主題。  
  
## <a name="resource-manager-in-the-includenetportableincludesnet-portable-mdmd"></a>[!INCLUDE[net_portable](../../../includes/net-portable-md.md)]的資源管理員  
 在[!INCLUDE[net_portable](../../../includes/net-portable-md.md)]專案中，所有對資源的存取都是透過 <xref:System.Resources.ResourceManager> 類別處理。 由於無法從<xref:System.Resources>專案存取像是 <xref:System.Resources.ResourceReader> 和 <xref:System.Resources.ResourceSet> 這類 [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] 命名空間中的類型，因此這些類型無法用來存取資源。  
  
 [!INCLUDE[net_portable](../../../includes/net-portable-md.md)]專案包含下表列出的四個 <xref:System.Resources.ResourceManager> 成員。 這些建構函式和方法可讓您具現化 <xref:System.Resources.ResourceManager> 物件並擷取字串資源。  
  
|`ResourceManager` 成員|描述|  
|------------------------------|-----------------|  
|<xref:System.Resources.ResourceManager.%23ctor%28System.String%2CSystem.Reflection.Assembly%29>|建立 <xref:System.Resources.ResourceManager> 執行個體以存取所指定組件中的具名資源檔。|  
|<xref:System.Resources.ResourceManager.%23ctor%28System.Type%29>|建立對應所指定類型的 <xref:System.Resources.ResourceManager> 執行個體。|  
|<xref:System.Resources.ResourceManager.GetString%28System.String%29>|擷取目前文化特性的具名資源。|  
|<xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>|擷取屬於所指定文化特性的具名資源。|  
  
 將其他 <xref:System.Resources.ResourceManager> 成員從[!INCLUDE[net_portable](../../../includes/net-portable-md.md)]中排除，表示無法從資源檔擷取序列化物件、非字串資料和影像。 若要使用[!INCLUDE[net_portable](../../../includes/net-portable-md.md)]的資源，您應該以字串形式儲存所有物件資料。 例如，您可以將數值轉換成字串以便儲存到資源檔中，並且可以擷取這些字串，然後使用數值資料類型的 `Parse` 或 `TryParse` 方法將它們轉換回數字。 您可以藉由呼叫 <xref:System.Convert.ToBase64String%2A?displayProperty=nameWithType> 方法將影像或其他二進位資料轉換成字串表示，並且藉由呼叫 <xref:System.Convert.FromBase64String%2A?displayProperty=nameWithType> 方法將它們還原為位元組陣列。  
  
## <a name="the-includenetportableincludesnet-portable-mdmd-and-windows-store-apps"></a>[!INCLUDE[net_portable](../../../includes/net-portable-md.md)]和 Windows 市集應用程式  
 [!INCLUDE[net_portable](../../../includes/net-portable-md.md)]專案會將資源儲存在 .resx 檔中，這些資源接著會編譯為 .resources 檔，並且在編譯時期內嵌於主要組件或附屬組件中。 另一方面，[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式則需要將資源儲存到 .resw 檔中，這些檔案接著會編譯成單一封裝資源索引 (PRI) 檔。 不過，儘管這兩種檔案格式不相容，[!INCLUDE[net_portable](../../../includes/net-portable-md.md)]仍能在 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式中運作。  
  
 若要從 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式使用您的類別庫，請在 Windows 市集應用程式專案中加入其參考。 Visual Studio 會明確將您組件中的資源擷取至 .resw 檔中，並用它來產生 PRI 檔，讓 [!INCLUDE[wrt](../../../includes/wrt-md.md)]能夠從該檔案中擷取資源。 在執行階段，[!INCLUDE[wrt](../../../includes/wrt-md.md)]會執行您[!INCLUDE[net_portable](../../../includes/net-portable-md.md)]中的程式碼，不過它會從 PRI 檔擷取您的可攜式類別庫資源。  
  
 如果您的[!INCLUDE[net_portable](../../../includes/net-portable-md.md)]專案包含當地語系化資源，則可以使用中樞和支點模型來部署這些資源，就像在桌面應用程式中部署程式庫一樣。 若要使用 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式中的主要資源檔和任何當地語系化資源檔，可以加入主要組件的參考。 在編譯時期，Visual Studio 會將您的主要資源檔和所有當地語系化資源檔中的資源擷取至不同的 .resw 檔。 然後會將 .resw 檔編譯成單一 PRI 檔案，供 [!INCLUDE[wrt](../../../includes/wrt-md.md)]在執行階段時存取。  
  
<a name="NonLoc"></a>   
## <a name="example-non-localized-includenetportableincludesnet-portable-mdmd"></a>範例：非當地語系化的[!INCLUDE[net_portable](../../../includes/net-portable-md.md)]  
 以下簡單的非當地語系化[!INCLUDE[net_portable](../../../includes/net-portable-md.md)]範例會使用資源來儲存資料行的名稱，並判斷要為表格式資料保留的字元數。 這個範例會使用名為 LibResources.resx 的檔案儲存下表中列出的字串資源。  
  
|資源名稱|資源值|  
|-------------------|--------------------|  
|Born|生日|  
|BornLength|12|  
|Hired|雇用日期|  
|HiredLength|12|  
|ID|ID|  
|ID.Length|12|  
|名稱|名稱|  
|NameLength|25|  
|標題|員工資料庫|  
  
 下列程式碼定義`UILibrary`類別，會使用名為資源管理員包裝函式`resources`Visual Studio 所產生時**存取修飾詞**檔案變更為**公用**. UILibrary 類別會在必要時剖析字串資料。 . 請注意，該類別位於 `MyCompany.Employees` 命名空間中。  
  
 [!code-csharp[Conceptual.Resources.Portable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/uilibrary.cs#1)]
 [!code-vb[Conceptual.Resources.Portable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/uilibrary.vb#1)]  
  
 下列程式碼將示範如何從主控台模式應用程式存取 `UILibrary` 類別及其資源。 它需要將 UILIbrary.dll 的參考加入主控台應用程式專案中。  
  
 [!code-csharp[Conceptual.Resources.Portable#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/program.cs#2)]
 [!code-vb[Conceptual.Resources.Portable#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/module1.vb#2)]  
  
 下列程式碼將示範如何從 `UILibrary`應用程式存取 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 類別及其資源。 它需要將 UILIbrary.dll 的參考加入 Windows 市集應用程式專案中。  
  
 [!code-csharp[Conceptual.Resources.PortableMetro#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portablemetro/cs/blankpage.xaml.cs#1)]  
  
## <a name="example-localized-includenetportableincludesnet-portable-mdmd"></a>範例：當地語系化的[!INCLUDE[net_portable](../../../includes/net-portable-md.md)]  
 下列當地語系化的[!INCLUDE[net_portable](../../../includes/net-portable-md.md)]範例包含法文 (法國) 和英文 (美國) 文化特性的資源。 英文 （美國） 文化特性是應用程式的預設文化特性;它的資源會顯示在資料表中[上一節](../../../docs/standard/cross-platform/app-resources-for-libraries-that-target-multiple-platforms.md#NonLoc)。 法文 (法國) 文化特性的資源檔命名為 LibResources.fr-FR.resx，並且包含下表所列的字串資源。 `UILibrary` 類別的原始程式碼與前一節中所顯示的內容相同。  
  
|資源名稱|資源值|  
|-------------------|--------------------|  
|Born|Date de naissance|  
|BornLength|20|  
|Hired|Date embauché|  
|HiredLength|16|  
|ID|ID|  
|名稱|Nom|  
|標題|Base de données des employés|  
  
 下列程式碼將示範如何從主控台模式應用程式存取 `UILibrary` 類別及其資源。 它需要將 UILIbrary.dll 的參考加入主控台應用程式專案中。  
  
 [!code-csharp[Conceptual.Resources.Portable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/program2.cs#3)]
 [!code-vb[Conceptual.Resources.Portable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/module2.vb#3)]  
  
 下列程式碼將示範如何從 `UILibrary`應用程式存取 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 類別及其資源。 它需要將 UILIbrary.dll 的參考加入 Windows 市集應用程式專案中。 它會使用靜態 `ApplicationLanguages.PrimaryLanguageOverride` 屬性將應用程式的慣用語言設定為法文。  
  
 [!code-csharp[Conceptual.Resources.PortableMetroLoc#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portablemetroloc/cs/blankpage.xaml.cs#1)]
 [!code-vb[Conceptual.Resources.PortableMetroLoc#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portablemetroloc/vb/blankpage.xaml.vb#1)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Resources.ResourceManager>  
 [桌面應用程式中的資源](../../../docs/framework/resources/index.md)  
 [封裝和部署資源](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)
