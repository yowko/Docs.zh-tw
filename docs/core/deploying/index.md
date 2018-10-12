---
title: .NET Core 應用程式部署
description: 部署 .NET Core 應用程式。
author: rpetrusha
ms.author: ronpet
ms.date: 09/03/2018
ms.openlocfilehash: 390af06e81788c3f64f255e5c85efdaa167274f4
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/06/2018
ms.locfileid: "48836624"
---
# <a name="net-core-application-deployment"></a><span data-ttu-id="d494a-103">.NET Core 應用程式部署</span><span class="sxs-lookup"><span data-stu-id="d494a-103">.NET Core application deployment</span></span>

<span data-ttu-id="d494a-104">您可以建立兩種類型的 .NET Core 應用程式部署︰</span><span class="sxs-lookup"><span data-stu-id="d494a-104">You can create two types of deployments for .NET Core applications:</span></span>

- <span data-ttu-id="d494a-105">與 Framework 相依的部署。</span><span class="sxs-lookup"><span data-stu-id="d494a-105">Framework-dependent deployment.</span></span> <span data-ttu-id="d494a-106">正如其名，與 Framework 相依的部署 (framework-dependent deployment, FDD) 仰賴存在於目標系統上的全系統共用 .NET Core 版本。</span><span class="sxs-lookup"><span data-stu-id="d494a-106">As the name implies, framework-dependent deployment (FDD) relies on the presence of a shared system-wide version of .NET Core on the target system.</span></span> <span data-ttu-id="d494a-107">因為 .NET Core 已存在，所以應用程式也可以在 .NET Core 安裝之間攜帶。</span><span class="sxs-lookup"><span data-stu-id="d494a-107">Because .NET Core is already present, your app is also portable between installations of .NET Core.</span></span> <span data-ttu-id="d494a-108">您的應用程式僅包含其自有程式碼和 .NET Core 程式庫以外的所有協力廠商相依性。</span><span class="sxs-lookup"><span data-stu-id="d494a-108">Your app contains only its own code and any third-party dependencies that are outside of the .NET Core libraries.</span></span> <span data-ttu-id="d494a-109">FDD 包含的 *.dll* 檔案，可以使用 [dotnet 公用程式](../tools/dotnet.md)從命令列啟動。</span><span class="sxs-lookup"><span data-stu-id="d494a-109">FDDs contain *.dll* files that can be launched by using the [dotnet utility](../tools/dotnet.md) from the command line.</span></span> <span data-ttu-id="d494a-110">例如，`dotnet app.dll` 執行名為 `app` 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="d494a-110">For example, `dotnet app.dll` runs an application named `app`.</span></span>

- <span data-ttu-id="d494a-111">自封式部署。</span><span class="sxs-lookup"><span data-stu-id="d494a-111">Self-contained deployment.</span></span> <span data-ttu-id="d494a-112">不同於 FDD，自封式部署 (SCD) 不仰賴任何存在於目標系統上的共用元件。</span><span class="sxs-lookup"><span data-stu-id="d494a-112">Unlike FDD, a self-contained deployment (SCD) doesn't rely on the presence of shared components on the target system.</span></span> <span data-ttu-id="d494a-113">包括 .NET Core 程式庫和 .NET Core 執行階段的所有元件，都隨附於應用程式，並與其他 .NET Core 應用程式隔離。</span><span class="sxs-lookup"><span data-stu-id="d494a-113">All components, including both the .NET Core libraries and the .NET Core runtime, are included with the application and are isolated from other .NET Core applications.</span></span> <span data-ttu-id="d494a-114">SCD 包含可執行檔 (例如，Windows 平台上 `app` 應用程式的 *app.exe*)，這是重新命名的特定平台 .NET Core 主應用程式版本，以及實際的應用程式 *.dll* 檔案 (例如 *app.dll*)。</span><span class="sxs-lookup"><span data-stu-id="d494a-114">SCDs include an executable (such as *app.exe* on Windows platforms for an application named `app`), which is  a renamed version of the platform-specific .NET Core host, and a *.dll* file (such as *app.dll*), which is the actual application.</span></span>

## <a name="framework-dependent-deployments-fdd"></a><span data-ttu-id="d494a-115">與 Framework 相依的部署 (FDD)</span><span class="sxs-lookup"><span data-stu-id="d494a-115">Framework-dependent deployments (FDD)</span></span>

<span data-ttu-id="d494a-116">針對 FDD，您只要部署您的應用程式與協力廠商相依性。</span><span class="sxs-lookup"><span data-stu-id="d494a-116">For an FDD, you deploy only your app and third-party dependencies.</span></span> <span data-ttu-id="d494a-117">您不必部署 .NET Core，因為您的應用程式會使用存在於目標系統上的 .NET Core 版本。</span><span class="sxs-lookup"><span data-stu-id="d494a-117">You don't have to deploy .NET Core, since your app will use the version of .NET Core that's present on the target system.</span></span> <span data-ttu-id="d494a-118">這是以 .NET Core 為目標是 .NET Core 與 ASP.NET Core 應用程式的預設部署模型。</span><span class="sxs-lookup"><span data-stu-id="d494a-118">This is the default deployment model for .NET Core and ASP.NET Core apps that target .NET Core.</span></span>

### <a name="why-create-a-framework-dependent-deployment"></a><span data-ttu-id="d494a-119">為何建立與 Framework 相依的部署？</span><span class="sxs-lookup"><span data-stu-id="d494a-119">Why create a framework-dependent deployment?</span></span>

<span data-ttu-id="d494a-120">部署 FDD 有許多優點︰</span><span class="sxs-lookup"><span data-stu-id="d494a-120">Deploying an FDD has a number of advantages:</span></span>

- <span data-ttu-id="d494a-121">您不必事先定義 .NET Core 應用程式執行所在的目標作業系統。</span><span class="sxs-lookup"><span data-stu-id="d494a-121">You don't have to define the target operating systems that your .NET Core app will run on in advance.</span></span> <span data-ttu-id="d494a-122">由於不論作業系統為何，.NET Core 對可執行檔和程式庫都使用通用的 PE 檔案格式，所以 .NET Core 可以執行您的應用程式，不理會基礎作業系統。</span><span class="sxs-lookup"><span data-stu-id="d494a-122">Because .NET Core uses a common PE file format for executables and libraries regardless of operating system, .NET Core can execute your app regardless of the underlying operating system.</span></span> <span data-ttu-id="d494a-123">如需 PE 檔格式的詳細資訊，請參閱 [.NET Assembly File Format](../../standard/assembly-format.md) (.NET 組件檔案格式)。</span><span class="sxs-lookup"><span data-stu-id="d494a-123">For more information on the PE file format, see [.NET Assembly File Format](../../standard/assembly-format.md).</span></span>

- <span data-ttu-id="d494a-124">部署套件的大小很小。</span><span class="sxs-lookup"><span data-stu-id="d494a-124">The size of your deployment package is small.</span></span> <span data-ttu-id="d494a-125">您只需要部署您的應用程式及其相依性，不用部署 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="d494a-125">You only deploy your app and its dependencies, not .NET Core itself.</span></span>

- <span data-ttu-id="d494a-126">多個應用程式使用相同的 .NET Core 安裝，這樣可減少主機系統的磁碟空間和記憶體使用量。</span><span class="sxs-lookup"><span data-stu-id="d494a-126">Multiple apps use the same .NET Core installation, which reduces both disk space and memory usage on host systems.</span></span>

<span data-ttu-id="d494a-127">另外還有幾個缺點︰</span><span class="sxs-lookup"><span data-stu-id="d494a-127">There are also a few disadvantages:</span></span>

- <span data-ttu-id="d494a-128">只有主機系統安裝了目標的 .NET Core 版本或更新版本，您的應用程式才能執行。</span><span class="sxs-lookup"><span data-stu-id="d494a-128">Your app can run only if the version of .NET Core that you target, or a later version, is already installed on the host system.</span></span>

- <span data-ttu-id="d494a-129">.NET Core 執行階段和程式庫在未來的版本中可能有所變更，但不會通知您。</span><span class="sxs-lookup"><span data-stu-id="d494a-129">It's possible for the .NET Core runtime and libraries to change without your knowledge in future releases.</span></span> <span data-ttu-id="d494a-130">只有極其罕見的情況，才可能變更應用程式的行為。</span><span class="sxs-lookup"><span data-stu-id="d494a-130">In rare cases, this may change the behavior of your app.</span></span>

## <a name="self-contained-deployments-scd"></a><span data-ttu-id="d494a-131">自封式部署 (SCD)</span><span class="sxs-lookup"><span data-stu-id="d494a-131">Self-contained deployments (SCD)</span></span>

<span data-ttu-id="d494a-132">針對自封式部署，您不僅要部署自己的應用程式和所有協力廠商相依性，還要部署建置應用程式所用的 .NET Core 版本。</span><span class="sxs-lookup"><span data-stu-id="d494a-132">For a self-contained deployment, you deploy your app and any required third-party dependencies along with the version of .NET Core that you used to build the app.</span></span> <span data-ttu-id="d494a-133">不過，建立 SCD 不包含各種平台的 [.NET Core 原生相依性](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md)本身 (例如，macOS 上的 OpenSSL)，所以在執行應用程式前要先行安裝。</span><span class="sxs-lookup"><span data-stu-id="d494a-133">Creating an SCD doesn't include the [native dependencies of .NET Core](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) on various platforms, so these must be present before the app runs.</span></span> <span data-ttu-id="d494a-134">如需執行階段之版本繫結的詳細資訊，請參閱 [.NET Core 中的版本繫結](../versions/selection.md)上的文章。</span><span class="sxs-lookup"><span data-stu-id="d494a-134">For more information on version binding at runtime, see the article on [version binding in .NET Core](../versions/selection.md).</span></span>

<span data-ttu-id="d494a-135">從 NET Core 2.1 SDK (2.1.300 版) 開始，.NET Core 就支援*修補版本向前復原*。</span><span class="sxs-lookup"><span data-stu-id="d494a-135">Starting with NET Core 2.1 SDK (version 2.1.300), .NET Core supports *patch version roll forward*.</span></span> <span data-ttu-id="d494a-136">當您建立自封式部署時，.NET Core 工具會自動包括您的應用程式以其為目標的最新 .NET Core 維護執行階段版本</span><span class="sxs-lookup"><span data-stu-id="d494a-136">When you create a self-contained deployment, .NET Core tools automatically include the latest serviced runtime of the .NET Core version that your application targets.</span></span> <span data-ttu-id="d494a-137">(最新的維護執行階段包括安全性修補程式與其他錯誤修正)。維護執行階段不需要存在於您的建置系統上，系統會自動從 NuGet.org 下載它。如需詳細資訊 (包括有關如何選擇退出修補版本向前復原的指示)，請參閱[自封式部署執行階段向前復原](runtime-patch-selection.md)。</span><span class="sxs-lookup"><span data-stu-id="d494a-137">(The latest serviced runtime includes security patches and other bug fixes.) The serviced runtime does not have to be present on your build system; it is downloaded automatically from NuGet.org. For more information, including instructions on how to opt out of patch version roll forward, see [Self-contained deployment runtime roll forward](runtime-patch-selection.md).</span></span>

<span data-ttu-id="d494a-138">FDD 和 SCD 使用不同的主機可執行檔，因此您可以使用自己的發行者簽章，為 SCD 簽署主機可執行檔。</span><span class="sxs-lookup"><span data-stu-id="d494a-138">FDD and SCD deployments use separate host executables, so you can sign a host executable for an SCD with your publisher signature.</span></span>

### <a name="why-deploy-a-self-contained-deployment"></a><span data-ttu-id="d494a-139">為什麼要部署自封式部署？</span><span class="sxs-lookup"><span data-stu-id="d494a-139">Why deploy a self-contained deployment?</span></span>

<span data-ttu-id="d494a-140">部署自封式部署有兩大優點︰</span><span class="sxs-lookup"><span data-stu-id="d494a-140">Deploying a Self-contained deployment has two major advantages:</span></span>

- <span data-ttu-id="d494a-141">您可以獨家控制隨應用程式部署的 .NET Core 版本。</span><span class="sxs-lookup"><span data-stu-id="d494a-141">You have sole control of the version of .NET Core that is deployed with your app.</span></span> <span data-ttu-id="d494a-142">只有您可以提供 .NET Core 服務。</span><span class="sxs-lookup"><span data-stu-id="d494a-142">.NET Core can be serviced only by you.</span></span>

- <span data-ttu-id="d494a-143">您可以保證目標系統能執行您的 .NET Core 應用程式，因為您提供的是它可以執行的 .NET Core 版本。</span><span class="sxs-lookup"><span data-stu-id="d494a-143">You can be assured that the target system can run your .NET Core app, since you're providing the version of .NET Core that it will run on.</span></span>

<span data-ttu-id="d494a-144">它也有一些缺點︰</span><span class="sxs-lookup"><span data-stu-id="d494a-144">It also has a number of disadvantages:</span></span>

- <span data-ttu-id="d494a-145">因為 .NET Core 包含在您的部署套件中，所以您必須事先選取部署套件建置所在的目標平台。</span><span class="sxs-lookup"><span data-stu-id="d494a-145">Because .NET Core is included in your deployment package, you must select the target platforms for which you build deployment packages in advance.</span></span>

- <span data-ttu-id="d494a-146">您的部署套件的大小相當大，因為您必須包含 .NET Core 以及應用程式及其協力廠商相依性。</span><span class="sxs-lookup"><span data-stu-id="d494a-146">The size of your deployment package is relatively large, since you have to include .NET Core as well as your app and its third-party dependencies.</span></span>

  <span data-ttu-id="d494a-147">從 .NET Core 2.0 開始，您就可以使用 .NET Core [*全球化不變模式*](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md)來減少 Linux 系統上的部署大小大約 28 MB。</span><span class="sxs-lookup"><span data-stu-id="d494a-147">Starting with .NET Core 2.0, you can reduce the size of your deployment on Linux systems by approximately 28 MB by using .NET Core [*globalization invariant mode*](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md).</span></span> <span data-ttu-id="d494a-148">一般而言，Linux 上的 .NET Core 依賴 [ICU 程式庫](https://github.com/dotnet/docs/issues/http%22//icu-project.org)來提供全球化支援。</span><span class="sxs-lookup"><span data-stu-id="d494a-148">Ordinarily, .NET Core on Linux relies on the [ICU libraries](https://github.com/dotnet/docs/issues/http%22//icu-project.org) for globalization support.</span></span> <span data-ttu-id="d494a-149">在不區分模式中，您的部署不包含程式庫，而且所有文化特性的行為[不因文化特性而異](xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType)。</span><span class="sxs-lookup"><span data-stu-id="d494a-149">In invariant mode, the libraries are not included with your deployment, and all cultures behave like the [invariant culture](xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType).</span></span>

- <span data-ttu-id="d494a-150">將多個自封式 .NET Core 應用程式部署到系統，會消耗大量的磁碟空間，因為每個應用程式都會重複 .NET Core 檔案。</span><span class="sxs-lookup"><span data-stu-id="d494a-150">Deploying numerous self-contained .NET Core apps to a system can consume significant amounts of disk space, since each app duplicates .NET Core files.</span></span>

## <a name="step-by-step-examples"></a><span data-ttu-id="d494a-151">逐步說明範例</span><span class="sxs-lookup"><span data-stu-id="d494a-151">Step-by-step examples</span></span>

<span data-ttu-id="d494a-152">如需使用 CLI 工具部署 .NET Core 應用程式的逐步說明範例，請參閱[使用 CLI 工具部署 .NET Core 應用程式](deploy-with-cli.md)。</span><span class="sxs-lookup"><span data-stu-id="d494a-152">For step-by-step examples of deploying .NET Core apps with CLI tools, see [Deploying .NET Core Apps with CLI Tools](deploy-with-cli.md).</span></span> <span data-ttu-id="d494a-153">如需使用 Visual Studio 部署 .NET Core 應用程式的逐步說明範例，請參閱[使用 Visual Studio 部署 .NET Core 應用程式](deploy-with-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="d494a-153">For step-by-step examples of deploying .NET Core apps with Visual Studio, see [Deploying .NET Core Apps with Visual Studio](deploy-with-vs.md).</span></span> <span data-ttu-id="d494a-154">每個主題都包含下列部署的範例：</span><span class="sxs-lookup"><span data-stu-id="d494a-154">Each topic includes examples of the following deployments:</span></span>

- <span data-ttu-id="d494a-155">與 Framework 相依的部署</span><span class="sxs-lookup"><span data-stu-id="d494a-155">Framework-dependent deployment</span></span>
- <span data-ttu-id="d494a-156">有協力廠商相依性的 Framework 相依部署</span><span class="sxs-lookup"><span data-stu-id="d494a-156">Framework-dependent deployment with third-party dependencies</span></span>
- <span data-ttu-id="d494a-157">自封式部署</span><span class="sxs-lookup"><span data-stu-id="d494a-157">Self-contained deployment</span></span>
- <span data-ttu-id="d494a-158">有協力廠商相依性的自封式部署</span><span class="sxs-lookup"><span data-stu-id="d494a-158">Self-contained deployment with third-party dependencies</span></span>

## <a name="see-also"></a><span data-ttu-id="d494a-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d494a-159">See also</span></span>

* [<span data-ttu-id="d494a-160">使用 CLI 工具部署 .NET Core 應用程式</span><span class="sxs-lookup"><span data-stu-id="d494a-160">Deploying .NET Core Apps with CLI Tools</span></span>](deploy-with-cli.md)
* [<span data-ttu-id="d494a-161">使用 Visual Studio 部署 .NET Core 應用程式</span><span class="sxs-lookup"><span data-stu-id="d494a-161">Deploying .NET Core Apps with Visual Studio</span></span>](deploy-with-vs.md)
* [<span data-ttu-id="d494a-162">套件、中繼套件和架構</span><span class="sxs-lookup"><span data-stu-id="d494a-162">Packages, Metapackages and Frameworks</span></span>](../packages.md)
* [<span data-ttu-id="d494a-163">.NET Core 執行階段識別項 (RID) 目錄</span><span class="sxs-lookup"><span data-stu-id="d494a-163">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
