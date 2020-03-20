---
title: 將字型與應用程式一起封裝
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applications [WPF], packaging fonts with
- fonts [WPF], packaging with applications
- typography [WPF], packaging fonts with applications
- packaging fonts with applications [WPF]
ms.assetid: db15ee48-4d24-49f5-8b9d-a64460865286
ms.openlocfilehash: cef2ae26ec4fccd25ca193ba7d441969f36b25a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187082"
---
# <a name="packaging-fonts-with-applications"></a>將字型與應用程式一起封裝
本主題概述了如何向[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]應用程式打包字體。  
  
> [!NOTE]
> 與大部分類型的軟體一樣，字型檔是經由授權而非販售的。 管理字體使用的許可證因供應商而異，但一般來說，大多數許可證（包括涵蓋 Microsoft 提供的應用程式和 Windows 的字體的許可證）不允許將字型內嵌到應用程式中或以其他方式重新分發。 因此，身為開發人員，您的職責是確保對於您內嵌在應用程式中或是以其他方式轉散發的任何字型，您必須有必要的授權權限。  

<a name="introduction_to_packaging_fonts"></a>
## <a name="introduction-to-packaging-fonts"></a>封裝字型簡介  
 您可以輕鬆地將字體打包為[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式中的資源，以顯示使用者介面文本和其他類型的基於文本的內容。 字型可以從應用程式的組件檔中分離出來或內嵌於其中。 您也可以建立僅含資源的字型庫，以供應用程式參考。  
  
 OpenType 和 TrueType® 字體包含一個類型標誌 fsType，指示字型內嵌許可許可權。 不過，此類型旗標只會參考儲存於文件中的內嵌字型，而不會參考內嵌於應用程式中的字型。 您可以通過創建<xref:System.Windows.Media.GlyphTypeface>物件並引用其<xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A>屬性來檢索字體的字型內嵌許可權。 有關 fsType 標誌的詳細資訊，請參閱[OpenType 規範](https://www.microsoft.com/typography/otspec/os2.htm)的"OS/2 和 Windows 指標"部分。  
  
 [Microsoft 排版](https://docs.microsoft.com/typography/)網站包含聯繫資訊，可説明您查找特定字體供應商或查找用於自訂工作的字體供應商。  
  
<a name="adding_fonts_as_content_items"></a>
## <a name="adding-fonts-as-content-items"></a>將字型新增為內容項目  
 您可以將字型新增到您的應用程式，以做為與應用程式組件檔分開的專案內容項目。 這表示內容項目不會內嵌為組件中的資源。 下列專案檔範例示範如何定義內容項目。  
  
```xml  
<Project DefaultTargets="Build"  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <!-- Other project build settings ... -->  
  
  <ItemGroup>  
    <Content Include="Peric.ttf" />  
    <Content Include="Pericl.ttf" />  
  </ItemGroup>  
</Project>  
```  
  
 為了確保應用程式可以在執行階段使用字型，必須可在應用程式的部署目錄中存取字型。 應用程式`<CopyToOutputDirectory>`專案檔案中的元素允許您在生成過程中自動將字體複製到應用程式部署目錄。 下列專案檔範例示範如何將字型複製到部署目錄。  
  
```xml  
<ItemGroup>  
  <Content Include="Peric.ttf">  
    <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>  
  </Content>  
  <Content Include="Pericl.ttf">  
    <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>  
  </Content>  
</ItemGroup>  
```  
  
 下列程式碼範例示範如何參考應用程式的字型以做為內容項目 - 參考的內容項目必須與應用程式的組件檔位於相同的目錄。  
  
 [!code-xaml[FontSnippets#FontPackageSnippet8](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet8)]  
  
<a name="adding_fonts_as_resource_items"></a>
## <a name="adding-fonts-as-resource-items"></a>將字型新增為資源項目  
 您可以將字型新增到您的應用程式，以做為內嵌於您應用程式組件檔中的專案資源項目。 針對資源使用不同的子目錄，可協助組織應用程式的專案檔。 下列專案檔範例示範如何將字型定義為個別子目錄中的資源項目。  
  
```xml  
<Project DefaultTargets="Build"  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <!-- Other project build settings ... -->  
  
  <ItemGroup>  
    <Resource Include="resources\Peric.ttf" />  
    <Resource Include="resources\Pericl.ttf" />  
  </ItemGroup>  
</Project>  
```  
  
> [!NOTE]
> 將字體作為資源添加到應用程式時，請確保設置`<Resource>`元素，而不是應用程式專案檔案中`<EmbeddedResource>`的元素。 不支援`<EmbeddedResource>`生成操作的元素。  
  
 下列標記範例示範如何參考應用程式的字型資源。  
  
 [!code-xaml[FontSnippets#FontPackageSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet1)]  
  
### <a name="referencing-font-resource-items-from-code"></a>從程式碼參考字型資源項目  
 為了從代碼中引用字體資源項，必須提供由兩部分組成的字體資源引用：基本統一資源識別項 （URI）;和字體位置引用。 這些值用作方法的<xref:System.Windows.Media.FontFamily.%23ctor%2A>參數。 以下代碼示例演示如何在稱為`resources`的專案子目錄中引用應用程式的字體資源。  
  
 [!code-csharp[FontSnippets#FontPackageSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet2)]
 [!code-vb[FontSnippets#FontPackageSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet2)]  
  
 基本統一資源識別項 （URI） 可以包括字體資源所在的應用程式子目錄。 在這種情況下，字體位置引用不需要指定目錄，但必須包含一個前導""，`./`該表示字體資源位於基本統一資源識別項 （URI） 指定的同一目錄中。 下列程式碼範例示範參考字型資源項目的替代方法 - 它相當於上述程式碼範例。  
  
 [!code-csharp[FontSnippets#FontPackageSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet5)]
 [!code-vb[FontSnippets#FontPackageSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet5)]  
  
### <a name="referencing-fonts-from-the-same-application-subdirectory"></a>從相同的應用程式子目錄參考字型  
 您可以將應用程式內容與資源檔置於應用程式專案的同一個使用者定義的子目錄內。 下列專案檔範例示範內容頁面和字型資源定義於相同的子目錄中。  
  
```xml  
<ItemGroup>  
  <Page Include="pages\HomePage.xaml" />  
</ItemGroup>  
<ItemGroup>  
  <Resource Include="pages\Peric.ttf" />  
  <Resource Include="pages\Pericl.ttf" />  
</ItemGroup>  
```  
  
 由於應用程式內容和字型位於相同的子目錄，因此，字型參考會相對於應用程式內容。 下列範例示範當字型與應用程式位於相同目錄時，如何參考應用程式的字型資源。  
  
 [!code-xaml[FontSnippets#FontPackageSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml#fontpackagesnippet3)]  
  
 [!code-csharp[FontSnippets#FontPackageSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml.cs#fontpackagesnippet4)]
 [!code-vb[FontSnippets#FontPackageSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/pages/homepage.xaml.vb#fontpackagesnippet4)]  
  
### <a name="enumerating-fonts-in-an-application"></a>列舉應用程式中的字型  
 要將字體枚舉為應用程式中的資源項，請使用 或<xref:System.Windows.Media.Fonts.GetFontFamilies%2A><xref:System.Windows.Media.Fonts.GetTypefaces%2A>方法。 下面的示例演示如何使用 方法<xref:System.Windows.Media.Fonts.GetFontFamilies%2A>從應用程式字體位置返回<xref:System.Windows.Media.FontFamily>物件集合。 在此案例中，應用程式包含名為 "resources"的子目錄。  
  
 [!code-csharp[FontSnippets#FontsSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet3)]
 [!code-vb[FontSnippets#FontsSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet3)]  
  
 下面的示例演示如何使用 方法<xref:System.Windows.Media.Fonts.GetTypefaces%2A>從應用程式字體位置返回<xref:System.Windows.Media.Typeface>物件集合。 在此案例中，應用程式包含名為 "resources"的子目錄。  
  
 [!code-csharp[FontSnippets#FontsSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet7)]
 [!code-vb[FontSnippets#FontsSnippet7](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet7)]  
  
<a name="creating_a_font_resource_library"></a>
## <a name="creating-a-font-resource-library"></a>建立字型資源程式庫  
 您可以建立僅含資源的程式庫 (其中僅包含字型) - 這種類型的程式庫專案不會包含任何程式碼。 建立僅含資源的程式庫是從使用資源的應用程式程式碼中減少資源的常見技術。 這也可讓程式庫組件包含於多個應用程式專案中。 下列專案檔範例顯示僅含資源的程式庫專案的主要部分。  
  
```xml  
<PropertyGroup>  
  <AssemblyName>FontLibrary</AssemblyName>  
  <OutputType>library</OutputType>  
  ...  
</PropertyGroup>  
...  
<ItemGroup>  
  <Resource Include="Kooten.ttf" />  
  <Resource Include="Pesca.ttf" />  
</ItemGroup  
```  
  
### <a name="referencing-a-font-in-a-resource-library"></a>參考資源程式庫中的字型  
 若要從您的應用程式參考資源程式庫中的字型，您必須在程式庫組件名稱前面加上字型參考。 在此案例中，字型資源組件是 "FontLibrary"。 若要將組件內的組件名稱與參考分隔開來，請使用 ';' 字元。 加入 "Component" 關鍵字，後面緊接著對字型名稱的參考，即可完成對字型程式庫資源的完整參考。 下列程式碼範例示範如何參考資源程式庫組件中的字型。  
  
 [!code-xaml[OpenTypeFontsSample#OpenTypeFontsSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontsSample/CS/Kootenay.xaml#opentypefontssample1)]  
  
> [!NOTE]
> 此 SDK 包含一組可用於[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式的示例 OpenType 字型。 字型定義於僅含資源的程式庫中。 有關詳細資訊，請參閱[示例打開字體包](sample-opentype-font-pack.md)。  
  
<a name="limitations_on_font_usage"></a>
## <a name="limitations-on-font-usage"></a>字型使用限制  
 下面的清單描述了在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式中字體的打包和使用的幾個限制：  
  
- **字型內嵌權限位元：** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式不會檢查或強制執行任何字型內嵌權限位元。 有關詳細資訊，請參閱[Introduction_to_Packing字體](#introduction_to_packaging_fonts)部分。  
  
- **源地字體：**[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式不允許字體引用 HTTP 或 ftp 統一資源識別項 （URI）。  
  
- **使用包的絕對 URI：標記法：**[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式不允許使用"pack："以程式設計<xref:System.Windows.Media.FontFamily>方式創建物件，作為對字體的絕對統一資源識別項 （URI） 引用的一部分。 例如，`"pack://application:,,,/resources/#Pericles Light"`不正確字體引用。  
  
- **自動字型內嵌︰** 在設計階段期間，不支援搜尋應用程式所使用的字型，也不支援自動將字型內嵌於應用程式的資源中。  
  
- **字型子集︰** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式不支援為非固定文件建立字型子集。  
  
- 萬一其中含有不正確的參考，應用程式就會回復以使用可用字型。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Documents.Typography>
- <xref:System.Windows.Media.FontFamily>
- [Microsoft 印刷︰連結、新聞和連絡人 (英文)](https://docs.microsoft.com/typography/)
- [OpenType 規格 (英文)](https://www.microsoft.com/typography/otspec/)
- [OpenType 字型功能](opentype-font-features.md)
- [範例 OpenType 字型套件](sample-opentype-font-pack.md)
