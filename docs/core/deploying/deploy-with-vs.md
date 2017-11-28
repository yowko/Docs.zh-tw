---
title: "使用 Visual Studio 部署 .NET Core 應用程式"
description: "了解使用 Visual Studio 的 .NET Core 應用程式部署"
keywords: ".NET、.NET Core、.NET Core 部署"
author: rpetrusha
ms.author: ronpet
ms.date: 04/18/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 01049a21-fd50-4419-9ab2-0e4a2e091050
ms.openlocfilehash: 884ecb110b4168c6dc1e4c664de1dcb8db3734c5
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2017
---
# <a name="deploying-net-core-apps-with-visual-studio"></a><span data-ttu-id="490f4-104">使用 Visual Studio 部署 .NET Core 應用程式</span><span class="sxs-lookup"><span data-stu-id="490f4-104">Deploying .NET Core apps with Visual Studio</span></span>

<span data-ttu-id="490f4-105">您可以將 .NET Core 應用程式部署為「與 Framework 相依的部署」，其中包含您的應用程式二進位檔，但取決於目標系統上是否有 .NET Core 存在，也可以部署為「自封式部署」，其中包含您的應用程式和 .NET Core 二進位檔。</span><span class="sxs-lookup"><span data-stu-id="490f4-105">You can deploy a .NET Core application either as a *framework-dependent deployment*, which includes your application binaries but depends on the presence of .NET Core on the target system, or as a *self-contained deployment*, which includes both your application and .NET Core binaries.</span></span> <span data-ttu-id="490f4-106">如需 .NET Core 應用程式部署的概觀，請參閱 [.NET Core 應用程式部署](index.md)。</span><span class="sxs-lookup"><span data-stu-id="490f4-106">For an overview of .NET Core application deployment, see [.NET Core Application Deployment](index.md).</span></span>

<span data-ttu-id="490f4-107">下列各節顯示如何使用 Microsoft Visual Studio 來建立下列類型的部署：</span><span class="sxs-lookup"><span data-stu-id="490f4-107">The following sections show how to use Microsoft Visual Studio to create the following kinds of deployments:</span></span>

- <span data-ttu-id="490f4-108">與 Framework 相依的部署</span><span class="sxs-lookup"><span data-stu-id="490f4-108">Framework-dependent deployment</span></span>
- <span data-ttu-id="490f4-109">有協力廠商相依性的 Framework 相依部署</span><span class="sxs-lookup"><span data-stu-id="490f4-109">Framework-dependent deployment with third-party dependencies</span></span>
- <span data-ttu-id="490f4-110">自封式部署</span><span class="sxs-lookup"><span data-stu-id="490f4-110">Self-contained deployment</span></span>
- <span data-ttu-id="490f4-111">有協力廠商相依性的自封式部署</span><span class="sxs-lookup"><span data-stu-id="490f4-111">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="490f4-112">如需使用 Visual Studio 來開發 .NET Core 應用程式的資訊，請參閱 [Windows 上 .NET Core 的必要條件](../windows-prerequisites.md#prerequisites-with-visual-studio-2017)。</span><span class="sxs-lookup"><span data-stu-id="490f4-112">For information on using Visual Studio to develop .NET Core applications, see [Prerequisites for .NET Core on Windows](../windows-prerequisites.md#prerequisites-with-visual-studio-2017).</span></span>

## <a name="framework-dependent-deployment"></a><span data-ttu-id="490f4-113">與 Framework 相依的部署</span><span class="sxs-lookup"><span data-stu-id="490f4-113">Framework-dependent deployment</span></span>

<span data-ttu-id="490f4-114">部署無任何協力廠商相依性的 Framework 相依部署，只涉及建置、測試和發行應用程式。</span><span class="sxs-lookup"><span data-stu-id="490f4-114">Deploying a framework-dependent deployment with no third-party dependencies simply involves building, testing, and publishing the app.</span></span> <span data-ttu-id="490f4-115">以 C# 撰寫的簡單範例會說明此程序。</span><span class="sxs-lookup"><span data-stu-id="490f4-115">A simple example written in C# illustrates the process.</span></span>  

1. <span data-ttu-id="490f4-116">建立專案。</span><span class="sxs-lookup"><span data-stu-id="490f4-116">Create the project.</span></span>

   <span data-ttu-id="490f4-117">選取 [檔案]  >  [新增]  >  [專案]。</span><span class="sxs-lookup"><span data-stu-id="490f4-117">Select **File** > **New** > **Project**.</span></span> <span data-ttu-id="490f4-118">在 [新增專案] 對話方塊中，選取 [已安裝] 專案類型窗格中的 [.NET Core]，然後選取中央窗格中的 [Console App (.NET Core)] (主控台應用程式 (.NET Core) 範本。</span><span class="sxs-lookup"><span data-stu-id="490f4-118">In the **New Project** dialog, select **.NET Core** in the **Installed** project types pane, and select the **Console App (.NET Core)** template in the center pane.</span></span> <span data-ttu-id="490f4-119">在 [名稱] 文字方塊中輸入專案名稱，例如 "FDD"。</span><span class="sxs-lookup"><span data-stu-id="490f4-119">Enter a project name, such as "FDD", in the **Name** text box.</span></span> <span data-ttu-id="490f4-120">選取 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="490f4-120">Select the **OK** button.</span></span>

1. <span data-ttu-id="490f4-121">新增應用程式的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="490f4-121">Add the application's source code.</span></span>

   <span data-ttu-id="490f4-122">在編輯器中開啟 *Program.cs* 檔案，並以下列程式碼取代自動產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="490f4-122">Open the *Program.cs* file in the editor and replace the auto-generated code with the following code.</span></span> <span data-ttu-id="490f4-123">它會提示使用者輸入文字，並顯示使用者輸入的個別文字。</span><span class="sxs-lookup"><span data-stu-id="490f4-123">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="490f4-124">它會使用規則運算式 `\w+` 分隔輸入文字中的字詞。</span><span class="sxs-lookup"><span data-stu-id="490f4-124">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](../../../samples/snippets/core/deploying/deployment-example.cs)]

1. <span data-ttu-id="490f4-125">建立應用程式的偵錯組建。</span><span class="sxs-lookup"><span data-stu-id="490f4-125">Create a Debug build of your app.</span></span>

   <span data-ttu-id="490f4-126">選取 [組建]  >  [組建方案]。</span><span class="sxs-lookup"><span data-stu-id="490f4-126">Select **Build** > **Build Solution**.</span></span> <span data-ttu-id="490f4-127">您也可以編譯並執行應用程式的偵錯組建，方法是選取 [偵錯]  >  [開始偵錯]。</span><span class="sxs-lookup"><span data-stu-id="490f4-127">You can also compile and run the Debug build of your application by selecting **Debug** > **Start Debugging**.</span></span>

1. <span data-ttu-id="490f4-128">部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="490f4-128">Deploy your app.</span></span>

   <span data-ttu-id="490f4-129">在您偵錯並測試程式之後，請建立要隨應用程式一起部署的檔案。</span><span class="sxs-lookup"><span data-stu-id="490f4-129">After you've debugged and tested the program, create the files to be deployed with your app.</span></span> <span data-ttu-id="490f4-130">若要從 Visual Studio 發行，請執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="490f4-130">To publish from Visual Studio, do the following:</span></span>

      1. <span data-ttu-id="490f4-131">在工具列上將方案組態從 [偵錯] 變更為 [發行]，以組建應用程式的發行 (而不是偵錯) 版本。</span><span class="sxs-lookup"><span data-stu-id="490f4-131">Change the solution configuration from **Debug** to **Release** on the toolbar to build a Release (rather than a Debug) version of your app.</span></span>

      1. <span data-ttu-id="490f4-132">以滑鼠右鍵按一下方案總管中的專案 (而非方案)，然後選取 [發行]。</span><span class="sxs-lookup"><span data-stu-id="490f4-132">Right-click on the project (not the solution) in **Solution Explorer**, and select **Publish**.</span></span>

      1. <span data-ttu-id="490f4-133">在 [發行]索引標籤中，選取 [發行]。</span><span class="sxs-lookup"><span data-stu-id="490f4-133">In the **Publish** tab, select **Publish**.</span></span> <span data-ttu-id="490f4-134">Visual Studio 會將構成應用程式的檔案寫入至本機檔案系統。</span><span class="sxs-lookup"><span data-stu-id="490f4-134">Visual Studio writes the files that comprise your application to the local file system.</span></span>

      1. <span data-ttu-id="490f4-135">[發行] 索引標籤現在會顯示單一設定檔 **FolderProfile**。</span><span class="sxs-lookup"><span data-stu-id="490f4-135">The **Publish** tab now shows a single profile, **FolderProfile**.</span></span> <span data-ttu-id="490f4-136">設定檔的組態設定顯示在索引標籤的 [摘要] 區段中。</span><span class="sxs-lookup"><span data-stu-id="490f4-136">The profile's configuration settings are shown in the **Summary** section of the tab.</span></span>

   <span data-ttu-id="490f4-137">產生的檔案會放在名為 `PublishOutput` 的目錄中，而該目錄位於您專案之 *.\bin\release* 子目錄的子目錄中。</span><span class="sxs-lookup"><span data-stu-id="490f4-137">The resulting files are placed in a directory named `PublishOutput` that is in a subdirectory of your project's *.\bin\release* subdirectory.</span></span>

<span data-ttu-id="490f4-138">隨著應用程式檔案一起，發佈程序會發出程式資料庫 (.pdb) 檔案，其中包含應用程式的偵錯資訊。</span><span class="sxs-lookup"><span data-stu-id="490f4-138">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="490f4-139">該檔案主要是用於例外狀況偵錯。</span><span class="sxs-lookup"><span data-stu-id="490f4-139">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="490f4-140">您可以選擇不與您的應用程式檔案一起封裝它。</span><span class="sxs-lookup"><span data-stu-id="490f4-140">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="490f4-141">不過，如果您要對應用程式的發行組建進行偵錯，則應該將其儲存。</span><span class="sxs-lookup"><span data-stu-id="490f4-141">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="490f4-142">以任何您想要的方式，部署整組應用程式檔案。</span><span class="sxs-lookup"><span data-stu-id="490f4-142">Deploy the complete set of application files in any way you like.</span></span> <span data-ttu-id="490f4-143">例如，您可以使用簡單的 `copy` 命令將它們封裝在 ZIP 檔案中，或與您選擇的任何安裝套件一起部署。</span><span class="sxs-lookup"><span data-stu-id="490f4-143">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span> <span data-ttu-id="490f4-144">安裝之後，使用者可以使用 `dotnet` 命令並提供應用程式的檔名 (例如，`dotnet fdd.dll`)，來執行您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="490f4-144">Once installed, users can then execute your application by using the `dotnet` command and providing the application filename, such as `dotnet fdd.dll`.</span></span>

<span data-ttu-id="490f4-145">除了應用程式二進位檔之外，安裝程式也應該配套共用的 Framework 安裝程式，，或勾選為必要條件當成應用程式安裝的一部分。</span><span class="sxs-lookup"><span data-stu-id="490f4-145">In addition to the application binaries, your installer should also either bundle the shared framework installer or check for it as a prerequisite as part of the application installation.</span></span>  <span data-ttu-id="490f4-146">共用 Framework 安裝需要系統管理員/根目錄存取權，因為它要通行全機器。</span><span class="sxs-lookup"><span data-stu-id="490f4-146">Installation of the shared framework requires Administrator/root access since it is machine-wide.</span></span>

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a><span data-ttu-id="490f4-147">有協力廠商相依性的 Framework 相依部署</span><span class="sxs-lookup"><span data-stu-id="490f4-147">Framework-dependent deployment with third-party dependencies</span></span>

<span data-ttu-id="490f4-148">部署具有一或多個協力廠商相依性的 Framework 相依部署時，需要任何相依性都可供專案使用。</span><span class="sxs-lookup"><span data-stu-id="490f4-148">Deploying a framework-dependent deployment with one or more third-party dependencies requires that any dependencies be available to your project.</span></span> <span data-ttu-id="490f4-149">在組建您的應用程式之前，需要執行下列其他步驟：</span><span class="sxs-lookup"><span data-stu-id="490f4-149">The following additional steps are required before you can build your app:</span></span>

1. <span data-ttu-id="490f4-150">使用 [NuGet 套件管理員]，將 NuGet 套件的參考新增至您的專案；如果您的系統上還沒有該套件，請安裝它。</span><span class="sxs-lookup"><span data-stu-id="490f4-150">Use the **NuGet Package Manager** to add a reference to a NuGet package to your project; and if the package is not already available on your system, install it.</span></span> <span data-ttu-id="490f4-151">若要開啟套件管理員，請選取 [工具]  >  [NuGet 套件管理員]  >  [管理方案的 NuGet 套件]。</span><span class="sxs-lookup"><span data-stu-id="490f4-151">To open the package manager, select **Tools** > **NuGet Package Manager** > **Manage NuGet Packages for Solution**.</span></span>

1. <span data-ttu-id="490f4-152">確認 `Newtonsoft.Json` 已安裝在您的系統上，如果尚未安裝，請安裝它。</span><span class="sxs-lookup"><span data-stu-id="490f4-152">Confirm that `Newtonsoft.Json` is installed on your system and, if it is not, install it.</span></span> <span data-ttu-id="490f4-153">[已安裝] 索引標籤會列出您系統上已安裝的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="490f4-153">The **Installed** tab lists NuGet packages installed on your system.</span></span> <span data-ttu-id="490f4-154">如果 `Newtonsoft.Json` 未列於該處，請選取 [瀏覽] 索引標籤，然後在 [搜尋] 方塊中輸入 "Newtonsoft.Json"。</span><span class="sxs-lookup"><span data-stu-id="490f4-154">If `Newtonsoft.Json` is not listed there, select the **Browse** tab and enter "Newtonsoft.Json" in the search box.</span></span> <span data-ttu-id="490f4-155">選取 `Newtonsoft.Json`，並先在右窗格中選取您的專案，然後選取 [安裝]。</span><span class="sxs-lookup"><span data-stu-id="490f4-155">Select `Newtonsoft.Json` and, in the right pane, select your project before selecting **Install**.</span></span>

1. <span data-ttu-id="490f4-156">如果 `Newtonsoft.Json` 已安裝在您的系統上，請在 [管理方案的套件] 索引標籤的右窗格中選取您的專案，以將它新增至您的專案中。</span><span class="sxs-lookup"><span data-stu-id="490f4-156">If `Newtonsoft.Json` is already installed on your system, add it to your project by selecting your project in the right pane of hte **Manage Packages for Solution** tab.</span></span>

<span data-ttu-id="490f4-157">請注意，具有協力廠商相依性的 Framework 相依部署，可攜性只與其協力廠商相依性一致。</span><span class="sxs-lookup"><span data-stu-id="490f4-157">Note that a framework-dependent deployment with third-party dependencies is only as portable as its third-party dependencies.</span></span> <span data-ttu-id="490f4-158">例如，如果協力廠商程式庫只支援 macOS，則應用程式就無法攜至 Windows 系統。</span><span class="sxs-lookup"><span data-stu-id="490f4-158">For example, if a third-party library only supports macOS, the app isn't portable to Windows systems.</span></span> <span data-ttu-id="490f4-159">如果協力廠商相依性本身依賴於原生程式碼，就會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="490f4-159">This happens if the third-party dependency itself depends on native code.</span></span> <span data-ttu-id="490f4-160">其中一個絶佳範例是 [Kestrel 伺服器](http://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel)，它需要對 [libuv](https://github.com/libuv/libuv) 的原生相依性。</span><span class="sxs-lookup"><span data-stu-id="490f4-160">A good example of this is [Kestrel server](http://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), which requires a native dependency on [libuv](https://github.com/libuv/libuv).</span></span> <span data-ttu-id="490f4-161">當具有這類協力廠商相依性的應用程式建立了 FDD 時，已發行輸出就會包含原生相依性支援的每個[執行階段識別碼 (RID)](../rid-catalog.md) 資料夾 (存在於其 NuGet 套件中)。</span><span class="sxs-lookup"><span data-stu-id="490f4-161">When an FDD is created for an application with this kind of third-party dependency, the published output contains a folder for each [Runtime Identifier (RID)](../rid-catalog.md) that the native dependency supports (and that exists in its NuGet package).</span></span>

## <span data-ttu-id="490f4-162"><a name="simpleSelf"></a> 沒有協力廠商相依性的自封式部署</span><span class="sxs-lookup"><span data-stu-id="490f4-162"><a name="simpleSelf"></a> Self-contained deployment without third-party dependencies</span></span>

<span data-ttu-id="490f4-163">部署無任何協力廠商相依性的自封式部署，涉及建立專案、修改 *csproj* 檔案、組建、測試以及發行應用程式。</span><span class="sxs-lookup"><span data-stu-id="490f4-163">Deploying a self-contained deployment with no third-party dependencies involves creating the project, modifying the *csproj* file, building, testing, and publishing the app.</span></span> <span data-ttu-id="490f4-164">以 C# 撰寫的簡單範例會說明此程序。</span><span class="sxs-lookup"><span data-stu-id="490f4-164">A simple example written in C# illustrates the process.</span></span> 

1. <span data-ttu-id="490f4-165">建立專案。</span><span class="sxs-lookup"><span data-stu-id="490f4-165">Create the project.</span></span>

   <span data-ttu-id="490f4-166">選取 [檔案]  >  [新增]  >  [專案]。</span><span class="sxs-lookup"><span data-stu-id="490f4-166">Select **File** > **New** > **Project**.</span></span> <span data-ttu-id="490f4-167">在 [新增專案] 對話方塊中，選取 [已安裝] 專案類型窗格中的 [.NET Core]，然後選取中央窗格中的 [Console App (.NET Core)] (主控台應用程式 (.NET Core)) 範本。</span><span class="sxs-lookup"><span data-stu-id="490f4-167">In the **Add New Project** dialog, select **.NET Core** in the **Installed** project types pane, and select the **Console App (.NET Core)** template in the center pane.</span></span> <span data-ttu-id="490f4-168">在 [名稱] 文字方塊中輸入專案名稱 (例如 "SCD")，然後選取 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="490f4-168">Enter a project name, such as "SCD", in the **Name** text box, and select the **OK** button.</span></span>

1. <span data-ttu-id="490f4-169">新增應用程式的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="490f4-169">Add the application's source code.</span></span>

   <span data-ttu-id="490f4-170">在您的編輯器中開啟 *Program.cs* 檔案，並以下列程式碼取代自動產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="490f4-170">Open the *Program.cs* file in your editor, and replace the auto-generated code with the following code.</span></span> <span data-ttu-id="490f4-171">它會提示使用者輸入文字，並顯示使用者輸入的個別文字。</span><span class="sxs-lookup"><span data-stu-id="490f4-171">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="490f4-172">它會使用規則運算式 `\w+` 分隔輸入文字中的字詞。</span><span class="sxs-lookup"><span data-stu-id="490f4-172">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](../../../samples/snippets/core/deploying/deployment-example.cs)]

1. <span data-ttu-id="490f4-173">定義您應用程式目標的平台。</span><span class="sxs-lookup"><span data-stu-id="490f4-173">Define the platforms that your app will target.</span></span>

   1. <span data-ttu-id="490f4-174">以滑鼠右鍵按一下方案總管中的專案 (而非方案)，然後選取 [編輯 SCD.csproj]。</span><span class="sxs-lookup"><span data-stu-id="490f4-174">Right-click on your project (not the solution) In **Solution Explorer**, and select **Edit SCD.csproj**.</span></span>

   1. <span data-ttu-id="490f4-175">在定義應用程式目標平台之 *csproj* 檔案的 `<PropertyGroup>` 區段中建立 `<RuntimeIdentifiers>` 標記，並指定每個目標平台的執行階段識別碼 (RID)。</span><span class="sxs-lookup"><span data-stu-id="490f4-175">Create a `<RuntimeIdentifiers>` tag in the `<PropertyGroup>` section of your *csproj* file that defines the platforms your app targets, and specify the runtime identifier (RID) of each platform that you target.</span></span> <span data-ttu-id="490f4-176">請注意，您也必須加上分號來分隔 RID。</span><span class="sxs-lookup"><span data-stu-id="490f4-176">Note that you also need to add a semicolon to separate the RIDs.</span></span> <span data-ttu-id="490f4-177">如需執行階段識別碼清單，請參閱 [Runtime IDentifier catalog](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="490f4-177">See [Runtime IDentifier catalog](../rid-catalog.md) for a list of runtime identifiers.</span></span> 

   <span data-ttu-id="490f4-178">例如，下列範例指出應用程式在 64 位元 Windows 10 作業系統和 64 位元 OS X 版本 10.11 作業系統上執行。</span><span class="sxs-lookup"><span data-stu-id="490f4-178">For example, the following example indicates that the app runs on 64-bit Windows 10 operating systems and the 64-bit OS X Version 10.11 operating system.</span></span>

```xml
<PropertyGroup>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
</PropertyGroup>
```
   <span data-ttu-id="490f4-179">請注意，`<RuntimeIdentifiers>` 項目可以移至您 *csproj* 檔案中的任何 `<PropertyGroup>`。</span><span class="sxs-lookup"><span data-stu-id="490f4-179">Note that the `<RuntimeIdentifiers>` element can go into any `<PropertyGroup>` that you have in your *csproj* file.</span></span> <span data-ttu-id="490f4-180">本節稍後會提供完整的 *csproj* 檔案範例。</span><span class="sxs-lookup"><span data-stu-id="490f4-180">A complete sample *csproj* file appears later in this section.</span></span>

1. <span data-ttu-id="490f4-181">建立應用程式的偵錯組建。</span><span class="sxs-lookup"><span data-stu-id="490f4-181">Create a Debug build of your app.</span></span>

   <span data-ttu-id="490f4-182">選取 [組建]  >  [組建方案]。</span><span class="sxs-lookup"><span data-stu-id="490f4-182">Select **Build** > **Build Solution**.</span></span> <span data-ttu-id="490f4-183">您也可以編譯並執行應用程式的偵錯組建，方法是選取 [偵錯]  >  [開始偵錯]。</span><span class="sxs-lookup"><span data-stu-id="490f4-183">You can also compile and run the Debug build of your application by selecting **Debug** > **Start Debugging**.</span></span>

1. <span data-ttu-id="490f4-184">發行您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="490f4-184">Publish your app.</span></span>

   <span data-ttu-id="490f4-185">在您偵錯並測試程式之後，請針對每個目標平台建立要隨應用程式一起部署的檔案。</span><span class="sxs-lookup"><span data-stu-id="490f4-185">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span>

   <span data-ttu-id="490f4-186">若要從 Visual Studio 發行您的應用程式，請執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="490f4-186">To publish your app from Visual Studio, do the following:</span></span>

      1. <span data-ttu-id="490f4-187">在工具列上將方案組態從 [偵錯] 變更為 [發行]，以組建應用程式的發行 (而不是偵錯) 版本。</span><span class="sxs-lookup"><span data-stu-id="490f4-187">Change the solution configuration from **Debug** to **Release** on the toolbar to build a Release (rather than a Debug) version of your app.</span></span>

      1. <span data-ttu-id="490f4-188">以滑鼠右鍵按一下方案總管中的專案 (而非方案)，然後選取 [發行]。</span><span class="sxs-lookup"><span data-stu-id="490f4-188">Right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span> 

      1. <span data-ttu-id="490f4-189">在 [發行] 索引標籤中，選取 [發行]。</span><span class="sxs-lookup"><span data-stu-id="490f4-189">In the **Publish** tab, select **Publish**.</span></span> <span data-ttu-id="490f4-190">Visual Studio 會將構成應用程式的檔案寫入至本機檔案系統。</span><span class="sxs-lookup"><span data-stu-id="490f4-190">Visual Studio writes the files that comprise your application to the local file system.</span></span>

      1. <span data-ttu-id="490f4-191">[發行] 索引標籤現在會顯示單一設定檔 **FolderProfile**。</span><span class="sxs-lookup"><span data-stu-id="490f4-191">The **Publish** tab now shows a single profile, **FolderProfile**.</span></span> <span data-ttu-id="490f4-192">設定檔的組態設定顯示在索引標籤的 [摘要] 區段中。[目標執行階段] 識別已發行的執行階段，而 [目標位置] 則識別自封式部署的檔案寫入位置。</span><span class="sxs-lookup"><span data-stu-id="490f4-192">The profile's configuration settings are shown in the **Summary** section of the tab. **Target Runtime** identifies which runtime has been published, and **Target Location** identifies where the files for the self-contained deployment were written.</span></span>

      1. <span data-ttu-id="490f4-193">Visual Studio 預設會將所有發行的檔案寫入到單一目錄。</span><span class="sxs-lookup"><span data-stu-id="490f4-193">Visual Studio by default writes all published files to a single directory.</span></span> <span data-ttu-id="490f4-194">為了方便起見，最好是建立每個目標執行階段的個別設定檔，並將已發行的檔案放在特定平台目錄中。</span><span class="sxs-lookup"><span data-stu-id="490f4-194">For convenience, it's best to create separate profiles for each target runtime and to place published files in a platform-specific directory.</span></span> <span data-ttu-id="490f4-195">這牽涉到建立每個目標平台的個別發行設定檔。</span><span class="sxs-lookup"><span data-stu-id="490f4-195">This involves creating a separate publishing profile for each target platform.</span></span> <span data-ttu-id="490f4-196">因此，現在請執行下列作業來重建每個平台的應用程式：</span><span class="sxs-lookup"><span data-stu-id="490f4-196">So now rebuild the application for each platform by doing the following:</span></span>

         1. <span data-ttu-id="490f4-197">選取 [建立新設定檔] 中的 [發行] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="490f4-197">Select **Create new profile** in the **Publish** dialog.</span></span>

         1. <span data-ttu-id="490f4-198">在 [挑選發行目標] 對話方塊中，將 [選擇資料夾] 位置變更為 *bin\Release\PublishOutput\win10 x64*。</span><span class="sxs-lookup"><span data-stu-id="490f4-198">In the **Pick a publish target** dialog, change the **Choose a folder** location to *bin\Release\PublishOutput\win10-x64*.</span></span> <span data-ttu-id="490f4-199">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="490f4-199">Select **OK**.</span></span>

         1. <span data-ttu-id="490f4-200">選取設定檔清單中的新設定檔 (**FolderProfile1**)，並確定 [目標執行階段] 是 `win10-x64`。</span><span class="sxs-lookup"><span data-stu-id="490f4-200">Select the new profile (**FolderProfile1**) in the list of profiles, and make sure that the **Target Runtime** is `win10-x64`.</span></span> <span data-ttu-id="490f4-201">如果不是，請選取 [設定]。</span><span class="sxs-lookup"><span data-stu-id="490f4-201">If it isn't, select **Settings**.</span></span> <span data-ttu-id="490f4-202">在 [設定檔設定] 對話方塊中，將 [目標執行階段] 變更為 `win10-x64`，然後選取 [儲存]。</span><span class="sxs-lookup"><span data-stu-id="490f4-202">In the **Profile Settings** dialog, change the **Target Runtime** to `win10-x64` and select **Save**.</span></span> <span data-ttu-id="490f4-203">否則，請選取 [取消]。</span><span class="sxs-lookup"><span data-stu-id="490f4-203">Otherwise, select **Cancel**.</span></span>

         1. <span data-ttu-id="490f4-204">選取 [發行] 來發行適用於 64 位元 Windows 10 平台的應用程式。</span><span class="sxs-lookup"><span data-stu-id="490f4-204">Select **Publish** to publish your app for 64-bit Windows 10 platforms.</span></span>

         1. <span data-ttu-id="490f4-205">請再次遵循上述步驟，以建立適用於 `osx.10.11-x64` 平台的設定檔。</span><span class="sxs-lookup"><span data-stu-id="490f4-205">Follow the previous steps again to create a profile for the `osx.10.11-x64` platform.</span></span> <span data-ttu-id="490f4-206">[目標位置] 是 *bin\Release\PublishOutput\osx.10.11-x64*，而 [目標執行階段] 是 `osx.10.11-x64`。</span><span class="sxs-lookup"><span data-stu-id="490f4-206">The **Target Location** is *bin\Release\PublishOutput\osx.10.11-x64*, and the **Target Runtime** is `osx.10.11-x64`.</span></span> <span data-ttu-id="490f4-207">Visual Studio 指派給此設定檔的名稱是 **FolderProfile2**。</span><span class="sxs-lookup"><span data-stu-id="490f4-207">The name that Visual Studio assigns to this profile is **FolderProfile2**.</span></span>

      <span data-ttu-id="490f4-208">請注意，每個目標位置都包含啟動應用程式所需的一組完整檔案 (應用程式檔案和所有的 .NET Core 檔案)。</span><span class="sxs-lookup"><span data-stu-id="490f4-208">Note that each target location contains the complete set of files (both your app files and all .NET Core files) needed to launch your app.</span></span>

<span data-ttu-id="490f4-209">隨著應用程式檔案一起，發佈程序會發出程式資料庫 (.pdb) 檔案，其中包含應用程式的偵錯資訊。</span><span class="sxs-lookup"><span data-stu-id="490f4-209">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="490f4-210">該檔案主要是用於例外狀況偵錯。</span><span class="sxs-lookup"><span data-stu-id="490f4-210">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="490f4-211">您可以選擇不與您的應用程式檔案一起封裝它。</span><span class="sxs-lookup"><span data-stu-id="490f4-211">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="490f4-212">不過，如果您要對應用程式的發行組建進行偵錯，則應該將其儲存。</span><span class="sxs-lookup"><span data-stu-id="490f4-212">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="490f4-213">請使用任何您想要的方式，部署已發行的檔案。</span><span class="sxs-lookup"><span data-stu-id="490f4-213">Deploy the published files in any way you like.</span></span> <span data-ttu-id="490f4-214">例如，您可以使用簡單的 `copy` 命令將它們封裝在 ZIP 檔案中，或與您選擇的任何安裝套件一起部署。</span><span class="sxs-lookup"><span data-stu-id="490f4-214">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

<span data-ttu-id="490f4-215">下面是此專案的完整 *csproj* 檔案。</span><span class="sxs-lookup"><span data-stu-id="490f4-215">The following is the complete *csproj* file for this project.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

## <a name="self-contained-deployment-with-third-party-dependencies"></a><span data-ttu-id="490f4-216">有協力廠商相依性的自封式部署</span><span class="sxs-lookup"><span data-stu-id="490f4-216">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="490f4-217">部署具有一或多個協力廠商相依性的自封式部署，涉及新增相依性。</span><span class="sxs-lookup"><span data-stu-id="490f4-217">Deploying a self-contained deployment with one or more third-party dependencies involves adding the dependencies.</span></span> <span data-ttu-id="490f4-218">在組建您的應用程式之前，需要執行下列其他步驟：</span><span class="sxs-lookup"><span data-stu-id="490f4-218">The following additional steps are required before you can build your app:</span></span>

1. <span data-ttu-id="490f4-219">使用 [NuGet 套件管理員]，將 NuGet 套件的參考新增至您的專案；如果您的系統上還沒有該套件，請安裝它。</span><span class="sxs-lookup"><span data-stu-id="490f4-219">Use the **NuGet Package Manager** to add a reference to a NuGet package to your project; and if the package is not already available on your system, install it.</span></span> <span data-ttu-id="490f4-220">若要開啟套件管理員，請選取 [工具]  >  [NuGet 套件管理員]  >  [管理方案的 NuGet 套件]。</span><span class="sxs-lookup"><span data-stu-id="490f4-220">To open the package manager, select **Tools** > **NuGet Package Manager** > **Manage NuGet Packages for Solution**.</span></span>

1. <span data-ttu-id="490f4-221">確認 `Newtonsoft.Json` 已安裝在您的系統上，如果尚未安裝，請安裝它。</span><span class="sxs-lookup"><span data-stu-id="490f4-221">Confirm that `Newtonsoft.Json` is installed on your system and, if it is not, install it.</span></span> <span data-ttu-id="490f4-222">[已安裝] 索引標籤會列出您系統上已安裝的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="490f4-222">The **Installed** tab lists NuGet packages installed on your system.</span></span> <span data-ttu-id="490f4-223">如果 `Newtonsoft.Json` 未列於該處，請選取 [瀏覽] 索引標籤，然後在 [搜尋] 方塊中輸入 "Newtonsoft.Json"。</span><span class="sxs-lookup"><span data-stu-id="490f4-223">If `Newtonsoft.Json` is not listed there, select the **Browse** tab and enter "Newtonsoft.Json" in the search box.</span></span> <span data-ttu-id="490f4-224">選取 `Newtonsoft.Json`，並先在右窗格中選取您的專案，然後選取 [安裝]。</span><span class="sxs-lookup"><span data-stu-id="490f4-224">Select `Newtonsoft.Json` and, in the right pane, select your project before selecting **Install**.</span></span>

1. <span data-ttu-id="490f4-225">如果 `Newtonsoft.Json` 已安裝在您的系統上，請在 [管理方案的封裝] 索引標籤的右窗格中選取您的專案，以將它新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="490f4-225">If `Newtonsoft.Json` is already installed on your system, add it to your project by selecting your project in the right pane of the **Manage Packages for Solution** tab.</span></span>

<span data-ttu-id="490f4-226">下面是此專案的完整 *csproj* 檔案：</span><span class="sxs-lookup"><span data-stu-id="490f4-226">The following is the complete *csproj* file for this project:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="490f4-227">當您部署應用程式時，應用程式中任何協力廠商相依性也包含在應用程式檔案中。</span><span class="sxs-lookup"><span data-stu-id="490f4-227">When you deploy your application, any third-party dependencies used in your app are also contained with your application files.</span></span> <span data-ttu-id="490f4-228">應用程式執行所在的系統上不需要協力廠商程式庫。</span><span class="sxs-lookup"><span data-stu-id="490f4-228">Third-party libraries aren't required on the system on which the app is running.</span></span>

<span data-ttu-id="490f4-229">請注意，您只能將具有協力廠商程式庫的自封式部署，部署到該程式庫支援的平台上。</span><span class="sxs-lookup"><span data-stu-id="490f4-229">Note that you can only deploy a self-contained deployment with a third-party library to platforms supported by that library.</span></span> <span data-ttu-id="490f4-230">這類似於在與 Framework 相依的部署中擁有仰賴原生相依性的協力廠商相依性；在其中，原生相依性不會存在於目標平台上，除非先前已在該處安裝這些相依性。</span><span class="sxs-lookup"><span data-stu-id="490f4-230">This is similar to having third-party dependencies with native dependencies in your framework-dependent deployment, where the native dependencies won't exist on the target platform unless they were previously installed there.</span></span>

# <a name="see-also"></a><span data-ttu-id="490f4-231">請參閱</span><span class="sxs-lookup"><span data-stu-id="490f4-231">See also</span></span>
<span data-ttu-id="490f4-232">[.NET Core 應用程式部署](index.md) </span><span class="sxs-lookup"><span data-stu-id="490f4-232">[.NET Core Application Deployment](index.md) </span></span>  
[<span data-ttu-id="490f4-233">.NET Core 執行階段識別項 (RID) 目錄</span><span class="sxs-lookup"><span data-stu-id="490f4-233">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)   
