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
ms.openlocfilehash: e846f45b55ac09d6ce6af4f3223c3bdba1dc83ba
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2019
ms.locfileid: "67506006"
---
# <a name="app-resources-for-libraries-that-target-multiple-platforms"></a>以多平台為目標之函式庫的應用程式資源
您可以使用.NET Framework[可攜式類別庫](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)專案類型，以確保您類別庫中的資源，可從多個平台。 這個專案類型會是適用於 Visual Studio 2012，並以.NET Framework 類別庫的可攜式子集為目標。 使用可攜式類別庫可確保您的程式庫，可以從傳統型應用程式、 Silverlight 應用程式、 Windows Phone 應用程式，存取和[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式。

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 可攜式類別庫專案可讓只有非常有限的中的類型子集<xref:System.Resources>命名空間提供給您的應用程式，但確實可讓您使用<xref:System.Resources.ResourceManager>類別來擷取資源。 不過，如果您要使用 Visual Studio 建立應用程式，則應該使用 Visual Studio 所建立的強類型包裝函式，而不要直接使用 <xref:System.Resources.ResourceManager> 類別。

 若要在 Visual Studio 中建立的強型別包裝函式，設定主要資源檔的**存取修飾詞**Visual Studio 資源設計工具中**公用**。 這樣會建立包含強類型 ResourceManager 包裝函式的 [resourceFileName].designer.cs 或 [resourceFileName].designer.vb 檔。 如需使用的強類型的資源包裝函式的詳細資訊，請參閱 「 產生強類型資源類別 > 一節[Resgen.exe （資源檔產生器）](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)主題。

## <a name="resource-manager-in-the-portable-class-library"></a>可攜式類別庫中的 resource Manager
 在可攜式類別庫專案中，所有資源的存取權都由<xref:System.Resources.ResourceManager>類別。 因為中的型別<xref:System.Resources>命名空間，例如<xref:System.Resources.ResourceReader>和<xref:System.Resources.ResourceSet>，會無法存取從可攜式類別庫專案，它們不會用來存取資源。

 可攜式類別庫專案包含四個<xref:System.Resources.ResourceManager>下表中列出的成員。 這些建構函式和方法可讓您具現化 <xref:System.Resources.ResourceManager> 物件並擷取字串資源。

|`ResourceManager` 成員|描述|
|------------------------------|-----------------|
|<xref:System.Resources.ResourceManager.%23ctor%28System.String%2CSystem.Reflection.Assembly%29>|建立 <xref:System.Resources.ResourceManager> 執行個體以存取所指定組件中的具名資源檔。|
|<xref:System.Resources.ResourceManager.%23ctor%28System.Type%29>|建立對應所指定類型的 <xref:System.Resources.ResourceManager> 執行個體。|
|<xref:System.Resources.ResourceManager.GetString%28System.String%29>|擷取目前文化特性的具名資源。|
|<xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>|擷取屬於所指定文化特性的具名資源。|

 其他排除<xref:System.Resources.ResourceManager>無法從資源檔擷取序列化物件、 非字串資料，以及映像的可攜式類別庫方法從的成員。 若要從可攜式類別庫中使用的資源，您應該以字串形式來儲存物件的所有資料。 例如，您可以將數值轉換成字串以便儲存到資源檔中，並且可以擷取這些字串，然後使用數值資料類型的 `Parse` 或 `TryParse` 方法將它們轉換回數字。 您可以藉由呼叫 <xref:System.Convert.ToBase64String%2A?displayProperty=nameWithType> 方法將影像或其他二進位資料轉換成字串表示，並且藉由呼叫 <xref:System.Convert.FromBase64String%2A?displayProperty=nameWithType> 方法將它們還原為位元組陣列。

## <a name="the-portable-class-library-and-windows-store-apps"></a>可攜式類別庫和 Windows 市集應用程式
 可攜式類別庫專案會儲存在.resx 檔，然後編譯成.resources 檔並在編譯時期內嵌至主要組件或附屬組件中的資源。 另一方面，[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式則需要將資源儲存到 .resw 檔中，這些檔案接著會編譯成單一封裝資源索引 (PRI) 檔。 不過，儘管不相容的檔案格式中，您的可攜式類別庫將運作[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式。

 若要從 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式使用您的類別庫，請在 Windows 市集應用程式專案中加入其參考。 Visual Studio 會以透明的方式從您的組件至.resw 檔擷取資源並用它來產生 PRI 檔案，Windows 執行階段可以從中擷取資源。 在執行階段，Windows 執行階段在可攜式類別庫，執行程式碼，但它會從 PRI 檔案中擷取您的可攜式類別庫資源。

 如果您的可攜式類別庫專案包含當地語系化的資源，您可以使用中樞和支點模型來部署它們，就像您一樣的傳統型應用程式中的程式庫。 若要使用 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式中的主要資源檔和任何當地語系化資源檔，可以加入主要組件的參考。 在編譯時期，Visual Studio 會將您的主要資源檔和所有當地語系化資源檔中的資源擷取至不同的 .resw 檔。 然後會.resw 檔案編譯成單一 PRI 檔案在執行階段存取的 Windows 執行階段。

<a name="NonLoc"></a>
## <a name="example-non-localized-portable-class-library"></a>範例：非當地語系化的可攜式類別庫
 下列簡單、 非當地語系化的可攜式類別庫範例會使用資源，來儲存資料行的名稱，並判斷要為表格式資料保留的字元數。 這個範例會使用名為 LibResources.resx 的檔案儲存下表中列出的字串資源。

|資源名稱|資源值|
|-------------------|--------------------|
|Born|生日|
|BornLength|12|
|Hired|雇用日期|
|HiredLength|12|
|識別碼|識別碼|
|ID.Length|12|
|名稱|名稱|
|NameLength|25|
|標題|員工資料庫|

 下列程式碼定義`UILibrary`類別，會使用名為資源管理員包裝函式`resources`Visual Studio 所產生時**存取修飾詞**檔案變更為**公用**. UILibrary 類別會在必要時剖析字串資料。 。 請注意，該類別位於 `MyCompany.Employees` 命名空間中。

 [!code-csharp[Conceptual.Resources.Portable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/uilibrary.cs#1)]
 [!code-vb[Conceptual.Resources.Portable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/uilibrary.vb#1)]

 下列程式碼將示範如何從主控台模式應用程式存取 `UILibrary` 類別及其資源。 它需要可以加入至 主控台應用程式專案的 UILibrary.dll 的參考。

 [!code-csharp[Conceptual.Resources.Portable#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/program.cs#2)]
 [!code-vb[Conceptual.Resources.Portable#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/module1.vb#2)]

 下列程式碼將示範如何從 `UILibrary`應用程式存取 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 類別及其資源。 它需要可以加入至 Windows 市集應用程式專案的 UILibrary.dll 的參考。

 [!code-csharp[Conceptual.Resources.PortableMetro#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portablemetro/cs/blankpage.xaml.cs#1)]

## <a name="example-localized-portable-class-library"></a>範例：當地語系化的可攜式類別庫
 下列當地語系化的可攜式類別庫範例包含法文 （法國） 和英文 （美國） 文化特性的資源。 英文 （美國） 文化特性是應用程式的預設文化特性;它的資源會顯示在資料表中[上一節](../../../docs/standard/cross-platform/app-resources-for-libraries-that-target-multiple-platforms.md#NonLoc)。 法文 (法國) 文化特性的資源檔命名為 LibResources.fr-FR.resx，並且包含下表所列的字串資源。 `UILibrary` 類別的原始程式碼與前一節中所顯示的內容相同。

|資源名稱|資源值|
|-------------------|--------------------|
|Born|Date de naissance|
|BornLength|20|
|Hired|Date embauché|
|HiredLength|16|
|識別碼|識別碼|
|名稱|Nom|
|標題|Base de données des employés|

 下列程式碼將示範如何從主控台模式應用程式存取 `UILibrary` 類別及其資源。 它需要可以加入至 主控台應用程式專案的 UILibrary.dll 的參考。

 [!code-csharp[Conceptual.Resources.Portable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/program2.cs#3)]
 [!code-vb[Conceptual.Resources.Portable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/module2.vb#3)]

 下列程式碼將示範如何從 `UILibrary`應用程式存取 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 類別及其資源。 它需要可以加入至 Windows 市集應用程式專案的 UILibrary.dll 的參考。 它會使用靜態 `ApplicationLanguages.PrimaryLanguageOverride` 屬性將應用程式的慣用語言設定為法文。

 [!code-csharp[Conceptual.Resources.PortableMetroLoc#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portablemetroloc/cs/blankpage.xaml.cs#1)]
 [!code-vb[Conceptual.Resources.PortableMetroLoc#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portablemetroloc/vb/blankpage.xaml.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Resources.ResourceManager>
- [桌面應用程式中的資源](../../../docs/framework/resources/index.md)
- [封裝和部署資源](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)
