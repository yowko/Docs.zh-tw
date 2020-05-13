---
title: 將應用程式當地語系化
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- localization [WPF], applications
- LocBaml tool [WPF]
- applications [WPF], localizing
ms.assetid: 5001227e-9326-48a4-9dcd-ba1b89ee6653
ms.openlocfilehash: dc7d8f4f56b26fffbd883e1e1d6e420026e1f94f
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209678"
---
# <a name="how-to-localize-an-application"></a>如何：將應用程式當地語系化

本教學課程說明如何使用 LocBaml 工具來建立當地語系化的應用程式。  
  
> [!NOTE]
> LocBaml 工具不是可實際執行的應用程式。 這只是個範例，示範如何使用一些當地語系化的 API，並說明如何撰寫當地語系化工具。  
  
## <a name="overview"></a>概觀

本文提供當地語系化應用程式的逐步方法。 首先，您要準備您的應用程式，以便可以將翻譯的文字解壓縮。 翻譯文字之後，您可以將翻譯的文字合併成原始應用程式的新複本。
  
## <a name="create-a-sample-application"></a>建立範例應用程式

在此步驟中，您會準備您的應用程式以進行當地語系化。 在 Windows Presentation Foundation （WPF）範例中，提供了一個 HelloApp 範例，將用於此討論中的程式碼範例。 如果您想要使用此範例，請從[LocBaml 工具範例](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml)下載 EXTENSIBLE APPLICATION MARKUP LANGUAGE （XAML）檔案。  
  
1. 將您的應用程式開發至您要當地語系化的開始點。  
  
2. 在專案檔中指定開發語言，讓 MSBuild 產生主要元件和附屬元件（副檔名為 .resources 的檔案），以包含中性語言資源。 HelloApp 範例中的專案檔是 HelloApp.csproj。 在該檔案中，您會發現識別如下的開發語言：  
  
   `<UICulture>en-US</UICulture>`  
  
3. 將 Uid 新增至您的 XAML 檔案。 UID 可用來追蹤對檔案的變更，以及識別必須轉譯的項目。 若要將 Uid 新增至您的檔案，請 `updateuid` 在您的專案檔上執行：  

   `msbuild -t:updateuid helloapp.csproj`

   若要確認您沒有遺漏或重複的 Uid，請執行 `checkuid` ：  

   `msbuild -t:checkuid helloapp.csproj`

   執行之後 `updateuid` ，您的檔案應該會包含 uid。 例如，在 HelloApp 的*Pane1*檔案中，您應該會找到下列各項：  

   ```xaml
   <StackPanel x:Uid="StackPanel_1">
     <TextBlock x:Uid="TextBlock_1">Hello World</TextBlock>
     <TextBlock x:Uid="TextBlock_2">Goodbye World</TextBlock>
   </StackPanel>
   ```

## <a name="create-the-neutral-language-resources-satellite-assembly"></a>建立中性語言資源附屬元件

將應用程式設定為產生中性語言資源附屬元件之後，您可以建立應用程式。 這會產生主要應用程式元件，以及 LocBaml 進行當地語系化所需的中性語言資源附屬元件。

若要建置應用程式：  
  
1. 編譯 HelloApp 以建立動態連結程式庫（DLL）：  
  
   `msbuild helloapp.csproj`
  
2. 新建立的主要應用程式元件 HelloApp 會建立在下列資料夾中： *C:\HelloApp\Bin\Debug*
  
3. 新建立的中性語言資源附屬元件 HelloApp 會建立在下列資料夾中： *C:\HelloApp\Bin\Debug\en-US*
  
## <a name="build-the-locbaml-tool"></a>建立 LocBaml 工具  
  
1. 建立 LocBaml 所需的所有檔案都位於 WPF 範例中。 從[LocBaml 工具範例](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml)下載 c # 檔案。  
  
2. 從命令列執行專案檔 (locbaml.csproj)，以建置工具：  

   `msbuild locbaml.csproj`
  
3. 移至*Bin\Release*目錄以尋找新建立的可執行檔（locbaml .exe）。 範例： *C:\LocBaml\Bin\Release\locbaml.exe*
  
4. 當您執行 LocBaml 時，可以指定的選項如下所示。

   | 選項 | 描述|
   | - | - |
   | `parse` 或 `-p` | 剖析 Baml、資源或 DLL 檔案，以產生 .csv 或 .txt 檔案。 |
   | `generate` 或 `-g` | 使用翻譯的檔案產生當地語系化的二進位檔案。 |
   | `out`或 `-o` {*filedirectory*] | 輸出檔名稱。 |
   | `culture`或 `-cul` {*culture*] | 輸出元件的地區設定。 |
   | `translation`或 `-trans` {*轉譯 .csv*] | 已翻譯或當地語系化的檔案。 |
   | `asmpath`或 `-asmpath` {*filedirectory*] | 如果您的 XAML 程式碼包含自訂控制項，您必須將提供 `asmpath` 給自訂控制群組件。 |
   | `nologo` | ，可顯示無標誌或著作權資訊。 |
   | `verbose` |  ，可顯示詳細模式資訊。 |
  
   > [!NOTE]
   > 如果您在執行此工具時需要選項清單，請輸入 `LocBaml.exe` ，然後按**enter**鍵。
  
## <a name="use-locbaml-to-parse-a-file"></a>使用 LocBaml 來剖析檔案

現在您已經建立 LocBaml 工具，就準備好用它來剖析 HelloApp.resources.dll，以擷取要當地語系化的文字內容。  
  
1. 將 LocBaml.exe 複製到應用程式的 bin\debug 資料夾，這是建立主要應用程式組件的位置。  
  
2. 若要剖析附屬組件檔案，並將輸出儲存成 .csv 檔案，請使用下列命令：  
  
   `LocBaml.exe /parse HelloApp.resources.dll /out:Hello.csv`
  
   > [!NOTE]
   > 如果輸入檔 HelloApp.resources.dll 不是在與 LocBaml.exe 相同的目錄中，請移動其中一個檔案，讓這兩個檔案都在相同的目錄中。  
  
3. 當您執行 LocBaml 來剖析檔案時，輸出中會包含以逗號 (.csv 檔案) 或定位點 (.txt 檔) 分隔的七個欄位。 下面顯示針對 HelloApp.resources.dll 所剖析的 .csv 檔案：

   | |
   |-|
   |HelloApp.g.en-US.resources:window1.baml,Stack1:System.Windows.Controls.StackPanel.$Content,Ignore,FALSE, FALSE,,#Text1;#Text2;|
   |HelloApp.g.en-US.resources:window1.baml,Text1:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Hello World|
   |HelloApp.g.en-US.resources:window1.baml,Text2:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Goodbye World|

   這七個欄位為：  
  
   - **BAML 名稱**。 有關來源語言附屬組件的 BAML 資源名稱。  
  
   - **資源金鑰**。 當地語系化的資源識別碼。  
  
   - **類別**。 值型別。 請參閱[當地語系化屬性和批註](localization-attributes-and-comments.md)。  
  
   - **可讀性**。 當地語系化工具是否能夠讀取該值。 請參閱[當地語系化屬性和批註](localization-attributes-and-comments.md)。  
  
   - **可修改性**。 當地語系化工具是否能夠修改該值。 請參閱[當地語系化屬性和批註](localization-attributes-and-comments.md)。  
  
   - **批註**。 該值的其他說明，有助於判斷某值當地語系化的方式。 請參閱[當地語系化屬性和批註](localization-attributes-and-comments.md)。  
  
   - **值**。 要轉譯成所需文化特性的文字值。  
  
   下表顯示這些欄位如何對應至 .csv 檔案的分隔值：  
  
   |BAML 名稱|資源索引鍵|類別|可讀性|可修改性|註解|值|  
   |---------------|------------------|--------------|-----------------|-------------------|--------------|-----------|
   |HelloApp.g.en-US.resources:window1.baml|Stack1:System.Windows.Controls.StackPanel.$Content|略過|FALSE|FALSE||#Text1;#Text2|
   |HelloApp.g.en-US.resources:window1.baml|Text1:System.Windows.Controls.TextBlock.$Content|無|TRUE|TRUE||Hello World|
   |HelloApp.g.en-US.resources:window1.baml|Text2:System.Windows.Controls.TextBlock.$Content|無|TRUE|TRUE||Goodbye World|
  
   請注意，[**批註**] 欄位的所有值都不包含任何值。如果欄位沒有值，則會是空的。 另請注意，第一個資料列中的專案既不是可讀取也不能修改，而且具有「忽略」做為它的**分類**值，全都表示此值無法當地語系化。  
  
4. 為了方便探索已剖析檔案中的可當地語系化專案，特別是在大型檔案中，您可以依**類別**、**可讀性**和可**修改**性來排序或篩選項目。 例如，您可以篩選出無法讀取及無法修改的值。  
  
## <a name="translate-the-localizable-content"></a>翻譯可當地語系化的內容

使用您可以用來轉譯擷取內容的任何工具。 執行這項操作的好方法是將資源寫入 .csv 檔案，並在 Microsoft Excel 中加以查看，對最後一個資料行（值）進行轉譯變更。  
  
## <a name="use-locbaml-to-generate-a-new-resourcesdll-file"></a>使用 LocBaml 產生新的 .resources .dll 檔案

藉由使用 LocBaml 來剖析 HelloApp.resources.dll 而識別的內容已轉譯，且必須合併回原始應用程式。 使用 `generate` 或 `-g` 選項來產生新的 .resources .dll 檔案。  
  
1. 使用下列語法來產生新的 HelloApp.resources.dll 檔案。 將文化特性標示為 en-US (/cul:en-US)。  
  
   `LocBaml.exe /generate HelloApp.resources.dll /trans:Hello.csv /out:c:\ /cul:en-US`  

   > [!NOTE]
   > 如果輸入檔 Hello.csv 不是在與可執行檔 LocBaml.exe 相同的目錄中，請移動其中一個檔案，讓這兩個檔案都在相同的目錄中。  
  
2. 將*C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll*目錄中的舊*HelloApp*取代為新建立的*HelloApp .resources*檔案。  
  
3. "Hello World" 和 "Goodbye World" 現在應該已在您的應用程式中轉譯。  
  
4. 若要轉譯為不同的文化特性，請使用您想要轉譯之語言的文化特性。 下列範例示範如何轉譯成加拿大法文：  
  
   `LocBaml.exe /generate HelloApp.resources.dll /trans:Hellofr-CA.csv /out:c:\ /cul:fr-CA`  
  
5. 在與主應用程式組件相同的組件中，建立新的特定文化特性資料夾，以存放新的附屬組件。 針對加拿大法文，資料夾會是 fr-CA。  
  
6. 將所產生的附屬組件複製到新的資料夾。  
  
7. 若要測試新的附屬組件，您需要變更您的應用程式用來執行的文化特性。 您可以使用下列其中一種作法：  
  
   - 變更作業系統的地區設定。
  
   - 在您的應用程式中，將下列程式碼加入 App.xaml.cs：  
  
     [!code-xaml[LocBamlChangeCultureSnippets#LocBamlChangeCultureMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml#locbamlchangeculturemarkup)]
     [!code-csharp[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml.cs#locbamlchangeculturecodebehind)]
     [!code-vb[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/VisualBasic/Application.xaml.vb#locbamlchangeculturecodebehind)]  
  
## <a name="tips-for-using-locbaml"></a>使用 LocBaml 的秘訣  
  
- 用來定義自訂控制項的所有相依組件，都必須複製到 LocBaml 的本機目錄中，或安裝至 GAC 中。 這是必要的，因為當地語系化 API 在讀取二進位 XAML （BAML）時，必須擁有相依元件的存取權。  
  
- 如果主要組件已簽署，所產生的資源 DLL 也必須簽署，才能將其載入。  
  
- 當地語系化資源 DLL 的版本必須與主要組件同步處理。
  
## <a name="see-also"></a>請參閱

- [WPF 的全球化](globalization-for-wpf.md)
- [使用自動配置概觀](use-automatic-layout-overview.md)
