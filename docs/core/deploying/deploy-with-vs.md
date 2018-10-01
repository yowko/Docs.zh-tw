---
title: 使用 Visual Studio 部署 .NET Core 應用程式
description: 了解使用 Visual Studio 的 .NET Core 應用程式部署
author: rpetrusha
ms.author: ronpet
ms.date: 09/03/2018
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 7a9410ca99f621ee6d0e8b263354ebc536f71a4a
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2018
ms.locfileid: "47204293"
---
# <a name="deploying-net-core-apps-with-visual-studio"></a><span data-ttu-id="6f0e9-103">使用 Visual Studio 部署 .NET Core 應用程式</span><span class="sxs-lookup"><span data-stu-id="6f0e9-103">Deploying .NET Core apps with Visual Studio</span></span>

<span data-ttu-id="6f0e9-104">您可以將 .NET Core 應用程式部署為「與 Framework 相依的部署」，其中包含您的應用程式二進位檔，但取決於目標系統上是否有 .NET Core 存在，也可以部署為「自封式部署」，其中包含您的應用程式和 .NET Core 二進位檔。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-104">You can deploy a .NET Core application either as a *framework-dependent deployment*, which includes your application binaries but depends on the presence of .NET Core on the target system, or as a *self-contained deployment*, which includes both your application and .NET Core binaries.</span></span> <span data-ttu-id="6f0e9-105">如需 .NET Core 應用程式部署的概觀，請參閱 [.NET Core 應用程式部署](index.md)。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-105">For an overview of .NET Core application deployment, see [.NET Core Application Deployment](index.md).</span></span>

<span data-ttu-id="6f0e9-106">下列各節顯示如何使用 Microsoft Visual Studio 來建立下列類型的部署：</span><span class="sxs-lookup"><span data-stu-id="6f0e9-106">The following sections show how to use Microsoft Visual Studio to create the following kinds of deployments:</span></span>

- <span data-ttu-id="6f0e9-107">與 Framework 相依的部署</span><span class="sxs-lookup"><span data-stu-id="6f0e9-107">Framework-dependent deployment</span></span>
- <span data-ttu-id="6f0e9-108">有協力廠商相依性的 Framework 相依部署</span><span class="sxs-lookup"><span data-stu-id="6f0e9-108">Framework-dependent deployment with third-party dependencies</span></span>
- <span data-ttu-id="6f0e9-109">自封式部署</span><span class="sxs-lookup"><span data-stu-id="6f0e9-109">Self-contained deployment</span></span>
- <span data-ttu-id="6f0e9-110">有協力廠商相依性的自封式部署</span><span class="sxs-lookup"><span data-stu-id="6f0e9-110">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="6f0e9-111">如需使用 Visual Studio 來開發 .NET Core 應用程式的資訊，請參閱 [Windows 上 .NET Core 的必要條件](../windows-prerequisites.md#prerequisites-with-visual-studio-2017)。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-111">For information on using Visual Studio to develop .NET Core applications, see [Prerequisites for .NET Core on Windows](../windows-prerequisites.md#prerequisites-with-visual-studio-2017).</span></span>

## <a name="framework-dependent-deployment"></a><span data-ttu-id="6f0e9-112">與 Framework 相依的部署</span><span class="sxs-lookup"><span data-stu-id="6f0e9-112">Framework-dependent deployment</span></span>

<span data-ttu-id="6f0e9-113">部署無任何協力廠商相依性的 Framework 相依部署，只涉及建置、測試和發行應用程式。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-113">Deploying a framework-dependent deployment with no third-party dependencies simply involves building, testing, and publishing the app.</span></span> <span data-ttu-id="6f0e9-114">以 C# 撰寫的簡單範例會說明此程序。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-114">A simple example written in C# illustrates the process.</span></span>  

1. <span data-ttu-id="6f0e9-115">建立專案。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-115">Create the project.</span></span>

   <span data-ttu-id="6f0e9-116">選取 [檔案]  >  [新增]  >  [專案]。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-116">Select **File** > **New** > **Project**.</span></span> <span data-ttu-id="6f0e9-117">在 [新增專案] 對話方塊中，展開 [已安裝] 專案類型窗格中的語言 (C# 或 Visual Basic) 專案類別，選擇 [.NET Core]，然後選擇中央窗格中的 [主控台應用程式 (.NET Core)] 範本。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-117">In the **New Project** dialog, expand your language's (C# or Visual Basic) project categories in the **Installed** project types pane, choose **.NET Core**, and then select the **Console App (.NET Core)** template in the center pane.</span></span> <span data-ttu-id="6f0e9-118">在 [名稱] 文字方塊中輸入專案名稱，例如 "FDD"。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-118">Enter a project name, such as "FDD", in the **Name** text box.</span></span> <span data-ttu-id="6f0e9-119">選取 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-119">Select the **OK** button.</span></span>

1. <span data-ttu-id="6f0e9-120">新增應用程式的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-120">Add the application's source code.</span></span>

   <span data-ttu-id="6f0e9-121">在編輯器中開啟 *Program.cs* 或 *Program.vb* 檔案，並用下列程式碼取代自動產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-121">Open the *Program.cs* or *Program.vb* file in the editor and replace the auto-generated code with the following code.</span></span> <span data-ttu-id="6f0e9-122">它會提示使用者輸入文字，並顯示使用者輸入的個別文字。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-122">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="6f0e9-123">它會使用規則運算式 `\w+` 分隔輸入文字中的字詞。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-123">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]

1. <span data-ttu-id="6f0e9-124">建立應用程式的偵錯組建。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-124">Create a Debug build of your app.</span></span>

   <span data-ttu-id="6f0e9-125">選取 [組建]  >  [組建方案]。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-125">Select **Build** > **Build Solution**.</span></span> <span data-ttu-id="6f0e9-126">您也可以編譯並執行應用程式的偵錯組建，方法是選取 [偵錯]  >  [開始偵錯]。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-126">You can also compile and run the Debug build of your application by selecting **Debug** > **Start Debugging**.</span></span>

1. <span data-ttu-id="6f0e9-127">部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-127">Deploy your app.</span></span>

   <span data-ttu-id="6f0e9-128">在您偵錯並測試程式之後，請建立要隨應用程式一起部署的檔案。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-128">After you've debugged and tested the program, create the files to be deployed with your app.</span></span> <span data-ttu-id="6f0e9-129">若要從 Visual Studio 發行，請執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="6f0e9-129">To publish from Visual Studio, do the following:</span></span>

      1. <span data-ttu-id="6f0e9-130">在工具列上將方案組態從 [偵錯] 變更為 [發行]，以組建應用程式的發行 (而不是偵錯) 版本。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-130">Change the solution configuration from **Debug** to **Release** on the toolbar to build a Release (rather than a Debug) version of your app.</span></span>

      1. <span data-ttu-id="6f0e9-131">以滑鼠右鍵按一下方案總管中的專案 (而非方案)，然後選取 [發行]。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-131">Right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

      1. <span data-ttu-id="6f0e9-132">在 [發行] 索引標籤中，選取 [發行]。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-132">In the **Publish** tab, select **Publish**.</span></span> <span data-ttu-id="6f0e9-133">Visual Studio 會將構成應用程式的檔案寫入至本機檔案系統。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-133">Visual Studio writes the files that comprise your application to the local file system.</span></span>

      1. <span data-ttu-id="6f0e9-134">[發行] 索引標籤現在會顯示單一設定檔 **FolderProfile**。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-134">The **Publish** tab now shows a single profile, **FolderProfile**.</span></span> <span data-ttu-id="6f0e9-135">設定檔的組態設定顯示在索引標籤的 [摘要] 區段中。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-135">The profile's configuration settings are shown in the **Summary** section of the tab.</span></span>

   <span data-ttu-id="6f0e9-136">產生的檔案會放在 Windows 系統上名為 `Publish` 的目錄，以及 Unix 系統上名為 `publish` 的目錄中，而該目錄位於您專案之 *.\bin\release\netcoreapp2.1* 子目錄的子目錄中。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-136">The resulting files are placed in a directory named `Publish` on Windows and `publish` on Unix systems that is in a subdirectory of your project's *.\bin\release\netcoreapp2.1* subdirectory.</span></span>

<span data-ttu-id="6f0e9-137">隨著應用程式檔案一起，發佈程序會發出程式資料庫 (.pdb) 檔案，其中包含應用程式的偵錯資訊。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-137">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="6f0e9-138">該檔案主要是用於例外狀況偵錯。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-138">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="6f0e9-139">您可以選擇不與您的應用程式檔案一起封裝它。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-139">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="6f0e9-140">不過，如果您要對應用程式的發行組建進行偵錯，則應該將其儲存。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-140">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="6f0e9-141">以任何您想要的方式，部署整組應用程式檔案。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-141">Deploy the complete set of application files in any way you like.</span></span> <span data-ttu-id="6f0e9-142">例如，您可以使用簡單的 `copy` 命令將它們封裝在 ZIP 檔案中，或與您選擇的任何安裝套件一起部署。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-142">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span> <span data-ttu-id="6f0e9-143">安裝之後，使用者可以使用 `dotnet` 命令並提供應用程式的檔名 (例如，`dotnet fdd.dll`)，來執行您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-143">Once installed, users can then execute your application by using the `dotnet` command and providing the application filename, such as `dotnet fdd.dll`.</span></span>

<span data-ttu-id="6f0e9-144">除了應用程式二進位檔之外，安裝程式也應該配套共用的 Framework 安裝程式，，或勾選為必要條件當成應用程式安裝的一部分。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-144">In addition to the application binaries, your installer should also either bundle the shared framework installer or check for it as a prerequisite as part of the application installation.</span></span>  <span data-ttu-id="6f0e9-145">共用 Framework 安裝需要系統管理員/根目錄存取權，因為它要通行全機器。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-145">Installation of the shared framework requires Administrator/root access since it is machine-wide.</span></span>

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a><span data-ttu-id="6f0e9-146">有協力廠商相依性的 Framework 相依部署</span><span class="sxs-lookup"><span data-stu-id="6f0e9-146">Framework-dependent deployment with third-party dependencies</span></span>

<span data-ttu-id="6f0e9-147">部署具有一或多個協力廠商相依性的 Framework 相依部署時，需要任何相依性都可供專案使用。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-147">Deploying a framework-dependent deployment with one or more third-party dependencies requires that any dependencies be available to your project.</span></span> <span data-ttu-id="6f0e9-148">在組建您的應用程式之前，需要執行下列其他步驟：</span><span class="sxs-lookup"><span data-stu-id="6f0e9-148">The following additional steps are required before you can build your app:</span></span>

1. <span data-ttu-id="6f0e9-149">使用 [NuGet 套件管理員]，將 NuGet 套件的參考新增至您的專案；如果您的系統上還沒有該套件，請安裝它。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-149">Use the **NuGet Package Manager** to add a reference to a NuGet package to your project; and if the package is not already available on your system, install it.</span></span> <span data-ttu-id="6f0e9-150">若要開啟套件管理員，請選取 [工具]  >  [NuGet 套件管理員]  >  [管理方案的 NuGet 套件]。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-150">To open the package manager, select **Tools** > **NuGet Package Manager** > **Manage NuGet Packages for Solution**.</span></span>

1. <span data-ttu-id="6f0e9-151">確認 `Newtonsoft.Json` 已安裝在您的系統上，如果尚未安裝，請安裝它。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-151">Confirm that `Newtonsoft.Json` is installed on your system and, if it is not, install it.</span></span> <span data-ttu-id="6f0e9-152">[已安裝] 索引標籤會列出您系統上已安裝的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-152">The **Installed** tab lists NuGet packages installed on your system.</span></span> <span data-ttu-id="6f0e9-153">如果 `Newtonsoft.Json` 未列於該處，請選取 [瀏覽] 索引標籤，然後在 [搜尋] 方塊中輸入 "Newtonsoft.Json"。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-153">If `Newtonsoft.Json` is not listed there, select the **Browse** tab and enter "Newtonsoft.Json" in the search box.</span></span> <span data-ttu-id="6f0e9-154">選取 `Newtonsoft.Json`，並先在右窗格中選取您的專案，然後選取 [安裝]。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-154">Select `Newtonsoft.Json` and, in the right pane, select your project before selecting **Install**.</span></span>

1. <span data-ttu-id="6f0e9-155">如果 `Newtonsoft.Json` 已安裝在您的系統上，請在 [管理方案的封裝] 索引標籤的右窗格中選取您的專案，以將它新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-155">If `Newtonsoft.Json` is already installed on your system, add it to your project by selecting your project in the right pane of the **Manage Packages for Solution** tab.</span></span>

<span data-ttu-id="6f0e9-156">請注意，具有協力廠商相依性的 Framework 相依部署，可攜性只與其協力廠商相依性一致。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-156">Note that a framework-dependent deployment with third-party dependencies is only as portable as its third-party dependencies.</span></span> <span data-ttu-id="6f0e9-157">例如，如果協力廠商程式庫只支援 macOS，則應用程式就無法攜至 Windows 系統。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-157">For example, if a third-party library only supports macOS, the app isn't portable to Windows systems.</span></span> <span data-ttu-id="6f0e9-158">如果協力廠商相依性本身依賴於原生程式碼，就會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-158">This happens if the third-party dependency itself depends on native code.</span></span> <span data-ttu-id="6f0e9-159">其中一個絶佳範例是 [Kestrel 伺服器](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel)，它需要對 [libuv](https://github.com/libuv/libuv) 的原生相依性。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-159">A good example of this is [Kestrel server](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), which requires a native dependency on [libuv](https://github.com/libuv/libuv).</span></span> <span data-ttu-id="6f0e9-160">當具有這類協力廠商相依性的應用程式建立了 FDD 時，已發行輸出就會包含原生相依性支援的每個[執行階段識別碼 (RID)](../rid-catalog.md) 資料夾 (存在於其 NuGet 套件中)。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-160">When an FDD is created for an application with this kind of third-party dependency, the published output contains a folder for each [Runtime Identifier (RID)](../rid-catalog.md) that the native dependency supports (and that exists in its NuGet package).</span></span>

## <a name="simpleSelf"></a> <span data-ttu-id="6f0e9-161">沒有協力廠商相依性的自封式部署</span><span class="sxs-lookup"><span data-stu-id="6f0e9-161">Self-contained deployment without third-party dependencies</span></span>

<span data-ttu-id="6f0e9-162">部署無任何協力廠商相依性的自封式部署，涉及建立專案、修改 *csproj* 檔案、組建、測試以及發行應用程式。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-162">Deploying a self-contained deployment with no third-party dependencies involves creating the project, modifying the *csproj* file, building, testing, and publishing the app.</span></span> <span data-ttu-id="6f0e9-163">以 C# 撰寫的簡單範例會說明此程序。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-163">A simple example written in C# illustrates the process.</span></span> <span data-ttu-id="6f0e9-164">您首先要建立、編碼和測試您的專案，就像相依於 Framework 的部署一樣：</span><span class="sxs-lookup"><span data-stu-id="6f0e9-164">You begin by creating, coding, and testing your project just as you would a framework-dependent deployment:</span></span>

1. <span data-ttu-id="6f0e9-165">建立專案。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-165">Create the project.</span></span>

   <span data-ttu-id="6f0e9-166">選取 [檔案]  >  [新增]  >  [專案]。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-166">Select **File** > **New** > **Project**.</span></span> <span data-ttu-id="6f0e9-167">在 [新增專案] 對話方塊中，展開 [已安裝] 專案類型窗格中的語言 (C# 或 Visual Basic) 專案類別，選擇 [.NET Core]，然後選擇中央窗格中的 [主控台應用程式 (.NET Core)] 範本。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-167">In the **New Project** dialog, expand your language's (C# or Visual Basic) project categories in the **Installed** project types pane, choose **.NET Core**, and then select the **Console App (.NET Core)** template in the center pane.</span></span> <span data-ttu-id="6f0e9-168">在 [名稱] 文字方塊中輸入專案名稱 (例如 "SCD")，然後選取 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-168">Enter a project name, such as "SCD", in the **Name** text box, and select the **OK** button.</span></span>

1. <span data-ttu-id="6f0e9-169">新增應用程式的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-169">Add the application's source code.</span></span>

   <span data-ttu-id="6f0e9-170">在您的編輯器中開啟 *Program.cs* 或檔案，並以下列程式碼取代自動產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-170">Open the *Program.cs* or file in your editor, and replace the auto-generated code with the following code.</span></span> <span data-ttu-id="6f0e9-171">它會提示使用者輸入文字，並顯示使用者輸入的個別文字。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-171">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="6f0e9-172">它會使用規則運算式 `\w+` 分隔輸入文字中的字詞。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-172">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]

1. <span data-ttu-id="6f0e9-173">決定您是否想使用全域無差異模式。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-173">Determine whether you want to use globalization invariant mode.</span></span>

   <span data-ttu-id="6f0e9-174">尤其當您的應用程式以 Linux 為目標時，使用全域無差異模式[能減少您部署的總大小](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-174">Particularly if your app targets Linux, you can reduce the total size of your deployment by taking advantage of [globalization invariant mode](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md).</span></span> <span data-ttu-id="6f0e9-175">全域無差異模式適用於非全域應用程式，其能使用格式化慣例、大小寫慣例及字串比較，還有不因文化特性而異的[排列次序](xref:System.Globalization.CultureInfo.InvariantCulture)。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-175">Globalization invariant mode is useful for applications that are not globally aware and that can use the formatting conventions, casing conventions, and string comparison and sort order of the [invariant culture](xref:System.Globalization.CultureInfo.InvariantCulture).</span></span>

   <span data-ttu-id="6f0e9-176">在您的專案 (而非解決方案) 點擊右鍵，進入 [方案總管]，然後選取 [Edit SCD.csproj] \(編輯 SCD.csproj\) 或 [Edit SCD.vbproj] \(編輯 SCD.vbproj\) 啟用非變異模式。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-176">To enable invariant mode, right-click on your project (not the solution) in **Solution Explorer**, and select **Edit SCD.csproj** or **Edit SCD.vbproj**.</span></span> <span data-ttu-id="6f0e9-177">接著，將反白處新增至檔案中：</span><span class="sxs-lookup"><span data-stu-id="6f0e9-177">Then add the following highlighted lines to the file:</span></span>

 [!code-xml[globalization-invariant-mode](~/samples/snippets/core/deploying/xml/invariant.csproj)]

1. <span data-ttu-id="6f0e9-178">建立應用程式的偵錯組建。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-178">Create a Debug build of your application.</span></span>

   <span data-ttu-id="6f0e9-179">選取 [組建]  >  [組建方案]。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-179">Select **Build** > **Build Solution**.</span></span> <span data-ttu-id="6f0e9-180">您也可以編譯並執行應用程式的偵錯組建，方法是選取 [偵錯]  >  [開始偵錯]。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-180">You can also compile and run the Debug build of your application by selecting **Debug** > **Start Debugging**.</span></span> <span data-ttu-id="6f0e9-181">透過此偵錯步驟，您可以識別應用程式在主機平台上執行時的問題。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-181">This debugging step lets you identify problems with your application when it's running on your host platform.</span></span> <span data-ttu-id="6f0e9-182">您仍然必須在每個目標平台上進行測試。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-182">You still will have to test it on each of your target platforms.</span></span>

   <span data-ttu-id="6f0e9-183">如果您啟用了不因全球化而異的模式，請務必測試您的應用程式是否適合缺少不區分文化特性的資料。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-183">If you've enabled globalization invariant mode, be particularly sure to test whether the absence of culture-sensitive data is suitable for your application.</span></span>

<span data-ttu-id="6f0e9-184">完成偵錯之後，您即可以發行獨立式部署：</span><span class="sxs-lookup"><span data-stu-id="6f0e9-184">Once you've finished debugging, you can publish your self-contained deployment:</span></span>

# <a name="visual-studio-156-and-earliertabvs156"></a>[<span data-ttu-id="6f0e9-185">Visual Studio 15.6 和更早版本</span><span class="sxs-lookup"><span data-stu-id="6f0e9-185">Visual Studio 15.6 and earlier</span></span>](#tab/vs156)

<span data-ttu-id="6f0e9-186">在您偵錯並測試程式之後，請針對每個目標平台建立要隨應用程式一起部署的檔案。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-186">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span>

<span data-ttu-id="6f0e9-187">若要從 Visual Studio 發行您的應用程式，請執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="6f0e9-187">To publish your app from Visual Studio, do the following:</span></span>

1. <span data-ttu-id="6f0e9-188">定義您應用程式目標的平台。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-188">Define the platforms that your app will target.</span></span>

   1. <span data-ttu-id="6f0e9-189">以滑鼠右鍵按一下 [方案總管] 中的專案 (而非解決方案)，然後選取 [編輯 SCD.csproj]。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-189">Right-click on your project (not the solution) in **Solution Explorer** and select **Edit SCD.csproj**.</span></span>

   1. <span data-ttu-id="6f0e9-190">在定義應用程式目標平台之 *csproj* 檔案的 `<PropertyGroup>` 區段中建立 `<RuntimeIdentifiers>` 標記，並指定每個目標平台的執行階段識別碼 (RID)。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-190">Create a `<RuntimeIdentifiers>` tag in the `<PropertyGroup>` section of your *csproj* file that defines the platforms your app targets, and specify the runtime identifier (RID) of each platform that you target.</span></span> <span data-ttu-id="6f0e9-191">請注意，您也必須加上分號來分隔 RID。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-191">Note that you also need to add a semicolon to separate the RIDs.</span></span> <span data-ttu-id="6f0e9-192">如需執行階段識別碼清單，請參閱 [Runtime IDentifier catalog](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-192">See [Runtime IDentifier catalog](../rid-catalog.md) for a list of runtime identifiers.</span></span>

   <span data-ttu-id="6f0e9-193">例如，下列範例指出應用程式在 64 位元 Windows 10 作業系統和 64 位元 OS X 版本 10.11 作業系統上執行。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-193">For example, the following example indicates that the app runs on 64-bit Windows 10 operating systems and the 64-bit OS X Version 10.11 operating system.</span></span>

   ```xml
   <PropertyGroup>
      <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
   </PropertyGroup>
   ```

   <span data-ttu-id="6f0e9-194">請注意，`<RuntimeIdentifiers>` 項目可以移至您 *csproj* 檔案中的任何 `<PropertyGroup>`。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-194">Note that the `<RuntimeIdentifiers>` element can go into any `<PropertyGroup>` that you have in your *csproj* file.</span></span> <span data-ttu-id="6f0e9-195">本節稍後會提供完整的 *csproj* 檔案範例。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-195">A complete sample *csproj* file appears later in this section.</span></span>

1. <span data-ttu-id="6f0e9-196">發行您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-196">Publish your app.</span></span>

   <span data-ttu-id="6f0e9-197">在您偵錯並測試程式之後，請針對每個目標平台建立要隨應用程式一起部署的檔案。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-197">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span>

   <span data-ttu-id="6f0e9-198">若要從 Visual Studio 發行您的應用程式，請執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="6f0e9-198">To publish your app from Visual Studio, do the following:</span></span>

      1. <span data-ttu-id="6f0e9-199">在工具列上將方案組態從 [偵錯] 變更為 [發行]，以組建應用程式的發行 (而不是偵錯) 版本。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-199">Change the solution configuration from **Debug** to **Release** on the toolbar to build a Release (rather than a Debug) version of your app.</span></span>

      1. <span data-ttu-id="6f0e9-200">以滑鼠右鍵按一下方案總管中的專案 (而非方案)，然後選取 [發行]。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-200">Right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

      1. <span data-ttu-id="6f0e9-201">在 [發行] 索引標籤中，選取 [發行]。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-201">In the **Publish** tab, select **Publish**.</span></span> <span data-ttu-id="6f0e9-202">Visual Studio 會將構成應用程式的檔案寫入至本機檔案系統。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-202">Visual Studio writes the files that comprise your application to the local file system.</span></span>

      1. <span data-ttu-id="6f0e9-203">[發行] 索引標籤現在會顯示單一設定檔 **FolderProfile**。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-203">The **Publish** tab now shows a single profile, **FolderProfile**.</span></span> <span data-ttu-id="6f0e9-204">設定檔的組態設定顯示在索引標籤的 [摘要] 區段中。[目標執行階段] 識別已發行的執行階段，而 [目標位置] 則識別自封式部署的檔案寫入位置。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-204">The profile's configuration settings are shown in the **Summary** section of the tab. **Target Runtime** identifies which runtime has been published, and **Target Location** identifies where the files for the self-contained deployment were written.</span></span>

      1. <span data-ttu-id="6f0e9-205">Visual Studio 預設會將所有發行的檔案寫入到單一目錄。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-205">Visual Studio by default writes all published files to a single directory.</span></span> <span data-ttu-id="6f0e9-206">為了方便起見，最好是建立每個目標執行階段的個別設定檔，並將已發行的檔案放在特定平台目錄中。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-206">For convenience, it's best to create separate profiles for each target runtime and to place published files in a platform-specific directory.</span></span> <span data-ttu-id="6f0e9-207">這牽涉到建立每個目標平台的個別發行設定檔。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-207">This involves creating a separate publishing profile for each target platform.</span></span> <span data-ttu-id="6f0e9-208">因此，現在請執行下列作業來重建每個平台的應用程式：</span><span class="sxs-lookup"><span data-stu-id="6f0e9-208">So now rebuild the application for each platform by doing the following:</span></span>

         1. <span data-ttu-id="6f0e9-209">選取 [建立新設定檔] 中的 [發行] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-209">Select **Create new profile** in the **Publish** dialog.</span></span>

         1. <span data-ttu-id="6f0e9-210">在 [挑選發行目標] 對話方塊中，將 [選擇資料夾] 位置變更為 *bin\Release\PublishOutput\win10 x64*。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-210">In the **Pick a publish target** dialog, change the **Choose a folder** location to *bin\Release\PublishOutput\win10-x64*.</span></span> <span data-ttu-id="6f0e9-211">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-211">Select **OK**.</span></span>

         1. <span data-ttu-id="6f0e9-212">選取設定檔清單中的新設定檔 (**FolderProfile1**)，並確定 [目標執行階段] 是 `win10-x64`。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-212">Select the new profile (**FolderProfile1**) in the list of profiles, and make sure that the **Target Runtime** is `win10-x64`.</span></span> <span data-ttu-id="6f0e9-213">如果不是，請選取 [設定]。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-213">If it isn't, select **Settings**.</span></span> <span data-ttu-id="6f0e9-214">在 [設定檔設定] 對話方塊中，將 [目標執行階段] 變更為 `win10-x64`，然後選取 [儲存]。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-214">In the **Profile Settings** dialog, change the **Target Runtime** to `win10-x64` and select **Save**.</span></span> <span data-ttu-id="6f0e9-215">否則，請選取 [取消]。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-215">Otherwise, select **Cancel**.</span></span>

         1. <span data-ttu-id="6f0e9-216">選取 [發行] 來發行適用於 64 位元 Windows 10 平台的應用程式。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-216">Select **Publish** to publish your app for 64-bit Windows 10 platforms.</span></span>

         1. <span data-ttu-id="6f0e9-217">請再次遵循上述步驟，以建立適用於 `osx.10.11-x64` 平台的設定檔。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-217">Follow the previous steps again to create a profile for the `osx.10.11-x64` platform.</span></span> <span data-ttu-id="6f0e9-218">[目標位置] 是 *bin\Release\PublishOutput\osx.10.11-x64*，而 [目標執行階段] 是 `osx.10.11-x64`。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-218">The **Target Location** is *bin\Release\PublishOutput\osx.10.11-x64*, and the **Target Runtime** is `osx.10.11-x64`.</span></span> <span data-ttu-id="6f0e9-219">Visual Studio 指派給此設定檔的名稱是 **FolderProfile2**。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-219">The name that Visual Studio assigns to this profile is **FolderProfile2**.</span></span>

      <span data-ttu-id="6f0e9-220">請注意，每個目標位置都包含啟動應用程式所需的一組完整檔案 (應用程式檔案和所有的 .NET Core 檔案)。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-220">Note that each target location contains the complete set of files (both your app files and all .NET Core files) needed to launch your app.</span></span>

<span data-ttu-id="6f0e9-221">隨著應用程式檔案一起，發佈程序會發出程式資料庫 (.pdb) 檔案，其中包含應用程式的偵錯資訊。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-221">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="6f0e9-222">該檔案主要是用於例外狀況偵錯。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-222">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="6f0e9-223">您可以選擇不與您的應用程式檔案一起封裝它。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-223">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="6f0e9-224">不過，如果您要對應用程式的發行組建進行偵錯，則應該將其儲存。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-224">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="6f0e9-225">請使用任何您想要的方式，部署已發行的檔案。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-225">Deploy the published files in any way you like.</span></span> <span data-ttu-id="6f0e9-226">例如，您可以使用簡單的 `copy` 命令將它們封裝在 ZIP 檔案中，或與您選擇的任何安裝套件一起部署。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-226">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

<span data-ttu-id="6f0e9-227">下面是此專案的完整 *csproj* 檔案。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-227">The following is the complete *csproj* file for this project.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

# <a name="visual-studio-157-and-latertabvs157"></a>[<span data-ttu-id="6f0e9-228">Visual Studio 15.7 和更新版本</span><span class="sxs-lookup"><span data-stu-id="6f0e9-228">Visual Studio 15.7 and later</span></span>](#tab/vs157)

<span data-ttu-id="6f0e9-229">在您偵錯並測試程式之後，請針對每個目標平台建立要隨應用程式一起部署的檔案。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-229">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span> <span data-ttu-id="6f0e9-230">這牽涉到建立每個目標平台的個別設定檔。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-230">This involves creating a separate profile for each target platform.</span></span>

<span data-ttu-id="6f0e9-231">請針對每個應用程式目標平台執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="6f0e9-231">For each platform that your application targets, do the following:</span></span>

1. <span data-ttu-id="6f0e9-232">為您的目標平台建立設定檔。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-232">Create a profile for your target platform.</span></span>

   <span data-ttu-id="6f0e9-233">如果這是您建立的第一個設定檔，請以滑鼠右鍵按一下 [方案總管] 中的專案 (而非解決方案)，然後選取 [發行]。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-233">If this is the first profile you've created, right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

   <span data-ttu-id="6f0e9-234">如果您已建立設定檔，請以滑鼠右鍵按一下專案，以開啟 [發行] 對話方塊 (如尚未開啟)。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-234">If you've already created a profile, right-click on the project to open the **Publish** dialog if it isn't already open.</span></span> <span data-ttu-id="6f0e9-235">然後選取 [新增設定檔]。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-235">Then select **New Profile**.</span></span>

   <span data-ttu-id="6f0e9-236">[挑選發行目標] 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-236">The **Pick a Publish Target** dialog box opens.</span></span>
  
1. <span data-ttu-id="6f0e9-237">選取 Visual Studio 發行您應用程式的位置。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-237">Select the location where Visual Studio publishes your application.</span></span>

   <span data-ttu-id="6f0e9-238">如果您僅要發行到單一平台，您可以在 [選擇資料夾] 文字方塊中接受預設值，這會將您應用程式的 Framework 相依部署發行至 \*\<project-directory>\bin\Release\netcoreapp2.1\publish\* 目錄。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-238">If you're only publishing to a single platform, you can accept the default value in the **Choose a folder** text box; this publishes the framework dependent deployment of your application to the \*\<project-directory>\bin\Release\netcoreapp2.1\publish\* directory.</span></span>

   <span data-ttu-id="6f0e9-239">如果您要發行到多個平台，請附加識別目標平台的字串。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-239">If you're publishing to more than one platform, append a string that identifies the target platform.</span></span> <span data-ttu-id="6f0e9-240">例如，如果您將字串 "linux" 附加至檔案路徑，Visual Studio 會將您應用程式的 Framework 相依部署發行至 *\<project-directory>\bin\Release\netcoreapp2.1\publish\linux* 目錄。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-240">For example, if you append the string "linux" to the file path, Visual Studio publishes the framework dependent deployment of your application to the *\<project-directory>\bin\Release\netcoreapp2.1\publish\linux* directory.</span></span>

1. <span data-ttu-id="6f0e9-241">若要建立設定檔，請選取下拉式清單圖示旁的 [發行] 按鈕，然後選取 [建立設定檔]。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-241">Create the profile by selecting the drop-down list icon next to the **Publish** button and selecting **Create Profile**.</span></span> <span data-ttu-id="6f0e9-242">然後選取 [建立設定檔] 按鈕來建立設定檔。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-242">Then select the **Create Profile** button to create the profile.</span></span>

1. <span data-ttu-id="6f0e9-243">指出您要發行獨立式部署，並定義應用程式目標平台。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-243">Indicate that you are publishing a self-contained deployment and define a platform that your app will target.</span></span>

   1. <span data-ttu-id="6f0e9-244">在 [發行] 對話方塊中，選取 [設定] 連結以開啟 [設定檔設定] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-244">In the **Publish** dialog, select the **Configure** link to open the **Profile Settings** dialog.</span></span>

   1. <span data-ttu-id="6f0e9-245">在 [部署模式] 清單方塊中，選取 [獨立式]。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-245">Select **Self-contained** in the **Deployment Mode** list box.</span></span>

   1. <span data-ttu-id="6f0e9-246">在 [目標執行階段] 清單方塊中，選取其中一個應用程式目標平台。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-246">In the **Target Runtime** list box, select one of the platforms that your application targets.</span></span>

   1. <span data-ttu-id="6f0e9-247">選取 [儲存] 以儲存變更並關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-247">Select **Save** to accept your changes and close the dialog.</span></span>

1. <span data-ttu-id="6f0e9-248">為您的設定檔命名。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-248">Name your profile.</span></span>

   1. <span data-ttu-id="6f0e9-249">選取 [動作] > [重新命名設定檔] 來為您的設定檔命名。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-249">Select **Actions** > **Rename Profile** to name your profile.</span></span>

   2. <span data-ttu-id="6f0e9-250">為您的設定檔指派可識別目標平台的名稱，然後選取 \*[儲存]。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-250">Assign your profile a name that identifies the target platform, then select \**Save*.</span></span>

<span data-ttu-id="6f0e9-251">重複這些步驟來定義其他應用程式目標平台。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-251">Repeat these steps to define any additional target platforms that your application targets.</span></span>

<span data-ttu-id="6f0e9-252">您已完成設定您的設定檔，並已準備好發行應用程式。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-252">You've configured your profiles and are now ready to publish your app.</span></span> <span data-ttu-id="6f0e9-253">若要這樣做：</span><span class="sxs-lookup"><span data-stu-id="6f0e9-253">To do this:</span></span>

   1. <span data-ttu-id="6f0e9-254">如果 [發行] 視窗目前未開啟，請以滑鼠右鍵按一下 [方案總管] 中的專案 (而非解決方案)，然後選取 [發行]。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-254">If the **Publish** window isn't currently open, right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

   2. <span data-ttu-id="6f0e9-255">選取您想要發行的設定檔，然後選取 [發行]。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-255">Select the profile that you'd like to publish, then select **Publish**.</span></span> <span data-ttu-id="6f0e9-256">為即將發行的每個設定檔執行此動作。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-256">Do this for each profile to be published.</span></span>

   <span data-ttu-id="6f0e9-257">請注意，每個目標位置 (在此範例中為 bin\release\netcoreapp2.1\publish\\*profile-name*) 都包含啟動應用程式所需的一組完整檔案 (應用程式檔案和所有的 .NET Core 檔案)。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-257">Note that each target location (in the case of our example, bin\release\netcoreapp2.1\publish\\*profile-name* contains the complete set of files (both your app files and all .NET Core files) needed to launch your app.</span></span>

<span data-ttu-id="6f0e9-258">隨著應用程式檔案一起，發佈程序會發出程式資料庫 (.pdb) 檔案，其中包含應用程式的偵錯資訊。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-258">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="6f0e9-259">該檔案主要是用於例外狀況偵錯。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-259">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="6f0e9-260">您可以選擇不與您的應用程式檔案一起封裝它。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-260">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="6f0e9-261">不過，如果您要對應用程式的發行組建進行偵錯，則應該將其儲存。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-261">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="6f0e9-262">請使用任何您想要的方式，部署已發行的檔案。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-262">Deploy the published files in any way you like.</span></span> <span data-ttu-id="6f0e9-263">例如，您可以使用簡單的 `copy` 命令將它們封裝在 ZIP 檔案中，或與您選擇的任何安裝套件一起部署。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-263">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

<span data-ttu-id="6f0e9-264">下面是此專案的完整 *csproj* 檔案。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-264">The following is the complete *csproj* file for this project.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="6f0e9-265">此外，Visual Studio 會針對每個平台目標建立個別的發行設定檔 (\*.pubxml) 。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-265">In addition, Visual Studio creates a separate publishing profile (\*.pubxml) for each platform that you target.</span></span> <span data-ttu-id="6f0e9-266">比方說，我們的 Linux 設定檔 (linux.pubxml) 的檔案會如下所示：</span><span class="sxs-lookup"><span data-stu-id="6f0e9-266">For example, the file for our linux profile (linux.pubxml) appears as follows:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<!--
https://go.microsoft.com/fwlink/?LinkID=208121. 
-->
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <PublishProtocol>FileSystem</PublishProtocol>
    <Configuration>Release</Configuration>
    <Platform>Any CPU</Platform>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <PublishDir>bin\Release\netcoreapp2.1\publish\linux</PublishDir>
    <RuntimeIdentifier>win-x86</RuntimeIdentifier>
    <SelfContained>true</SelfContained>
    <_IsPortable>false</_IsPortable>
  </PropertyGroup>
</Project>
```

---

## <a name="self-contained-deployment-with-third-party-dependencies"></a><span data-ttu-id="6f0e9-267">有協力廠商相依性的自封式部署</span><span class="sxs-lookup"><span data-stu-id="6f0e9-267">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="6f0e9-268">部署具有一或多個協力廠商相依性的自封式部署，涉及新增相依性。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-268">Deploying a self-contained deployment with one or more third-party dependencies involves adding the dependencies.</span></span> <span data-ttu-id="6f0e9-269">在組建您的應用程式之前，需要執行下列其他步驟：</span><span class="sxs-lookup"><span data-stu-id="6f0e9-269">The following additional steps are required before you can build your app:</span></span>

1. <span data-ttu-id="6f0e9-270">使用 [NuGet 套件管理員]，將 NuGet 套件的參考新增至您的專案；如果您的系統上還沒有該套件，請安裝它。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-270">Use the **NuGet Package Manager** to add a reference to a NuGet package to your project; and if the package is not already available on your system, install it.</span></span> <span data-ttu-id="6f0e9-271">若要開啟套件管理員，請選取 [工具]  >  [NuGet 套件管理員]  >  [管理方案的 NuGet 套件]。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-271">To open the package manager, select **Tools** > **NuGet Package Manager** > **Manage NuGet Packages for Solution**.</span></span>

1. <span data-ttu-id="6f0e9-272">確認 `Newtonsoft.Json` 已安裝在您的系統上，如果尚未安裝，請安裝它。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-272">Confirm that `Newtonsoft.Json` is installed on your system and, if it is not, install it.</span></span> <span data-ttu-id="6f0e9-273">[已安裝] 索引標籤會列出您系統上已安裝的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-273">The **Installed** tab lists NuGet packages installed on your system.</span></span> <span data-ttu-id="6f0e9-274">如果 `Newtonsoft.Json` 未列於該處，請選取 [瀏覽] 索引標籤，然後在 [搜尋] 方塊中輸入 "Newtonsoft.Json"。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-274">If `Newtonsoft.Json` is not listed there, select the **Browse** tab and enter "Newtonsoft.Json" in the search box.</span></span> <span data-ttu-id="6f0e9-275">選取 `Newtonsoft.Json`，並先在右窗格中選取您的專案，然後選取 [安裝]。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-275">Select `Newtonsoft.Json` and, in the right pane, select your project before selecting **Install**.</span></span>

1. <span data-ttu-id="6f0e9-276">如果 `Newtonsoft.Json` 已安裝在您的系統上，請在 [管理方案的封裝] 索引標籤的右窗格中選取您的專案，以將它新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-276">If `Newtonsoft.Json` is already installed on your system, add it to your project by selecting your project in the right pane of the **Manage Packages for Solution** tab.</span></span>

<span data-ttu-id="6f0e9-277">下面是此專案的完整 *csproj* 檔案：</span><span class="sxs-lookup"><span data-stu-id="6f0e9-277">The following is the complete *csproj* file for this project:</span></span>

# <a name="visual-studio-156-and-earliertabvs156"></a>[<span data-ttu-id="6f0e9-278">Visual Studio 15.6 和更早版本</span><span class="sxs-lookup"><span data-stu-id="6f0e9-278">Visual Studio 15.6 and earlier</span></span>](#tab/vs156)

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
  </ItemGroup>
</Project>
```

# <a name="visual-studio-157-and-latertabvs157"></a>[<span data-ttu-id="6f0e9-279">Visual Studio 15.7 和更新版本</span><span class="sxs-lookup"><span data-stu-id="6f0e9-279">Visual Studio 15.7 and later</span></span>](#tab/vs157)

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
  </ItemGroup>
</Project>
```

---

<span data-ttu-id="6f0e9-280">當您部署應用程式時，應用程式中任何協力廠商相依性也包含在應用程式檔案中。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-280">When you deploy your application, any third-party dependencies used in your app are also contained with your application files.</span></span> <span data-ttu-id="6f0e9-281">應用程式執行所在的系統上不需要協力廠商程式庫。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-281">Third-party libraries aren't required on the system on which the app is running.</span></span>

<span data-ttu-id="6f0e9-282">請注意，您只能將具有協力廠商程式庫的自封式部署，部署到該程式庫支援的平台上。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-282">Note that you can only deploy a self-contained deployment with a third-party library to platforms supported by that library.</span></span> <span data-ttu-id="6f0e9-283">這類似於在與 Framework 相依的部署中擁有仰賴原生相依性的協力廠商相依性；在其中，原生相依性不會存在於目標平台上，除非先前已在該處安裝這些相依性。</span><span class="sxs-lookup"><span data-stu-id="6f0e9-283">This is similar to having third-party dependencies with native dependencies in your framework-dependent deployment, where the native dependencies won't exist on the target platform unless they were previously installed there.</span></span>

## <a name="see-also"></a><span data-ttu-id="6f0e9-284">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f0e9-284">See also</span></span>

* [<span data-ttu-id="6f0e9-285">.NET Core 應用程式部署</span><span class="sxs-lookup"><span data-stu-id="6f0e9-285">.NET Core Application Deployment</span></span>](index.md)
* [<span data-ttu-id="6f0e9-286">.NET Core 執行階段識別項 (RID) 目錄</span><span class="sxs-lookup"><span data-stu-id="6f0e9-286">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
