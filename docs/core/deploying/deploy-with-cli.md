---
title: 使用 CLI 工具部署.NET Core 應用程式
description: 了解使用命令列介面 (CLI) 工具的 .NET Core 應用程式部署
author: rpetrusha
ms.author: ronpet
ms.date: 04/18/2017
ms.openlocfilehash: dbef9d91aa4e7af8e6e0ed2d8f361238385d4976
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43855018"
---
# <a name="deploying-net-core-apps-with-command-line-interface-cli-tools"></a><span data-ttu-id="add65-103">使用命令列介面 (CLI) 工具部署 .NET Core 應用程式</span><span class="sxs-lookup"><span data-stu-id="add65-103">Deploying .NET Core apps with command-line interface (CLI) tools</span></span>

<span data-ttu-id="add65-104">您可以將 .NET Core 應用程式部署為「與 Framework 相依的部署」，其中包含您的應用程式二進位檔，但取決於目標系統上是否有 .NET Core 存在，也可以部署為「自封式部署」，其中包含您的應用程式和 .NET Core 二進位檔。</span><span class="sxs-lookup"><span data-stu-id="add65-104">You can deploy a .NET Core application either as a *framework-dependent deployment*, which includes your application binaries but depends on the presence of .NET Core on the target system, or as a *self-contained deployment*, which includes both your application and the .NET Core binaries.</span></span> <span data-ttu-id="add65-105">如需概觀，請參閱 [.NET Core 應用程式部署](index.md)。</span><span class="sxs-lookup"><span data-stu-id="add65-105">For an overview, see [.NET Core Application Deployment](index.md).</span></span>

<span data-ttu-id="add65-106">下列各節顯示如何使用 [.NET Core 命令列介面工具](../tools/index.md)來建立下列類型的部署：</span><span class="sxs-lookup"><span data-stu-id="add65-106">The following sections show how to use [.NET Core command-line interface tools](../tools/index.md) to create the following kinds of deployments:</span></span>

- <span data-ttu-id="add65-107">與 Framework 相依的部署</span><span class="sxs-lookup"><span data-stu-id="add65-107">Framework-dependent deployment</span></span>
- <span data-ttu-id="add65-108">有協力廠商相依性的 Framework 相依部署</span><span class="sxs-lookup"><span data-stu-id="add65-108">Framework-dependent deployment with third-party dependencies</span></span>
- <span data-ttu-id="add65-109">自封式部署</span><span class="sxs-lookup"><span data-stu-id="add65-109">Self-contained deployment</span></span>
- <span data-ttu-id="add65-110">有協力廠商相依性的自封式部署</span><span class="sxs-lookup"><span data-stu-id="add65-110">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="add65-111">在命令列工作時，您可以使用您選擇的程式編輯器。</span><span class="sxs-lookup"><span data-stu-id="add65-111">When working from the command line, you can use a program editor of your choice.</span></span> <span data-ttu-id="add65-112">如果您的程式編輯器是 [Visual Studio Code](https://code.visualstudio.com)，您也可以在 Visual Studio 程式碼環境內選取 [檢視]  >  [整合式終端機] 來開啟命令主控台。</span><span class="sxs-lookup"><span data-stu-id="add65-112">If your program editor is [Visual Studio Code](https://code.visualstudio.com), you can open a command console inside your Visual Studio Code environment by selecting **View** > **Integrated Terminal**.</span></span>

## <a name="framework-dependent-deployment"></a><span data-ttu-id="add65-113">與 Framework 相依的部署</span><span class="sxs-lookup"><span data-stu-id="add65-113">Framework-dependent deployment</span></span>

<span data-ttu-id="add65-114">部署無任何協力廠商相依性的 Framework 相依部署，只涉及建置、測試和發行應用程式。</span><span class="sxs-lookup"><span data-stu-id="add65-114">Deploying a framework-dependent deployment with no third-party dependencies simply involves building, testing, and publishing the app.</span></span> <span data-ttu-id="add65-115">以 C# 撰寫的簡單範例會說明此程序。</span><span class="sxs-lookup"><span data-stu-id="add65-115">A simple example written in C# illustrates the process.</span></span>

1. <span data-ttu-id="add65-116">建立專案目錄。</span><span class="sxs-lookup"><span data-stu-id="add65-116">Create a project directory.</span></span>

   <span data-ttu-id="add65-117">建立專案的目錄，並將其設為您目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="add65-117">Create a directory for your project and make it your current directory.</span></span>

1. <span data-ttu-id="add65-118">建立專案。</span><span class="sxs-lookup"><span data-stu-id="add65-118">Create the project.</span></span>

   <span data-ttu-id="add65-119">從命令列鍵入 [dotnet new console](../tools/dotnet-new.md)，以在該目錄中建立新的 C# 主控台專案。</span><span class="sxs-lookup"><span data-stu-id="add65-119">From the command line, type [dotnet new console](../tools/dotnet-new.md) to create a new C# console project in that directory.</span></span>

1. <span data-ttu-id="add65-120">新增應用程式的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="add65-120">Add the application's source code.</span></span>

   <span data-ttu-id="add65-121">在您的編輯器中開啟 *Program.cs* 檔案，並以下列程式碼取代自動產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="add65-121">Open the *Program.cs* file in your editor and replace the auto-generated code with the following code.</span></span> <span data-ttu-id="add65-122">它會提示使用者輸入文字，並顯示使用者輸入的個別文字。</span><span class="sxs-lookup"><span data-stu-id="add65-122">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="add65-123">它會使用規則運算式 `\w+` 分隔輸入文字中的字詞。</span><span class="sxs-lookup"><span data-stu-id="add65-123">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](../../../samples/snippets/core/deploying/deployment-example.cs)]

1. <span data-ttu-id="add65-124">更新專案的相依性和工具。</span><span class="sxs-lookup"><span data-stu-id="add65-124">Update the project's dependencies and tools.</span></span>

   <span data-ttu-id="add65-125">執行 [dotnet restore](../tools/dotnet-restore.md) ([請參閱注意事項](#dotnet-restore-note)) 命令以還原專案中指定的相依性。</span><span class="sxs-lookup"><span data-stu-id="add65-125">Run the [dotnet restore](../tools/dotnet-restore.md) ([see note](#dotnet-restore-note)) command to restore the dependencies specified in your project.</span></span>

1. <span data-ttu-id="add65-126">建立應用程式的偵錯組建。</span><span class="sxs-lookup"><span data-stu-id="add65-126">Create a Debug build of your app.</span></span>

   <span data-ttu-id="add65-127">使用 [dotnet build](../tools/dotnet-build.md) 命令來組建您的應用程式，或者使用 [dotnet run](../tools/dotnet-run.md) 命令來組建並執行它。</span><span class="sxs-lookup"><span data-stu-id="add65-127">Use the [dotnet build](../tools/dotnet-build.md) command to build your application or the [dotnet run](../tools/dotnet-run.md) command to build and run it.</span></span>

1. <span data-ttu-id="add65-128">部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="add65-128">Deploy your app.</span></span>

   <span data-ttu-id="add65-129">在您偵錯並測試程式之後，請使用下列命令來建立部署：</span><span class="sxs-lookup"><span data-stu-id="add65-129">After you've debugged and tested the program, create the deployment by using the following command:</span></span>

      ```console
      dotnet publish -f netcoreapp1.1 -c Release
      ```
   <span data-ttu-id="add65-130">這會建立應用程式的發行 (而非偵錯) 版本。</span><span class="sxs-lookup"><span data-stu-id="add65-130">This creates a Release (rather than a Debug) version of your app.</span></span> <span data-ttu-id="add65-131">產生的檔案會放在名為 *publish* 的目錄中，而該目錄位於您專案之 *bin* 目錄的子目錄中。</span><span class="sxs-lookup"><span data-stu-id="add65-131">The resulting files are placed in a directory named *publish*      that's in a subdirectory of your project's *bin* directory.</span></span>

   <span data-ttu-id="add65-132">隨著應用程式檔案一起，發佈程序會發出程式資料庫 (.pdb) 檔案，其中包含應用程式的偵錯資訊。</span><span class="sxs-lookup"><span data-stu-id="add65-132">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="add65-133">該檔案主要是用於例外狀況偵錯。</span><span class="sxs-lookup"><span data-stu-id="add65-133">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="add65-134">您可以選擇不與您的應用程式檔案一起散發它。</span><span class="sxs-lookup"><span data-stu-id="add65-134">You can choose not to distribute it with your application's files.</span></span> <span data-ttu-id="add65-135">不過，如果您要對應用程式的發行組建進行偵錯，則應該將其儲存。</span><span class="sxs-lookup"><span data-stu-id="add65-135">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

   <span data-ttu-id="add65-136">您可以使用任何您想要的方式，部署整組應用程式檔案。</span><span class="sxs-lookup"><span data-stu-id="add65-136">You can deploy the complete set of application files in any way you like.</span></span> <span data-ttu-id="add65-137">例如，您可以使用簡單的 `copy` 命令將它們封裝在 ZIP 檔案中，或與您選擇的任何安裝套件一起部署。</span><span class="sxs-lookup"><span data-stu-id="add65-137">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

1. <span data-ttu-id="add65-138">執行應用程式</span><span class="sxs-lookup"><span data-stu-id="add65-138">Run your app</span></span>

   <span data-ttu-id="add65-139">安裝之後，使用者可以使用 `dotnet` 命令並提供應用程式的檔名 (例如，`dotnet fdd.dll`)，來執行您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="add65-139">Once installed, users can execute your application by using the `dotnet` command and providing the application filename, such as `dotnet fdd.dll`.</span></span>

   <span data-ttu-id="add65-140">除了應用程式二進位檔之外，安裝程式也應該配套共用的 Framework 安裝程式，，或勾選為必要條件當成應用程式安裝的一部分。</span><span class="sxs-lookup"><span data-stu-id="add65-140">In addition to the application binaries, your installer should also either bundle the shared framework installer or check for it as a prerequisite as part of the application installation.</span></span>  <span data-ttu-id="add65-141">共用的 Framwork 安裝需要系統管理員/根目錄存取權。</span><span class="sxs-lookup"><span data-stu-id="add65-141">Installation of the shared framework requires Administrator/root access.</span></span>

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a><span data-ttu-id="add65-142">有協力廠商相依性的 Framework 相依部署</span><span class="sxs-lookup"><span data-stu-id="add65-142">Framework-dependent deployment with third-party dependencies</span></span>

<span data-ttu-id="add65-143">部署具有一或多個協力廠商相依性的 Framework 相依部署時，需要這些相依性都可供專案使用。</span><span class="sxs-lookup"><span data-stu-id="add65-143">Deploying a framework-dependent deployment with one or more third-party dependencies requires that those dependencies be available to your project.</span></span> <span data-ttu-id="add65-144">在執行 `dotnet restore` ([請參閱注意事項](#dotnet-restore-note)) 命令之前，需要執行兩個額外步驟：</span><span class="sxs-lookup"><span data-stu-id="add65-144">Two additional steps are required before you can run the `dotnet restore` ([see note](#dotnet-restore-note)) command:</span></span>

1. <span data-ttu-id="add65-145">將任何協力廠商程式庫參考新增至您 *csproj* 檔案的 `<ItemGroup>` 區段。</span><span class="sxs-lookup"><span data-stu-id="add65-145">Add references to required third-party libraries to the `<ItemGroup>` section of your *csproj* file.</span></span> <span data-ttu-id="add65-146">下列 `<ItemGroup>` 區段會包含對 [Json.NET](http://www.newtonsoft.com/json) 的相依性作為協力廠商程式庫：</span><span class="sxs-lookup"><span data-stu-id="add65-146">The following `<ItemGroup>` section contains a dependency on [Json.NET](http://www.newtonsoft.com/json) as a third-party library:</span></span>

      ```xml
      <ItemGroup>
        <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
      </ItemGroup>
      ```

1. <span data-ttu-id="add65-147">如果尚未如此做，請下載包含協力廠商相依性的 NuGet 封裝。</span><span class="sxs-lookup"><span data-stu-id="add65-147">If you haven't already, download the NuGet package containing the third-party dependency.</span></span> <span data-ttu-id="add65-148">若要下載套件，請在新增相依性後執行 `dotnet restore` ([請參閱注意事項](#dotnet-restore-note)) 命令。</span><span class="sxs-lookup"><span data-stu-id="add65-148">To download the package, execute the `dotnet restore` ([see note](#dotnet-restore-note)) command after adding the dependency.</span></span> <span data-ttu-id="add65-149">因為相依性是在發行時於本機 NuGet 快取外解析，所以必須能在系統中取得。</span><span class="sxs-lookup"><span data-stu-id="add65-149">Because the dependency is resolved out of the local NuGet cache at publish time, it must be available on your system.</span></span>

<span data-ttu-id="add65-150">請注意，具有協力廠商相依性的 Framework 相依部署，可攜性只與其協力廠商相依性一致。</span><span class="sxs-lookup"><span data-stu-id="add65-150">Note that a framework-dependent deployment with third-party dependencies is only as portable as its third-party dependencies.</span></span> <span data-ttu-id="add65-151">例如，如果協力廠商程式庫只支援 macOS，則應用程式就無法攜至 Windows 系統。</span><span class="sxs-lookup"><span data-stu-id="add65-151">For example, if a third-party library only supports macOS, the app isn't portable to Windows systems.</span></span> <span data-ttu-id="add65-152">如果協力廠商相依性本身依賴於原生程式碼，就會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="add65-152">This happens if the third-party dependency itself depends on native code.</span></span> <span data-ttu-id="add65-153">其中一個絶佳範例是 [Kestrel 伺服器](/aspnet/core/fundamentals/servers/kestrel)，它需要對 [libuv](https://github.com/libuv/libuv) 的原生相依性。</span><span class="sxs-lookup"><span data-stu-id="add65-153">A good example of this is [Kestrel server](/aspnet/core/fundamentals/servers/kestrel), which requires a native dependency on [libuv](https://github.com/libuv/libuv).</span></span> <span data-ttu-id="add65-154">當具有這類協力廠商相依性的應用程式建立了 FDD 時，已發行輸出就會包含原生相依性支援的每個[執行階段識別碼 (RID)](../rid-catalog.md) 資料夾 (存在於其 NuGet 套件中)。</span><span class="sxs-lookup"><span data-stu-id="add65-154">When an FDD is created for an application with this kind of third-party dependency, the published output contains a folder for each [Runtime Identifier (RID)](../rid-catalog.md) that the native dependency supports (and that exists in its NuGet package).</span></span>

## <a name="simpleSelf"></a> <span data-ttu-id="add65-155">沒有協力廠商相依性的自封式部署</span><span class="sxs-lookup"><span data-stu-id="add65-155">Self-contained deployment without third-party dependencies</span></span>

<span data-ttu-id="add65-156">部署沒有協力廠商相依性的自封式部署，涉及建立專案、修改 *csproj* 檔案、組建、測試以及發行應用程式。</span><span class="sxs-lookup"><span data-stu-id="add65-156">Deploying a self-contained deployment without third-party dependencies involves creating the project, modifying the *csproj* file, building, testing, and publishing the app.</span></span> <span data-ttu-id="add65-157">以 C# 撰寫的簡單範例會說明此程序。</span><span class="sxs-lookup"><span data-stu-id="add65-157">A simple example written in C# illustrates the process.</span></span> <span data-ttu-id="add65-158">此範例示範如何從命令列使用 [dotnet 公用程式](../tools/dotnet.md)建立自封式部署。</span><span class="sxs-lookup"><span data-stu-id="add65-158">The example shows how to create a self-contained deployment using the [dotnet utility](../tools/dotnet.md) from the command line.</span></span>

1. <span data-ttu-id="add65-159">建立專案的目錄。</span><span class="sxs-lookup"><span data-stu-id="add65-159">Create a directory for the project.</span></span>

   <span data-ttu-id="add65-160">建立專案的目錄，並將其設為您目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="add65-160">Create a directory for your project, and make it your current directory.</span></span>

1. <span data-ttu-id="add65-161">建立專案。</span><span class="sxs-lookup"><span data-stu-id="add65-161">Create the project.</span></span>

   <span data-ttu-id="add65-162">從命令列鍵入 [dotnet new console](../tools/dotnet-new.md)，以在該目錄中建立新的 C# 主控台專案。</span><span class="sxs-lookup"><span data-stu-id="add65-162">From the command line, type [dotnet new console](../tools/dotnet-new.md) to create a new C# console project in that directory.</span></span>

1. <span data-ttu-id="add65-163">新增應用程式的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="add65-163">Add the application's source code.</span></span>

   <span data-ttu-id="add65-164">在您的編輯器中開啟 *Program.cs* 檔案，並以下列程式碼取代自動產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="add65-164">Open the *Program.cs* file in your editor and replace the auto-generated code with the following code.</span></span> <span data-ttu-id="add65-165">它會提示使用者輸入文字，並顯示使用者輸入的個別文字。</span><span class="sxs-lookup"><span data-stu-id="add65-165">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="add65-166">它會使用規則運算式 `\w+` 分隔輸入文字中的字詞。</span><span class="sxs-lookup"><span data-stu-id="add65-166">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](../../../samples/snippets/core/deploying/deployment-example.cs)]

1. <span data-ttu-id="add65-167">定義您應用程式目標的平台。</span><span class="sxs-lookup"><span data-stu-id="add65-167">Define the platforms that your app will target.</span></span>

   <span data-ttu-id="add65-168">在定義應用程式目標平台之 *csproj* 檔案的 `<PropertyGroup>` 區段中建立 `<RuntimeIdentifiers>` 標記，並指定每個目標平台的執行階段識別碼 (RID)。</span><span class="sxs-lookup"><span data-stu-id="add65-168">Create a `<RuntimeIdentifiers>` tag in the `<PropertyGroup>` section of your *csproj* file that defines the platforms your app targets and specify the runtime identifier (RID) for each platform that you target.</span></span> <span data-ttu-id="add65-169">請注意，您也必須加上分號來分隔 RID。</span><span class="sxs-lookup"><span data-stu-id="add65-169">Note that you also need to add a semicolon to separate the RIDs.</span></span> <span data-ttu-id="add65-170">如需執行階段識別碼清單，請參閱 [Runtime IDentifier catalog](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="add65-170">See [Runtime IDentifier catalog](../rid-catalog.md) for a list of runtime identifiers.</span></span>

   <span data-ttu-id="add65-171">例如，下列 `<PropertyGroup>` 區段指出應用程式在 64 位元 Windows 10 作業系統和 64 位元 OS X 版本 10.11 作業系統上執行。</span><span class="sxs-lookup"><span data-stu-id="add65-171">For example, the following `<PropertyGroup>` section indicates that the app runs on 64-bit Windows 10 operating systems and the 64-bit OS X Version 10.11 operating system.</span></span>

     ```xml
     <PropertyGroup>
         <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
     </PropertyGroup>
     ```

   <span data-ttu-id="add65-172">請注意，`<RuntimeIdentifiers>` 項目可以出現在 *csproj* 檔案的任何 `<PropertyGroup>` 中。</span><span class="sxs-lookup"><span data-stu-id="add65-172">Note that the `<RuntimeIdentifiers>` element can appear in any `<PropertyGroup>` in your *csproj* file.</span></span> <span data-ttu-id="add65-173">本節稍後會提供完整的 *csproj* 檔案範例。</span><span class="sxs-lookup"><span data-stu-id="add65-173">A complete sample *csproj* file appears later in this section.</span></span>

1. <span data-ttu-id="add65-174">更新專案的相依性和工具。</span><span class="sxs-lookup"><span data-stu-id="add65-174">Update the project's dependencies and tools.</span></span>

   <span data-ttu-id="add65-175">執行 [dotnet restore](../tools/dotnet-restore.md) ([請參閱注意事項](#dotnet-restore-note)) 命令以還原專案中指定的相依性。</span><span class="sxs-lookup"><span data-stu-id="add65-175">Run the [dotnet restore](../tools/dotnet-restore.md) ([see note](#dotnet-restore-note)) command to restore the dependencies specified in your project.</span></span>

1. <span data-ttu-id="add65-176">建立應用程式的偵錯組建。</span><span class="sxs-lookup"><span data-stu-id="add65-176">Create a Debug build of your app.</span></span>

   <span data-ttu-id="add65-177">從命令列中，使用 [dotnet build](../tools/dotnet-build.md) 命令。</span><span class="sxs-lookup"><span data-stu-id="add65-177">From the command line, use the [dotnet build](../tools/dotnet-build.md) command.</span></span>

1. <span data-ttu-id="add65-178">在您偵錯並測試程式之後，請針對每個目標平台建立要隨應用程式一起部署的檔案。</span><span class="sxs-lookup"><span data-stu-id="add65-178">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span>

   <span data-ttu-id="add65-179">針對這兩個目標平台使用 `dotnet publish` 命令，如下所示：</span><span class="sxs-lookup"><span data-stu-id="add65-179">Use the `dotnet publish` command for both target platforms as follows:</span></span>

      ```console
      dotnet publish -c Release -r win10-x64
      dotnet publish -c Release -r osx.10.11-x64
      ```

   <span data-ttu-id="add65-180">這會建立每個目標平台的應用程式發行 (而非偵錯) 版本。</span><span class="sxs-lookup"><span data-stu-id="add65-180">This creates a Release (rather than a Debug) version of your app for each target platform.</span></span> <span data-ttu-id="add65-181">產生的檔案會放在名為 *publish* 的子目錄中，而該目錄位於您專案之 *.\bin\Release\netcoreapp1.1\<執行階段識別碼>* 子目錄的子目錄中。</span><span class="sxs-lookup"><span data-stu-id="add65-181">The resulting files are placed in a subdirectory named *publish* that's in a subdirectory of your project's *.\bin\Release\netcoreapp1.1\<runtime_identifier>* subdirectory.</span></span> <span data-ttu-id="add65-182">請注意，每個子目錄都包含啟動應用程式所需的一組完整檔案 (應用程式檔案和所有的 .NET Core 檔案)。</span><span class="sxs-lookup"><span data-stu-id="add65-182">Note that each subdirectory contains the complete set of files (both your app files and all .NET Core files) needed to launch your app.</span></span>

<span data-ttu-id="add65-183">隨著應用程式檔案一起，發佈程序會發出程式資料庫 (.pdb) 檔案，其中包含應用程式的偵錯資訊。</span><span class="sxs-lookup"><span data-stu-id="add65-183">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="add65-184">該檔案主要是用於例外狀況偵錯。</span><span class="sxs-lookup"><span data-stu-id="add65-184">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="add65-185">您可以選擇不與您的應用程式檔案一起封裝它。</span><span class="sxs-lookup"><span data-stu-id="add65-185">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="add65-186">不過，如果您要對應用程式的發行組建進行偵錯，則應該將其儲存。</span><span class="sxs-lookup"><span data-stu-id="add65-186">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="add65-187">請使用任何您想要的方式，部署已發行的檔案。</span><span class="sxs-lookup"><span data-stu-id="add65-187">Deploy the published files in any way you like.</span></span> <span data-ttu-id="add65-188">例如，您可以使用簡單的 `copy` 命令將它們封裝在 ZIP 檔案中，或與您選擇的任何安裝套件一起部署。</span><span class="sxs-lookup"><span data-stu-id="add65-188">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

<span data-ttu-id="add65-189">下面是此專案的完整 *csproj* 檔案。</span><span class="sxs-lookup"><span data-stu-id="add65-189">The following is the complete *csproj* file for this project.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

## <a name="self-contained-deployment-with-third-party-dependencies"></a><span data-ttu-id="add65-190">有協力廠商相依性的自封式部署</span><span class="sxs-lookup"><span data-stu-id="add65-190">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="add65-191">部署具有一或多個協力廠商相依性的自封式部署，涉及新增相依性。</span><span class="sxs-lookup"><span data-stu-id="add65-191">Deploying a self-contained deployment with one or more third-party dependencies involves adding the dependencies.</span></span> <span data-ttu-id="add65-192">在執行 `dotnet restore` ([請參閱注意事項](#dotnet-restore-note)) 命令之前，需要執行兩個額外步驟：</span><span class="sxs-lookup"><span data-stu-id="add65-192">Two additional steps are required before you can run the `dotnet restore` ([see note](#dotnet-restore-note)) command:</span></span>

1. <span data-ttu-id="add65-193">將任何協力廠商程式庫參考新增至您 *csproj* 檔案的 `<ItemGroup>` 區段。</span><span class="sxs-lookup"><span data-stu-id="add65-193">Add references to any third-party libraries to the `<ItemGroup>` section of your *csproj* file.</span></span> <span data-ttu-id="add65-194">下列 `<ItemGroup>` 區段會使用 Json.NET 作為協力廠商程式庫。</span><span class="sxs-lookup"><span data-stu-id="add65-194">The following `<ItemGroup>` section uses Json.NET as a third-party library.</span></span>

    ```xml
      <ItemGroup>
        <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
      </ItemGroup>
    ```

1. <span data-ttu-id="add65-195">如果尚未如此做，請將包含協力廠商相依性的 NuGet 封裝下載至您的系統。</span><span class="sxs-lookup"><span data-stu-id="add65-195">If you haven't already, download the NuGet package containing the third-party dependency to your system.</span></span> <span data-ttu-id="add65-196">請在新增相依性後執行 `dotnet restore` ([請參閱注意](#dotnet-restore-note)) 命令，讓應用程式取得相依性。</span><span class="sxs-lookup"><span data-stu-id="add65-196">To make the dependency available to your app, execute the `dotnet restore` ([see note](#dotnet-restore-note)) command after adding the dependency.</span></span> <span data-ttu-id="add65-197">因為相依性是在發行時於本機 NuGet 快取外解析，所以必須能在系統中取得。</span><span class="sxs-lookup"><span data-stu-id="add65-197">Because the dependency is resolved out of the local NuGet cache at publish time, it must be available on your system.</span></span>

<span data-ttu-id="add65-198">下面是此專案的完整 *csproj* 檔案：</span><span class="sxs-lookup"><span data-stu-id="add65-198">The following is the complete *csproj* file for this project:</span></span>

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

<span data-ttu-id="add65-199">當您部署應用程式時，應用程式中任何協力廠商相依性也包含在應用程式檔案中。</span><span class="sxs-lookup"><span data-stu-id="add65-199">When you deploy your application, any third-party dependencies used in your app are also contained with your application files.</span></span> <span data-ttu-id="add65-200">應用程式執行所在的系統上不需要協力廠商程式庫。</span><span class="sxs-lookup"><span data-stu-id="add65-200">Third-party libraries aren't required on the system on which the app is running.</span></span>

<span data-ttu-id="add65-201">請注意，您只能將具有協力廠商程式庫的自封式部署，部署到該程式庫支援的平台上。</span><span class="sxs-lookup"><span data-stu-id="add65-201">Note that you can only deploy a self-contained deployment with a third-party library to platforms supported by that library.</span></span> <span data-ttu-id="add65-202">這類似於在與 Framework 相依的部署中擁有仰賴原生相依性的協力廠商相依性；在其中，原生相依性必須與部署應用程式的平台相容。</span><span class="sxs-lookup"><span data-stu-id="add65-202">This is similar to having third-party dependencies with native dependencies in a framework-dependent deployment, where the native dependencies must be compatible with the platform to which the app is deployed.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

## <a name="see-also"></a><span data-ttu-id="add65-203">另請參閱</span><span class="sxs-lookup"><span data-stu-id="add65-203">See also</span></span>

* [<span data-ttu-id="add65-204">.NET Core 應用程式部署</span><span class="sxs-lookup"><span data-stu-id="add65-204">.NET Core Application Deployment</span></span>](index.md)
* [<span data-ttu-id="add65-205">.NET Core 執行階段識別項 (RID) 目錄</span><span class="sxs-lookup"><span data-stu-id="add65-205">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
