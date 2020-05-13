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
# <a name="how-to-localize-an-application"></a><span data-ttu-id="08a32-102">如何：將應用程式當地語系化</span><span class="sxs-lookup"><span data-stu-id="08a32-102">How to: Localize an application</span></span>

<span data-ttu-id="08a32-103">本教學課程說明如何使用 LocBaml 工具來建立當地語系化的應用程式。</span><span class="sxs-lookup"><span data-stu-id="08a32-103">This tutorial explains how to create a localized application by using the LocBaml tool.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="08a32-104">LocBaml 工具不是可實際執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="08a32-104">The LocBaml tool is not a production-ready application.</span></span> <span data-ttu-id="08a32-105">這只是個範例，示範如何使用一些當地語系化的 API，並說明如何撰寫當地語系化工具。</span><span class="sxs-lookup"><span data-stu-id="08a32-105">It is presented as a sample that uses some of the localization APIs and illustrates how you might write a localization tool.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="08a32-106">概觀</span><span class="sxs-lookup"><span data-stu-id="08a32-106">Overview</span></span>

<span data-ttu-id="08a32-107">本文提供當地語系化應用程式的逐步方法。</span><span class="sxs-lookup"><span data-stu-id="08a32-107">This article gives you a step-by-step approach to localizing an application.</span></span> <span data-ttu-id="08a32-108">首先，您要準備您的應用程式，以便可以將翻譯的文字解壓縮。</span><span class="sxs-lookup"><span data-stu-id="08a32-108">First, you prepare your application so that the text that will be translated can be extracted.</span></span> <span data-ttu-id="08a32-109">翻譯文字之後，您可以將翻譯的文字合併成原始應用程式的新複本。</span><span class="sxs-lookup"><span data-stu-id="08a32-109">After the text is translated, you merge the translated text into a new copy of the original application.</span></span>
  
## <a name="create-a-sample-application"></a><span data-ttu-id="08a32-110">建立範例應用程式</span><span class="sxs-lookup"><span data-stu-id="08a32-110">Create a sample application</span></span>

<span data-ttu-id="08a32-111">在此步驟中，您會準備您的應用程式以進行當地語系化。</span><span class="sxs-lookup"><span data-stu-id="08a32-111">In this step, you prepare your app for localization.</span></span> <span data-ttu-id="08a32-112">在 Windows Presentation Foundation （WPF）範例中，提供了一個 HelloApp 範例，將用於此討論中的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="08a32-112">In the Windows Presentation Foundation (WPF) samples, a HelloApp sample is supplied that will be used for the code examples in this discussion.</span></span> <span data-ttu-id="08a32-113">如果您想要使用此範例，請從[LocBaml 工具範例](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml)下載 EXTENSIBLE APPLICATION MARKUP LANGUAGE （XAML）檔案。</span><span class="sxs-lookup"><span data-stu-id="08a32-113">If you would like to use this sample, download the Extensible Application Markup Language (XAML) files from the [LocBaml Tool Sample](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml).</span></span>  
  
1. <span data-ttu-id="08a32-114">將您的應用程式開發至您要當地語系化的開始點。</span><span class="sxs-lookup"><span data-stu-id="08a32-114">Develop your application to the point where you want to start localization.</span></span>  
  
2. <span data-ttu-id="08a32-115">在專案檔中指定開發語言，讓 MSBuild 產生主要元件和附屬元件（副檔名為 .resources 的檔案），以包含中性語言資源。</span><span class="sxs-lookup"><span data-stu-id="08a32-115">Specify the development language in the project file so that MSBuild generates a main assembly and a satellite assembly (a file with the .resources.dll extension) to contain the neutral language resources.</span></span> <span data-ttu-id="08a32-116">HelloApp 範例中的專案檔是 HelloApp.csproj。</span><span class="sxs-lookup"><span data-stu-id="08a32-116">The project file in the HelloApp sample is HelloApp.csproj.</span></span> <span data-ttu-id="08a32-117">在該檔案中，您會發現識別如下的開發語言：</span><span class="sxs-lookup"><span data-stu-id="08a32-117">In that file, you will find the development language identified as follows:</span></span>  
  
   `<UICulture>en-US</UICulture>`  
  
3. <span data-ttu-id="08a32-118">將 Uid 新增至您的 XAML 檔案。</span><span class="sxs-lookup"><span data-stu-id="08a32-118">Add Uids to your XAML files.</span></span> <span data-ttu-id="08a32-119">UID 可用來追蹤對檔案的變更，以及識別必須轉譯的項目。</span><span class="sxs-lookup"><span data-stu-id="08a32-119">Uids are used to keep track of changes to files and to identify items that must be translated.</span></span> <span data-ttu-id="08a32-120">若要將 Uid 新增至您的檔案，請 `updateuid` 在您的專案檔上執行：</span><span class="sxs-lookup"><span data-stu-id="08a32-120">To add Uids to your files, run `updateuid` on your project file:</span></span>  

   `msbuild -t:updateuid helloapp.csproj`

   <span data-ttu-id="08a32-121">若要確認您沒有遺漏或重複的 Uid，請執行 `checkuid` ：</span><span class="sxs-lookup"><span data-stu-id="08a32-121">To verify that you have no missing or duplicate Uids, run `checkuid`:</span></span>  

   `msbuild -t:checkuid helloapp.csproj`

   <span data-ttu-id="08a32-122">執行之後 `updateuid` ，您的檔案應該會包含 uid。</span><span class="sxs-lookup"><span data-stu-id="08a32-122">After running `updateuid`, your files should contain Uids.</span></span> <span data-ttu-id="08a32-123">例如，在 HelloApp 的*Pane1*檔案中，您應該會找到下列各項：</span><span class="sxs-lookup"><span data-stu-id="08a32-123">For example, in the *Pane1.xaml* file of HelloApp, you should find the following:</span></span>  

   ```xaml
   <StackPanel x:Uid="StackPanel_1">
     <TextBlock x:Uid="TextBlock_1">Hello World</TextBlock>
     <TextBlock x:Uid="TextBlock_2">Goodbye World</TextBlock>
   </StackPanel>
   ```

## <a name="create-the-neutral-language-resources-satellite-assembly"></a><span data-ttu-id="08a32-124">建立中性語言資源附屬元件</span><span class="sxs-lookup"><span data-stu-id="08a32-124">Create the neutral-language resources satellite assembly</span></span>

<span data-ttu-id="08a32-125">將應用程式設定為產生中性語言資源附屬元件之後，您可以建立應用程式。</span><span class="sxs-lookup"><span data-stu-id="08a32-125">After the application is configured to generate a neutral-language resources satellite assembly, you build the application.</span></span> <span data-ttu-id="08a32-126">這會產生主要應用程式元件，以及 LocBaml 進行當地語系化所需的中性語言資源附屬元件。</span><span class="sxs-lookup"><span data-stu-id="08a32-126">This generates the main application assembly as well as the neutral-language resources satellite assembly that's required by LocBaml for localization.</span></span>

<span data-ttu-id="08a32-127">若要建置應用程式：</span><span class="sxs-lookup"><span data-stu-id="08a32-127">To build the application:</span></span>  
  
1. <span data-ttu-id="08a32-128">編譯 HelloApp 以建立動態連結程式庫（DLL）：</span><span class="sxs-lookup"><span data-stu-id="08a32-128">Compile HelloApp to create a dynamic-link library (DLL):</span></span>  
  
   `msbuild helloapp.csproj`
  
2. <span data-ttu-id="08a32-129">新建立的主要應用程式元件 HelloApp 會建立在下列資料夾中： *C:\HelloApp\Bin\Debug*</span><span class="sxs-lookup"><span data-stu-id="08a32-129">The newly created main application assembly, HelloApp.exe, is created in the following folder: *C:\HelloApp\Bin\Debug*</span></span>
  
3. <span data-ttu-id="08a32-130">新建立的中性語言資源附屬元件 HelloApp 會建立在下列資料夾中： *C:\HelloApp\Bin\Debug\en-US*</span><span class="sxs-lookup"><span data-stu-id="08a32-130">The newly created neutral-language resources satellite assembly, HelloApp.resources.dll, is created in the following folder: *C:\HelloApp\Bin\Debug\en-US*</span></span>
  
## <a name="build-the-locbaml-tool"></a><span data-ttu-id="08a32-131">建立 LocBaml 工具</span><span class="sxs-lookup"><span data-stu-id="08a32-131">Build the LocBaml tool</span></span>  
  
1. <span data-ttu-id="08a32-132">建立 LocBaml 所需的所有檔案都位於 WPF 範例中。</span><span class="sxs-lookup"><span data-stu-id="08a32-132">All the files necessary to build LocBaml are located in the WPF samples.</span></span> <span data-ttu-id="08a32-133">從[LocBaml 工具範例](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml)下載 c # 檔案。</span><span class="sxs-lookup"><span data-stu-id="08a32-133">Download the C# files from the [LocBaml Tool Sample](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml).</span></span>  
  
2. <span data-ttu-id="08a32-134">從命令列執行專案檔 (locbaml.csproj)，以建置工具：</span><span class="sxs-lookup"><span data-stu-id="08a32-134">From the command line, run the project file (locbaml.csproj) to build the tool:</span></span>  

   `msbuild locbaml.csproj`
  
3. <span data-ttu-id="08a32-135">移至*Bin\Release*目錄以尋找新建立的可執行檔（locbaml .exe）。</span><span class="sxs-lookup"><span data-stu-id="08a32-135">Go to the *Bin\Release* directory to find the newly created executable file (locbaml.exe).</span></span> <span data-ttu-id="08a32-136">範例： *C:\LocBaml\Bin\Release\locbaml.exe*</span><span class="sxs-lookup"><span data-stu-id="08a32-136">Example: *C:\LocBaml\Bin\Release\locbaml.exe*</span></span>
  
4. <span data-ttu-id="08a32-137">當您執行 LocBaml 時，可以指定的選項如下所示。</span><span class="sxs-lookup"><span data-stu-id="08a32-137">The options that you can specify when you run LocBaml are as follows.</span></span>

   | <span data-ttu-id="08a32-138">選項</span><span class="sxs-lookup"><span data-stu-id="08a32-138">Option</span></span> | <span data-ttu-id="08a32-139">描述</span><span class="sxs-lookup"><span data-stu-id="08a32-139">Description</span></span>|
   | - | - |
   | <span data-ttu-id="08a32-140">`parse` 或 `-p`</span><span class="sxs-lookup"><span data-stu-id="08a32-140">`parse` or `-p`</span></span> | <span data-ttu-id="08a32-141">剖析 Baml、資源或 DLL 檔案，以產生 .csv 或 .txt 檔案。</span><span class="sxs-lookup"><span data-stu-id="08a32-141">Parses Baml, resources, or DLL files to generate a .csv or .txt file.</span></span> |
   | <span data-ttu-id="08a32-142">`generate` 或 `-g`</span><span class="sxs-lookup"><span data-stu-id="08a32-142">`generate` or `-g`</span></span> | <span data-ttu-id="08a32-143">使用翻譯的檔案產生當地語系化的二進位檔案。</span><span class="sxs-lookup"><span data-stu-id="08a32-143">Generates a localized binary file by using a translated file.</span></span> |
   | <span data-ttu-id="08a32-144">`out`或 `-o` {*filedirectory*]</span><span class="sxs-lookup"><span data-stu-id="08a32-144">`out` or `-o` {*filedirectory*]</span></span> | <span data-ttu-id="08a32-145">輸出檔名稱。</span><span class="sxs-lookup"><span data-stu-id="08a32-145">Output file name.</span></span> |
   | <span data-ttu-id="08a32-146">`culture`或 `-cul` {*culture*]</span><span class="sxs-lookup"><span data-stu-id="08a32-146">`culture` or `-cul` {*culture*]</span></span> | <span data-ttu-id="08a32-147">輸出元件的地區設定。</span><span class="sxs-lookup"><span data-stu-id="08a32-147">Locale of output assemblies.</span></span> |
   | <span data-ttu-id="08a32-148">`translation`或 `-trans` {*轉譯 .csv*]</span><span class="sxs-lookup"><span data-stu-id="08a32-148">`translation` or `-trans` {*translation.csv*]</span></span> | <span data-ttu-id="08a32-149">已翻譯或當地語系化的檔案。</span><span class="sxs-lookup"><span data-stu-id="08a32-149">Translated or localized file.</span></span> |
   | <span data-ttu-id="08a32-150">`asmpath`或 `-asmpath` {*filedirectory*]</span><span class="sxs-lookup"><span data-stu-id="08a32-150">`asmpath` or `-asmpath` {*filedirectory*]</span></span> | <span data-ttu-id="08a32-151">如果您的 XAML 程式碼包含自訂控制項，您必須將提供 `asmpath` 給自訂控制群組件。</span><span class="sxs-lookup"><span data-stu-id="08a32-151">If your XAML code contains custom controls, you must supply the `asmpath` to the custom control assembly.</span></span> |
   | `nologo` | <span data-ttu-id="08a32-152">，可顯示無標誌或著作權資訊。</span><span class="sxs-lookup"><span data-stu-id="08a32-152">Displays no logo or copyright information.</span></span> |
   | `verbose` | <span data-ttu-id="08a32-153"> ，可顯示詳細模式資訊。</span><span class="sxs-lookup"><span data-stu-id="08a32-153">Displays verbose mode information.</span></span> |
  
   > [!NOTE]
   > <span data-ttu-id="08a32-154">如果您在執行此工具時需要選項清單，請輸入 `LocBaml.exe` ，然後按**enter**鍵。</span><span class="sxs-lookup"><span data-stu-id="08a32-154">If you need a list of the options when you are running the tool, enter `LocBaml.exe` and then press **Enter**.</span></span>
  
## <a name="use-locbaml-to-parse-a-file"></a><span data-ttu-id="08a32-155">使用 LocBaml 來剖析檔案</span><span class="sxs-lookup"><span data-stu-id="08a32-155">Use LocBaml to parse a file</span></span>

<span data-ttu-id="08a32-156">現在您已經建立 LocBaml 工具，就準備好用它來剖析 HelloApp.resources.dll，以擷取要當地語系化的文字內容。</span><span class="sxs-lookup"><span data-stu-id="08a32-156">Now that you have created the LocBaml tool, you are ready to use it to parse HelloApp.resources.dll to extract the text content that will be localized.</span></span>  
  
1. <span data-ttu-id="08a32-157">將 LocBaml.exe 複製到應用程式的 bin\debug 資料夾，這是建立主要應用程式組件的位置。</span><span class="sxs-lookup"><span data-stu-id="08a32-157">Copy LocBaml.exe to your application's bin\debug folder, where the main application assembly was created.</span></span>  
  
2. <span data-ttu-id="08a32-158">若要剖析附屬組件檔案，並將輸出儲存成 .csv 檔案，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="08a32-158">To parse the satellite assembly file and store the output as a .csv file, use the following command:</span></span>  
  
   `LocBaml.exe /parse HelloApp.resources.dll /out:Hello.csv`
  
   > [!NOTE]
   > <span data-ttu-id="08a32-159">如果輸入檔 HelloApp.resources.dll 不是在與 LocBaml.exe 相同的目錄中，請移動其中一個檔案，讓這兩個檔案都在相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="08a32-159">If the input file, HelloApp.resources.dll, is not in the same directory as LocBaml.exe move one of the files so that both files are in the same directory.</span></span>  
  
3. <span data-ttu-id="08a32-160">當您執行 LocBaml 來剖析檔案時，輸出中會包含以逗號 (.csv 檔案) 或定位點 (.txt 檔) 分隔的七個欄位。</span><span class="sxs-lookup"><span data-stu-id="08a32-160">When you run LocBaml to parse files, the output consists of seven fields delimited by commas (.csv files) or tabs (.txt files).</span></span> <span data-ttu-id="08a32-161">下面顯示針對 HelloApp.resources.dll 所剖析的 .csv 檔案：</span><span class="sxs-lookup"><span data-stu-id="08a32-161">The following shows the parsed .csv file for the HelloApp.resources.dll:</span></span>

   | |
   |-|
   |<span data-ttu-id="08a32-162">HelloApp.g.en-US.resources:window1.baml,Stack1:System.Windows.Controls.StackPanel.$Content,Ignore,FALSE, FALSE,,#Text1;#Text2;</span><span class="sxs-lookup"><span data-stu-id="08a32-162">HelloApp.g.en-US.resources:window1.baml,Stack1:System.Windows.Controls.StackPanel.$Content,Ignore,FALSE, FALSE,,#Text1;#Text2;</span></span>|
   |<span data-ttu-id="08a32-163">HelloApp.g.en-US.resources:window1.baml,Text1:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Hello World</span><span class="sxs-lookup"><span data-stu-id="08a32-163">HelloApp.g.en-US.resources:window1.baml,Text1:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Hello World</span></span>|
   |<span data-ttu-id="08a32-164">HelloApp.g.en-US.resources:window1.baml,Text2:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Goodbye World</span><span class="sxs-lookup"><span data-stu-id="08a32-164">HelloApp.g.en-US.resources:window1.baml,Text2:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Goodbye World</span></span>|

   <span data-ttu-id="08a32-165">這七個欄位為：</span><span class="sxs-lookup"><span data-stu-id="08a32-165">The seven fields are:</span></span>  
  
   - <span data-ttu-id="08a32-166">**BAML 名稱**。</span><span class="sxs-lookup"><span data-stu-id="08a32-166">**BAML Name**.</span></span> <span data-ttu-id="08a32-167">有關來源語言附屬組件的 BAML 資源名稱。</span><span class="sxs-lookup"><span data-stu-id="08a32-167">The name of the BAML resource with respect to the source language satellite assembly.</span></span>  
  
   - <span data-ttu-id="08a32-168">**資源金鑰**。</span><span class="sxs-lookup"><span data-stu-id="08a32-168">**Resource Key**.</span></span> <span data-ttu-id="08a32-169">當地語系化的資源識別碼。</span><span class="sxs-lookup"><span data-stu-id="08a32-169">The localized resource identifier.</span></span>  
  
   - <span data-ttu-id="08a32-170">**類別**。</span><span class="sxs-lookup"><span data-stu-id="08a32-170">**Category**.</span></span> <span data-ttu-id="08a32-171">值型別。</span><span class="sxs-lookup"><span data-stu-id="08a32-171">The value type.</span></span> <span data-ttu-id="08a32-172">請參閱[當地語系化屬性和批註](localization-attributes-and-comments.md)。</span><span class="sxs-lookup"><span data-stu-id="08a32-172">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   - <span data-ttu-id="08a32-173">**可讀性**。</span><span class="sxs-lookup"><span data-stu-id="08a32-173">**Readability**.</span></span> <span data-ttu-id="08a32-174">當地語系化工具是否能夠讀取該值。</span><span class="sxs-lookup"><span data-stu-id="08a32-174">Whether the value can be read by a localizer.</span></span> <span data-ttu-id="08a32-175">請參閱[當地語系化屬性和批註](localization-attributes-and-comments.md)。</span><span class="sxs-lookup"><span data-stu-id="08a32-175">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   - <span data-ttu-id="08a32-176">**可修改性**。</span><span class="sxs-lookup"><span data-stu-id="08a32-176">**Modifiability**.</span></span> <span data-ttu-id="08a32-177">當地語系化工具是否能夠修改該值。</span><span class="sxs-lookup"><span data-stu-id="08a32-177">Whether the value can be modified by a localizer.</span></span> <span data-ttu-id="08a32-178">請參閱[當地語系化屬性和批註](localization-attributes-and-comments.md)。</span><span class="sxs-lookup"><span data-stu-id="08a32-178">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   - <span data-ttu-id="08a32-179">**批註**。</span><span class="sxs-lookup"><span data-stu-id="08a32-179">**Comments**.</span></span> <span data-ttu-id="08a32-180">該值的其他說明，有助於判斷某值當地語系化的方式。</span><span class="sxs-lookup"><span data-stu-id="08a32-180">Additional description of the value to help determine how a value is localized.</span></span> <span data-ttu-id="08a32-181">請參閱[當地語系化屬性和批註](localization-attributes-and-comments.md)。</span><span class="sxs-lookup"><span data-stu-id="08a32-181">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   - <span data-ttu-id="08a32-182">**值**。</span><span class="sxs-lookup"><span data-stu-id="08a32-182">**Value**.</span></span> <span data-ttu-id="08a32-183">要轉譯成所需文化特性的文字值。</span><span class="sxs-lookup"><span data-stu-id="08a32-183">The text value to translate to the desired culture.</span></span>  
  
   <span data-ttu-id="08a32-184">下表顯示這些欄位如何對應至 .csv 檔案的分隔值：</span><span class="sxs-lookup"><span data-stu-id="08a32-184">The following table shows how these fields map to the delimited values of the .csv file:</span></span>  
  
   |<span data-ttu-id="08a32-185">BAML 名稱</span><span class="sxs-lookup"><span data-stu-id="08a32-185">BAML name</span></span>|<span data-ttu-id="08a32-186">資源索引鍵</span><span class="sxs-lookup"><span data-stu-id="08a32-186">Resource key</span></span>|<span data-ttu-id="08a32-187">類別</span><span class="sxs-lookup"><span data-stu-id="08a32-187">Category</span></span>|<span data-ttu-id="08a32-188">可讀性</span><span class="sxs-lookup"><span data-stu-id="08a32-188">Readability</span></span>|<span data-ttu-id="08a32-189">可修改性</span><span class="sxs-lookup"><span data-stu-id="08a32-189">Modifiability</span></span>|<span data-ttu-id="08a32-190">註解</span><span class="sxs-lookup"><span data-stu-id="08a32-190">Comments</span></span>|<span data-ttu-id="08a32-191">值</span><span class="sxs-lookup"><span data-stu-id="08a32-191">Value</span></span>|  
   |---------------|------------------|--------------|-----------------|-------------------|--------------|-----------|
   |<span data-ttu-id="08a32-192">HelloApp.g.en-US.resources:window1.baml</span><span class="sxs-lookup"><span data-stu-id="08a32-192">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="08a32-193">Stack1:System.Windows.Controls.StackPanel.$Content</span><span class="sxs-lookup"><span data-stu-id="08a32-193">Stack1:System.Windows.Controls.StackPanel.$Content</span></span>|<span data-ttu-id="08a32-194">略過</span><span class="sxs-lookup"><span data-stu-id="08a32-194">Ignore</span></span>|<span data-ttu-id="08a32-195">FALSE</span><span class="sxs-lookup"><span data-stu-id="08a32-195">FALSE</span></span>|<span data-ttu-id="08a32-196">FALSE</span><span class="sxs-lookup"><span data-stu-id="08a32-196">FALSE</span></span>||<span data-ttu-id="08a32-197">#Text1;#Text2</span><span class="sxs-lookup"><span data-stu-id="08a32-197">#Text1;#Text2</span></span>|
   |<span data-ttu-id="08a32-198">HelloApp.g.en-US.resources:window1.baml</span><span class="sxs-lookup"><span data-stu-id="08a32-198">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="08a32-199">Text1:System.Windows.Controls.TextBlock.$Content</span><span class="sxs-lookup"><span data-stu-id="08a32-199">Text1:System.Windows.Controls.TextBlock.$Content</span></span>|<span data-ttu-id="08a32-200">無</span><span class="sxs-lookup"><span data-stu-id="08a32-200">None</span></span>|<span data-ttu-id="08a32-201">TRUE</span><span class="sxs-lookup"><span data-stu-id="08a32-201">TRUE</span></span>|<span data-ttu-id="08a32-202">TRUE</span><span class="sxs-lookup"><span data-stu-id="08a32-202">TRUE</span></span>||<span data-ttu-id="08a32-203">Hello World</span><span class="sxs-lookup"><span data-stu-id="08a32-203">Hello World</span></span>|
   |<span data-ttu-id="08a32-204">HelloApp.g.en-US.resources:window1.baml</span><span class="sxs-lookup"><span data-stu-id="08a32-204">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="08a32-205">Text2:System.Windows.Controls.TextBlock.$Content</span><span class="sxs-lookup"><span data-stu-id="08a32-205">Text2:System.Windows.Controls.TextBlock.$Content</span></span>|<span data-ttu-id="08a32-206">無</span><span class="sxs-lookup"><span data-stu-id="08a32-206">None</span></span>|<span data-ttu-id="08a32-207">TRUE</span><span class="sxs-lookup"><span data-stu-id="08a32-207">TRUE</span></span>|<span data-ttu-id="08a32-208">TRUE</span><span class="sxs-lookup"><span data-stu-id="08a32-208">TRUE</span></span>||<span data-ttu-id="08a32-209">Goodbye World</span><span class="sxs-lookup"><span data-stu-id="08a32-209">Goodbye World</span></span>|
  
   <span data-ttu-id="08a32-210">請注意，[**批註**] 欄位的所有值都不包含任何值。如果欄位沒有值，則會是空的。</span><span class="sxs-lookup"><span data-stu-id="08a32-210">Notice that all the values for the **Comments** field contain no values; if a field doesn't have a value, it is empty.</span></span> <span data-ttu-id="08a32-211">另請注意，第一個資料列中的專案既不是可讀取也不能修改，而且具有「忽略」做為它的**分類**值，全都表示此值無法當地語系化。</span><span class="sxs-lookup"><span data-stu-id="08a32-211">Also notice that the item in the first row is neither readable nor modifiable, and has "Ignore" as its **Category** value, all of which indicates that the value is not localizable.</span></span>  
  
4. <span data-ttu-id="08a32-212">為了方便探索已剖析檔案中的可當地語系化專案，特別是在大型檔案中，您可以依**類別**、**可讀性**和可**修改**性來排序或篩選項目。</span><span class="sxs-lookup"><span data-stu-id="08a32-212">To facilitate discovery of localizable items in parsed files, particularly in large files, you can sort or filter the items by **Category**, **Readability**, and **Modifiability**.</span></span> <span data-ttu-id="08a32-213">例如，您可以篩選出無法讀取及無法修改的值。</span><span class="sxs-lookup"><span data-stu-id="08a32-213">For example, you can filter out unreadable and unmodifiable values.</span></span>  
  
## <a name="translate-the-localizable-content"></a><span data-ttu-id="08a32-214">翻譯可當地語系化的內容</span><span class="sxs-lookup"><span data-stu-id="08a32-214">Translate the localizable content</span></span>

<span data-ttu-id="08a32-215">使用您可以用來轉譯擷取內容的任何工具。</span><span class="sxs-lookup"><span data-stu-id="08a32-215">Use any tool that you have available to translate the extracted content.</span></span> <span data-ttu-id="08a32-216">執行這項操作的好方法是將資源寫入 .csv 檔案，並在 Microsoft Excel 中加以查看，對最後一個資料行（值）進行轉譯變更。</span><span class="sxs-lookup"><span data-stu-id="08a32-216">A good way to do this is to write the resources to a .csv file and view them in Microsoft Excel, making translation changes to the last column (value).</span></span>  
  
## <a name="use-locbaml-to-generate-a-new-resourcesdll-file"></a><span data-ttu-id="08a32-217">使用 LocBaml 產生新的 .resources .dll 檔案</span><span class="sxs-lookup"><span data-stu-id="08a32-217">Use LocBaml to generate a new .resources.dll file</span></span>

<span data-ttu-id="08a32-218">藉由使用 LocBaml 來剖析 HelloApp.resources.dll 而識別的內容已轉譯，且必須合併回原始應用程式。</span><span class="sxs-lookup"><span data-stu-id="08a32-218">The content that was identified by parsing HelloApp.resources.dll with LocBaml has been translated and must be merged back into the original application.</span></span> <span data-ttu-id="08a32-219">使用 `generate` 或 `-g` 選項來產生新的 .resources .dll 檔案。</span><span class="sxs-lookup"><span data-stu-id="08a32-219">Use the `generate` or `-g` option to generate a new .resources.dll file.</span></span>  
  
1. <span data-ttu-id="08a32-220">使用下列語法來產生新的 HelloApp.resources.dll 檔案。</span><span class="sxs-lookup"><span data-stu-id="08a32-220">Use the following syntax to generate a new HelloApp.resources.dll file.</span></span> <span data-ttu-id="08a32-221">將文化特性標示為 en-US (/cul:en-US)。</span><span class="sxs-lookup"><span data-stu-id="08a32-221">Mark the culture as en-US (/cul:en-US).</span></span>  
  
   `LocBaml.exe /generate HelloApp.resources.dll /trans:Hello.csv /out:c:\ /cul:en-US`  

   > [!NOTE]
   > <span data-ttu-id="08a32-222">如果輸入檔 Hello.csv 不是在與可執行檔 LocBaml.exe 相同的目錄中，請移動其中一個檔案，讓這兩個檔案都在相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="08a32-222">If the input file, Hello.csv, is not in the same directory as the executable, LocBaml.exe, move one of the files so that both files are in the same directory.</span></span>  
  
2. <span data-ttu-id="08a32-223">將*C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll*目錄中的舊*HelloApp*取代為新建立的*HelloApp .resources*檔案。</span><span class="sxs-lookup"><span data-stu-id="08a32-223">Replace the old *HelloApp.resources.dll* file in the *C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll* directory with your newly created *HelloApp.resources.dll* file.</span></span>  
  
3. <span data-ttu-id="08a32-224">"Hello World" 和 "Goodbye World" 現在應該已在您的應用程式中轉譯。</span><span class="sxs-lookup"><span data-stu-id="08a32-224">"Hello World" and "Goodbye World" should now be translated in your application.</span></span>  
  
4. <span data-ttu-id="08a32-225">若要轉譯為不同的文化特性，請使用您想要轉譯之語言的文化特性。</span><span class="sxs-lookup"><span data-stu-id="08a32-225">To translate to a different culture, use the culture of the language that you are translating to.</span></span> <span data-ttu-id="08a32-226">下列範例示範如何轉譯成加拿大法文：</span><span class="sxs-lookup"><span data-stu-id="08a32-226">The following example shows how to translate to French-Canadian:</span></span>  
  
   `LocBaml.exe /generate HelloApp.resources.dll /trans:Hellofr-CA.csv /out:c:\ /cul:fr-CA`  
  
5. <span data-ttu-id="08a32-227">在與主應用程式組件相同的組件中，建立新的特定文化特性資料夾，以存放新的附屬組件。</span><span class="sxs-lookup"><span data-stu-id="08a32-227">In the same assembly as the main application assembly, create a new culture-specific folder to house the new satellite assembly.</span></span> <span data-ttu-id="08a32-228">針對加拿大法文，資料夾會是 fr-CA。</span><span class="sxs-lookup"><span data-stu-id="08a32-228">For French-Canadian, the folder would be fr-CA.</span></span>  
  
6. <span data-ttu-id="08a32-229">將所產生的附屬組件複製到新的資料夾。</span><span class="sxs-lookup"><span data-stu-id="08a32-229">Copy the generated satellite assembly to the new folder.</span></span>  
  
7. <span data-ttu-id="08a32-230">若要測試新的附屬組件，您需要變更您的應用程式用來執行的文化特性。</span><span class="sxs-lookup"><span data-stu-id="08a32-230">To test the new satellite assembly, you need to change the culture under which your application will run.</span></span> <span data-ttu-id="08a32-231">您可以使用下列其中一種作法：</span><span class="sxs-lookup"><span data-stu-id="08a32-231">You can do this in one of two ways:</span></span>  
  
   - <span data-ttu-id="08a32-232">變更作業系統的地區設定。</span><span class="sxs-lookup"><span data-stu-id="08a32-232">Change your operating system's regional settings.</span></span>
  
   - <span data-ttu-id="08a32-233">在您的應用程式中，將下列程式碼加入 App.xaml.cs：</span><span class="sxs-lookup"><span data-stu-id="08a32-233">In your application, add the following code to App.xaml.cs:</span></span>  
  
     [!code-xaml[LocBamlChangeCultureSnippets#LocBamlChangeCultureMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml#locbamlchangeculturemarkup)]
     [!code-csharp[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml.cs#locbamlchangeculturecodebehind)]
     [!code-vb[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/VisualBasic/Application.xaml.vb#locbamlchangeculturecodebehind)]  
  
## <a name="tips-for-using-locbaml"></a><span data-ttu-id="08a32-234">使用 LocBaml 的秘訣</span><span class="sxs-lookup"><span data-stu-id="08a32-234">Tips for Using LocBaml</span></span>  
  
- <span data-ttu-id="08a32-235">用來定義自訂控制項的所有相依組件，都必須複製到 LocBaml 的本機目錄中，或安裝至 GAC 中。</span><span class="sxs-lookup"><span data-stu-id="08a32-235">All dependent assemblies that define custom controls must be copied into the local directory of LocBaml or installed into the GAC.</span></span> <span data-ttu-id="08a32-236">這是必要的，因為當地語系化 API 在讀取二進位 XAML （BAML）時，必須擁有相依元件的存取權。</span><span class="sxs-lookup"><span data-stu-id="08a32-236">This is necessary because the localization API must have access to the dependent assemblies when it reads the binary XAML (BAML).</span></span>  
  
- <span data-ttu-id="08a32-237">如果主要組件已簽署，所產生的資源 DLL 也必須簽署，才能將其載入。</span><span class="sxs-lookup"><span data-stu-id="08a32-237">If the main assembly is signed, the generated resource DLL must also be signed in order for it to be loaded.</span></span>  
  
- <span data-ttu-id="08a32-238">當地語系化資源 DLL 的版本必須與主要組件同步處理。</span><span class="sxs-lookup"><span data-stu-id="08a32-238">The version of the localized resource DLL needs to be synchronized with the main assembly.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="08a32-239">請參閱</span><span class="sxs-lookup"><span data-stu-id="08a32-239">See also</span></span>

- [<span data-ttu-id="08a32-240">WPF 的全球化</span><span class="sxs-lookup"><span data-stu-id="08a32-240">Globalization for WPF</span></span>](globalization-for-wpf.md)
- [<span data-ttu-id="08a32-241">使用自動配置概觀</span><span class="sxs-lookup"><span data-stu-id="08a32-241">Use Automatic Layout Overview</span></span>](use-automatic-layout-overview.md)
