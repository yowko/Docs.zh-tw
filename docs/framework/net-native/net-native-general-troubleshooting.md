---
title: .NET Native 一般疑難排解
ms.date: 03/30/2017
ms.assetid: ee8c5e17-35ea-48a1-8767-83298caac1e8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ea5f61b0e250c4f51a966bc60959f7559d8e2fe2
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049392"
---
# <a name="net-native-general-troubleshooting"></a><span data-ttu-id="704ec-102">.NET Native 一般疑難排解</span><span class="sxs-lookup"><span data-stu-id="704ec-102">.NET Native General Troubleshooting</span></span>

<span data-ttu-id="704ec-103">本主題說明如何針對使用 .NET Native 開發應用程式時可能遇到的潛在問題進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="704ec-103">This topic describes how to troubleshoot potential issues that you might encounter when developing apps with .NET Native.</span></span>

- <span data-ttu-id="704ec-104">**問題：** 您的組建輸出視窗未正確更新。</span><span class="sxs-lookup"><span data-stu-id="704ec-104">**Issue:** Your build output window isn't properly updated.</span></span>

  <span data-ttu-id="704ec-105">**分析**在組建完成之前，不會更新 [組建輸出] 視窗。</span><span class="sxs-lookup"><span data-stu-id="704ec-105">**Resolution:** The build output window isn't updated until the build completes.</span></span> <span data-ttu-id="704ec-106">建置時間可能長達數分鐘，因此您可能晚點才會看到更新。</span><span class="sxs-lookup"><span data-stu-id="704ec-106">Build times may be up to several minutes, so you might experience a delay in seeing the updates.</span></span>

- <span data-ttu-id="704ec-107">**問題：** 您應用程式的 ARM 零售組建時間已增加。</span><span class="sxs-lookup"><span data-stu-id="704ec-107">**Issue:** Your app’s retail build time for ARM has increased.</span></span>

  <span data-ttu-id="704ec-108">**分析**當您將應用程式部署至 ARM 裝置時，會叫用 .NET Native 的基礎結構。</span><span class="sxs-lookup"><span data-stu-id="704ec-108">**Resolution:** When you deploy an app to your ARM device, the .NET Native infrastructure is invoked.</span></span> <span data-ttu-id="704ec-109">這個編譯會執行大量最佳化，同時確保該非靜態語意 (例如反映) 仍然能夠正常運作。</span><span class="sxs-lookup"><span data-stu-id="704ec-109">This compilation performs a large number of optimizations while ensuring that non-static semantics such as reflection continue to work.</span></span> <span data-ttu-id="704ec-110">此外，應用程式使用的 .NET Framework 部分已靜態連結，以取得最佳效能，因此也必須編譯成機器碼。</span><span class="sxs-lookup"><span data-stu-id="704ec-110">In addition, the portion of the .NET Framework that the app uses is statically linked in for optimal performance and has to be compiled into native code as well.</span></span> <span data-ttu-id="704ec-111">這就是編譯需要更多時間的原因。</span><span class="sxs-lookup"><span data-stu-id="704ec-111">This is why compilation takes longer.</span></span>

  <span data-ttu-id="704ec-112">不過，對於標準開發電腦上的大多數應用程式而言，編譯時間仍然在標準編譯的一分鐘內。</span><span class="sxs-lookup"><span data-stu-id="704ec-112">However, compilation times are still within a minute of standard compilation for most apps on a standard development machine.</span></span>  <span data-ttu-id="704ec-113">一般而言，光是在標準開發電腦上產生 .NET Framework 的原生映像就需要數分鐘。</span><span class="sxs-lookup"><span data-stu-id="704ec-113">Typically, just generating native images for the .NET Framework on a standard development machine takes several minutes.</span></span>  <span data-ttu-id="704ec-114">即使執行所有最佳化來改善產生的程式碼 (包括使用 .NET Framework)，應用程式建置時間通常還是需要一到兩分鐘。</span><span class="sxs-lookup"><span data-stu-id="704ec-114">Even with all the optimizations to improve the generated code and with including the .NET Framework, app build times are typically a minute or two.</span></span>

  <span data-ttu-id="704ec-115">我們將調查多執行緒編譯和其他最佳化，持續提升編譯效能。</span><span class="sxs-lookup"><span data-stu-id="704ec-115">We are continuing to work on improving compilation performance by investigating multi-threaded compilation and other optimizations.</span></span>

- <span data-ttu-id="704ec-116">**問題：** 您不知道您的應用程式是使用 .NET Native 編譯。</span><span class="sxs-lookup"><span data-stu-id="704ec-116">**Issue:** You don’t know if your app was compiled using .NET Native.</span></span>

  <span data-ttu-id="704ec-117">**分析**如果叫用 .NET Native 編譯器，您會發現組建時間較長，而且 [工作管理員] 會顯示各種 .NET Native 元件進程，例如 ILC.OUT .exe 和 nutc_driver。</span><span class="sxs-lookup"><span data-stu-id="704ec-117">**Resolution:** If the .NET Native compiler is invoked, you'll notice longer build times, and Task Manager will show various .NET Native component processes such as ILC.exe and nutc_driver.exe.</span></span>

  <span data-ttu-id="704ec-118">使用 .NET Native 成功建立專案之後，\\ \\您會*在 obj* \ 設定架構*專案名稱*ilc\out. 中找到輸出。您可以在 bin\\*arch*\\*config*\AppX 下找到最終的原生套件內容。</span><span class="sxs-lookup"><span data-stu-id="704ec-118">After you successfully build your project with .NET Native, you'll find the output under obj\\*config*\ *arch*\\*projectname*.ilc\out.  The final native package contents can be found under bin\\*arch*\\*config*\AppX.</span></span> <span data-ttu-id="704ec-119">如果已部署應用程式，則最終的原生套件內容位於 \bin\\*arch*\\*config*\AppX 下。</span><span class="sxs-lookup"><span data-stu-id="704ec-119">The final native package contents are under \bin\\*arch*\\*config*\AppX if you have deployed the app.</span></span>

- <span data-ttu-id="704ec-120">**問題：** 您 .NET Native 編譯的應用程式會擲回執行時間例外狀況（通常是[MissingMetadataException](missingmetadataexception-class-net-native.md)或[MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md)例外狀況），而不會在沒有 .NET Native 的情況下進行編譯。</span><span class="sxs-lookup"><span data-stu-id="704ec-120">**Issue:** Your .NET Native-compiled app is throwing runtime exceptions (typically [MissingMetadataException](missingmetadataexception-class-net-native.md) or [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exceptions) that it did not throw when compiled without .NET Native.</span></span>

  <span data-ttu-id="704ec-121">**分析**會擲回例外狀況，因為 .NET Native 並未提供可透過反映取得的中繼資料或執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="704ec-121">**Resolution:** The exceptions are thrown because .NET Native did not provide either the metadata or the implementation code that is otherwise available through reflection.</span></span> <span data-ttu-id="704ec-122">(如需詳細資訊，請參閱 [.NET Native 和編譯](net-native-and-compilation.md))。若要排除例外狀況，您必須在[執行階段指示詞 (rd.xml) 檔案](runtime-directives-rd-xml-configuration-file-reference.md)中新增一個項目，如此一來，.NET Native 工具鏈便可以在執行階段提供中繼資料或實作程式碼。</span><span class="sxs-lookup"><span data-stu-id="704ec-122">(For more information, see [.NET Native and Compilation](net-native-and-compilation.md).) To eliminate the exception, you have to add an entry to your [runtime directives (rd.xml) file](runtime-directives-rd-xml-configuration-file-reference.md) so that the .NET Native tool chain can make the metadata or implementation code available at runtime.</span></span> <span data-ttu-id="704ec-123">您可以使用兩個疑難排解工具，這些工具會產生要加入執行階段指示詞檔案的必要項目：</span><span class="sxs-lookup"><span data-stu-id="704ec-123">Two troubleshooters are available that will generate the necessary entry to add to your runtime directives file:</span></span>

  - <span data-ttu-id="704ec-124">針對類型的 [MissingMetadataException 疑難排解工具](https://dotnet.github.io/native/troubleshooter/type.html) 。</span><span class="sxs-lookup"><span data-stu-id="704ec-124">The [MissingMetadataException troubleshooter](https://dotnet.github.io/native/troubleshooter/type.html) for types.</span></span>

  - <span data-ttu-id="704ec-125">針對方法的 [MissingMetadataException 疑難排解工具](https://dotnet.github.io/native/troubleshooter/method.html) 。</span><span class="sxs-lookup"><span data-stu-id="704ec-125">The [MissingMetadataException troubleshooter](https://dotnet.github.io/native/troubleshooter/method.html) for methods.</span></span>

  <span data-ttu-id="704ec-126">如需詳細資訊，請參閱[反映和 .NET Native](reflection-and-net-native.md)。</span><span class="sxs-lookup"><span data-stu-id="704ec-126">For more information, see [Reflection and .NET Native](reflection-and-net-native.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="704ec-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="704ec-127">See also</span></span>

- [<span data-ttu-id="704ec-128">將您的 Windows 市集應用程式移轉至 .NET Native</span><span class="sxs-lookup"><span data-stu-id="704ec-128">Migrating Your Windows Store App to .NET Native</span></span>](migrating-your-windows-store-app-to-net-native.md)
