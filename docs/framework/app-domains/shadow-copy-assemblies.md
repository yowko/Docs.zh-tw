---
title: 陰影複製組件
description: 探索 .NET 中元件的陰影複製，讓應用程式域中使用的元件可以在不卸載應用程式域的情況下進行更新。
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], shadow copying
- application domains, shadow copying assemblies
- shadow copying assemblies
ms.assetid: de8b8759-fca7-4260-896b-5a4973157672
ms.openlocfilehash: a7ff72763dd26dbc50cd37e070c2d25ababa00f3
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104557"
---
# <a name="shadow-copying-assemblies"></a><span data-ttu-id="f5463-103">陰影複製組件</span><span class="sxs-lookup"><span data-stu-id="f5463-103">Shadow Copying Assemblies</span></span>

<span data-ttu-id="f5463-104">陰影複製可讓應用程式定義域中使用的組件更新，而不需卸載應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="f5463-104">Shadow copying enables assemblies that are used in an application domain to be updated without unloading the application domain.</span></span> <span data-ttu-id="f5463-105">這對必須連續運作的應用程式特別有用，例如 ASP.NET 網站。</span><span class="sxs-lookup"><span data-stu-id="f5463-105">This is particularly useful for applications that must be available continuously, such as ASP.NET sites.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f5463-106">Windows 8.x 存放區應用程式不支援陰影複製。</span><span class="sxs-lookup"><span data-stu-id="f5463-106">Shadow copying is not supported in Windows 8.x Store apps.</span></span>

<span data-ttu-id="f5463-107">Common Language Runtime 在載入組件時會鎖定組件檔案，因此在卸載組件之前無法更新檔案。</span><span class="sxs-lookup"><span data-stu-id="f5463-107">The common language runtime locks an assembly file when the assembly is loaded, so the file cannot be updated until the assembly is unloaded.</span></span> <span data-ttu-id="f5463-108">若要從應用程式定義域卸載組件，唯一的方式為卸載應用程式定義域，如此在正常情況下，就無法在磁碟上更新組件，直到使用組件的所有應用程式定義域已卸載為止。</span><span class="sxs-lookup"><span data-stu-id="f5463-108">The only way to unload an assembly from an application domain is by unloading the application domain, so under normal circumstances, an assembly cannot be updated on disk until all the application domains that are using it have been unloaded.</span></span>

<span data-ttu-id="f5463-109">當設定應用程式定義域來陰影複製檔案時，會從應用程式路徑複製組件到另一個位置，並從該位置載入。</span><span class="sxs-lookup"><span data-stu-id="f5463-109">When an application domain is configured to shadow copy files, assemblies from the application path are copied to another location and loaded from that location.</span></span> <span data-ttu-id="f5463-110">複本會遭到鎖定，但原始組件檔已解除鎖定，而且可以更新。</span><span class="sxs-lookup"><span data-stu-id="f5463-110">The copy is locked, but the original assembly file is unlocked and can be updated.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f5463-111">唯一可以進行陰影複製的組件是儲存在應用程式目錄或其子目錄的，在設定應用程式定義域時可由 <xref:System.AppDomainSetup.ApplicationBase%2A> 和 <xref:System.AppDomainSetup.PrivateBinPath%2A> 屬性指定。</span><span class="sxs-lookup"><span data-stu-id="f5463-111">The only assemblies that can be shadow copied are those stored in the application directory or its subdirectories, specified by the <xref:System.AppDomainSetup.ApplicationBase%2A> and <xref:System.AppDomainSetup.PrivateBinPath%2A> properties when the application domain is configured.</span></span> <span data-ttu-id="f5463-112">儲存在全域組件快取的組件不會進行陰影複製。</span><span class="sxs-lookup"><span data-stu-id="f5463-112">Assemblies stored in the global assembly cache are not shadow copied.</span></span>

<span data-ttu-id="f5463-113">本文包含下列各節：</span><span class="sxs-lookup"><span data-stu-id="f5463-113">This article contains the following sections:</span></span>

- <span data-ttu-id="f5463-114">[啟用和使用陰影複製](#EnablingAndUsing)描述基本的用法，以及陰影複製可用的選項。</span><span class="sxs-lookup"><span data-stu-id="f5463-114">[Enabling and Using Shadow Copying](#EnablingAndUsing) describes the basic use and the options that are available for shadow copying.</span></span>

- <span data-ttu-id="f5463-115">[啟動效能](#StartupPerformance)描述為了在 .NET Framework 4 中陰影複製而進行的變更，以改善啟動效能，也描述如何還原為舊版的行為。</span><span class="sxs-lookup"><span data-stu-id="f5463-115">[Startup Performance](#StartupPerformance) describes the changes that are made to shadow copying in the .NET Framework 4 to improve startup performance, and how to revert to the behavior of earlier versions.</span></span>

- <span data-ttu-id="f5463-116">[已淘汰方法](#ObsoleteMethods)會描述對 .NET Framework 2.0 中控制陰影複製屬性和方法所進行的變更。</span><span class="sxs-lookup"><span data-stu-id="f5463-116">[Obsolete Methods](#ObsoleteMethods) describes the changes that were made to the properties and methods that control shadow copying in the .NET Framework 2.0.</span></span>

<a name="EnablingAndUsing"></a>

## <a name="enabling-and-using-shadow-copying"></a><span data-ttu-id="f5463-117">啟用及使用陰影複製</span><span class="sxs-lookup"><span data-stu-id="f5463-117">Enabling and Using Shadow Copying</span></span>

<span data-ttu-id="f5463-118">您可以使用 <xref:System.AppDomainSetup> 類別的屬性，如下所示，設定用於陰影複製的應用程式定義域：</span><span class="sxs-lookup"><span data-stu-id="f5463-118">You can use the properties of the <xref:System.AppDomainSetup> class as follows to configure an application domain for shadow copying:</span></span>

- <span data-ttu-id="f5463-119">將 <xref:System.AppDomainSetup.ShadowCopyFiles%2A> 屬性設為字串值 `"true"` 來啟用陰影複製。</span><span class="sxs-lookup"><span data-stu-id="f5463-119">Enable shadow copying by setting the <xref:System.AppDomainSetup.ShadowCopyFiles%2A> property to the string value `"true"`.</span></span>

  <span data-ttu-id="f5463-120">根據預設，在載入組件之前，此設定會複製在應用程式路徑的所有組件到下載快取。</span><span class="sxs-lookup"><span data-stu-id="f5463-120">By default, this setting causes all assemblies in the application path to be copied to a download cache before they are loaded.</span></span> <span data-ttu-id="f5463-121">這與 Common Language Runtime 所維護的快取相同，用以儲存從其他電腦下載的檔案，而且當這些檔案不再必需時，Common Language Runtime 會自動刪除這些檔案。</span><span class="sxs-lookup"><span data-stu-id="f5463-121">This is the same cache maintained by the common language runtime to store files downloaded from other computers, and the common language runtime automatically deletes the files when they are no longer needed.</span></span>

- <span data-ttu-id="f5463-122">使用 <xref:System.AppDomainSetup.CachePath%2A> 屬性和 <xref:System.AppDomainSetup.ApplicationName%2A> 屬性，選擇性地設定用於陰影複製檔案的自訂位置。</span><span class="sxs-lookup"><span data-stu-id="f5463-122">Optionally set a custom location for shadow copied files by using the <xref:System.AppDomainSetup.CachePath%2A> property and the <xref:System.AppDomainSetup.ApplicationName%2A> property.</span></span>

  <span data-ttu-id="f5463-123">藉由串連 <xref:System.AppDomainSetup.ApplicationName%2A> 屬性至 <xref:System.AppDomainSetup.CachePath%2A> 屬性做為子目錄，形成此位置的基底路徑。</span><span class="sxs-lookup"><span data-stu-id="f5463-123">The base path for the location is formed by concatenating the <xref:System.AppDomainSetup.ApplicationName%2A> property to the <xref:System.AppDomainSetup.CachePath%2A> property as a subdirectory.</span></span> <span data-ttu-id="f5463-124">這會陰影複製組件到這個路徑的子目錄，而非本身的基底路徑。</span><span class="sxs-lookup"><span data-stu-id="f5463-124">Assemblies are shadow copied to subdirectories of this path, not to the base path itself.</span></span>

  > [!NOTE]
  > <span data-ttu-id="f5463-125">如果未設定 <xref:System.AppDomainSetup.ApplicationName%2A> 屬性，則會忽略 <xref:System.AppDomainSetup.CachePath%2A> 屬性，並使用下載快取。</span><span class="sxs-lookup"><span data-stu-id="f5463-125">If the <xref:System.AppDomainSetup.ApplicationName%2A> property is not set, the <xref:System.AppDomainSetup.CachePath%2A> property is ignored and the download cache is used.</span></span> <span data-ttu-id="f5463-126">不會有例外狀況擲回。</span><span class="sxs-lookup"><span data-stu-id="f5463-126">No exception is thrown.</span></span>

  <span data-ttu-id="f5463-127">如果您指定自訂位置，則當您不再需要檔案時，要負責清除目錄及複製檔案。</span><span class="sxs-lookup"><span data-stu-id="f5463-127">If you specify a custom location, you are responsible for cleaning up the directories and copied files when they are no longer needed.</span></span> <span data-ttu-id="f5463-128">它們不會自動刪除。</span><span class="sxs-lookup"><span data-stu-id="f5463-128">They are not deleted automatically.</span></span>

  <span data-ttu-id="f5463-129">有幾個理由可能會讓您想設定陰影複製檔案的自訂位置。</span><span class="sxs-lookup"><span data-stu-id="f5463-129">There are a few reasons why you might want to set a custom location for shadow copied files.</span></span> <span data-ttu-id="f5463-130">如果您的應用程式會產生大量的複本，則您可能會想要設定陰影複製檔案的自訂位置。</span><span class="sxs-lookup"><span data-stu-id="f5463-130">You might want to set a custom location for shadow copied files if your application generates a large number of copies.</span></span> <span data-ttu-id="f5463-131">下載快取會受大小所限制，而非存留期，因此 Common Language Runtime 很可能會嘗試刪除仍在使用中的檔案。</span><span class="sxs-lookup"><span data-stu-id="f5463-131">The download cache is limited by size, not by lifetime, so it is possible that the common language runtime will attempt to delete a file that is still in use.</span></span> <span data-ttu-id="f5463-132">設定自訂位置的另一個理由是執行您應用程式的使用者沒有寫入權限，來寫入 Common Language Runtime 為下載快取所使用的目錄位置。</span><span class="sxs-lookup"><span data-stu-id="f5463-132">Another reason to set a custom location is when users running your application do not have write access to the directory location the common language runtime uses for the download cache.</span></span>

- <span data-ttu-id="f5463-133">使用 <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> 屬性來選擇性地限制陰影複製的組件。</span><span class="sxs-lookup"><span data-stu-id="f5463-133">Optionally limit the assemblies that are shadow copied by using the <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> property.</span></span>

  <span data-ttu-id="f5463-134">當您啟用應用程式定義域的陰影複製時，預設會複製所有組件到應用程式路徑中；也就是 <xref:System.AppDomainSetup.ApplicationBase%2A> 和 <xref:System.AppDomainSetup.PrivateBinPath%2A> 屬性所指定的目錄中。</span><span class="sxs-lookup"><span data-stu-id="f5463-134">When you enable shadow copying for an application domain, the default is to copy all assemblies in the application path — that is, in the directories specified by the <xref:System.AppDomainSetup.ApplicationBase%2A> and <xref:System.AppDomainSetup.PrivateBinPath%2A> properties.</span></span> <span data-ttu-id="f5463-135">您可以藉由建立字串限制所選目錄的複製，該字串只包含您想要陰影複製的目錄，並指派字串至 <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="f5463-135">You can limit the copying to selected directories by creating a string that contains only those directories you want to shadow copy, and assigning the string to the <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> property.</span></span> <span data-ttu-id="f5463-136">請以分號分隔目錄。</span><span class="sxs-lookup"><span data-stu-id="f5463-136">Separate the directories with semicolons.</span></span> <span data-ttu-id="f5463-137">只會對在所選目錄中的組件陰影複製。</span><span class="sxs-lookup"><span data-stu-id="f5463-137">The only assemblies that are shadow copied are the ones in the selected directories.</span></span>

  > [!NOTE]
  > <span data-ttu-id="f5463-138">如果您不指派字串給 <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> 屬性，或如果您將這個屬性設定為 `null`，則會陰影複製 <xref:System.AppDomainSetup.ApplicationBase%2A> 和 <xref:System.AppDomainSetup.PrivateBinPath%2A> 屬性所指定目錄中的所有組件。</span><span class="sxs-lookup"><span data-stu-id="f5463-138">If you don’t assign a string to the <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> property, or if you set this property to `null`, all assemblies in the directories specified by the <xref:System.AppDomainSetup.ApplicationBase%2A> and <xref:System.AppDomainSetup.PrivateBinPath%2A> properties are shadow copied.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="f5463-139">目錄路徑不可包含分號，因為分號是分隔符號字元。</span><span class="sxs-lookup"><span data-stu-id="f5463-139">Directory paths must not contain semicolons, because the semicolon is the delimiter character.</span></span> <span data-ttu-id="f5463-140">分號沒有逸出字元。</span><span class="sxs-lookup"><span data-stu-id="f5463-140">There is no escape character for semicolons.</span></span>

<a name="StartupPerformance"></a>

## <a name="startup-performance"></a><span data-ttu-id="f5463-141">啟動效能</span><span class="sxs-lookup"><span data-stu-id="f5463-141">Startup Performance</span></span>

<span data-ttu-id="f5463-142">當使用陰影複製的應用程式定義域啟動時，複製應用程式目錄中的組件到陰影複製目錄會有延遲；或當組件已經在該位置時，驗證組件也會有延遲。</span><span class="sxs-lookup"><span data-stu-id="f5463-142">When an application domain that uses shadow copying starts, there is a delay while assemblies in the application directory are copied to the shadow copy directory, or verified if they are already in that location.</span></span> <span data-ttu-id="f5463-143">在 .NET Framework 4 之前，系統會將所有組件複製到暫存目錄。</span><span class="sxs-lookup"><span data-stu-id="f5463-143">Before the .NET Framework 4, all assemblies were copied to a temporary directory.</span></span> <span data-ttu-id="f5463-144">會開啟每個組件來確認組件名稱，且會驗證強式名稱。</span><span class="sxs-lookup"><span data-stu-id="f5463-144">Each assembly was opened to verify the assembly name, and the strong name was validated.</span></span> <span data-ttu-id="f5463-145">會檢查每個組件，以查看它是否已更新為比陰影複製目錄中的複本還要新。</span><span class="sxs-lookup"><span data-stu-id="f5463-145">Each assembly was checked to see whether it had been updated more recently than the copy in the shadow copy directory.</span></span> <span data-ttu-id="f5463-146">若是如此，則將它複製到陰影複製目錄中。</span><span class="sxs-lookup"><span data-stu-id="f5463-146">If so, it was copied to the shadow copy directory.</span></span> <span data-ttu-id="f5463-147">最後會捨棄暫時複本。</span><span class="sxs-lookup"><span data-stu-id="f5463-147">Finally, the temporary copies were discarded.</span></span>

<span data-ttu-id="f5463-148">從 .NET Framework 4 開始，預設啟動行為會直接比較應用程式目錄中每個組件的檔案日期和時間，以及陰影複製目錄中複本的檔案日期和時間。</span><span class="sxs-lookup"><span data-stu-id="f5463-148">Beginning with the .NET Framework 4, the default startup behavior is to directly compare the file date and time of each assembly in the application directory with the file date and time of the copy in the shadow copy directory.</span></span> <span data-ttu-id="f5463-149">如果已更新組件，便會使用和舊版 .NET Framework 相同的程序複製組件；否則會載入陰影複製目錄中的複本。</span><span class="sxs-lookup"><span data-stu-id="f5463-149">If the assembly has been updated, it is copied by using the same procedure as in earlier versions of the .NET Framework; otherwise, the copy in the shadow copy directory is loaded.</span></span>

<span data-ttu-id="f5463-150">對於組件不常變更，且變更通常發生在組件一小部分的應用程式而言，會產生最大的效能改進。</span><span class="sxs-lookup"><span data-stu-id="f5463-150">The resulting performance improvement is largest for applications in which assemblies do not change frequently and changes usually occur in a small subset of assemblies.</span></span> <span data-ttu-id="f5463-151">如果應用程式中大部分的組件經常變更，則新的預設行為可能會導致效能變差。</span><span class="sxs-lookup"><span data-stu-id="f5463-151">If a majority of assemblies in an application change frequently, the new default behavior might cause a performance regression.</span></span> <span data-ttu-id="f5463-152">您可以使用將專案[ \<shadowCopyVerifyByTimestamp> 新增至設定檔，以還原](../configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md)舊版 .NET Framework 的啟動行為 `enabled="false"` 。</span><span class="sxs-lookup"><span data-stu-id="f5463-152">You can restore the startup behavior of previous versions of the .NET Framework by adding the [\<shadowCopyVerifyByTimestamp> element](../configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md) to the configuration file, with `enabled="false"`.</span></span>

<a name="ObsoleteMethods"></a>

## <a name="obsolete-methods"></a><span data-ttu-id="f5463-153">已淘汰的方法</span><span class="sxs-lookup"><span data-stu-id="f5463-153">Obsolete Methods</span></span>

<span data-ttu-id="f5463-154"><xref:System.AppDomain> 類別有幾種方法，例如 <xref:System.AppDomain.SetShadowCopyFiles%2A> 和 <xref:System.AppDomain.ClearShadowCopyPath%2A>，可用來控制應用程式定義域上的陰影複製，但這些已經在 .NET Framework 2.0 版中標記為已淘汰。</span><span class="sxs-lookup"><span data-stu-id="f5463-154">The <xref:System.AppDomain> class has several methods, such as <xref:System.AppDomain.SetShadowCopyFiles%2A> and <xref:System.AppDomain.ClearShadowCopyPath%2A>, that can be used to control shadow copying on an application domain, but these have been marked obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="f5463-155">建議使用 <xref:System.AppDomainSetup> 類別的屬性來設定用於陰影複製的應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="f5463-155">The recommended way to configure an application domain for shadow copying is to use the properties of the <xref:System.AppDomainSetup> class.</span></span>

## <a name="see-also"></a><span data-ttu-id="f5463-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5463-156">See also</span></span>

- <xref:System.AppDomainSetup.ShadowCopyFiles%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.CachePath%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.ApplicationName%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.ShadowCopyDirectories%2A?displayProperty=nameWithType>
- [<span data-ttu-id="f5463-157">\<shadowCopyVerifyByTimestamp>元素</span><span class="sxs-lookup"><span data-stu-id="f5463-157">\<shadowCopyVerifyByTimestamp> Element</span></span>](../configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md)
