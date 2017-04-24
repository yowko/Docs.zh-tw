---
title: "將字型與應用程式一起封裝 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "應用程式, 封裝字型"
  - "字型, 與應用程式一起封裝"
  - "將字型與應用程式一起封裝"
  - "印刷樣式, 將字型與應用程式一起封裝"
ms.assetid: db15ee48-4d24-49f5-8b9d-a64460865286
caps.latest.revision: 29
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 25
---
# 將字型與應用程式一起封裝
本主題提供如何將字型與 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 應用程式一起封裝的概觀。  
  
> [!NOTE]
>  與大部分類型的軟體一樣，字型檔是經由授權而非販售的。  控制字型使用的授權隨著各家廠商而異，但一般大部分的授權 \(包含 [!INCLUDE[TLA#tla_ms#initcap](../../../../includes/tlasharptla-mssharpinitcap-md.md)] 隨附應用程式和 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] 所提供字型的授權\)，都不允許將字型內嵌在應用程式中或是以其他方式轉散發。  因此，身為開發人員，您的職責是確保對於您內嵌在應用程式中或是以其他方式轉散發的任何字型，您必須有必要的授權權利。  
  
   
  
<a name="introduction_to_packaging_fonts"></a>   
## 封裝字型簡介  
 您可以輕鬆將字型封裝為 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式內的資源，以顯示使用者介面文字和其他類型的文字內容。  字型可以內嵌在應用程式組件檔內，也可以分離出來。  您也可以建立僅含資源的字型程式庫，供應用程式參考。  
  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 和 [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)] 字型包含一個類型旗標 fsType，用於表示該字型的字型內嵌授權權利。  然而，這個類型旗標僅代表儲存在文件中的內嵌字型，而不代表內嵌在應用程式中的字型。  藉由建立 <xref:System.Windows.Media.GlyphTypeface> 物件和參考其 <xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A> 屬性，您可以擷取字型的字型內嵌權利。  如需 fsType 旗標的詳細資訊，請參閱 [OpenType 規格](http://www.microsoft.com/typography/otspec/os2.htm)中的＜OS\/2 和 Windows 度量資訊＞小節 \(英文\)。  
  
 [Microsoft 印刷樣式](http://www.microsoft.com/typography/links/) 網站 \(英文\) 包含的連絡資訊，可以協助您找出特定字型廠商或找到可以為您自訂字型作業的字型廠商。  
  
<a name="adding_fonts_as_content_items"></a>   
## 將字型加入為內容項目  
 您可以在應用程式中加入字型做為專案內容項目，從應用程式的組件檔分離出來。  這代表內容項目不會內嵌為組件內的資源。  下列專案檔範例顯示如何定義內容項目。  
  
```  
<Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <!-- Other project build settings ... -->  
  
  <ItemGroup>  
    <Content Include="Peric.ttf" />  
    <Content Include="Pericl.ttf" />  
  </ItemGroup>  
</Project>  
```  
  
 為了確保應用程式可以在執行階段使用字型，在應用程式部署目錄中必須可以存取字型。  應用程式專案檔中的 `<CopyToOutputDirectory>` 項目，可以讓您在建置處理期間自動將字型複製到應用程式部署目錄中。  下列專案檔範例顯示如何將字型複製到部署目錄。  
  
```  
<ItemGroup>  
  <Content Include="Peric.ttf">  
    <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>  
  </Content>  
  <Content Include="Pericl.ttf">  
    <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>  
  </Content>  
</ItemGroup>  
```  
  
 下列程式碼範例顯示如何將應用程式字型參考為內容項目，參考的內容項目必須與應用程式組件檔位於相同目錄。  
  
 [!code-xml[FontSnippets#FontPackageSnippet8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet8)]  
  
<a name="adding_fonts_as_resource_items"></a>   
## 將字型加入為資源項目  
 您可以在應用程式中加入字型做為專案資源項目，內嵌在應用程式的組件檔中。  針對資源使用不同的子目錄有助於組織應用程式專案檔。  下列專案檔範例顯示如何將字型定義為在不同子目錄中的資源項目。  
  
```  
<Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <!-- Other project build settings ... -->  
  
  <ItemGroup>  
    <Resource Include="resources\Peric.ttf" />  
    <Resource Include="resources\Pericl.ttf" />  
  </ItemGroup>  
</Project>  
```  
  
> [!NOTE]
>  當您在應用程式中加入字型做為資源時，請確定您在應用程式專案檔中設定的是 `<Resource>` 項目，而非 `<EmbeddedResource>` 項目。  `<EmbeddedResource>` 項目的建置動作是不受支援的。  
  
 下列標記範例顯示如何參考應用程式的字型資源。  
  
 [!code-xml[FontSnippets#FontPackageSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet1)]  
  
### 從程式碼參考字型資源項目  
 為了要從程式碼參考字型資源，您必須提供由兩個部分組成的字型資源參考：基底[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] 和字型位置參考。  這些值會用來做為 <xref:System.Windows.Media.FontFamily.%23ctor%2A> 方法的參數。  下列程式碼範例顯示如何參考稱為 `resources` 的專案子目錄中的應用程式字型資源。  
  
 [!code-csharp[FontSnippets#FontPackageSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet2)]
 [!code-vb[FontSnippets#FontPackageSnippet2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet2)]  
  
 基底[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] 可以包含字型資源所在的應用程式子目錄。  在這個情況下，字型位置參考不需要指定目錄，但應該要包含前置的 "`./`"，代表字型資源位於基底[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] 所指定的目錄中。  下列程式碼範例顯示另一種字型資源項目的參考方式，這跟前述程式碼範例是相等的。  
  
 [!code-csharp[FontSnippets#FontPackageSnippet5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet5)]
 [!code-vb[FontSnippets#FontPackageSnippet5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet5)]  
  
### 從相同應用程式子目錄參考字型  
 您可以在相同的應用程式專案的使用者定義子目錄內，同時置放應用程式內容和資源檔。  下列專案檔範例顯示在相同子目錄中定義的內容頁面和字型資源。  
  
```  
<ItemGroup>  
  <Page Include="pages\HomePage.xaml" />  
</ItemGroup>  
<ItemGroup>  
  <Resource Include="pages\Peric.ttf" />  
  <Resource Include="pages\Pericl.ttf" />  
</ItemGroup>  
```  
  
 因為應用程式內容和字型位於相同子目錄中，字型參考是相對於應用程式內容的。  下列範例顯示當字型和應用程式位於相同目錄中時，如何參考應用程式字型資源。  
  
 [!code-xml[FontSnippets#FontPackageSnippet3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml#fontpackagesnippet3)]  
  
 [!code-csharp[FontSnippets#FontPackageSnippet4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml.cs#fontpackagesnippet4)]
 [!code-vb[FontSnippets#FontPackageSnippet4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/pages/homepage.xaml.vb#fontpackagesnippet4)]  
  
### 在應用程式中列舉字型  
 若要在應用程式中列舉字型做為資源項目，請使用 <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> 或 <xref:System.Windows.Media.Fonts.GetTypefaces%2A> 方法。  下列範例顯示如何使用 <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> 方法，以從應用程式字型位置傳回 <xref:System.Windows.Media.FontFamily> 物件的集合。  在這個案例中，應用程式包含名為 "resources" 的子目錄。  
  
 [!code-csharp[FontSnippets#FontsSnippet3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet3)]
 [!code-vb[FontSnippets#FontsSnippet3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet3)]  
  
 下列範例顯示如何使用 <xref:System.Windows.Media.Fonts.GetTypefaces%2A> 方法，以從應用程式字型位置傳回 <xref:System.Windows.Media.Typeface> 物件的集合。  在這個案例中，應用程式包含名為 "resources" 的子目錄。  
  
 [!code-csharp[FontSnippets#FontsSnippet7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet7)]
 [!code-vb[FontSnippets#FontsSnippet7](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet7)]  
  
<a name="creating_a_font_resource_library"></a>   
## 建立字型資源程式庫  
 您可以建立只包含字型的僅含資源程式庫，這類型的程式庫專案沒有程式碼。  對於降低資源與使用該資源的應用程式程式碼間的耦合，建立僅含資源程式庫是一個常用的技巧。  這樣做也可以讓程式庫組件包含在多個應用程式專案中。  下列專案檔範例顯示僅含資源程式庫專案的主要部分。  
  
```  
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
  
### 參考資源程式庫中的字型  
 若要從應用程式參考資源程式庫中的字型，必須使用程式庫組件名稱做為字型參考的前置字元。  在這個案例中，字型資源組件是 "FontLibrary"。  若要區隔組件名稱與組件內的資源，請使用 ';' 字元。  在字型名稱的參考後加入 "Component" 關鍵字，即完成對字型程式庫資源的完整參考。  下列程式碼範例顯示如何參考資源程式庫組件中的字型。  
  
 [!code-xml[OpenTypeFontsSample#OpenTypeFontsSample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontsSample/CS/Kootenay.xaml#opentypefontssample1)]  
  
> [!NOTE]
>  本 SDK 包含一組範例 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 字型，可以供您用於 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式。  這些字型是定義在僅含資源程式庫中。  如需詳細資訊，請參閱[範例 OpenType 字型套件](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md)。  
  
<a name="limitations_on_font_usage"></a>   
## 字型使用的限制  
 下列清單描述在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式中封裝和使用字型的數個限制：  
  
-   **字型內嵌使用權限位元**：[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式不會檢查或強制任何的字型內嵌使用權限位元。  如需詳細資訊，請參閱[封裝字型簡介](#introduction_to_packaging_fonts)一節。  
  
-   **來源網站字型**：[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式不允許對於 http 或 ftp [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] 的字型參考。  
  
-   **使用 pack: 標記法的絕對 URI**：[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式不允許您使用 "pack:" 做為字型的絕對[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] 參考的一部分，以程式設計方式建立 <xref:System.Windows.Media.FontFamily> 物件。  舉例來說，`"pack://application:,,,/resources/#Pericles Light"` 是無效的字型參考。  
  
-   **自動字型內嵌**：設計階段期間，並不支援搜尋應用程式的字型使用和自動內嵌應用程式資源中的字型。  
  
-   **字型子集**：[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式不支援建立非固定格式文件的字型子集。  
  
-   在發生不正確參考的情況下，應用程式會回復成使用可用的字型。  
  
## 請參閱  
 <xref:System.Windows.Documents.Typography>   
 <xref:System.Windows.Media.FontFamily>   
 [Microsoft 印刷樣式：連結、最新消息和聯絡資訊](http://www.microsoft.com/typography/links/)   
 [OpenType 規格](http://www.microsoft.com/typography/otspec/)   
 [OpenType 字型功能](../../../../docs/framework/wpf/advanced/opentype-font-features.md)   
 [範例 OpenType 字型套件](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md)