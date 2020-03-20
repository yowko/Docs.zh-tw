---
title: 如何：將應用程式當地語系化
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- localization [WPF], applications
- LocBaml tool [WPF]
- applications [WPF], localizing
ms.assetid: 5001227e-9326-48a4-9dcd-ba1b89ee6653
ms.openlocfilehash: f2e7e5e8879e89806cfd457a1af80f51b91871cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174208"
---
# <a name="how-to-localize-an-application"></a>如何：將應用程式當地語系化
本教學課程說明如何使用 LocBaml 工具來建立當地語系化的應用程式。  
  
> [!NOTE]
> LocBaml 工具不是可實際執行的應用程式。 這只是個範例，示範如何使用一些當地語系化的 API，並說明如何撰寫當地語系化工具。  
  
<a name="Introduction"></a>
## <a name="overview"></a>概觀  
 此討論提供將應用程式當地語系化的逐步方法。 首先，您要準備您的應用程式，以便從中擷取要轉譯的文字。 轉譯文字之後，您要轉譯的文字合併至原始應用程式的新複本中。  
  
<a name="Requirements"></a>
## <a name="requirements"></a>需求  
 在討論過程中，您將使用 Microsoft 生成引擎 （MSBuild），該引擎是從命令列運行的編譯器。  
  
 此外，也會指引您使用專案檔。 有關如何使用 MSBuild 和專案檔案的說明，請參閱[生成和部署](../app-development/building-and-deploying-wpf-applications.md)。  
  
 此討論中的所有範例都是使用 en-US (美式英文) 做為文化特性。 這可讓您逐步執行範例中的所有步驟，而不需要安裝不同的語言。  
  
<a name="create_sample_app"></a>
## <a name="create-a-sample-application"></a>建立範例應用程式  
 在此步驟中，您將準備要當地語系化的應用程式。 在 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 範例中有提供一個 HelloApp 範例，將用於此討論中的程式碼範例。 如果要使用此示例，請從[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)][LocBaml 工具示例](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml)下載檔案。  
  
1. 將您的應用程式開發至您要當地語系化的開始點。  
  
2. 在專案檔案中指定開發語言，以便 MSBuild 生成主程式集和附屬程式集（具有 .resources.dll 副檔名的檔）以包含中性語言資源。 HelloApp 範例中的專案檔是 HelloApp.csproj。 在該檔案中，您會發現識別如下的開發語言：  
  
     `<UICulture>en-US</UICulture>`  
  
3. 將 UID 加入您的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案。 UID 可用來追蹤對檔案的變更，以及識別必須轉譯的項目。 要將 Uid 添加到檔，請在專案檔案上運行**更新：**  
  
     **msbuild -t：更新helloapp.csproj**  
  
     要驗證您沒有丟失或重複的 Uid，請運行**checkuid**：  
  
     **msbuild -t：checkuid helloapp.csproj**  
  
     運行**updateuid**後，您的檔應包含 Uids。 例如，在 HelloApp 的 Pane1.xaml 檔案中，您應該會發現下列項目：  
  
     `<StackPanel x:Uid="StackPanel_1">`  
  
     `<TextBlock x:Uid="TextBlock_1">Hello World</TextBlock>`  
  
     `<TextBlock x:Uid="TextBlock_2">Goodbye World</TextBlock>`  
  
     `</StackPanel>`  
  
<a name="create_dll"></a>
## <a name="create-the-neutral-language-resources-satellite-assembly"></a>建立中性語言資源附屬組件  
 設定應用程式來產生中性語言資源附屬組件之後，您要建置應用程式。 這會產生主應用程式組件，以及 LocBaml 進行當地語系化所需的中性語言資源附屬組件。 若要建置應用程式：  
  
1. 編譯 HelloApp 以創建動態連結程式庫 （DLL）：  
  
     **msbuild helloapp.csproj**  
  
2. 新建立的主應用程式組件 HelloApp.exe 會建立在下列資料夾中：  
  
     `C:\HelloApp\Bin\Debug\`  
  
3. 新建立的中性語言資源附屬組件 HelloApp.resources.dll 會建立下列資料夾中：  
  
     `C:\HelloApp\Bin\Debug\en-US\`  
  
<a name="build_locbaml"></a>
## <a name="build-the-locbaml-tool"></a>建置 LocBaml 工具  
  
1. 建置 LocBaml 時所需的所有檔案都位在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 範例中。 從[LocBaml 工具示例](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml)下載 C# 檔。  
  
2. 從命令列執行專案檔 (locbaml.csproj)，以建置工具：  
  
     **msbuild locbaml.csproj**  
  
3. 移至 Bin\Release 目錄，尋找新建立的可執行檔 (locbaml.exe)。 範例：C:\LocBaml\Bin\Release\locbaml.exe。  
  
4. 當您執行 LocBaml 時，可指定的選項如下：  
  
    - **解析**或 **-p：** 分析 Baml、資源或 DLL 檔以生成 .csv 或 .txt 檔。  
  
    - **生成**或 **-g：** 使用已翻譯的檔生成當地語系化的二進位檔案。  
  
    - **輸出**或 **-o** [*檔目錄*] **：** 輸出檔案名。  
  
    - **區域性**或 **-cul** =*區域性*= **：** 輸出程式集的局部性。  
  
    - **翻譯**或 **-轉**式 [*翻譯.csv*] **：** 翻譯或當地語系化檔。  
  
    - **asmpath**或 **-asmpath：** [*檔目錄*] **：** 如果[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]代碼包含自訂控制項，則必須向自訂控制項程式集提供**asmpath。**  
  
    - **nologo：** 顯示無標誌或著作權資訊。  
  
    - **verbose：** 顯示詳細模式資訊。  
  
    > [!NOTE]
    > 如果您在運行該工具時需要選項清單，請鍵入**LocBaml.exe**並按 ENTER。  
  
<a name="parse_dll"></a>
## <a name="use-locbaml-to-parse-a-file"></a>使用 LocBaml 來剖析檔案  
 現在您已經建立 LocBaml 工具，就準備好用它來剖析 HelloApp.resources.dll，以擷取要當地語系化的文字內容。  
  
1. 將 LocBaml.exe 複製到應用程式的 bin\debug 資料夾，這是建立主要應用程式組件的位置。  
  
2. 若要剖析附屬組件檔案，並將輸出儲存成 .csv 檔案，請使用下列命令：  
  
     **LocBaml.exe /parse HelloApp.resources.dll /out:Hello.csv**  
  
    > [!NOTE]
    > 如果輸入檔 HelloApp.resources.dll 不是在與 LocBaml.exe 相同的目錄中，請移動其中一個檔案，讓這兩個檔案都在相同的目錄中。  
  
3. 當您執行 LocBaml 來剖析檔案時，輸出中會包含以逗號 (.csv 檔案) 或定位點 (.txt 檔) 分隔的七個欄位。 下面顯示針對 HelloApp.resources.dll 所剖析的 .csv 檔案：

   | |
   |-|
   |HelloApp.g.en-US.resources:window1.baml,Stack1:System.Windows.Controls.StackPanel.$Content,Ignore,FALSE, FALSE,,#Text1;#Text2;|
   |HelloApp.g.en-US.resources:window1.baml,Text1:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Hello World|
   |HelloApp.g.en-US.resources:window1.baml,Text2:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Goodbye World|

   這七個欄位為：  
  
   1. **BAML 名稱**。 有關來源語言附屬組件的 BAML 資源名稱。  
  
   2. **資源金鑰**。 當地語系化的資源識別碼。  
  
   3. **類別**。 值型別。 請參閱[當地語系化屬性和注釋](localization-attributes-and-comments.md)。  
  
   4. **可讀性**。 當地語系化工具是否能夠讀取該值。 請參閱[當地語系化屬性和注釋](localization-attributes-and-comments.md)。  
  
   5. **可修改性**。 當地語系化工具是否能夠修改該值。 請參閱[當地語系化屬性和注釋](localization-attributes-and-comments.md)。  
  
   6. **評論**. 該值的其他說明，有助於判斷某值當地語系化的方式。 請參閱[當地語系化屬性和注釋](localization-attributes-and-comments.md)。  
  
   7. **值**。 要轉譯成所需文化特性的文字值。  
  
   下表顯示這些欄位如何對應至 .csv 檔案的分隔值：  
  
   |BAML 名稱|資源索引鍵|類別|可讀性|可修改性|註解|值|  
   |---------------|------------------|--------------|-----------------|-------------------|--------------|-----------|
   |HelloApp.g.en-US.resources:window1.baml|Stack1:System.Windows.Controls.StackPanel.$Content|略過|FALSE|FALSE||#Text1;#Text2|
   |HelloApp.g.en-US.resources:window1.baml|Text1:System.Windows.Controls.TextBlock.$Content|None|TRUE|TRUE||Hello World|
   |HelloApp.g.en-US.resources:window1.baml|Text2:System.Windows.Controls.TextBlock.$Content|None|TRUE|TRUE||Goodbye World|
  
   請注意，"注釋"欄位的所有值不包含任何值;因此，注釋欄位的所有值都不包含"**注釋"** 欄位的所有值。如果欄位沒有值，則該欄位為空。 另請注意，第一行中的項既不可讀，也不可修改，並且具有"忽略"作為其**類別**值，所有這些都指示該值不可當地語系化。  
  
4. 為了便於在解析檔中（特別是在大型檔中）發現可當地語系化項，您可以按**類別**、**可讀性和****可修改性**對項進行排序或篩選。 例如，您可以篩選出無法讀取及無法修改的值。  
  
<a name="translate_loc_content"></a>
## <a name="translate-the-localizable-content"></a>轉譯可當地語系化的內容  
 使用您可以用來轉譯擷取內容的任何工具。 執行此操作的一個好方法是將資源寫入 .csv 檔並在 Microsoft Excel 中查看它們，對最後一列（值）進行翻譯更改。  
  
<a name="merge_translations"></a>
## <a name="use-locbaml-to-generate-a-new-resourcesdll-file"></a>使用 LocBaml 來產生新的 .resources.dll 檔案  
 藉由使用 LocBaml 來剖析 HelloApp.resources.dll 而識別的內容已轉譯，且必須合併回原始應用程式。 使用**生成**或 **-g**選項生成新的 .resources.DLL 檔案。  
  
1. 使用下列語法來產生新的 HelloApp.resources.dll 檔案。 將文化特性標示為 en-US (/cul:en-US)。  
  
     **LocBaml.exe /generate HelloApp.resources.dll /trans:Hello.csv /out:c:\ /cul:en-US**  
  
    > [!NOTE]
    > 如果輸入檔 Hello.csv 不是在與可執行檔 LocBaml.exe 相同的目錄中，請移動其中一個檔案，讓這兩個檔案都在相同的目錄中。  
  
2. 以新建立的 HelloApp.resources.dll 檔案，取代 C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll 目錄中舊的 HelloApp.resources.dll 檔案。  
  
3. "Hello World" 和 "Goodbye World" 現在應該已在您的應用程式中轉譯。  
  
4. 若要轉譯為不同的文化特性，請使用您想要轉譯之語言的文化特性。 下列範例示範如何轉譯成加拿大法文：  
  
     **LocBaml.exe /generate HelloApp.resources.dll /trans:Hellofr-CA.csv /out:c:\ /cul:fr-CA**  
  
5. 在與主應用程式組件相同的組件中，建立新的特定文化特性資料夾，以存放新的附屬組件。 針對加拿大法文，資料夾會是 fr-CA。  
  
6. 將所產生的附屬組件複製到新的資料夾。  
  
7. 若要測試新的附屬組件，您需要變更您的應用程式用來執行的文化特性。 您可以使用下列其中一種作法：  
  
    - 更改作業系統的地區設定 （**開始**&#124;**控制台**&#124;**區域和語言選項**）。  
  
    - 在您的應用程式中，將下列程式碼加入 App.xaml.cs：  
  
   [!code-xaml[LocBamlChangeCultureSnippets#LocBamlChangeCultureMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml#locbamlchangeculturemarkup)]
   [!code-csharp[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml.cs#locbamlchangeculturecodebehind)]
   [!code-vb[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/VisualBasic/Application.xaml.vb#locbamlchangeculturecodebehind)]  
  
<a name="Some_Tips_for_Using_LocBaml"></a>
## <a name="some-tips-for-using-locbaml"></a>使用 LocBaml 的一些秘訣  
  
- 用來定義自訂控制項的所有相依組件，都必須複製到 LocBaml 的本機目錄中，或安裝至 GAC 中。 這是必需的，因為當地語系化 API 在讀取二進位 XAML （BAML） 時必須有權訪問依存性程式集。  
  
- 如果主要組件已簽署，所產生的資源 DLL 也必須簽署，才能將其載入。  
  
- 當地語系化資源 DLL 的版本必須與主要組件同步處理。  
  
<a name="Whats_Next"></a>
## <a name="whats-next"></a>接下來  
 您現在對於如何使用 LocBaml 工具，應該有基本的了解。  您應該能夠建立包含 UID 的檔案。 藉由使用 LocBaml 工具，您應該能夠剖析檔案來擷取可當地語系化的內容，而在內容轉譯之後，您應該能夠產生將轉譯內容合併的 .resources.dll 檔案。 本主題可能無法顧及所有細節，但是您現在已經有了使用 LocBaml 將應用程式當地語系化所需的知識。  
  
## <a name="see-also"></a>另請參閱

- [WPF 的全球化](globalization-for-wpf.md)
- [使用自動配置概觀](use-automatic-layout-overview.md)
