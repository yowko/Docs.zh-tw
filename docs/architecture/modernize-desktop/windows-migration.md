---
title: Windows 10 遷移
description: 深入探討 Windows 10 的功能，例如封裝和 XAML 群島。
ms.date: 09/16/2019
ms.openlocfilehash: cd17088b086a32fd3bb37e617d3a1047acedde0e
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2020
ms.locfileid: "83423205"
---
# <a name="windows-10-migration"></a><span data-ttu-id="1c9bb-103">Windows 10 遷移</span><span class="sxs-lookup"><span data-stu-id="1c9bb-103">Windows 10 migration</span></span>

<span data-ttu-id="1c9bb-104">請考慮下列情況：您有一個在 Windows 7 天內開發的工作桌面應用程式。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-104">Consider the following situation: You have a working desktop application that was developed in the Windows 7 days.</span></span> <span data-ttu-id="1c9bb-105">它使用的是目前提供的 WPF 技術，而且可以正常運作，但當您在 Windows 10 上執行它時，它會有過時的 UI 和行為。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-105">It's using WPF technology available at that time and working fine but it has an outdated UI and behaviors when you run it on Windows 10.</span></span> <span data-ttu-id="1c9bb-106">當您觀賞幻想式道具影片（例如矩陣），而您看到使用 Nokia 8110 裝置的 Neo 時，就是如此。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-106">It is like when you watch a futuristic movie like Matrix and you see Neo using the Nokia 8110 device.</span></span> <span data-ttu-id="1c9bb-107">電影在20年後可正常運作，但它可以從裝置現代化中獲益。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-107">The film works great after 20 years but it would rather benefit from a device modernization.</span></span>

<span data-ttu-id="1c9bb-108">隨著 Windows 10 的發行，Microsoft 引進了許多創新功能來支援平板電腦和觸控裝置等案例，並為 Microsoft 作業系統的使用者提供最佳的體驗。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-108">With the release of Windows 10, Microsoft introduced many innovations to support scenarios like tablets and touch devices and to provide the best experience for users for a Microsoft operating system ever.</span></span> <span data-ttu-id="1c9bb-109">例如，您可以：</span><span class="sxs-lookup"><span data-stu-id="1c9bb-109">For example, you can:</span></span>

- <span data-ttu-id="1c9bb-110">使用 Windows Hello 登入您的臉部。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-110">Sign in with your face using Windows Hello.</span></span>
- <span data-ttu-id="1c9bb-111">使用畫筆繪製或手寫自動辨識和 digitalized 的文字。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-111">Use a pen to draw or handwrite text that is automatically recognized and digitalized.</span></span>
- <span data-ttu-id="1c9bb-112">使用 WinML，在雲端上執行建置於本機的自訂 AI 模型。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-112">Run locally customized AI models built on the cloud using WinML.</span></span>

<span data-ttu-id="1c9bb-113">Windows 開發人員可以透過 Windows 執行階段（WinRT）程式庫來啟用所有這些功能。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-113">All these features are enabled for Windows developers through Windows Runtime (WinRT) libraries.</span></span> <span data-ttu-id="1c9bb-114">您可以在現有的桌面應用程式中利用這些功能，因為程式庫也會同時公開到 .NET Framework 和 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-114">You can take advantage of these features in your existing desktop apps because the libraries are exposed to both the .NET Framework and .NET Core as well.</span></span> <span data-ttu-id="1c9bb-115">您甚至可以使用 XAML Islands 將您的 UI 現代化，並根據時間改善應用程式的視覺效果和行為。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-115">You can even modernize your UI with the use of XAML Islands and improve the visuals and behavior of your apps according to the times.</span></span>

<span data-ttu-id="1c9bb-116">這裡要注意的一點是，您不需要放棄 .NET Framework 技術，就能遵循這項現代化路徑。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-116">One important thing to note here is that you don't need to abandon .NET Framework technology to follow this modernization path.</span></span> <span data-ttu-id="1c9bb-117">您可以放心地掌握 Windows 10 的所有優點，而不需要遷移至 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-117">You can safely stay on there and have all the benefits of Windows 10 without the pressure to migrate to .NET Core.</span></span> <span data-ttu-id="1c9bb-118">因此，您可以同時取得選擇現代化路徑的能力和彈性。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-118">So, you get both the power and the flexibility to choose your modernization path.</span></span>

## <a name="winrt-apis"></a><span data-ttu-id="1c9bb-119">WinRT Api</span><span class="sxs-lookup"><span data-stu-id="1c9bb-119">WinRT APIs</span></span>

<span data-ttu-id="1c9bb-120">WinRT Api 是物件導向、結構良好的應用程式設計介面（Api），可讓 Windows 10 開發人員存取作業系統所提供的所有專案。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-120">WinRT APIs are object-oriented, well-structured application programming interfaces (APIs) that give Windows 10 developers access to everything the operating system has to offer.</span></span> <span data-ttu-id="1c9bb-121">透過 WinRT Api，您可以在桌面應用程式中整合功能，例如推播通知、裝置 Api、Microsoft 筆跡和 WinML。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-121">Through WinRT APIs, you can integrate functionalities like Push Notifications, Device APIs, Microsoft Ink, and WinML, among others on your desktop apps.</span></span>

<span data-ttu-id="1c9bb-122">一般來說，您可以從傳統桌面應用程式呼叫 WinRT Api。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-122">In general, WinRT APIs can be called from a classic desktop app.</span></span> <span data-ttu-id="1c9bb-123">不過，有兩個主要區域對此規則造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="1c9bb-123">However, two main areas present an exception to this rule:</span></span>

* <span data-ttu-id="1c9bb-124">需要套件身分識別的 Api。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-124">APIs that require a package identity.</span></span>
* <span data-ttu-id="1c9bb-125">需要 XAML 或複合等視覺效果的 Api。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-125">APIs that require visualization like XAML or Composition.</span></span>

### <a name="universal-windows-platform-uwp-packages"></a><span data-ttu-id="1c9bb-126">通用 Windows 平臺（UWP）套件</span><span class="sxs-lookup"><span data-stu-id="1c9bb-126">Universal Windows Platform (UWP) packages</span></span>

#### <a name="application-package-identity"></a><span data-ttu-id="1c9bb-127">應用程式套件識別</span><span class="sxs-lookup"><span data-stu-id="1c9bb-127">Application Package Identity</span></span>

<span data-ttu-id="1c9bb-128">UWP 應用程式具有部署系統，作業系統會在其中管理應用程式的安裝和卸載。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-128">UWP apps have a deployment system where the OS manages the installation and uninstallation of application.</span></span> <span data-ttu-id="1c9bb-129">這需要以宣告方式安裝，這表示在安裝期間不會執行任何使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-129">That requires the installation to be declarative, meaning that no user code is executed during install.</span></span> <span data-ttu-id="1c9bb-130">相反地，應用程式想要與系統整合的所有專案（例如通訊協定、檔案類型和擴充功能）都會在應用程式資訊清單中宣告。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-130">Instead, everything the app wants to integrate with the system, such as protocols, file types, and extensions, is declared in the application manifest.</span></span> <span data-ttu-id="1c9bb-131">在部署期間，部署管線會設定這些整合點。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-131">At deployment time, the deployment pipeline configures those integration points.</span></span> <span data-ttu-id="1c9bb-132">作業系統管理所有這項功能並持續追蹤的唯一方法，是讓每個「套件」都有一個身分識別，也就是應用程式的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-132">The only way for the OS to manage all this functionality and keep track of it is for each 'package' to have an identity, a unique identifier for the application.</span></span>

<span data-ttu-id="1c9bb-133">某些 WinRT Api 需要此套件身分識別才能如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-133">Some WinRT APIs require this package identity to work as expected.</span></span> <span data-ttu-id="1c9bb-134">不過，傳統的桌面應用程式（例如原生 c + + 或 .NET 應用程式）會使用不同的部署系統，而不需要套件身分識別。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-134">However, classic desktop apps like native C++ or .NET apps, use different deployment systems that don't require a package identity.</span></span> <span data-ttu-id="1c9bb-135">如果您想要在桌面應用程式中使用這些 WinRT Api，您必須為它們提供套件識別。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-135">If you want to use these WinRT APIs in your desktop application, you need to provide them a package identity.</span></span>

<span data-ttu-id="1c9bb-136">其中一種方法是建立額外的封裝專案。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-136">One way to proceed is to build an additional packaging project.</span></span> <span data-ttu-id="1c9bb-137">在封裝專案內，您要指向原始的原始程式碼專案，並指定您想要提供的身分識別資訊。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-137">Inside the packaging project, you point to the original source code project and specify the Identity information you want to provide.</span></span><span data-ttu-id="1c9bb-138">如果您安裝套件並執行已安裝的應用程式，它會自動取得識別，讓您的程式碼能夠呼叫所有需要身分識別的 WinRT Api。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-138"> If you install the package and run the installed app, it will automatically get an identify enabling your code to call all WinRT APIs requiring Identity.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<Package xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10">
    <Identity Name="YOUR-APP-GUID "
              Publisher="CN=YOUR COMPANY"
              Version="1.x.x.x" />
</Package>
```

<span data-ttu-id="1c9bb-139">您可以藉由檢查包含 API 的類型是否以[DualApiPartition](xref:Windows.Foundation.Metadata.DualApiPartitionAttribute)屬性標記，以檢查哪些 api 需要已封裝的應用程式識別。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-139">You can check which APIs need a packaged application identity by inspecting if the type that contains the API is marked with the [DualApiPartition](xref:Windows.Foundation.Metadata.DualApiPartitionAttribute) attribute.</span></span><span data-ttu-id="1c9bb-140">如果是，您可以從未封裝的傳統桌面應用程式呼叫。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-140"> If it is, you can call if from an unpackaged traditional desktop app.</span></span> <span data-ttu-id="1c9bb-141">否則，您必須透過封裝專案的協助，將傳統桌面應用程式轉換成 UWP。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-141">Otherwise, you must convert your classic desktop app to a UWP with the help of a packaging project.</span></span>

<https://docs.microsoft.com/windows/desktop/apiindex/uwp-apis-callable-from-a-classic-desktop-app>

#### <a name="benefits-of-packaging"></a><span data-ttu-id="1c9bb-142">封裝的優點</span><span class="sxs-lookup"><span data-stu-id="1c9bb-142">Benefits of packaging</span></span>

<span data-ttu-id="1c9bb-143">除了提供這些 Api 的存取權之外，您還可以建立桌面應用程式的 Windows 應用程式套件，以獲得一些額外的好處，包括：</span><span class="sxs-lookup"><span data-stu-id="1c9bb-143">Besides giving you access to these APIs, you get some additional benefits by creating a Windows App package for your desktop application including:</span></span>

* <span data-ttu-id="1c9bb-144">**簡化部署**。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-144">**Streamlined deployment**.</span></span> <span data-ttu-id="1c9bb-145">應用程式具備絕佳的部署體驗，確保使用者可以安心地安裝應用程式並加以更新。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-145">Apps have a great deployment experience ensuring that users can confidently install an application and update it.</span></span> <span data-ttu-id="1c9bb-146">如果使用者選擇卸載應用程式，它會完全移除，且不會留下任何追蹤來防止 Windows rot 問題。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-146">If a user chooses to uninstall the app, it's removed completely with no trace left behind preventing the Windows rot problem.</span></span>

* <span data-ttu-id="1c9bb-147">**自動更新和授權**。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-147">**Automatic updates and licensing**.</span></span> <span data-ttu-id="1c9bb-148">您的應用程式可以參與 Microsoft Store 的內建授權和自動更新功能。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-148">Your application can participate in the Microsoft Store's built-in licensing and automatic update facilities.</span></span> <span data-ttu-id="1c9bb-149">由於自動更新只會下載檔案已變更的部分，因此是一項非常可靠又有效率的機制。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-149">Automatic update is a highly reliable and efficient mechanism, because only the changed parts of files are downloaded.</span></span>

* <span data-ttu-id="1c9bb-150">**增加觸達對象並簡化營利**。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-150">**Increased reach and simplified monetization**.</span></span> <span data-ttu-id="1c9bb-151">也許不是您的案例，但如果您選擇透過 Microsoft Store 散發應用程式，就會抵達數百萬部 Windows 10 使用者。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-151">Maybe not your case but if you choose to distribute your application through the Microsoft Store you reach millions of Windows 10 users.</span></span>

* <span data-ttu-id="1c9bb-152">**新增 UWP 功能**。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-152">**Add UWP features**.</span></span> <span data-ttu-id="1c9bb-153">您可以依照自己的步調，將 UWP 功能新增至應用程式的套件。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-153">You can add UWP features to your app's package at your own pace.</span></span>

#### <a name="prepare-for-packaging"></a><span data-ttu-id="1c9bb-154">準備封裝</span><span class="sxs-lookup"><span data-stu-id="1c9bb-154">Prepare for packaging</span></span>

<span data-ttu-id="1c9bb-155">在繼續封裝您的桌面應用程式之前，您必須先處理幾個重點，才能開始處理。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-155">Before proceeding to package your desktop application, there are some points you have to address before starting the process.</span></span> <span data-ttu-id="1c9bb-156">您的應用程式必須遵守任何 Microsoft Store 規則和原則，並在 UWP 應用程式模型中執行。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-156">Your application must respect any of the Microsoft Store rules and policies and run in the UWP application model.</span></span> <span data-ttu-id="1c9bb-157">例如，它必須在 .NET Framework 4.6.2 或更新版本上執行，並寫入登錄區 `HKEY_CURRENT_USER` ，而 AppData 資料夾將會虛擬化到使用者特定的應用程式-本機位置。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-157">For example, it has to run on the .NET Framework 4.6.2 or later and writes to the `HKEY_CURRENT_USER` registry hive and the AppData folders will be virtualized to a user-specific app-local location.</span></span>

<span data-ttu-id="1c9bb-158">封裝的設計目標是要將應用程式狀態與系統狀態分開，同時維持與其他應用程式的相容性。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-158">The design goal for packaging is to separate the application state from system state while maintaining compatibility with other apps.</span></span> <span data-ttu-id="1c9bb-159">Windows 10 藉由將應用程式放在 UWP 套件內來完成此目標。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-159">Windows 10 accomplishes this goal by placing the application inside a UWP package.</span></span> <span data-ttu-id="1c9bb-160">它會在執行時間偵測並重新導向檔案系統和登錄的某些變更，以滿足封裝所提供之應用程式的信任和全新安裝和卸載行為的承諾。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-160">It detects and redirects some changes to the file system and registry at run time to fulfill the promise of a trusted and clean install and uninstall behavior of an application provided by packaging.</span></span>

<span data-ttu-id="1c9bb-161">您為桌面應用程式建立的套件是僅限桌上型電腦的完全信任應用程式，不會進行沙箱處理，雖然應用程式已套用輕量虛擬化以寫入 `HKCU` 和 `AppData` 。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-161">Packages that you create for your desktop application are desktop-only, full-trust applications that aren't sandboxed, although there's lightweight virtualization applied to the app for writes to `HKCU` and `AppData`.</span></span> <span data-ttu-id="1c9bb-162">此虛擬化可讓他們以傳統桌面應用程式的相同方式與其他應用程式互動。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-162">This virtualization allows them to interact with other apps the same way classic desktop applications do.</span></span>

##### <a name="installation"></a><span data-ttu-id="1c9bb-163">安裝</span><span class="sxs-lookup"><span data-stu-id="1c9bb-163">Installation</span></span>

<span data-ttu-id="1c9bb-164">應用程式套件會安裝在 *% ProgramFiles% \\ WindowsApps \\ package_name*底下，且可執行檔標題為  `app_name.exe` 。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-164">App packages are installed under *%ProgramFiles%\\WindowsApps\\package_name*, with the executable titled `app_name.exe`.</span></span> <span data-ttu-id="1c9bb-165">每個套件資料夾都包含資訊清單（名為 `AppxManifest.xml` ），其中包含已封裝應用程式的特殊 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-165">Each package folder contains a manifest (named `AppxManifest.xml`) that contains a special XML namespace for packaged apps.</span></span> <span data-ttu-id="1c9bb-166">在該資訊清單檔案內是一個  `<EntryPoint>`   元素，它會參考完全信任的應用程式。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-166">Inside that manifest file is an `<EntryPoint>` element, which references the full-trust app.</span></span> <span data-ttu-id="1c9bb-167">當該應用程式啟動時，它不會在應用程式容器內執行，而是會以一般的使用者身分執行。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-167">When that application is launched, it doesn't run inside an app container, but instead it runs as the user as it normally would.</span></span>

<span data-ttu-id="1c9bb-168">部署之後，套件檔案會由作業系統標示為唯讀並嚴密地鎖定。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-168">After deployment, package files are marked read-only and heavily locked down by the operating system.</span></span> <span data-ttu-id="1c9bb-169">如果這些檔案遭到竄改，Windows 會防止這些 App 啟動。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-169">Windows prevents apps from launching if these files are tampered with.</span></span>

##### <a name="file-system"></a><span data-ttu-id="1c9bb-170">檔案系統</span><span class="sxs-lookup"><span data-stu-id="1c9bb-170">File system</span></span>

<span data-ttu-id="1c9bb-171">作業系統支援封裝桌面應用程式的不同層級檔案系統作業，視資料夾位置而定。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-171">The OS supports different levels of file system operations for packaged desktop applications, depending on the folder location.</span></span>

<span data-ttu-id="1c9bb-172">嘗試存取使用者的*AppData*資料夾時，系統會在幕後建立私用的每個使用者、每個應用程式的位置。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-172">When trying to access the user's *AppData* folder, the system creates a private per-user, per-app location behind the scenes.</span></span> <span data-ttu-id="1c9bb-173">這會建立封裝的應用程式在實際修改私用複本時，正在編輯實際*AppData*的假像。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-173">This creates the illusion that the packaged application is editing the real *AppData* when it's actually modifying a private copy.</span></span> <span data-ttu-id="1c9bb-174">透過這種方式將寫入重新導向，系統就可以追蹤 App 執行的所有檔案修改。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-174">By redirecting writes this way, the system can track all file modifications made by the app.</span></span> <span data-ttu-id="1c9bb-175">然後，它可以在卸載減少系統 "rot" 時清除所有這些檔案，並為使用者提供更好的應用程式移除體驗。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-175">It can then clean all those files when uninstalling reducing system "rot" and providing a better application removal experience for the user.</span></span>

##### <a name="registry"></a><span data-ttu-id="1c9bb-176">登錄</span><span class="sxs-lookup"><span data-stu-id="1c9bb-176">Registry</span></span>

<span data-ttu-id="1c9bb-177">應用程式套件包含一個登錄 .dat 檔案，其可做為  `HKLM\Software` 實際登錄中的邏輯對等檔案   。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-177">App packages contain a registry.dat file, which serves as the logical equivalent of `HKLM\Software` in the real registry.</span></span> <span data-ttu-id="1c9bb-178">在執行階段，此虛擬登錄會將此登錄區的內容合併至原生系統登錄區，以提供兩者的單一檢視。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-178">At runtime, this virtual registry merges the contents of this hive into the native system hive to provide a singular view of both.</span></span>

<span data-ttu-id="1c9bb-179">所有寫入都會在封裝升級期間保留，而且只會在應用程式卸載時刪除。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-179">All writes are kept during package upgrade and only deleted when the application is uninstalled.</span></span>

##### <a name="uninstallation"></a><span data-ttu-id="1c9bb-180">解除安裝</span><span class="sxs-lookup"><span data-stu-id="1c9bb-180">Uninstallation</span></span>

<span data-ttu-id="1c9bb-181">當使用者卸載套件時，位於底下的所有檔案和資料夾  `C:\Program Files\WindowsApps\package_name` 都會被移除，以及在處理過程中所捕捉到的 AppData 或登錄的任何重新導向寫入。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-181">When the user uninstalls a package, all files and folders located under `C:\Program Files\WindowsApps\package_name` are removed, as well as any redirected writes to AppData or the registry that were captured during the process.</span></span>

<span data-ttu-id="1c9bb-182">如需封裝的應用程式如何處理安裝、檔案存取、登錄和卸載的詳細資訊，請參閱 <https://docs.microsoft.com/windows/msix/desktop/desktop-to-uwp-behind-the-scenes> 。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-182">For details about how a packaged application handles installation, file access, registry, and uninstallation, see <https://docs.microsoft.com/windows/msix/desktop/desktop-to-uwp-behind-the-scenes>.</span></span>

<span data-ttu-id="1c9bb-183">您可以取得要檢查的完整專案清單 <https://docs.microsoft.com/windows/msix/desktop/desktop-to-uwp-prepare> 。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-183">You can get a complete list of things to check on <https://docs.microsoft.com/windows/msix/desktop/desktop-to-uwp-prepare>.</span></span>

## <a name="how-to-add-winrt-apis-to-your-desktop-project"></a><span data-ttu-id="1c9bb-184">如何將 WinRT Api 新增至您的桌面專案</span><span class="sxs-lookup"><span data-stu-id="1c9bb-184">How to add WinRT APIs to your desktop project</span></span>

<span data-ttu-id="1c9bb-185">在本節中，您可以找到如何整合現有 WPF 應用程式中快顯通知的逐步解說。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-185">In this section, you can find a walkthrough on how to integrate Toast Notifications in an existing WPF application.</span></span> <span data-ttu-id="1c9bb-186">雖然程式碼的觀點很簡單，但它有助於說明整個程式。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-186">Although it's simple from the code perspective, it helps illustrate the whole process.</span></span> <span data-ttu-id="1c9bb-187">通知是您可以在 .NET 應用程式中使用的許多可用的 WinRT Api 之一。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-187">Notifications are one of the many available WinRT APIs available that you can use in .NET app.</span></span> <span data-ttu-id="1c9bb-188">在此情況下，API 需要套件身分識別。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-188">In this case, the API requires a Package Identity.</span></span> <span data-ttu-id="1c9bb-189">如果 Api 不需要套件身分識別，則此程式更直接。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-189">This process is more straightforward if the APIs don't require Package Identity.</span></span>

<span data-ttu-id="1c9bb-190">讓我們來看一個現有的 WPF 範例應用程式，它會讀取檔案，並在螢幕上顯示其內容。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-190">Let's take an existing WPF sample app that reads files and shows its contents on the screen.</span></span> <span data-ttu-id="1c9bb-191">其目標是要在應用程式啟動時顯示快顯通知。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-191">The goal is to display a Toast Notification when the application starts.</span></span>

![執行中範例應用程式的螢幕擷取畫面](./media/windows-migration/sample-application.png)

<span data-ttu-id="1c9bb-193">首先，您應該簽入下列連結，不論您要使用的 Windows 10 API 是否需要套件身分識別：</span><span class="sxs-lookup"><span data-stu-id="1c9bb-193">First, you should check in the following link whether the Windows 10 API that you'll use requires a Package Identity:</span></span>

<https://docs.microsoft.com/windows/apps/desktop/modernize/desktop-to-uwp-supported-api>

<span data-ttu-id="1c9bb-194">我們的範例會使用 <xref:Windows.UI.Notifications.Notification?displayProperty=nameWithType> 需要已封裝身分識別的 API：</span><span class="sxs-lookup"><span data-stu-id="1c9bb-194">Our sample will use the <xref:Windows.UI.Notifications.Notification?displayProperty=nameWithType> API that requires a packaged identity:</span></span>

![Microsoft 檔中的通知類別](./media/windows-migration/notification-class-documentation.png)

<span data-ttu-id="1c9bb-196">若要存取 WinRT API，請將參考新增至 `Microsoft.Windows.SDK.Contracts`   NuGet 套件，此套件將會在幕後執行魔術（請參閱中的詳細資料 <https://blogs.windows.com/windowsdeveloper/2019/04/30/calling-windows-10-apis-from-a-desktop-application-just-got-easier/> ）。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-196">To access the WinRT API, add a reference to the `Microsoft.Windows.SDK.Contracts` NuGet package and this package will do the magic behind the scenes (see details at <https://blogs.windows.com/windowsdeveloper/2019/04/30/calling-windows-10-apis-from-a-desktop-application-just-got-easier/>).</span></span>

<span data-ttu-id="1c9bb-197">您現在已經準備好開始新增一些程式碼。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-197">You're now prepared to start adding some code.</span></span>

<span data-ttu-id="1c9bb-198">建立 `ShowToastNotification` 將在應用程式啟動時呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-198">Create a `ShowToastNotification` method that will be called on application startup.</span></span> <span data-ttu-id="1c9bb-199">它只會從 XML 模式建立快顯通知：</span><span class="sxs-lookup"><span data-stu-id="1c9bb-199">It just builds a toast notification from an XML pattern:</span></span>

```csharp
private void ShowNotification(string title, string content, string image)
{
    string xmlString = $@"<toast><visual><binding template = 'ToastGeneric'><text>{title}</text><text>{content}</text><image src=>'{image}'</image></binding></visual></toast>";
    XmlDocument toastXml = new XmlDocument();
    toastXml.LoadXml(xmlString);
    ToastNotification toast = new ToastNotification(toastXml);
    ToastNotificationManager.CreateToastNotifier().Show(toast);
}
```

<span data-ttu-id="1c9bb-200">雖然專案會建立，但有一些錯誤，因為通知 API 需要套件識別，但您並未提供它。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-200">Although the project builds, there are errors because the Notifications API requires a Package Identity and you didn't provide it.</span></span> <span data-ttu-id="1c9bb-201">將 Windows 封裝專案新增至方案將會修正此問題：</span><span class="sxs-lookup"><span data-stu-id="1c9bb-201">Adding a Windows Packaging Project to the solution will fix the issue:</span></span>

![Visual Studio 中 [新增專案] 對話方塊的螢幕擷取畫面](./media/windows-migration/add-packaging-project.png)

<span data-ttu-id="1c9bb-203">選取您想要支援的最低 Windows 版本，以及您的目標版本。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-203">Select the minimum Windows version you want to support and the version you're targeting.</span></span> <span data-ttu-id="1c9bb-204">並非所有的 Windows 10 版本都支援所有 WinRT Api。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-204">Not all the WinRT APIs are supported in all Windows 10 versions.</span></span> <span data-ttu-id="1c9bb-205">每個 Windows 10 更新都會加入僅此版本提供的新 Api;下層支援無法使用。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-205">Each Windows 10 update adds new APIs that are only available from this version; down-level support isn't available.</span></span>

![選取最低 Windows 版本](./media/windows-migration/select-versions.png)

<span data-ttu-id="1c9bb-207">下一個步驟是藉由新增專案參考，將 WPF 應用程式新增至 Windows 封裝專案：</span><span class="sxs-lookup"><span data-stu-id="1c9bb-207">Next step is to add the WPF application to the Windows Packaging Project by adding a project reference:</span></span>

![將 WPF 應用程式新增至 Windows 封裝專案](./media/windows-migration/add-application.png)

![參考管理員](./media/windows-migration/reference-manager.png)

<span data-ttu-id="1c9bb-210">Windows 封裝專案可以封裝數個應用程式，因此您應該設定哪一個是進入點：</span><span class="sxs-lookup"><span data-stu-id="1c9bb-210">A Windows Packaging Project can package several apps so you should set which one is the Entry Point:</span></span>

![設定進入點](./media/windows-migration/set-entry-point.png)

<span data-ttu-id="1c9bb-212">下一步是在解決方案設定中，將 WPF 專案設為啟始專案。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-212">Next step is to set the WPF Project as the startup Project in the solution configuration.</span></span> <span data-ttu-id="1c9bb-213">您可以按 F5 來編譯並查看結果。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-213">You can press F5 to compile and build and see the results.</span></span>

![執行和顯示結果的範例應用程式](./media/windows-migration/sample-app-result.png)

<span data-ttu-id="1c9bb-215">讓我們產生套件，讓您可以安裝您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-215">Let's generate the package so you can install your app.</span></span> <span data-ttu-id="1c9bb-216">以滑鼠右鍵按一下 [**存放區**] [  >  **建立應用程式套件**]。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-216">Right click on **Store** > **Create App Packages**.</span></span>

![[建立應用程式套件] 對話方塊](./media/windows-migration/create-app-packages.png)

<span data-ttu-id="1c9bb-218">選取 [側載] 選項以從您的電腦部署應用程式：</span><span class="sxs-lookup"><span data-stu-id="1c9bb-218">Select the sideloading option to deploy the app from your machine:</span></span>

![選取側載選項](./media/windows-migration/select-sideloading-option.png)

<span data-ttu-id="1c9bb-220">選取您應用程式的應用程式架構：</span><span class="sxs-lookup"><span data-stu-id="1c9bb-220">Select the application architecture of your app:</span></span>

![選取應用程式架構](./media/windows-migration/select-app-architecture.png)

<span data-ttu-id="1c9bb-222">最後，按一下 [**建立**] 來建立封裝。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-222">Finally, create the package by clicking on **Create**.</span></span>

## <a name="xaml-islands"></a><span data-ttu-id="1c9bb-223">XAML Islands</span><span class="sxs-lookup"><span data-stu-id="1c9bb-223">XAML Islands</span></span>

<span data-ttu-id="1c9bb-224">XAML 孤島是一組元件，可讓 Windows 桌面開發人員在其現有的 Win32 應用程式（包括 Windows Forms 和 WPF）上使用 UWP XAML 控制項。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-224">XAML Islands are a set of components that enable Windows desktop developers to use UWP XAML controls on their existing Win32 applications, including Windows Forms and WPF.</span></span>

![XAML 群島的結構](./media/windows-migration/xaml-islands.png)

<span data-ttu-id="1c9bb-226">您可以使用您的標準控制項來進行 Win32 應用程式的映射，並在其中包含來自現代化世界之控制項的「島」 UWP UI。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-226">You can image your Win32 app with your standard controls and among them an "island" of UWP UI containing controls from the modern world.</span></span> <span data-ttu-id="1c9bb-227">概念類似于在網頁內擁有一個 iFrame，其中顯示來自的內容`different page.`</span><span class="sxs-lookup"><span data-stu-id="1c9bb-227">The concept is similar as having an iFrame inside a web page that shows content from a `different page.`</span></span>

<span data-ttu-id="1c9bb-228">除了從 Windows 10 Api 新增功能之外，您還可以使用 XAML 島，在應用程式內新增 UWP XAML 的片段。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-228">Besides adding functionality from the Windows 10 APIs, you can add pieces of UWP XAML inside of your app using XAML Islands.</span></span>

<span data-ttu-id="1c9bb-229">Windows 10 1903 update 引進了一組 Api，可讓您在 Win32 視窗中裝載 UWP XAML 內容。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-229">Windows 10 1903 update introduces a set of APIs that allows hosting UWP XAML content in Win32 windows.</span></span> <span data-ttu-id="1c9bb-230">只有在 Windows 10 1903 上執行的應用程式可以使用 XAML 島。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-230">Only apps running on Windows 10 1903 can use XAML Islands.</span></span>

### <a name="the-road-to-xaml-islands"></a><span data-ttu-id="1c9bb-231">XAML 島的道路</span><span class="sxs-lookup"><span data-stu-id="1c9bb-231">The road to XAML Islands</span></span>

<span data-ttu-id="1c9bb-232">當 Microsoft 引進 WinRT Api 做為架構，將 Win32 應用程式（Windows Forms、WPF 和原生 Win32 應用程式）現代化時，從2012開始的 XAML 孤島。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-232">The road to XAML Islands started in 2012 when Microsoft introduced the WinRT APIs as a framework to modernize the Win32 apps (Windows Forms, WPF, and native Win32 apps).</span></span> <span data-ttu-id="1c9bb-233">不過，WinRT 中新的 UI 控制項適用于新的應用程式，但不適用於現有的應用程式。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-233">However, the new UI controls inside WinRT were available for new applications but not for existing ones.</span></span>

<span data-ttu-id="1c9bb-234">隨著 Windows 10 的2015，UWP 已經出生。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-234">In 2015, along with Windows 10, UWP was born.</span></span> <span data-ttu-id="1c9bb-235">UWP 可讓您建立可跨 Windows 裝置（例如 XBox、Mobile 和 Desktop）工作的應用程式。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-235">UWP allows you to create apps that work across Windows devices like XBox, Mobile, and Desktop.</span></span> <span data-ttu-id="1c9bb-236">一年後，Microsoft 宣佈了桌面橋接器（先前稱為 Project Centennial）。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-236">One year later, Microsoft announced Desktop Bridge (formerly known as Project Centennial).</span></span> <span data-ttu-id="1c9bb-237">桌面橋接器是一組工具，可讓開發人員將其現有的 Win32 應用程式帶入 Microsoft Store。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-237">Desktop Bridge is a set of tools that allowed developers to bring their existing Win32 apps to the Microsoft Store.</span></span> <span data-ttu-id="1c9bb-238">2017中新增了更多功能，可讓開發人員利用一些新的 Windows 10 Api 來增強其 Win32 應用程式，例如行動中心的動態磚和通知。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-238">More capabilities were added in 2017, allowing developers to enhance their Win32 apps leveraging some of the new Windows 10 APIs, like live tiles and notifications on the action center.</span></span> <span data-ttu-id="1c9bb-239">但還是沒有新的 UI 控制項。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-239">But still, no new UI controls.</span></span>

<span data-ttu-id="1c9bb-240">在組建2018中，Microsoft 宣佈了一種方法，讓開發人員可以將新的 Windows 10 XAML 控制項用於目前的 Win32 應用程式，而不需要將其應用程式完全遷移至 UWP。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-240">At Build 2018, Microsoft announced a way for developers to use the new Windows 10 XAML controls into their current Win32 apps, without fully migrating their apps to UWP.</span></span> <span data-ttu-id="1c9bb-241">其品牌為 UWP XAML 群島。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-241">It was branded as UWP XAML Islands.</span></span>

### <a name="how-it-works"></a><span data-ttu-id="1c9bb-242">運作方式</span><span class="sxs-lookup"><span data-stu-id="1c9bb-242">How it works</span></span>

<span data-ttu-id="1c9bb-243">Windows 10 1903 update 引進數個 XAML 裝載 Api。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-243">The Windows 10 1903 update introduces several XAML hosting APIs.</span></span> <span data-ttu-id="1c9bb-244">其中兩個是 `WindowsXamlManager`   和  `DesktopWindowXamlSource` 。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-244">Two of them are `WindowsXamlManager` and `DesktopWindowXamlSource`.</span></span>

<span data-ttu-id="1c9bb-245"> `WindowsXamlManager`   類別會處理 UWP XAML 架構。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-245">The `WindowsXamlManager` class handles the UWP XAML Framework.</span></span> <span data-ttu-id="1c9bb-246">其 `InitializeForCurrentThread` 方法會在 Win32 應用程式的目前線程內載入 UWP XAML 架構。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-246">Its `InitializeForCurrentThread` method loads the UWP XAML Framework inside the current thread of the Win32 app.</span></span>

<span data-ttu-id="1c9bb-247"> `DesktopWindowXamlSource`   是 XAML 島內容的實例。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-247">The `DesktopWindowXamlSource` is the instance of your XAML Island content.</span></span> <span data-ttu-id="1c9bb-248">它具有 `Content` 屬性，您必須負責具現化和設定。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-248">It has the `Content` property, which you're responsible for instantiating and setting.</span></span> <span data-ttu-id="1c9bb-249">會 `DesktopWindowXamlSource`   呈現並從 HWND 取得其輸入。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-249">The `DesktopWindowXamlSource` renders and gets its input from an HWND.</span></span> <span data-ttu-id="1c9bb-250">它需要知道它將附加 XAML 島的其他 HWND，而且您必須負責調整大小和定位父系的 HWND。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-250">It needs to know to which other HWND it will attach the XAML Island's one, and you're responsible for sizing and positioning the parent's HWND.</span></span>

<span data-ttu-id="1c9bb-251">WPF 或 Windows Forms 開發人員通常不會處理其程式碼內的 HWND，因此可能很難瞭解並處理 HWND 指標和基礎接線內容，以溝通 Win32 和 UWP 的世界。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-251">WPF or Windows Forms developers don't usually deal with HWND inside their code, so it may be hard to understand and handle HWND pointers and the underlying wiring stuff to communicate Win32 and UWP worlds.</span></span>

#### <a name="the-xaml-islands-net-wrappers"></a><span data-ttu-id="1c9bb-252">XAML 島 .NET 包裝函式</span><span class="sxs-lookup"><span data-stu-id="1c9bb-252">The XAML Islands .NET Wrappers</span></span>

<span data-ttu-id="1c9bb-253">Windows 社區工具組已設定適用于 WPF 或 Windows Forms 的 XAML 島 .NET 包裝函式，可讓您更輕鬆地使用 XAML 島。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-253">The Windows Community Toolkit has a set the XAML Islands .NET wrappers for WPF or Windows Forms that make easier to use XAML Islands.</span></span> <span data-ttu-id="1c9bb-254">這些包裝函式會管理 Hwnd、焦點管理及其他專案。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-254">These wrappers manage the HWNDs, the focus management, among other things.</span></span> <span data-ttu-id="1c9bb-255">Windows Forms 和 WPF 開發人員應該使用這些包裝函式。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-255">Windows Forms and WPF developers should use these wrappers.</span></span>

<span data-ttu-id="1c9bb-256">Windows 社區工具組提供兩種類型的控制項：包裝的控制項和裝載控制項。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-256">The Windows Community Toolkit offers two types of controls: Wrapped Controls and Hosting Controls.</span></span>

##### <a name="wrapped-controls"></a><span data-ttu-id="1c9bb-257">包裝的控制項</span><span class="sxs-lookup"><span data-stu-id="1c9bb-257">Wrapped Controls</span></span>

<span data-ttu-id="1c9bb-258">這些包裝的控制項會將一些 UWP 控制項包裝到 Windows Forms 或 WPF 控制項中，以隱藏這些開發人員的 UWP 概念。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-258">These wrapped controls wrap some UWP controls into Windows Forms or WPF controls, hiding UWP concepts for those developers.</span></span> <span data-ttu-id="1c9bb-259">這些控制項包括：</span><span class="sxs-lookup"><span data-stu-id="1c9bb-259">These controls are:</span></span>

* <span data-ttu-id="1c9bb-260">Web 視圖和 WebViewCompatible</span><span class="sxs-lookup"><span data-stu-id="1c9bb-260">WebView and WebViewCompatible</span></span>
* <span data-ttu-id="1c9bb-261">InkCanvas 和 InkToolbar</span><span class="sxs-lookup"><span data-stu-id="1c9bb-261">InkCanvas and InkToolbar</span></span>
* <span data-ttu-id="1c9bb-262">MediaPlayerElement</span><span class="sxs-lookup"><span data-stu-id="1c9bb-262">MediaPlayerElement</span></span>
* <span data-ttu-id="1c9bb-263">MapControl</span><span class="sxs-lookup"><span data-stu-id="1c9bb-263">MapControl</span></span>

<span data-ttu-id="1c9bb-264">將 `Microsoft.Toolkit.Wpf.UI.Controls` 套件新增至您的專案，包括命名空間的參考，然後開始使用它們。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-264">Add the `Microsoft.Toolkit.Wpf.UI.Controls` package to your project, include the reference to the namespace, and start using them.</span></span>

```xml
<Window
        ...
        xmlns:uwpControls="clr-namespace:Microsoft.Toolkit.Wpf.UI.Controls;assembly=Microsoft.Toolkit.Wpf.UI.Controls">
<Grid>
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto"/>
        <RowDefinition Height="\*"/>
    </Grid.RowDefinitions>
    <uwpControls:InkToolbar TargetInkCanvas="{x:Reference Name=inkCanvas}"/>
    <uwpControls:InkCanvas Grid.Row="1" x:Name="inkCanvas" />
</Grid>
```

##### <a name="hosting-controls"></a><span data-ttu-id="1c9bb-265">裝載控制項</span><span class="sxs-lookup"><span data-stu-id="1c9bb-265">Hosting controls</span></span>

<span data-ttu-id="1c9bb-266">XAML 島的強大功能延伸至大部分的第一方控制項、協力廠商控制項，以及針對 UWP 所開發的自訂控制項，可以整合到 Windows Forms 和 WPF 做為具有完整功能 UI 的「群島」。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-266">The power of XAML Islands extends to most first-party controls, third-party controls, and custom controls developed for UWP, which can be integrated into Windows Forms and WPF as "Islands" with fully functional UI.</span></span> <span data-ttu-id="1c9bb-267">`WindowsXamlHost`WPF 和 Windows Forms 的控制項允許這麼做。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-267">The `WindowsXamlHost` control for WPF and Windows Forms allows doing this.</span></span>

<span data-ttu-id="1c9bb-268">例如，若要 `WindowsXamlHost` 在 WPF 中使用控制項，請將參考新增至 `Microsoft.Toolkit.Wpf.UI.XamlHost` Windows 社區工具組所提供的封裝。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-268">For example, to use the `WindowsXamlHost` control in WPF, add a reference to the `Microsoft.Toolkit.Wpf.UI.XamlHost` package provided by the Windows Community Toolkit.</span></span>

<span data-ttu-id="1c9bb-269">將放 `WindowsXamlHost` 入 UI 程式碼之後，請指定您要載入的 UWP 類型。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-269">Once you've placed your `WindowsXamlHost` into your UI code, specify which UWP type you want to load.</span></span> <span data-ttu-id="1c9bb-270">您可以選擇使用包裝的控制項，例如， `Button` 或由數個不同控制項（自訂 UWP 控制項）所組成的更複雜的控制項。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-270">You can choose to use a wrapped control like a `Button` or a more complex one composed by several different controls, which are a custom UWP control.</span></span>

<span data-ttu-id="1c9bb-271">下列範例顯示如何新增 UWP `Button` ：</span><span class="sxs-lookup"><span data-stu-id="1c9bb-271">The following example shows how to add a UWP `Button`:</span></span>

```xml
<Window
        ...
        xmlns:xamlhost="clr-namespace:Microsoft.Toolkit.Wpf.UI.XamlHost;assembly=Microsoft.Toolkit.Wpf.UI.XamlHost">

<xamlhost:WindowsXamlHost x:Name="myUwpButton"
                          InitialTypeName="Windows.UI.Xaml.Controls.Button" />
```

<span data-ttu-id="1c9bb-272">有一個清楚的建議可以解決這種情況，而且最好要有一個包含自訂複合控制項的單一且更大的 XAML 島，而不是每個有一個控制項的孤島。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-272">There's a clear recommendation on how to approach this and it's better to have one single and bigger XAML Island containing a custom composite control than to have several islands with one control on each.</span></span>

<span data-ttu-id="1c9bb-273">XAML 的核心功能之一就是系結，而且它可以在您的 Win32 程式碼與島之間運作。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-273">One of the core features of XAML is binding and it works between your Win32 code and the island.</span></span> <span data-ttu-id="1c9bb-274">因此，您可以系結 `Textbox` 具有 UWP 的 Win32 `Textbox` 。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-274">So, you can bind, for instance, a Win32 `Textbox` with a UWP `Textbox`.</span></span> <span data-ttu-id="1c9bb-275">其中一個要考慮的重要事項是，這些系結是單向系結，從 UWP 到 Win32，因此如果您在 `Textbox` XAML 島內部更新，Win32 文字方塊就會更新，但不會有其他的影響。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-275">One important thing to consider is that these bindings are one-way bindings, from UWP to Win32, so if you update the `Textbox` inside the XAML Island the Win32 Textbox will be updated, but not the other way around.</span></span>

<span data-ttu-id="1c9bb-276">若要查看如何使用 XAML Islands 的逐步解說，請參閱：</span><span class="sxs-lookup"><span data-stu-id="1c9bb-276">To see a walkthrough about how to use XAML Islands, see:</span></span>

<https://docs.microsoft.com/windows/apps/desktop/modernize/host-standard-control-with-xaml-islands>

#### <a name="adding-uwp-xaml-custom-controls"></a><span data-ttu-id="1c9bb-277">新增 UWP XAML 自訂控制項</span><span class="sxs-lookup"><span data-stu-id="1c9bb-277">Adding UWP XAML custom controls</span></span>

<span data-ttu-id="1c9bb-278">XAML 自訂控制項是由您或協力廠商（包括 WinUI 2.x 控制項）所建立的控制項（或使用者控制項）。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-278">A XAML custom control is a control (or user control) created by you or by third parties (including WinUI 2.x controls).</span></span> <span data-ttu-id="1c9bb-279">若要在 Windows Forms 或 WPF 應用程式中裝載自訂 UWP 控制項，您需要：</span><span class="sxs-lookup"><span data-stu-id="1c9bb-279">To host a custom UWP control in a Windows Forms or WPF app, you'll need:</span></span>

- <span data-ttu-id="1c9bb-280">`WindowsXamlHost`在您的 .Net Core 3.x 應用程式中使用 UWP 控制項。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-280">To use the `WindowsXamlHost` UWP control in your .NET Core 3.x app.</span></span>
- <span data-ttu-id="1c9bb-281">建立可定義物件的 UWP 應用程式專案 `XamlApplication` 。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-281">To create a UWP app project that defines a `XamlApplication` object.</span></span>

<span data-ttu-id="1c9bb-282">您的 WPF 或 Windows Forms 專案必須能夠存取 `Microsoft.Toolkit.Win32.UI.XamlHost.XamlApplication` Windows 社區工具組所提供之類別的實例。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-282">Your WPF or Windows Forms project must have access to an instance of the `Microsoft.Toolkit.Win32.UI.XamlHost.XamlApplication` class provided by the Windows Community Toolkit.</span></span> <span data-ttu-id="1c9bb-283">這個物件會作為根中繼資料提供者，以便在應用程式目前目錄的元件中載入自訂 UWP XAML 類型的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-283">This object acts as a root metadata provider for loading metadata for custom UWP XAML types in assemblies in the current directory of your application.</span></span> <span data-ttu-id="1c9bb-284">建議的做法是將空白應用程式（通用 Windows）專案新增至與 WPF 或 Windows Forms 專案相同的方案，並修訂此專案中的預設應用程式類別。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-284">The recommended way to do this is to add a Blank App (Universal Windows) project to the same solution as your WPF or Windows Forms project and revise the default App class in this project.</span></span>

<span data-ttu-id="1c9bb-285">自訂 UWP XAML 控制項可以包含在此 UWP 應用程式或獨立的 UWP 類別庫專案中，您可以在與 WPF 或 Windows Forms 專案相同的方案中參考該專案。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-285">The custom UWP XAML control can be included on this UWP app or in an independent UWP Class Library project that you reference in the same solution as your WPF or Windows Forms project.</span></span>

<span data-ttu-id="1c9bb-286">您可以在下列位置查看詳細的逐步程式描述：</span><span class="sxs-lookup"><span data-stu-id="1c9bb-286">You can check a detailed step-by-step process description at:</span></span>

<https://docs.microsoft.com/windows/apps/desktop/modernize/host-custom-control-with-xaml-islands>

#### <a name="the-windows-ui-library-winui-2"></a><span data-ttu-id="1c9bb-287">Windows UI 程式庫（WinUI 2）</span><span class="sxs-lookup"><span data-stu-id="1c9bb-287">The Windows UI Library (WinUI 2)</span></span>

<span data-ttu-id="1c9bb-288">除了作業系統隨附的收件匣 Windows 10 控制項以外，相同的 UWP XAML 小組也會在 Windows UI 程式庫（**WinUI 2**）中提供其他控制項。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-288">Besides the inbox Windows 10 controls that comes with the OS, the same UWP XAML team also deliver additional controls in the Windows UI Library (**WinUI 2**).</span></span> <span data-ttu-id="1c9bb-289">WinUI 2 為 Windows UWP 應用程式提供官方的原生 Microsoft UI 控制項和功能，這些控制項可以在 XAML 島內使用。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-289">WinUI 2 provides official native Microsoft UI controls and features for Windows UWP apps and these controls can be used inside of XAML Islands.</span></span>

<span data-ttu-id="1c9bb-290">WinUI 2 是開放原始碼，您可以在找到資訊 <https://github.com/microsoft/microsoft-ui-xaml> 。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-290">WinUI 2 is open source and you can find information at <https://github.com/microsoft/microsoft-ui-xaml>.</span></span>

<span data-ttu-id="1c9bb-291">下列文章示範如何從 WinUI 2 程式庫裝載 UWP XAML 控制項：<https://docs.microsoft.com/windows/apps/desktop/modernize/host-custom-control-with-xaml-islands></span><span class="sxs-lookup"><span data-stu-id="1c9bb-291">The following article demonstrates how to host a UWP XAML control from the WinUI 2 library: <https://docs.microsoft.com/windows/apps/desktop/modernize/host-custom-control-with-xaml-islands></span></span>

### <a name="do-you-need-xaml-islands"></a><span data-ttu-id="1c9bb-292">您需要 XAML 群島</span><span class="sxs-lookup"><span data-stu-id="1c9bb-292">Do you need XAML Islands</span></span>

<span data-ttu-id="1c9bb-293">XAML 島適用于現有的 Win32 應用程式，想要利用新的 UWP 控制項和行為來改善其使用者體驗，而不需要完整重寫應用程式。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-293">XAML Islands are intended for existing Win32 apps that want to improve their user experience by leveraging new UWP controls and behaviors without a full rewrite of the app.</span></span> <span data-ttu-id="1c9bb-294">您可以使用 [Windows 10 api](/windows/uwp/porting/desktop-to-uwp-enhance)，但必須等到 XAML Islands 才會使用非 UI 相關的 api。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-294">You could already [leverage Windows 10 APIs](/windows/uwp/porting/desktop-to-uwp-enhance), but up until XAML Islands, only non-UI related APIs.</span></span>

<span data-ttu-id="1c9bb-295">如果您正在開發新的 Windows 應用程式， [UWP 應用程式](/windows/uwp/get-started/universal-application-platform-guide)   可能是正確的方法。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-295">If you're developing a new Windows App, a [UWP App](/windows/uwp/get-started/universal-application-platform-guide) is probably the right approach.</span></span>

### <a name="the-road-ahead-xaml-islands-winui-30"></a><span data-ttu-id="1c9bb-296">更早的 XAML 島： WinUI 3。0</span><span class="sxs-lookup"><span data-stu-id="1c9bb-296">The road ahead XAML Islands: WinUI 3.0</span></span>

<span data-ttu-id="1c9bb-297">從 Windows 8 開始，Windows UI 平臺（包括 XAML UI 架構、視覺組合圖層和輸入處理）已隨附為 Windows 不可或缺的一部分。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-297">Since Windows 8, the Windows UI platform, including the XAML UI framework, visual composition layer, and input processing has been shipped as an integral part of Windows.</span></span> <span data-ttu-id="1c9bb-298">這表示若要受益于最新的 UI 技術改良功能，您必須升級至最新版本的 UI，並在開發應用程式時減緩創新的步調。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-298">This means that to benefit from the latest improvements on UI technologies, you must upgrade to the latest version of the UI, slowing down the pace of innovation when you develop your apps.</span></span> <span data-ttu-id="1c9bb-299">為了分離這兩個進化週期並促進創新，Microsoft 正積極處理 WinUI 專案。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-299">To decouple these two evolution cycles and foster innovation, Microsoft is actively working on the WinUI project.</span></span>

<span data-ttu-id="1c9bb-300">從2018開始，Microsoft 已開始將一些新的 XAML UI 控制項和功能當做以 UWP SDK 為基礎的個別 NuGet 套件來傳送。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-300">Starting with WinUI 2 in 2018, Microsoft started shipping some new XAML UI controls and features as separate NuGet packages that build on top of the UWP SDK.</span></span>

![WinUI 2.0 的結構](./media/windows-migration/winui2.png)

<span data-ttu-id="1c9bb-302">WinUI 3 正在開發中，將大幅擴充 WinUI 的範圍，以包含完整的 UI 平臺，這會與 UWP SDK 完全分離：</span><span class="sxs-lookup"><span data-stu-id="1c9bb-302">WinUI 3 is under active development and will greatly expand the scope of WinUI to include the full UI platform, which will be fully decoupled from the UWP SDK:</span></span>

![WinUI 3.0 的結構](./media/windows-migration/winui3.png)

<span data-ttu-id="1c9bb-304">XAML 架構現在會在 GitHub 上開發，並以 [NuGet](/nuget/what-is-nuget)套件的頻外發行   。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-304">XAML framework will now be developed on GitHub and shipped out of band as [NuGet](/nuget/what-is-nuget) packages.</span></span>

<span data-ttu-id="1c9bb-305">隨附于 OS 一部分的現有 UWP XAML Api 將不再收到新的功能更新。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-305">The existing UWP XAML APIs that ship as part of the OS will no longer receive new feature updates.</span></span> <span data-ttu-id="1c9bb-306">他們仍然會根據 Windows 10 支援週期來接收安全性更新和重大修正程式。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-306">They will still receive security updates and critical fixes according to the Windows 10 support lifecycle.</span></span>

<span data-ttu-id="1c9bb-307">通用 Windows 平臺包含的不只是 XAML 架構（例如，應用程式和安全性模型、媒體管線、Xbox 和 Windows 10 shell 整合、廣泛的裝置支援），而且會繼續進化。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-307">The Universal Windows Platform contains more than just the XAML framework (for example, application and security model, media pipeline, Xbox and Windows 10 shell integrations, broad device support) and will continue to evolve.</span></span> <span data-ttu-id="1c9bb-308">所有新的 XAML 功能只會當做 WinUI 的一部分來開發和傳送。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-308">All new XAML features will just be developed and ship as part of WinUI instead.</span></span>

#### <a name="winui-3-in-desktop-app-and-winui-xaml-islands"></a><span data-ttu-id="1c9bb-309">桌面應用程式中的 WinUI 3 和 WinUI XAML 群島</span><span class="sxs-lookup"><span data-stu-id="1c9bb-309">WinUI 3 in desktop app and WinUI XAML Islands</span></span>

<span data-ttu-id="1c9bb-310">如您所見，WinUI 3 是 UWP XAML 的演進，它會在 UWP 應用程式模型及其所有需求（MSIX 封裝識別碼、沙箱、CoreWindow 等等）中自然運作。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-310">As you can see, WinUI 3 is the evolution of UWP XAML and it works naturally within the UWP app model and all its requirements (MSIX packaged ID, sandbox, CoreWindow, and so on.</span></span> <span data-ttu-id="1c9bb-311">若只要在 Win32 應用程式模型中使用 WinUI 3，WinUI 內容應該使用**WINUI XAML Islands**由另一個 UI 架構（WINDOWS FORMS、WPF 等等）主控。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-311">To use just WinUI 3 in a Win32 app model, the WinUI content should be hosted by another UI Framework (Windows Forms, WPF, and so on) using **WinUI XAML Islands**.</span></span> <span data-ttu-id="1c9bb-312">如果您想要演變應用程式和混合技術，這是正確的路徑。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-312">This is the right path if you want to evolve your app and mix technologies.</span></span> <span data-ttu-id="1c9bb-313">不過，如果您想要取代 WinUI 的整個舊 UI，您的應用程式就不應該載入僅裝載 WinUI 的 UI 架構。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-313">However, if you want to replace your entire old UI for WinUI, your app shouldn't load UI Frameworks for just hosting WinUI.</span></span>

<span data-ttu-id="1c9bb-314">WinUI 3 將解決**在桌面應用程式中新增 WinUI 的這項**重要意見反應。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-314">WinUI 3 will address this critical feedback adding **WinUI in desktop apps**.</span></span> <span data-ttu-id="1c9bb-315">這可讓 Win32 應用程式以獨立 UI 架構的形式使用 WinUI 3;不需要載入 Windows Forms 或 WPF。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-315">This will allow that Win32 apps can use WinUI 3 as standalone UI Framework; no need to load Windows Forms or WPF.</span></span>

<span data-ttu-id="1c9bb-316">在此匯總中，WinUI 3 可讓開發人員輕鬆地混合和比對的正確組合：</span><span class="sxs-lookup"><span data-stu-id="1c9bb-316">Within this aggregation, WinUI 3 will let developers easily mix and match the right combination of:</span></span>

* <span data-ttu-id="1c9bb-317">應用程式模型： UWP、Win32</span><span class="sxs-lookup"><span data-stu-id="1c9bb-317">App model: UWP, Win32</span></span>
* <span data-ttu-id="1c9bb-318">平臺： .NET Core 或原生</span><span class="sxs-lookup"><span data-stu-id="1c9bb-318">Platform: .NET Core or Native</span></span>
* <span data-ttu-id="1c9bb-319">Language： .NET （C \# ，Visual Basic），Standard c + +</span><span class="sxs-lookup"><span data-stu-id="1c9bb-319">Language: .NET (C\#, Visual Basic), standard C++</span></span>
* <span data-ttu-id="1c9bb-320">封裝： MSIX，AppX 用於 Microsoft Store，未封裝</span><span class="sxs-lookup"><span data-stu-id="1c9bb-320">Packaging: MSIX, AppX for the Microsoft Store, unpackaged</span></span>
* <span data-ttu-id="1c9bb-321">Interop：使用 WinUI 3 來延伸現有的 WPF、WinForms 和 MFC 應用程式（使用 WinUI XAML Islands）。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-321">Interop: use WinUI 3 to extend existing WPF, WinForms, and MFC apps using WinUI XAML Islands.</span></span>

<span data-ttu-id="1c9bb-322">如果您想要瞭解更多詳細資料，Microsoft 會在中分享此藍圖 <https://github.com/microsoft/microsoft-ui-xaml/blob/master/docs/roadmap.md> 。</span><span class="sxs-lookup"><span data-stu-id="1c9bb-322">If you want to know more details, Microsoft is sharing this roadmap in <https://github.com/microsoft/microsoft-ui-xaml/blob/master/docs/roadmap.md>.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="1c9bb-323">[上一個](migrate-modern-applications.md) 
>[下一步](example-migration-core.md)</span><span class="sxs-lookup"><span data-stu-id="1c9bb-323">[Previous](migrate-modern-applications.md)
[Next](example-migration-core.md)</span></span>
