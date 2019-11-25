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
ms.openlocfilehash: b32c2e354ea48e25ddb0aa561eb576cbfd89e3fb
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204746"
---
# <a name="app-resources-for-libraries-that-target-multiple-platforms"></a>以多平台為目標之函式庫的應用程式資源
You can use the .NET Framework [Portable Class Library](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) project type to ensure that resources in your class libraries can be accessed from multiple platforms. This project type is available in Visual Studio 2012 and targets the portable subset of the .NET Framework class library. Using  a Portable Class Library ensures that your library can be accessed from desktop apps, Silverlight apps, Windows Phone apps, and Windows 8.x Store apps.

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 The Portable Class Library project makes only a very limited subset of the types in the <xref:System.Resources> namespace available to your application, but it does allow you to use the <xref:System.Resources.ResourceManager> class to retrieve resources. 不過，如果您要使用 Visual Studio 建立應用程式，則應該使用 Visual Studio 所建立的強類型包裝函式，而不要直接使用 <xref:System.Resources.ResourceManager> 類別。

 To create a strongly typed wrapper in Visual Studio, set the main resource file's **Access Modifier** in the Visual Studio Resource Designer to **Public**. 這樣會建立包含強類型 ResourceManager 包裝函式的 [resourceFileName].designer.cs 或 [resourceFileName].designer.vb 檔。 For more information about using a strongly typed resource wrapper, see the "Generating a Strongly Typed Resource Class" section in the [Resgen.exe (Resource File Generator)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) topic.

## <a name="resource-manager-in-the-portable-class-library"></a>Resource Manager in the Portable Class Library
 In a Portable Class Library project, all access to resources is handled by the <xref:System.Resources.ResourceManager> class. Because types in the <xref:System.Resources> namespace, such as <xref:System.Resources.ResourceReader> and <xref:System.Resources.ResourceSet>, are not accessible from a Portable Class Library project, they cannot be used to access resources.

 The Portable Class Library project includes the four <xref:System.Resources.ResourceManager> members listed in the following table. 這些建構函式和方法可讓您具現化 <xref:System.Resources.ResourceManager> 物件並擷取字串資源。

|`ResourceManager` 成員|描述|
|------------------------------|-----------------|
|<xref:System.Resources.ResourceManager.%23ctor%28System.String%2CSystem.Reflection.Assembly%29>|建立 <xref:System.Resources.ResourceManager> 執行個體以存取所指定組件中的具名資源檔。|
|<xref:System.Resources.ResourceManager.%23ctor%28System.Type%29>|建立對應所指定類型的 <xref:System.Resources.ResourceManager> 執行個體。|
|<xref:System.Resources.ResourceManager.GetString%28System.String%29>|擷取目前文化特性的具名資源。|
|<xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>|擷取屬於所指定文化特性的具名資源。|

 The exclusion of other <xref:System.Resources.ResourceManager> members from the Portable Class Library means that serialized objects, non-string data, and images cannot be retrieved from a resource file. To use resources from a Portable Class Library, you should store all  object data in string form. 例如，您可以將數值轉換成字串以便儲存到資源檔中，並且可以擷取這些字串，然後使用數值資料類型的 `Parse` 或 `TryParse` 方法將它們轉換回數字。 您可以藉由呼叫 <xref:System.Convert.ToBase64String%2A?displayProperty=nameWithType> 方法將影像或其他二進位資料轉換成字串表示，並且藉由呼叫 <xref:System.Convert.FromBase64String%2A?displayProperty=nameWithType> 方法將它們還原為位元組陣列。

## <a name="the-portable-class-library-and-windows-store-apps"></a>The Portable Class Library and Windows Store Apps
 Portable Class Library projects store resources in .resx files, which are then compiled into .resources files and embedded in the main assembly or in satellite assemblies at compile time. Windows 8.x Store apps, on the other hand, require resources to be stored in .resw files, which are then compiled into a single package resource index (PRI) file. However, despite the incompatible file formats, your Portable Class Library will work in a Windows 8.x Store app.

 To consume your class library from a Windows 8.x Store app, add a reference to it in your Windows Store app project. Visual Studio will transparently extract the resources from your assembly into a .resw file and use it to generate a PRI file from which the Windows Runtime can extract resources. At run time, the Windows Runtime executes the code in your Portable Class Library, but it retrieves your Portable Class Library's resources from the PRI file.

 If your Portable Class Library project includes localized resources, you use the hub-and-spoke model to deploy them just as you would for a library in a desktop app. To consume your main resource file and any localized resource files in your Windows 8.x Store app, you add a reference to the main assembly. 在編譯時期，Visual Studio 會將您的主要資源檔和所有當地語系化資源檔中的資源擷取至不同的 .resw 檔。 It then compiles the .resw files into a single PRI file that the Windows Runtime accesses at run time.

<a name="NonLoc"></a>
## <a name="example-non-localized-portable-class-library"></a>Example: Non-Localized Portable Class Library
 The following simple, non-localized Portable Class Library example uses resources to store the names of columns and to determine the number of characters to reserve for tabular data. 這個範例會使用名為 LibResources.resx 的檔案儲存下表中列出的字串資源。

|資源名稱|資源值|
|-------------------|--------------------|
|Born|生日|
|BornLength|12|
|Hired|雇用日期|
|HiredLength|12|
|識別碼|識別碼|
|ID.Length|12|
|[屬性]|[屬性]|
|NameLength|25|
|標題|員工資料庫|

 The following code defines a `UILibrary` class that uses the Resource Manager wrapper named `resources` generated by Visual Studio when the **Access Modifier** for the file is changed to **Public**. UILibrary 類別會在必要時剖析字串資料。 執行個體時提供 SQL Server 登入。 請注意，該類別位於 `MyCompany.Employees` 命名空間中。

 [!code-csharp[Conceptual.Resources.Portable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/uilibrary.cs#1)]
 [!code-vb[Conceptual.Resources.Portable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/uilibrary.vb#1)]

 下列程式碼將示範如何從主控台模式應用程式存取 `UILibrary` 類別及其資源。 It requires a reference to UILibrary.dll to be added to the console app project.

 [!code-csharp[Conceptual.Resources.Portable#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/program.cs#2)]
 [!code-vb[Conceptual.Resources.Portable#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/module1.vb#2)]

 The following code illustrates how the `UILibrary` class and its resources can be accessed from a Windows 8.x Store app. It requires a reference to UILibrary.dll to be added to the Windows Store app project.

 [!code-csharp[Conceptual.Resources.PortableMetro#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portablemetro/cs/blankpage.xaml.cs#1)]

## <a name="example-localized-portable-class-library"></a>Example: Localized Portable Class Library
 The following localized Portable Class Library example includes resources for the French (France) and English (United States) cultures. The English (United States) culture is the app's default culture; its resources are shown in the table in the [previous section](../../../docs/standard/cross-platform/app-resources-for-libraries-that-target-multiple-platforms.md#NonLoc). 法文 (法國) 文化特性的資源檔命名為 LibResources.fr-FR.resx，並且包含下表所列的字串資源。 `UILibrary` 類別的原始程式碼與前一節中所顯示的內容相同。

|資源名稱|資源值|
|-------------------|--------------------|
|Born|Date de naissance|
|BornLength|20|
|Hired|Date embauché|
|HiredLength|16|
|識別碼|識別碼|
|[屬性]|Nom|
|標題|Base de données des employés|

 下列程式碼將示範如何從主控台模式應用程式存取 `UILibrary` 類別及其資源。 It requires a reference to UILibrary.dll to be added to the console app project.

 [!code-csharp[Conceptual.Resources.Portable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/program2.cs#3)]
 [!code-vb[Conceptual.Resources.Portable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/module2.vb#3)]

 The following code illustrates how the `UILibrary` class and its resources can be accessed from a Windows 8.x Store app. It requires a reference to UILibrary.dll to be added to the Windows Store app project. 它會使用靜態 `ApplicationLanguages.PrimaryLanguageOverride` 屬性將應用程式的慣用語言設定為法文。

 [!code-csharp[Conceptual.Resources.PortableMetroLoc#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portablemetroloc/cs/blankpage.xaml.cs#1)]
 [!code-vb[Conceptual.Resources.PortableMetroLoc#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portablemetroloc/vb/blankpage.xaml.vb#1)]  
  
## <a name="see-also"></a>請參閱

- <xref:System.Resources.ResourceManager>
- [桌面應用程式中的資源](../../../docs/framework/resources/index.md)
- [封裝和部署資源](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)
