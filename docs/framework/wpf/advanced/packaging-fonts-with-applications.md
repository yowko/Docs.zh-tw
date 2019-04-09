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
ms.openlocfilehash: fb91d4b413db512021b90f0d4ba3049fe7333601
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59123784"
---
# <a name="packaging-fonts-with-applications"></a>將字型與應用程式一起封裝
本主題提供的概觀與封裝字型您[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]應用程式。  
  
> [!NOTE]
>  與大部分類型的軟體一樣，字型檔是經由授權而非販售的。 控制字型使用的授權不同廠商但一般大部分的授權，包括各家[!INCLUDE[TLA#tla_ms#initcap](../../../../includes/tlasharptla-mssharpinitcap-md.md)]提供與應用程式和[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]，不允許將字型內嵌在應用程式或功能重新分配。 因此，身為開發人員，您的職責是確保對於您內嵌在應用程式中或是以其他方式轉散發的任何字型，您必須有必要的授權權限。  

<a name="introduction_to_packaging_fonts"></a>   
## <a name="introduction-to-packaging-fonts"></a>封裝字型簡介  
 您可以輕鬆地將字型封裝內的資源為您[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式顯示使用者介面文字與其他類型的文字為基礎之內容。 字型可以從應用程式的組件檔中分離出來或內嵌於其中。 您也可以建立僅含資源的字型庫，以供應用程式參考。  
  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 和[!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)]字型包含類型旗標 fsType，表示字型的字型內嵌授權權限。 不過，此類型旗標只會參考儲存於文件中的內嵌字型，而不會參考內嵌於應用程式中的字型。 您可以擷取內嵌字型的權限，藉由建立字型<xref:System.Windows.Media.GlyphTypeface>物件，並參考其<xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A>屬性。 請參閱 「 OS/2 和 Windows 度量 」 一節[OpenType 規格](https://www.microsoft.com/typography/otspec/os2.htm)如需 fsType 旗標。  
  
 [Microsoft 印刷](https://docs.microsoft.com/typography/)Web 站台都包含可協助您找出特定字型供應商，或尋找自訂工作的字型的供應商的連絡資訊。  
  
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
  
 為了確保應用程式可以在執行階段使用字型，必須可在應用程式的部署目錄中存取字型。 `<CopyToOutputDirectory>`應用程式的專案檔中的項目可讓您自動將字型複製到應用程式部署目錄中，建置程序期間變更。 下列專案檔範例示範如何將字型複製到部署目錄。  
  
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
>  當您將字型當做資源新增您的應用程式時，請確定您要設定`<Resource>`項目，而非`<EmbeddedResource>`您的應用程式專案檔中的項目。 `<EmbeddedResource>`不支援建置動作的項目。  
  
 下列標記範例示範如何參考應用程式的字型資源。  
  
 [!code-xaml[FontSnippets#FontPackageSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet1)]  
  
### <a name="referencing-font-resource-items-from-code"></a>從程式碼參考字型資源項目  
 若要從程式碼參考字型資源項目，您必須提供兩部分的字型資源參考︰ 基底[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]; 以及字型位置參考。 使用這些值做為參數<xref:System.Windows.Media.FontFamily.%23ctor%2A>方法。 下列程式碼範例示範如何參考呼叫的專案子目錄中的應用程式的字型資源`resources`。  
  
 [!code-csharp[FontSnippets#FontPackageSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet2)]
 [!code-vb[FontSnippets#FontPackageSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet2)]  
  
 基底[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]可以包含字型資源所在的 [application] 子目錄。 在此情況下，就不需要指定的目錄中，字型位置參考，但必須包含前置字元 」`./`"，表示字型資源位於相同的目錄指定的基底[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]。 下列程式碼範例示範參考字型資源項目的替代方法 - 它相當於上述程式碼範例。  
  
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
 若要列舉字型做為應用程式中的資源項目，請使用<xref:System.Windows.Media.Fonts.GetFontFamilies%2A>或<xref:System.Windows.Media.Fonts.GetTypefaces%2A>方法。 下列範例示範如何使用<xref:System.Windows.Media.Fonts.GetFontFamilies%2A>方法傳回的集合<xref:System.Windows.Media.FontFamily>從應用程式字型位置的物件。 在此案例中，應用程式包含名為 "resources"的子目錄。  
  
 [!code-csharp[FontSnippets#FontsSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet3)]
 [!code-vb[FontSnippets#FontsSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet3)]  
  
 下列範例示範如何使用<xref:System.Windows.Media.Fonts.GetTypefaces%2A>方法傳回的集合<xref:System.Windows.Media.Typeface>從應用程式字型位置的物件。 在此案例中，應用程式包含名為 "resources"的子目錄。  
  
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
>  此 SDK 包含一組範例[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]您可以搭配使用的字型[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式。 字型定義於僅含資源的程式庫中。 如需詳細資訊，請參閱[範例 OpenType 字型套件](sample-opentype-font-pack.md)。  
  
<a name="limitations_on_font_usage"></a>   
## <a name="limitations-on-font-usage"></a>字型使用限制  
 下列清單描述上的封裝和使用字型中的幾項限制[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式：  
  
-   **字型內嵌權限位元：**[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式不會檢查或強制執行任何字型內嵌權限位元。 請參閱[封裝字型簡介](#introduction_to_packaging_fonts)節的詳細資訊。  
  
-   **原始字型的網站：** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式不允許 http 或 ftp 的字型參考[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]。  
  
-   **使用組件的絕對 URI： 標記法：** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式不允許您建立<xref:System.Windows.Media.FontFamily>物件以程式設計方式使用 「 組件:"一部分絕對[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]字型參考。 比方說，`"pack://application:,,,/resources/#Pericles Light"`是無效的字型參考。  
  
-   **自動字型內嵌：** 在設計階段期間沒有支援搜尋的應用程式使用的字型和自動將字型內嵌在應用程式的資源。  
  
-   **字型子集︰**[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式不支援為非固定文件建立字型子集。  
  
-   萬一其中含有不正確的參考，應用程式就會回復以使用可用字型。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Documents.Typography>
- <xref:System.Windows.Media.FontFamily>
- [Microsoft 印刷︰連結、 新聞和連絡人](https://docs.microsoft.com/typography/)
- [OpenType 規格](https://www.microsoft.com/typography/otspec/)
- [OpenType 字型功能](opentype-font-features.md)
- [範例 OpenType 字型套件](sample-opentype-font-pack.md)
