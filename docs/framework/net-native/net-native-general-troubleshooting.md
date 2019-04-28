---
title: .NET Native 一般疑難排解
ms.date: 03/30/2017
ms.assetid: ee8c5e17-35ea-48a1-8767-83298caac1e8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f81ff8a347235ab1a765b4f41051dab2da786b89
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61866865"
---
# <a name="net-native-general-troubleshooting"></a><span data-ttu-id="5def3-102">.NET Native 一般疑難排解</span><span class="sxs-lookup"><span data-stu-id="5def3-102">.NET Native General Troubleshooting</span></span>
<span data-ttu-id="5def3-103">本主題說明如何對使用 [!INCLUDE[net_native](../../../includes/net-native-md.md)] 開發應用程式時可能遇到的問題進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="5def3-103">This topic describes how to troubleshoot potential issues that you might encounter when developing apps with [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span>  
  
-   <span data-ttu-id="5def3-104">**問題：** 您的建置輸出視窗未正確更新。</span><span class="sxs-lookup"><span data-stu-id="5def3-104">**Issue:** Your build output window isn't properly updated.</span></span>  
  
     <span data-ttu-id="5def3-105">**解決方式：** 組建完成之前，不會更新建置輸出視窗。</span><span class="sxs-lookup"><span data-stu-id="5def3-105">**Resolution:** The build output window isn't updated until the build completes.</span></span> <span data-ttu-id="5def3-106">建置時間可能長達數分鐘，因此您可能晚點才會看到更新。</span><span class="sxs-lookup"><span data-stu-id="5def3-106">Build times may be up to several minutes, so you might experience a delay in seeing the updates.</span></span>  
  
-   <span data-ttu-id="5def3-107">**問題：** 增加您的應用程式正式版本建置階段 ARM。</span><span class="sxs-lookup"><span data-stu-id="5def3-107">**Issue:** Your app’s retail build time for ARM has increased.</span></span>  
  
     <span data-ttu-id="5def3-108">**解決方式：** 當您將應用程式部署至 ARM 裝置時，[!INCLUDE[net_native](../../../includes/net-native-md.md)]基礎結構會叫用。</span><span class="sxs-lookup"><span data-stu-id="5def3-108">**Resolution:** When you deploy an app to your ARM device, the [!INCLUDE[net_native](../../../includes/net-native-md.md)] infrastructure is invoked.</span></span> <span data-ttu-id="5def3-109">這個編譯會執行大量最佳化，同時確保該非靜態語意 (例如反映) 仍然能夠正常運作。</span><span class="sxs-lookup"><span data-stu-id="5def3-109">This compilation performs a large number of optimizations while ensuring that non-static semantics such as reflection continue to work.</span></span> <span data-ttu-id="5def3-110">此外，應用程式使用的 .NET Framework 部分已靜態連結，以取得最佳效能，因此也必須編譯成機器碼。</span><span class="sxs-lookup"><span data-stu-id="5def3-110">In addition, the portion of the .NET Framework that the app uses is statically linked in for optimal performance and has to be compiled into native code as well.</span></span> <span data-ttu-id="5def3-111">這就是編譯需要更多時間的原因。</span><span class="sxs-lookup"><span data-stu-id="5def3-111">This is why compilation takes longer.</span></span>  
  
     <span data-ttu-id="5def3-112">不過，對於標準開發電腦上的大多數應用程式而言，編譯時間仍然在標準編譯的一分鐘內。</span><span class="sxs-lookup"><span data-stu-id="5def3-112">However, compilation times are still within a minute of standard compilation for most apps on a standard development machine.</span></span>  <span data-ttu-id="5def3-113">一般而言，光是在標準開發電腦上產生 .NET Framework 的原生映像就需要數分鐘。</span><span class="sxs-lookup"><span data-stu-id="5def3-113">Typically, just generating native images for the .NET Framework on a standard development machine takes several minutes.</span></span>  <span data-ttu-id="5def3-114">即使執行所有最佳化來改善產生的程式碼 (包括使用 .NET Framework)，應用程式建置時間通常還是需要一到兩分鐘。</span><span class="sxs-lookup"><span data-stu-id="5def3-114">Even with all the optimizations to improve the generated code and with including the .NET Framework, app build times are typically a minute or two.</span></span>  
  
     <span data-ttu-id="5def3-115">我們將調查多執行緒編譯和其他最佳化，持續提升編譯效能。</span><span class="sxs-lookup"><span data-stu-id="5def3-115">We are continuing to work on improving compilation performance by investigating multi-threaded compilation and other optimizations.</span></span>  
  
-   <span data-ttu-id="5def3-116">**問題：** 您不知道您的應用程式是否使用已編譯[!INCLUDE[net_native](../../../includes/net-native-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5def3-116">**Issue:** You don’t know if your app was compiled using [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span>  
  
     <span data-ttu-id="5def3-117">**解決方式：** 如果[!INCLUDE[net_native](../../../includes/net-native-md.md)]編譯器會叫用，您會發現再建置時間，且工作管理員 會顯示各種[!INCLUDE[net_native](../../../includes/net-native-md.md)]元件處理序，例如 ILC.exe 和 nutc_driver.exe。</span><span class="sxs-lookup"><span data-stu-id="5def3-117">**Resolution:** If the [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiler is invoked, you'll notice longer build times, and Task Manager will show various [!INCLUDE[net_native](../../../includes/net-native-md.md)] component processes such as ILC.exe and nutc_driver.exe.</span></span>  
  
     <span data-ttu-id="5def3-118">使用 [!INCLUDE[net_native](../../../includes/net-native-md.md)] 成功建置專案之後，您將在 obj\\*config*\ *arch*\\<專案名稱>.ilc\out 下找到輸出。您可以在 bin\\*arch*\\*config*\AppX 下找到最終的原生套件內容。</span><span class="sxs-lookup"><span data-stu-id="5def3-118">After you successfully build your project with [!INCLUDE[net_native](../../../includes/net-native-md.md)], you'll find the output under obj\\*config*\ *arch*\\*projectname*.ilc\out.  The final native package contents can be found under bin\\*arch*\\*config*\AppX.</span></span> <span data-ttu-id="5def3-119">如果已部署應用程式，則最終的原生套件內容位於 \bin\\*arch*\\*config*\AppX 下。</span><span class="sxs-lookup"><span data-stu-id="5def3-119">The final native package contents are under \bin\\*arch*\\*config*\AppX if you have deployed the app.</span></span>  
  
-   <span data-ttu-id="5def3-120">**問題：**.NET Native 編譯應用程式會擲回執行階段例外狀況 (通常[MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)或是[MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md)例外狀況)，它未擲回時不編譯.NET 原生。</span><span class="sxs-lookup"><span data-stu-id="5def3-120">**Issue:** Your .NET Native-compiled app is throwing runtime exceptions (typically [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) or [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) exceptions) that it did not throw when compiled without .NET Native.</span></span>  
  
     <span data-ttu-id="5def3-121">**解決方式：** 因為.NET Native 未提供的中繼資料或實作程式碼可透過反映，則會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="5def3-121">**Resolution:** The exceptions are thrown because .NET Native did not provide either the metadata or the implementation code that is otherwise available through reflection.</span></span> <span data-ttu-id="5def3-122">(如需詳細資訊，請參閱 [.NET Native 和編譯](../../../docs/framework/net-native/net-native-and-compilation.md))。若要排除例外狀況，您必須在[執行階段指示詞 (rd.xml) 檔案](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)中新增一個項目，如此一來，.NET Native 工具鏈便可以在執行階段提供中繼資料或實作程式碼。</span><span class="sxs-lookup"><span data-stu-id="5def3-122">(For more information, see [.NET Native and Compilation](../../../docs/framework/net-native/net-native-and-compilation.md).) To eliminate the exception, you have to add an entry to your [runtime directives (rd.xml) file](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md) so that the .NET Native tool chain can make the metadata or implementation code available at runtime.</span></span> <span data-ttu-id="5def3-123">您可以使用兩個疑難排解工具，這些工具會產生要加入執行階段指示詞檔案的必要項目：</span><span class="sxs-lookup"><span data-stu-id="5def3-123">Two troubleshooters are available that will generate the necessary entry to add to your runtime directives file:</span></span>  
  
    -   <span data-ttu-id="5def3-124">針對類型的 [MissingMetadataException 疑難排解工具](https://dotnet.github.io/native/troubleshooter/type.html) 。</span><span class="sxs-lookup"><span data-stu-id="5def3-124">The [MissingMetadataException troubleshooter](https://dotnet.github.io/native/troubleshooter/type.html) for types.</span></span>  
  
    -   <span data-ttu-id="5def3-125">針對方法的 [MissingMetadataException 疑難排解工具](https://dotnet.github.io/native/troubleshooter/method.html) 。</span><span class="sxs-lookup"><span data-stu-id="5def3-125">The [MissingMetadataException troubleshooter](https://dotnet.github.io/native/troubleshooter/method.html) for methods.</span></span>  
  
     <span data-ttu-id="5def3-126">如需詳細資訊，請參閱[反映和 .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md)。</span><span class="sxs-lookup"><span data-stu-id="5def3-126">For more information, see [Reflection and .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5def3-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5def3-127">See also</span></span>

- [<span data-ttu-id="5def3-128">將您的 Windows 市集應用程式移轉至 .NET Native</span><span class="sxs-lookup"><span data-stu-id="5def3-128">Migrating Your Windows Store App to .NET Native</span></span>](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md)
