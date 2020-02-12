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
ms.openlocfilehash: 3bf475117a85c2fced260dcc9460d55cd7007277
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77123658"
---
# <a name="app-resources-for-libraries-that-target-multiple-platforms"></a>以多平台為目標之函式庫的應用程式資源
您可以使用 .NET Framework 的[可移植類別庫](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)專案類型，以確保您的類別庫中的資源可從多個平臺存取。 此專案類型在 Visual Studio 2012 中提供，並以 .NET Framework Class Library 的可移植子集為目標。 使用可移植的類別庫，可確保您的程式庫可以從桌面應用程式、Silverlight 應用程式、Windows Phone 應用程式和 Windows 8.x 存放區應用程式存取。

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 「便攜類別庫」專案只會在應用程式可用的 <xref:System.Resources> 命名空間中，提供非常有限的類型子集，但它可讓您使用 <xref:System.Resources.ResourceManager> 類別來取出資源。 不過，如果您要使用 Visual Studio 建立應用程式，則應該使用 Visual Studio 所建立的強類型包裝函式，而不要直接使用 <xref:System.Resources.ResourceManager> 類別。

 若要在 Visual Studio 中建立強型別包裝函式，請在 Visual Studio 資源設計工具中將主要資源檔的**存取修飾**詞設定為**Public**。 這樣會建立包含強類型 ResourceManager 包裝函式的 [resourceFileName].designer.cs 或 [resourceFileName].designer.vb 檔。 如需使用強型別資源包裝函式的詳細資訊，請參閱[resgen.exe （資源檔](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)產生器）主題中的「產生強型別資源類別」一節。

## <a name="resource-manager-in-the-portable-class-library"></a>可移植類別庫中的 Resource Manager
 在可移植的類別庫專案中，對資源的所有存取都是由 <xref:System.Resources.ResourceManager> 類別處理。 因為 <xref:System.Resources> 命名空間中的類型（例如 <xref:System.Resources.ResourceReader> 和 <xref:System.Resources.ResourceSet>）無法從可移植的類別庫專案存取，所以無法用來存取資源。

 可移植的類別庫專案包含下表所列的四個 <xref:System.Resources.ResourceManager> 成員。 這些建構函式和方法可讓您具現化 <xref:System.Resources.ResourceManager> 物件並擷取字串資源。

|`ResourceManager` 成員|描述|
|------------------------------|-----------------|
|<xref:System.Resources.ResourceManager.%23ctor%28System.String%2CSystem.Reflection.Assembly%29>|建立 <xref:System.Resources.ResourceManager> 執行個體以存取所指定組件中的具名資源檔。|
|<xref:System.Resources.ResourceManager.%23ctor%28System.Type%29>|建立對應所指定類型的 <xref:System.Resources.ResourceManager> 執行個體。|
|<xref:System.Resources.ResourceManager.GetString%28System.String%29>|擷取目前文化特性的具名資源。|
|<xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>|擷取屬於所指定文化特性的具名資源。|

 從可移植類別庫排除其他 <xref:System.Resources.ResourceManager> 成員，表示無法從資源檔抓取序列化物件、非字串資料和影像。 若要使用可移植類別庫中的資源，您應該以字串形式儲存所有物件資料。 例如，您可以將數值轉換成字串以便儲存到資源檔中，並且可以擷取這些字串，然後使用數值資料類型的 `Parse` 或 `TryParse` 方法將它們轉換回數字。 您可以藉由呼叫 <xref:System.Convert.ToBase64String%2A?displayProperty=nameWithType> 方法將影像或其他二進位資料轉換成字串表示，並且藉由呼叫 <xref:System.Convert.FromBase64String%2A?displayProperty=nameWithType> 方法將它們還原為位元組陣列。

## <a name="the-portable-class-library-and-windows-store-apps"></a>可移植的類別庫和 Windows Store 應用程式
 可移植的類別庫專案會將資源儲存在 .resx 檔案中，然後編譯為 .resources 檔案，並內嵌在主要元件中，或是在編譯時期的附屬元件中。 另一方面，Windows 8.x 的存放區應用程式則需要將資源儲存在 .resw 檔案中，然後再編譯成單一套件資源索引（PRI）檔案。 不過，儘管不相容的檔案格式，您的可移植類別庫仍可在 Windows 8.x 存放應用程式中使用。

 若要從 Windows 8.x 存放區應用程式取用您的類別庫，請在您的 Windows Store 應用程式專案中新增對它的參考。 Visual Studio 會以透明方式將元件中的資源解壓縮至 .resw 檔案，並使用它來產生 PRI 檔案，讓 Windows 執行階段可以從中解壓縮資源。 在執行時間，Windows 執行階段會執行您的可移植類別庫中的程式碼，但它會從 PRI 檔案中抓取您的可移植類別庫資源。

 如果您的可移植類別庫專案包含當地語系化的資源，您就可以使用中樞和輪輻模型來部署它們，就像您在桌面應用程式中的程式庫一樣。 若要在您的 Windows 8.x 存放區應用程式中使用您的主要資源檔和任何當地語系化的資源檔，您可以加入主要元件的參考。 在編譯時期，Visual Studio 會將您的主要資源檔和所有當地語系化資源檔中的資源擷取至不同的 .resw 檔。 然後，它會將 .resw 檔案編譯成 Windows 執行階段在執行時間存取的單一 PRI 檔案。

<a name="NonLoc"></a>
## <a name="example-non-localized-portable-class-library"></a>範例：非當地語系化的可移植類別庫
 下列簡單、非當地語系化的可移植類別庫範例會使用資源來儲存資料行的名稱，並決定要為表格式資料保留的字元數。 這個範例會使用名為 LibResources.resx 的檔案儲存下表中列出的字串資源。

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

 下列程式碼會定義一個 `UILibrary` 類別，它會在檔案的**存取修飾**詞變更為**Public**時，使用 Visual Studio 所產生的 Resource Manager `resources` 包裝函式。 UILibrary 類別會在必要時剖析字串資料。 。 請注意，該類別位於 `MyCompany.Employees` 命名空間中。

 [!code-csharp[Conceptual.Resources.Portable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/uilibrary.cs#1)]
 [!code-vb[Conceptual.Resources.Portable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/uilibrary.vb#1)]

 下列程式碼將示範如何從主控台模式應用程式存取 `UILibrary` 類別及其資源。 它需要將 Uilibrary.dll 的參考新增至主控台應用程式專案。

 [!code-csharp[Conceptual.Resources.Portable#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/program.cs#2)]
 [!code-vb[Conceptual.Resources.Portable#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/module1.vb#2)]

 下列程式碼說明如何從 Windows 8.x 存放區應用程式存取 `UILibrary` 類別及其資源。 它需要將 Uilibrary.dll 的參考加入 Windows Store 應用程式專案中。

 [!code-csharp[Conceptual.Resources.PortableMetro#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portablemetro/cs/blankpage.xaml.cs#1)]

## <a name="example-localized-portable-class-library"></a>範例：當地語系化的可移植類別庫
 下列當地語系化的可移植類別庫範例包含法文（法國）和英文（美國）文化特性的資源。 英文（美國）文化特性是應用程式的預設文化特性;其資源會顯示在[上一節](../../../docs/standard/cross-platform/app-resources-for-libraries-that-target-multiple-platforms.md#NonLoc)的表格中。 法文 (法國) 文化特性的資源檔命名為 LibResources.fr-FR.resx，並且包含下表所列的字串資源。 `UILibrary` 類別的原始程式碼與前一節中所顯示的內容相同。

|資源名稱|資源值|
|-------------------|--------------------|
|Born|Date de naissance|
|BornLength|20|
|Hired|Date embauché|
|HiredLength|16|
|ID|ID|
|名稱|Nom|
|標題|Base de données des employés|

 下列程式碼將示範如何從主控台模式應用程式存取 `UILibrary` 類別及其資源。 它需要將 Uilibrary.dll 的參考新增至主控台應用程式專案。

 [!code-csharp[Conceptual.Resources.Portable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/program2.cs#3)]
 [!code-vb[Conceptual.Resources.Portable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/module2.vb#3)]

 下列程式碼說明如何從 Windows 8.x 存放區應用程式存取 `UILibrary` 類別及其資源。 它需要將 Uilibrary.dll 的參考加入 Windows Store 應用程式專案中。 它會使用靜態 `ApplicationLanguages.PrimaryLanguageOverride` 屬性將應用程式的慣用語言設定為法文。

 [!code-csharp[Conceptual.Resources.PortableMetroLoc#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portablemetroloc/cs/blankpage.xaml.cs#1)]
 [!code-vb[Conceptual.Resources.PortableMetroLoc#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portablemetroloc/vb/blankpage.xaml.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Resources.ResourceManager>
- [桌面應用程式中的資源](../../../docs/framework/resources/index.md)
- [封裝和部署資源](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)
