---
title: 建立桌面應用程式的附屬組件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- deploying applications [.NET Framework], resources
- resource files, deploying
- hub-and-spoke resource deployment model
- resource files, packaging
- application resources, packaging
- public keys, obtaining
- satellite assemblies
- assemblies [.NET Framework], signing
- application resources, deploying
- Al.exe
- GAC (global assembly cache), satellite assemblies
- Assembly Linker
- directory locations for satellite assemblies
- global assembly cache, satellite assemblies
- packaging application resources
- compiling satellite assemblies
- re-signing assemblies
ms.assetid: 8d5c6044-2919-41d2-8321-274706b295ac
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c5ad89e24bfc55497af52b827717b8b3965bd600
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70041013"
---
# <a name="creating-satellite-assemblies-for-desktop-apps"></a><span data-ttu-id="99e9f-102">建立桌面應用程式的附屬組件</span><span class="sxs-lookup"><span data-stu-id="99e9f-102">Creating Satellite Assemblies for Desktop Apps</span></span>

<span data-ttu-id="99e9f-103">資源檔在當地語系化的應用程式中扮演重要角色。</span><span class="sxs-lookup"><span data-stu-id="99e9f-103">Resource files play a central role in localized applications.</span></span> <span data-ttu-id="99e9f-104">它們可讓應用程式以使用者自己的語言和文化特性顯示字串、影像和其他資料，以及在使用者自己的語言或文化特性的資源無法使用時提供替代資料。</span><span class="sxs-lookup"><span data-stu-id="99e9f-104">They enable an application to display strings, images, and other data in the user's own language and culture, and to provide alternate data if resources for the user's own language or culture are unavailable.</span></span> <span data-ttu-id="99e9f-105">.NET Framework 會使用中樞和支點模型來尋找並擷取當地語系化的資源。</span><span class="sxs-lookup"><span data-stu-id="99e9f-105">The .NET Framework uses a hub-and-spoke model to locate and retrieve localized resources.</span></span> <span data-ttu-id="99e9f-106">中樞是主要組件，其中包含未當地語系化的可執行程式碼以及稱為中性或預設文化特性之單一文化特性的資源。</span><span class="sxs-lookup"><span data-stu-id="99e9f-106">The hub is the main assembly that contains the non-localizable executable code and the resources for a single culture, which is called the neutral or default culture.</span></span> <span data-ttu-id="99e9f-107">預設文化特性是應用程式的後援文化特性；當地語系化的資源無法使用時會使用它。</span><span class="sxs-lookup"><span data-stu-id="99e9f-107">The default culture is the fallback culture for the application; it is used when no localized resources are available.</span></span> <span data-ttu-id="99e9f-108">您使用 <xref:System.Resources.NeutralResourcesLanguageAttribute> 屬性來指定應用程式之預設文化特性的文化特性。</span><span class="sxs-lookup"><span data-stu-id="99e9f-108">You use the <xref:System.Resources.NeutralResourcesLanguageAttribute> attribute to designate the culture of the application's default culture.</span></span> <span data-ttu-id="99e9f-109">每個支點都會連線至附屬組件，其中包含單一當地語系化文化特性但未包含任何程式碼的資源。</span><span class="sxs-lookup"><span data-stu-id="99e9f-109">Each spoke connects to a satellite assembly that contains the resources for a single localized culture but does not contain any code.</span></span> <span data-ttu-id="99e9f-110">因為附屬組件不是主要組件的一部分，所以您可以輕鬆地更新或取代對應至特定文化特性的資源，而不需要取代應用程式的主要組件。</span><span class="sxs-lookup"><span data-stu-id="99e9f-110">Because the satellite assemblies are not part of the main assembly, you can easily update or replace resources that correspond to a specific culture without replacing the main assembly for the application.</span></span>

> [!NOTE]
> <span data-ttu-id="99e9f-111">應用程式之預設文化特性的資源也可以儲存在附屬組件中。</span><span class="sxs-lookup"><span data-stu-id="99e9f-111">The resources of an application's default culture can also be stored in a satellite assembly.</span></span> <span data-ttu-id="99e9f-112">若要這樣做，請將 <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType> 的值指派給 <xref:System.Resources.NeutralResourcesLanguageAttribute> 屬性。</span><span class="sxs-lookup"><span data-stu-id="99e9f-112">To do this, you assign the <xref:System.Resources.NeutralResourcesLanguageAttribute> attribute a value of <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType>.</span></span>

## <a name="satellite-assembly-name-and-location"></a><span data-ttu-id="99e9f-113">附屬組件名稱和位置</span><span class="sxs-lookup"><span data-stu-id="99e9f-113">Satellite Assembly Name and Location</span></span>

<span data-ttu-id="99e9f-114">中樞和支點模型需要您將資源放入特定位置，以輕鬆地找到和使用它們。</span><span class="sxs-lookup"><span data-stu-id="99e9f-114">The hub-and-spoke model requires that you place resources in specific locations so that they can be easily located and used.</span></span> <span data-ttu-id="99e9f-115">如果您未如預期編譯和命名資源，或未將它們放在正確位置，則 Common Language Runtime 會找不到它們，並改為使用預設文化特性的資源。</span><span class="sxs-lookup"><span data-stu-id="99e9f-115">If you do not compile and name resources as expected, or if you do not place them in the correct locations, the common language runtime will not be able to locate them and will use the resources of the default culture instead.</span></span> <span data-ttu-id="99e9f-116">以 <xref:System.Resources.ResourceManager> 物件代表的 .NET Framework Resource Manager 是用來自動存取當地語系化資源。</span><span class="sxs-lookup"><span data-stu-id="99e9f-116">The .NET Framework Resource Manager, represented by a <xref:System.Resources.ResourceManager> object, is used to automatically access localized resources.</span></span> <span data-ttu-id="99e9f-117">Resource Manager 需要下列各項：</span><span class="sxs-lookup"><span data-stu-id="99e9f-117">The Resource Manager requires the following:</span></span>

- <span data-ttu-id="99e9f-118">單一附屬組件必須包括特定文化特性的所有資源。</span><span class="sxs-lookup"><span data-stu-id="99e9f-118">A single satellite assembly must include all the resources for a particular culture.</span></span> <span data-ttu-id="99e9f-119">換句話說，您應該將多個 .txt 或 .resx 檔案編譯成單一二進位 .resources 檔案。</span><span class="sxs-lookup"><span data-stu-id="99e9f-119">In other words, you should compile multiple .txt or .resx files into a single binary .resources file.</span></span>

- <span data-ttu-id="99e9f-120">在儲存該文化特性資源之每個當地語系化文化特性的應用程式目錄中，都必須有不同的子目錄。</span><span class="sxs-lookup"><span data-stu-id="99e9f-120">There must be a separate subdirectory in the application directory for each localized culture that stores that culture's resources.</span></span> <span data-ttu-id="99e9f-121">子目錄名稱必須與文化特性名稱相同。</span><span class="sxs-lookup"><span data-stu-id="99e9f-121">The subdirectory name must be the same as the culture name.</span></span> <span data-ttu-id="99e9f-122">或者，您可以在全域組件快取中儲存附屬組件。</span><span class="sxs-lookup"><span data-stu-id="99e9f-122">Alternately, you can store your satellite assemblies in the global assembly cache.</span></span> <span data-ttu-id="99e9f-123">在此情況下，組件強式名稱的文化特性資訊元件必須指出其文化特性。</span><span class="sxs-lookup"><span data-stu-id="99e9f-123">In this case, the culture information component of the assembly's strong name must indicate its culture.</span></span> <span data-ttu-id="99e9f-124">(請參閱本主題稍後的[在全域組件快取中安裝附屬組件](#SN)一節)。</span><span class="sxs-lookup"><span data-stu-id="99e9f-124">(See the [Installing Satellite Assemblies in the Global Assembly Cache](#SN) section later in this topic.)</span></span>

  > [!NOTE]
  > <span data-ttu-id="99e9f-125">如果您的應用程式包括子文化特性的資源，請將每個子文化特性放在應用程式目錄下的不同子目錄中。</span><span class="sxs-lookup"><span data-stu-id="99e9f-125">If your application includes resources for subcultures, place each subculture in a separate subdirectory under the application directory.</span></span> <span data-ttu-id="99e9f-126">請不要將子文化特性放在其主要文化特性目錄的子目錄中。</span><span class="sxs-lookup"><span data-stu-id="99e9f-126">Do not place subcultures in subdirectories under their main culture's directory.</span></span>

- <span data-ttu-id="99e9f-127">附屬組件的名稱必須與應用程式相同，而且必須使用副檔名 ".resources.dll"。</span><span class="sxs-lookup"><span data-stu-id="99e9f-127">The satellite assembly must have the same name as the application, and must use the file name extension ".resources.dll".</span></span> <span data-ttu-id="99e9f-128">例如，如果應用程式命名為 Example.exe，則每個附屬組件的名稱應該是 Example.resources.dll。</span><span class="sxs-lookup"><span data-stu-id="99e9f-128">For example, if an application is named Example.exe, the name of each satellite assembly should be Example.resources.dll.</span></span> <span data-ttu-id="99e9f-129">請注意，附屬組件名稱不會指出其資源檔的文化特性。</span><span class="sxs-lookup"><span data-stu-id="99e9f-129">Note that the satellite assembly name does not indicate the culture of its resource files.</span></span> <span data-ttu-id="99e9f-130">不過，附屬組件會出現在確實指定文化特性的目錄中。</span><span class="sxs-lookup"><span data-stu-id="99e9f-130">However, the satellite assembly appears in a directory that does specify the culture.</span></span>

- <span data-ttu-id="99e9f-131">附屬組件文化特性的資訊必須包括在組件的中繼資料內。</span><span class="sxs-lookup"><span data-stu-id="99e9f-131">Information about the culture of the satellite assembly must be included in the assembly's metadata.</span></span> <span data-ttu-id="99e9f-132">若要將文化特性名稱儲存在附屬組件的中繼資料內，請在使用[組件連結器](../../../docs/framework/tools/al-exe-assembly-linker.md)將資源內嵌在附屬組件時指定 `/culture` 選項。</span><span class="sxs-lookup"><span data-stu-id="99e9f-132">To store the culture name in the satellite assembly's metadata, you specify the `/culture` option when you use [Assembly Linker](../../../docs/framework/tools/al-exe-assembly-linker.md) to embed resources in the satellite assembly.</span></span>

<span data-ttu-id="99e9f-133">下圖顯示未在[全域組件快取](../../../docs/framework/app-domains/gac.md)中安裝之應用程式的範例目錄結構和位置需求。</span><span class="sxs-lookup"><span data-stu-id="99e9f-133">The following illustration shows a sample directory structure and location requirements for applications that you are not installing in the [global assembly cache](../../../docs/framework/app-domains/gac.md).</span></span> <span data-ttu-id="99e9f-134">副檔名為 .txt 和 .resources 的項目將不會隨附最終應用程式。</span><span class="sxs-lookup"><span data-stu-id="99e9f-134">The items with .txt and .resources extensions will not ship with the final application.</span></span> <span data-ttu-id="99e9f-135">這些是用來建立最終附屬資源組件的中繼資源檔。</span><span class="sxs-lookup"><span data-stu-id="99e9f-135">These are the intermediate resource files used to create the final satellite resource assemblies.</span></span> <span data-ttu-id="99e9f-136">在此範例中，您可以將 .resx 檔案取代為 .txt 檔案。</span><span class="sxs-lookup"><span data-stu-id="99e9f-136">In this example, you could substitute .resx files for the .txt files.</span></span> <span data-ttu-id="99e9f-137">如需詳細資訊，請參閱[封裝和部署資源](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)。</span><span class="sxs-lookup"><span data-stu-id="99e9f-137">For more information, see [Packaging and Deploying Resources](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md).</span></span>

<span data-ttu-id="99e9f-138">下圖顯示附屬組件目錄：</span><span class="sxs-lookup"><span data-stu-id="99e9f-138">The following image shows the satellite assembly directory:</span></span>

![使用當地語系化文化特性 (Culture) 子目錄的附屬組件目錄。](./media/creating-satellite-assemblies-for-desktop-apps/satellite-assembly-directory.gif)

## <a name="compiling-satellite-assemblies"></a><span data-ttu-id="99e9f-140">編譯附屬組件</span><span class="sxs-lookup"><span data-stu-id="99e9f-140">Compiling Satellite Assemblies</span></span>

<span data-ttu-id="99e9f-141">您使用[資源檔產生器 (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)，將包含資源的文字檔或 XML (.resx) 檔案編譯成二進位 .resources 檔案。</span><span class="sxs-lookup"><span data-stu-id="99e9f-141">You use [Resource File Generator (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) to compile text files or XML (.resx) files that contain resources to binary .resources files.</span></span> <span data-ttu-id="99e9f-142">您接著使用[組件連結器 (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) 將 .resources 檔案編譯成附屬組件。</span><span class="sxs-lookup"><span data-stu-id="99e9f-142">You then use [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) to compile .resources files into satellite assemblies.</span></span> <span data-ttu-id="99e9f-143">Al.exe 會從您指定的 .resources 檔案建立組件。</span><span class="sxs-lookup"><span data-stu-id="99e9f-143">Al.exe creates an assembly from the .resources files that you specify.</span></span> <span data-ttu-id="99e9f-144">附屬組件只能包含資源，而不能包含任何可執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="99e9f-144">Satellite assemblies can contain only resources; they cannot contain any executable code.</span></span>

<span data-ttu-id="99e9f-145">下列 Al.exe 命令會從德文資源檔 strings.de.resources 建立應用程式 `Example` 的附屬組件。</span><span class="sxs-lookup"><span data-stu-id="99e9f-145">The following Al.exe command creates a satellite assembly for the application `Example` from the German resources file strings.de.resources.</span></span>

```console
al -target:lib -embed:strings.de.resources -culture:de -out:Example.resources.dll
```

<span data-ttu-id="99e9f-146">下列 Al.exe 命令也會從 strings.de.resources 檔案建立應用程式 `Example` 的附屬組件。</span><span class="sxs-lookup"><span data-stu-id="99e9f-146">The following Al.exe command also creates a satellite assembly for the application `Example` from the file strings.de.resources.</span></span> <span data-ttu-id="99e9f-147">**/template** 選項會讓附屬組件從父組件 (Example.dll) 繼承所有組件中繼資料，但其文化特性資訊除外。</span><span class="sxs-lookup"><span data-stu-id="99e9f-147">The **/template** option causes the satellite assembly to inherit all assembly metadata except for its culture information from the parent assembly (Example.dll).</span></span>

```console
al -target:lib -embed:strings.de.resources -culture:de -out:Example.resources.dll -template:Example.dll
```

<span data-ttu-id="99e9f-148">下表更詳細描述在這些命令中使用的 Al.exe 選項。</span><span class="sxs-lookup"><span data-stu-id="99e9f-148">The following table describes the Al.exe options used in these commands in more detail.</span></span>

|<span data-ttu-id="99e9f-149">選項</span><span class="sxs-lookup"><span data-stu-id="99e9f-149">Option</span></span>|<span data-ttu-id="99e9f-150">說明</span><span class="sxs-lookup"><span data-stu-id="99e9f-150">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="99e9f-151">**-target:** lib</span><span class="sxs-lookup"><span data-stu-id="99e9f-151">**-target:** lib</span></span>|<span data-ttu-id="99e9f-152">指定將附屬組件編譯成程式庫 (.dll) 檔案。</span><span class="sxs-lookup"><span data-stu-id="99e9f-152">Specifies that your satellite assembly is compiled to a library (.dll) file.</span></span> <span data-ttu-id="99e9f-153">因為附屬組件未包含可執行程式碼，而且不是應用程式的主要組件，所以您必須將附屬組件儲存為 DLL。</span><span class="sxs-lookup"><span data-stu-id="99e9f-153">Because a satellite assembly does not contain executable code and is not an application's main assembly, you must save satellite assemblies as DLLs.</span></span>|
|<span data-ttu-id="99e9f-154">**-embed:** strings.de.resources</span><span class="sxs-lookup"><span data-stu-id="99e9f-154">**-embed:** strings.de.resources</span></span>|<span data-ttu-id="99e9f-155">指定要在 Al.exe 編譯組件時內嵌的資源檔名稱。</span><span class="sxs-lookup"><span data-stu-id="99e9f-155">Specifies the name of the resource file to embed when Al.exe compiles the assembly.</span></span> <span data-ttu-id="99e9f-156">您可以在附屬組件中內嵌多個 .resources 檔案；但是，如果您遵循中樞和支點模型，則必須為每個文化特性編譯一個附屬組件。</span><span class="sxs-lookup"><span data-stu-id="99e9f-156">You can embed multiple .resources files in a satellite assembly, but if you are following the hub-and-spoke model, you must compile one satellite assembly for each culture.</span></span> <span data-ttu-id="99e9f-157">不過，您可以為字串和物件建立個別的 .resources 檔案。</span><span class="sxs-lookup"><span data-stu-id="99e9f-157">However, you can create separate .resources files for strings and objects.</span></span>|
|<span data-ttu-id="99e9f-158">**-culture:** de</span><span class="sxs-lookup"><span data-stu-id="99e9f-158">**-culture:** de</span></span>|<span data-ttu-id="99e9f-159">指定要編譯之資源的文化特性。</span><span class="sxs-lookup"><span data-stu-id="99e9f-159">Specifies the culture of the resource to compile.</span></span> <span data-ttu-id="99e9f-160">Common Language Runtime 在搜尋所指定文化特性的資源時會使用這項資訊。</span><span class="sxs-lookup"><span data-stu-id="99e9f-160">The common language runtime uses this information when it searches for the resources for a specified culture.</span></span> <span data-ttu-id="99e9f-161">如果您省略這個選項，Al.exe 還是會編譯資源，但執行階段在使用者要求資源時會找不到。</span><span class="sxs-lookup"><span data-stu-id="99e9f-161">If you omit this option, Al.exe will still compile the resource, but the runtime will not be able to find it when a user requests it.</span></span>|
|<span data-ttu-id="99e9f-162">**-out:** Example.resources.dll</span><span class="sxs-lookup"><span data-stu-id="99e9f-162">**-out:** Example.resources.dll</span></span>|<span data-ttu-id="99e9f-163">指定輸出檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="99e9f-163">Specifies the name of the output file.</span></span> <span data-ttu-id="99e9f-164">名稱必須遵循命名標準 <基底名稱>  .resources.<副檔名>  ，其中 <基底名稱>  為主要組件的名稱，<副檔名>  則為有效的副檔名 (例如 .dll)。</span><span class="sxs-lookup"><span data-stu-id="99e9f-164">The name must follow the naming standard *baseName*.resources.*extension*, where *baseName* is the name of the main assembly and *extension* is a valid file name extension (such as .dll).</span></span> <span data-ttu-id="99e9f-165">請注意，執行階段無法根據輸出檔名稱來判斷附屬組件的文化特性；您必須使用 **/culture** 選項來指定它。</span><span class="sxs-lookup"><span data-stu-id="99e9f-165">Note that the runtime is not able to determine the culture of a satellite assembly based on its output file name; you must use the **/culture** option to specify it.</span></span>|
|<span data-ttu-id="99e9f-166">**-template:** Example.dll</span><span class="sxs-lookup"><span data-stu-id="99e9f-166">**-template:** Example.dll</span></span>|<span data-ttu-id="99e9f-167">指定附屬組件要從中繼承所有組件中繼資料的組件，但不包括文化特性欄位。</span><span class="sxs-lookup"><span data-stu-id="99e9f-167">Specifies an assembly from which the satellite assembly will inherit all assembly metadata except the culture field.</span></span> <span data-ttu-id="99e9f-168">只有在您指定的組件具有[強式名稱](../../../docs/framework/app-domains/strong-named-assemblies.md)時，此選項才會影響附屬組件。</span><span class="sxs-lookup"><span data-stu-id="99e9f-168">This option affects satellite assemblies only if you specify an assembly that has a [strong name](../../../docs/framework/app-domains/strong-named-assemblies.md).</span></span>|

<span data-ttu-id="99e9f-169">如需 Al.exe 的完整可用選項清單，請參閱[組件連結器 (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md)。</span><span class="sxs-lookup"><span data-stu-id="99e9f-169">For a complete list of options available with Al.exe, see [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md).</span></span>

## <a name="satellite-assemblies-an-example"></a><span data-ttu-id="99e9f-170">附屬組件：範例</span><span class="sxs-lookup"><span data-stu-id="99e9f-170">Satellite Assemblies: An Example</span></span>

<span data-ttu-id="99e9f-171">下列簡單 "Hello world" 範例會顯示包含當地語系化問候語的訊息方塊。</span><span class="sxs-lookup"><span data-stu-id="99e9f-171">The following is a simple "Hello world" example that displays a message box containing a localized greeting.</span></span> <span data-ttu-id="99e9f-172">此範例包括英文 (美國)、法文 (法國) 和俄文 (俄國) 文化特性的資源，而其後援文化特性是英文。</span><span class="sxs-lookup"><span data-stu-id="99e9f-172">The example includes resources for the English (United States), French (France), and Russian (Russia) cultures, and its fallback culture is English.</span></span> <span data-ttu-id="99e9f-173">若要建立範例，請執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="99e9f-173">To create the example, do the following:</span></span>

1. <span data-ttu-id="99e9f-174">建立名為 Greeting.resx 或 Greeting.txt 的資源檔，以包含預設文化特性的資源。</span><span class="sxs-lookup"><span data-stu-id="99e9f-174">Create a resource file named Greeting.resx or Greeting.txt to contain the resource for the default culture.</span></span> <span data-ttu-id="99e9f-175">將名為 `HelloString` 且其值為 "Hello world!" 的單一字串儲存</span><span class="sxs-lookup"><span data-stu-id="99e9f-175">Store a single string named `HelloString` whose value is "Hello world!"</span></span> <span data-ttu-id="99e9f-176">在此檔案中。</span><span class="sxs-lookup"><span data-stu-id="99e9f-176">in this file.</span></span>

2. <span data-ttu-id="99e9f-177">若要指出英文 (en) 是應用程式的預設文化特性，請將下列 <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> 屬性新增至應用程式的 AssemblyInfo 檔案或將編譯為應用程式主要組件的主要原始程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="99e9f-177">To indicate that English (en) is the application's default culture, add the following <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> attribute to the application's AssemblyInfo file or to the main source code file that will be compiled into the application's main assembly.</span></span>

    [!code-csharp[Conceptual.Resources.Locating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.locating/cs/assemblyinfo.cs#2)]
    [!code-vb[Conceptual.Resources.Locating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.locating/vb/assemblyinfo.vb#2)]

3. <span data-ttu-id="99e9f-178">將其他文化特性 (en-US、fr-FR 和 ru-RU) 的支援新增至應用程式，如下所示：</span><span class="sxs-lookup"><span data-stu-id="99e9f-178">Add support for additional cultures (en-US, fr-FR, and ru-RU) to the application as follows:</span></span>

    - <span data-ttu-id="99e9f-179">若要支援 en-US 或英文 (美國) 文化特性，請建立名為 Greeting.en-US.resx 或 Greeting.en-US.txt 的資源檔，並在其中儲存名為 `HelloString` 且其值為 "Hi world!" 的單一字串。</span><span class="sxs-lookup"><span data-stu-id="99e9f-179">To support the en-US or English (United States) culture, create a resource file named Greeting.en-US.resx or Greeting.en-US.txt, and store in it a single string named `HelloString` whose value is "Hi world!"</span></span>

    - <span data-ttu-id="99e9f-180">若要支援 fr-FR 或法文 (法國) 文化特性，請建立名為 Greeting.fr-FR.resx 或 Greeting.fr-FR.txt 的資源檔，並在其中儲存名為 `HelloString` 且其值為 "Salut tout le monde!" 的單一字串。</span><span class="sxs-lookup"><span data-stu-id="99e9f-180">To support the fr-FR or French (France) culture, create a resource file named Greeting.fr-FR.resx or Greeting.fr-FR.txt, and store in it a single string named `HelloString` whose value is "Salut tout le monde!"</span></span>

    - <span data-ttu-id="99e9f-181">若要支援 ru-RU 或俄文 (俄國) 文化特性，請建立名為 Greeting.ru-RU.resx 或 Greeting.ru-RU.txt 的資源檔，並在其中儲存名為 `HelloString` 且其值為 "Всем привет!" 的單一字串。</span><span class="sxs-lookup"><span data-stu-id="99e9f-181">To support the ru-RU or Russian (Russia) culture, create a resource file named Greeting.ru-RU.resx or Greeting.ru-RU.txt, and store in it a single string named `HelloString` whose value is "Всем привет!"</span></span>

4. <span data-ttu-id="99e9f-182">使用 [Resgen.exe](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)，將每一個文字或 XML 資源檔編譯成二進位 .resources 檔案。</span><span class="sxs-lookup"><span data-stu-id="99e9f-182">Use [Resgen.exe](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) to compile each text or XML resource file to a binary .resources file.</span></span> <span data-ttu-id="99e9f-183">輸出是根檔案名稱與 .resx 或 .txt 檔案相同的一組檔案，但副檔名為 .resources。</span><span class="sxs-lookup"><span data-stu-id="99e9f-183">The output is a set of files that have the same root file name as the .resx or .txt files, but a .resources extension.</span></span> <span data-ttu-id="99e9f-184">如果您使用 Visual Studio 建立範例，則會自動處理編譯程序。</span><span class="sxs-lookup"><span data-stu-id="99e9f-184">If you create the example with Visual Studio, the compilation process is handled automatically.</span></span> <span data-ttu-id="99e9f-185">如果您不要使用 Visual Studio，請執行下列命令將 .resx 檔案編譯為 .resources 檔案：</span><span class="sxs-lookup"><span data-stu-id="99e9f-185">If you aren't using Visual Studio, run the following commands to compile the .resx files into .resources files:</span></span>

    ```console
    resgen Greeting.resx
    resgen Greeting.en-us.resx
    resgen Greeting.fr-FR.resx
    resgen Greeting.ru-RU.resx
    ```

    <span data-ttu-id="99e9f-186">如果您的資源是文字檔，而非 XML 檔案，請將副檔名 .resx 取代為 .txt。</span><span class="sxs-lookup"><span data-stu-id="99e9f-186">If your resources are in text files instead of XML files, replace the .resx extension with .txt.</span></span>

5. <span data-ttu-id="99e9f-187">將下列原始程式碼與預設文化特性的資源編譯為應用程式的主要組件：</span><span class="sxs-lookup"><span data-stu-id="99e9f-187">Compile the following source code along with the resources for the default culture into the application's main assembly:</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="99e9f-188">如果您使用命令列建立範例而非 Visual Studio，則應該將 <xref:System.Resources.ResourceManager> 類別建構函式的呼叫修改為下列：`ResourceManager rm = new ResourceManager("Greetings", typeof(Example).Assembly);`</span><span class="sxs-lookup"><span data-stu-id="99e9f-188">If you are using the command line rather than Visual Studio to create the example, you should modify the call to the <xref:System.Resources.ResourceManager> class constructor to the following: `ResourceManager rm = new ResourceManager("Greetings", typeof(Example).Assembly);`</span></span>

    [!code-csharp[Conceptual.Resources.Locating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.locating/cs/program.cs#1)]
    [!code-vb[Conceptual.Resources.Locating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.locating/vb/module1.vb#1)]

    <span data-ttu-id="99e9f-189">如果應用程式命名為 Example，而且您從命令列進行編譯，則 C# 編譯器的命令是：</span><span class="sxs-lookup"><span data-stu-id="99e9f-189">If the application is named Example and you are compiling from the command line, the command for the C# compiler is:</span></span>

    ```console
    csc Example.cs -res:Greeting.resources
    ```

    <span data-ttu-id="99e9f-190">對應的 Visual Basic 編譯器命令為：</span><span class="sxs-lookup"><span data-stu-id="99e9f-190">The corresponding Visual Basic compiler command is:</span></span>

    ```console
    vbc Example.vb -res:Greeting.resources
    ```

6. <span data-ttu-id="99e9f-191">在應用程式所支援之每個當地語系化文化特性的主要應用程式目錄中，建立子目錄。</span><span class="sxs-lookup"><span data-stu-id="99e9f-191">Create a subdirectory in the main application directory for each localized culture supported by the application.</span></span> <span data-ttu-id="99e9f-192">您應該建立 en-US、fr-FR 和 ru-RU 子目錄。</span><span class="sxs-lookup"><span data-stu-id="99e9f-192">You should create an en-US, an fr-FR, and an ru-RU subdirectory.</span></span> <span data-ttu-id="99e9f-193">Visual Studio 會在編譯程序時自動建立這些子目錄。</span><span class="sxs-lookup"><span data-stu-id="99e9f-193">Visual Studio creates these subdirectories automatically as part of the compilation process.</span></span>

7. <span data-ttu-id="99e9f-194">將個別文化特性特定 .resources 檔案內嵌到附屬組件，並將它們儲存到適當的目錄。</span><span class="sxs-lookup"><span data-stu-id="99e9f-194">Embed the individual culture-specific .resources files into satellite assemblies and save them to the appropriate directory.</span></span> <span data-ttu-id="99e9f-195">針對每個 .resources 檔案執行這項作業的命令為：</span><span class="sxs-lookup"><span data-stu-id="99e9f-195">The command to do this for each .resources file is:</span></span>

    ```console
    al -target:lib -embed:Greeting.culture.resources -culture:culture -out:culture\Example.resources.dll
    ```

    <span data-ttu-id="99e9f-196">其中 *culture* 是附屬組件會包含其資源的文化特性名稱。</span><span class="sxs-lookup"><span data-stu-id="99e9f-196">where *culture* is the name of the culture whose resources the satellite assembly contains.</span></span> <span data-ttu-id="99e9f-197">Visual Studio 會自動處理這個程序。</span><span class="sxs-lookup"><span data-stu-id="99e9f-197">Visual Studio handles this process automatically.</span></span>

<span data-ttu-id="99e9f-198">您接著可以執行此範例。</span><span class="sxs-lookup"><span data-stu-id="99e9f-198">You can then run the example.</span></span> <span data-ttu-id="99e9f-199">它會隨機讓其中一個支援的文化特性成為目前文化特性，並顯示當地語系化的問候語。</span><span class="sxs-lookup"><span data-stu-id="99e9f-199">It will randomly make one of the supported cultures the current culture and display a localized greeting.</span></span>

<a name="SN"></a>

## <a name="installing-satellite-assemblies-in-the-global-assembly-cache"></a><span data-ttu-id="99e9f-200">在全域組件快取中安裝附屬組件</span><span class="sxs-lookup"><span data-stu-id="99e9f-200">Installing Satellite Assemblies in the Global Assembly Cache</span></span>

<span data-ttu-id="99e9f-201">您可以將組件安裝在全域組件快取中，而不是在本機應用程式子目錄中安裝組件。</span><span class="sxs-lookup"><span data-stu-id="99e9f-201">Instead of installing assemblies in a local application subdirectory, you can install them in the global assembly cache.</span></span> <span data-ttu-id="99e9f-202">如果您有供多個應用程式使用的類別庫和類別庫資源組件，則這特別有用。</span><span class="sxs-lookup"><span data-stu-id="99e9f-202">This is particularly useful if you have class libraries and class library resource assemblies that are used by multiple applications.</span></span>

<span data-ttu-id="99e9f-203">在全域組件快取中安裝組件時，需要組件具有強式名稱。</span><span class="sxs-lookup"><span data-stu-id="99e9f-203">Installing assemblies in the global assembly cache requires that they have strong names.</span></span> <span data-ttu-id="99e9f-204">強式名稱組件會使用有效的公開/私密金鑰組進行簽署。</span><span class="sxs-lookup"><span data-stu-id="99e9f-204">Strong-named assemblies are signed with a valid public/private key pair.</span></span> <span data-ttu-id="99e9f-205">它們包含執行階段用來判斷要用來滿足繫結要求之組件的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="99e9f-205">They contain version information that the runtime uses to determine which assembly to use to satisfy a binding request.</span></span> <span data-ttu-id="99e9f-206">如需強式名稱和版本控制的詳細資訊，請參閱[組件版本控制](../../../docs/framework/app-domains/assembly-versioning.md)。</span><span class="sxs-lookup"><span data-stu-id="99e9f-206">For more information about strong names and versioning, see [Assembly Versioning](../../../docs/framework/app-domains/assembly-versioning.md).</span></span> <span data-ttu-id="99e9f-207">如需強式名稱的詳細資訊，請參閱[強式名稱的組件](../../../docs/framework/app-domains/strong-named-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="99e9f-207">For more information about strong names, see [Strong-Named Assemblies](../../../docs/framework/app-domains/strong-named-assemblies.md).</span></span>

<span data-ttu-id="99e9f-208">當您開發應用程式時，可能無法存取最終公開/私密金鑰組。</span><span class="sxs-lookup"><span data-stu-id="99e9f-208">When you are developing an application, it is unlikely that you will have access to the final public/private key pair.</span></span> <span data-ttu-id="99e9f-209">若要在全域組件快取中安裝附屬組件，並確認它的運作正常，您可以使用稱為延遲簽署的技術。</span><span class="sxs-lookup"><span data-stu-id="99e9f-209">In order to install a satellite assembly in the global assembly cache and ensure that it works as expected, you can use a technique called delayed signing.</span></span> <span data-ttu-id="99e9f-210">當您延遲簽署組件時，請在建置時間於檔案中保留強式名稱簽章的空間。</span><span class="sxs-lookup"><span data-stu-id="99e9f-210">When you delay sign an assembly, at build time you reserve space in the file for the strong name signature.</span></span> <span data-ttu-id="99e9f-211">有最終公開/私密金鑰組可用時，會將實際簽署延遲到稍後。</span><span class="sxs-lookup"><span data-stu-id="99e9f-211">The actual signing is delayed until later, when the final public/private key pair is available.</span></span> <span data-ttu-id="99e9f-212">如需延遲簽署的詳細資訊，請參閱[延遲簽署組件](../../../docs/framework/app-domains/delay-sign-assembly.md)。</span><span class="sxs-lookup"><span data-stu-id="99e9f-212">For more information about delayed signing, see [Delay Signing an Assembly](../../../docs/framework/app-domains/delay-sign-assembly.md).</span></span>

### <a name="obtaining-the-public-key"></a><span data-ttu-id="99e9f-213">取得公開金鑰</span><span class="sxs-lookup"><span data-stu-id="99e9f-213">Obtaining the Public Key</span></span>

<span data-ttu-id="99e9f-214">若要延遲簽署組件，您必須具有公開金鑰的存取權。</span><span class="sxs-lookup"><span data-stu-id="99e9f-214">To delay sign an assembly, you must have access to the public key.</span></span> <span data-ttu-id="99e9f-215">您可以從公司中進行最後簽署的組織中取得實際公開金鑰，或使用[強式名稱工具 (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) 建立公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="99e9f-215">You can either obtain the real public key from the organization in your company that will do the eventual signing, or create a public key by using the [Strong Name Tool (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md).</span></span>

<span data-ttu-id="99e9f-216">下列 Sn.exe 命令會建立測試公開/私密金鑰組。</span><span class="sxs-lookup"><span data-stu-id="99e9f-216">The following Sn.exe command creates a test public/private key pair.</span></span> <span data-ttu-id="99e9f-217">**–k** 選項會指定 Sn.exe 應該建立新的金鑰組，並將它儲存在名為 TestKeyPair.snk 的檔案中。</span><span class="sxs-lookup"><span data-stu-id="99e9f-217">The **–k** option specifies that Sn.exe should create a new key pair and save it in a file named TestKeyPair.snk.</span></span>

```console
sn –k TestKeyPair.snk
```

<span data-ttu-id="99e9f-218">您可以從包含測試金鑰組的檔案中擷取公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="99e9f-218">You can extract the public key from the file that contains the test key pair.</span></span> <span data-ttu-id="99e9f-219">下列命令會從 TestKeyPair.snk 擷取公開金鑰，並將它儲存在 PublicKey.snk 中：</span><span class="sxs-lookup"><span data-stu-id="99e9f-219">The following command extracts the public key from TestKeyPair.snk and saves it in PublicKey.snk:</span></span>

```console
sn –p TestKeyPair.snk PublicKey.snk
```

### <a name="delay-signing-an-assembly"></a><span data-ttu-id="99e9f-220">延遲簽署組件</span><span class="sxs-lookup"><span data-stu-id="99e9f-220">Delay Signing an Assembly</span></span>

<span data-ttu-id="99e9f-221">在您取得或建立公開金鑰之後，請使用[組件連結器 (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) 編譯組件，並指定延遲簽署。</span><span class="sxs-lookup"><span data-stu-id="99e9f-221">After you obtain or create the public key, you use the [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) to compile the assembly and specify delayed signing.</span></span>

<span data-ttu-id="99e9f-222">下列 Al.exe 命令會從 strings.ja.resources 檔案建立應用程式 StringLibrary 的強式名稱附屬組件：</span><span class="sxs-lookup"><span data-stu-id="99e9f-222">The following Al.exe command creates a strong-named satellite assembly for the application StringLibrary from the strings.ja.resources file:</span></span>

```console
al -target:lib -embed:strings.ja.resources -culture:ja -out:StringLibrary.resources.dll -delay+ -keyfile:PublicKey.snk
```

<span data-ttu-id="99e9f-223"> 選項指定組件連結器應該延遲簽署組件。</span><span class="sxs-lookup"><span data-stu-id="99e9f-223">The **-delay+** option specifies that the Assembly Linker should delay sign the assembly.</span></span> <span data-ttu-id="99e9f-224">**-keyfile** 選項指定金鑰檔名稱，其中包含要用來延遲簽署組件的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="99e9f-224">The **-keyfile** option specifies the name of the key file that contains the public key to use to delay sign the assembly.</span></span>

### <a name="re-signing-an-assembly"></a><span data-ttu-id="99e9f-225">重新簽署組件</span><span class="sxs-lookup"><span data-stu-id="99e9f-225">Re-signing an Assembly</span></span>

<span data-ttu-id="99e9f-226">部署您的應用程式之前，必須使用實際金鑰組來重新簽署延遲簽署的附屬組件。</span><span class="sxs-lookup"><span data-stu-id="99e9f-226">Before you deploy your application, you must re-sign the delay signed satellite assembly with the real key pair.</span></span> <span data-ttu-id="99e9f-227">您可以使用 Sn.exe 完成這項動作。</span><span class="sxs-lookup"><span data-stu-id="99e9f-227">You can do this by using Sn.exe.</span></span>

<span data-ttu-id="99e9f-228">下列 Sn.exe 命令會使用 RealKeyPair.snk 檔案中所儲存的金鑰組來簽署 StringLibrary.resources.dll。</span><span class="sxs-lookup"><span data-stu-id="99e9f-228">The following Sn.exe command signs StringLibrary.resources.dll with the key pair stored in the file RealKeyPair.snk.</span></span> <span data-ttu-id="99e9f-229">**–R** 選項指定要重新簽署先前簽署的組件還是延遲簽署的組件。</span><span class="sxs-lookup"><span data-stu-id="99e9f-229">The **–R** option specifies that a previously signed or delay signed assembly is to be re-signed.</span></span>

```console
sn –R StringLibrary.resources.dll RealKeyPair.snk
```

### <a name="installing-a-satellite-assembly-in-the-global-assembly-cache"></a><span data-ttu-id="99e9f-230">在全域組件快取中安裝附屬組件</span><span class="sxs-lookup"><span data-stu-id="99e9f-230">Installing a Satellite Assembly in the Global Assembly Cache</span></span>

<span data-ttu-id="99e9f-231">執行階段在資源後援程序中搜尋資源時，會先尋找[全域組件快取](../../../docs/framework/app-domains/gac.md)</span><span class="sxs-lookup"><span data-stu-id="99e9f-231">When the runtime searches for resources in the resource fallback process, it looks in the [global assembly cache](../../../docs/framework/app-domains/gac.md) first.</span></span> <span data-ttu-id="99e9f-232">(如需詳細資訊，請參閱[封裝和部署資源](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)主題的＜資源後援程序＞一節)。只要附屬組件是使用強式名稱進行簽署，就可以使用[全域組件快取工具 (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) 將它安裝在全域組件快取中。</span><span class="sxs-lookup"><span data-stu-id="99e9f-232">(For more information, see the "Resource Fallback Process" section of the [Packaging and Deploying Resources](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md) topic.) As soon as a satellite assembly is signed with a strong name, it can be installed in the global assembly cache by using the [Global Assembly Cache Tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span></span>

<span data-ttu-id="99e9f-233">下列 Gacutil.exe 命令會在全域組件快取中安裝 StringLibrary.resources.dll：</span><span class="sxs-lookup"><span data-stu-id="99e9f-233">The following Gacutil.exe command installs StringLibrary.resources.dll in the global assembly cache:</span></span>

```console
gacutil -i:StringLibrary.resources.dll
```

<span data-ttu-id="99e9f-234">**/i** 選項指定 Gacutil.exe 應該將指定的組件安裝到全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="99e9f-234">The **/i** option specifies that Gacutil.exe should install the specified assembly into the global assembly cache.</span></span> <span data-ttu-id="99e9f-235">在快取中安裝附屬組件之後，其所含的資源可供設計成使用附屬組件的所有應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="99e9f-235">After the satellite assembly is installed in the cache, the resources it contains become available to all applications that are designed to use the satellite assembly.</span></span>

### <a name="resources-in-the-global-assembly-cache-an-example"></a><span data-ttu-id="99e9f-236">全域組件快取中的資源：範例</span><span class="sxs-lookup"><span data-stu-id="99e9f-236">Resources in the Global Assembly Cache: An Example</span></span>

<span data-ttu-id="99e9f-237">下列範例會使用 .NET Framework 類別庫中的方法，從資源檔擷取並傳回當地語系化的問候。</span><span class="sxs-lookup"><span data-stu-id="99e9f-237">The following example uses a method in a .NET Framework class library to extract and return a localized greeting from a resource file.</span></span> <span data-ttu-id="99e9f-238">程式庫和其資源都會註冊在全域組件快取中。</span><span class="sxs-lookup"><span data-stu-id="99e9f-238">The library and its resources are registered in the global assembly cache.</span></span> <span data-ttu-id="99e9f-239">此範例包括英文 (美國)、法文 (法國)、俄文 (俄國) 和英文文化特性的資源。</span><span class="sxs-lookup"><span data-stu-id="99e9f-239">The example includes resources for the English (United States), French (France), Russian (Russia), and English cultures.</span></span> <span data-ttu-id="99e9f-240">英文是預設文化特性；其資源儲存在主要組件中。</span><span class="sxs-lookup"><span data-stu-id="99e9f-240">English is the default culture; its resources are stored in the main assembly.</span></span> <span data-ttu-id="99e9f-241">此範例一開始會使用公開金鑰來延遲簽署程式庫和其附屬組件，然後使用公開/私密金鑰組來重新簽署它們。</span><span class="sxs-lookup"><span data-stu-id="99e9f-241">The example initially delay signs the library and its satellite assemblies with a public key, then re-signs them with a public/private key pair.</span></span> <span data-ttu-id="99e9f-242">若要建立範例，請執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="99e9f-242">To create the example, do the following:</span></span>

1. <span data-ttu-id="99e9f-243">如果您未使用 Visual Studio，請使用下列[強式名稱工具 (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) 命令來建立名為 ResKey.snk 的公開/私密金鑰組：</span><span class="sxs-lookup"><span data-stu-id="99e9f-243">If you are not using Visual Studio, use the following [Strong Name Tool (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) command to create a public/private key pair named ResKey.snk:</span></span>

    ```console
    sn –k ResKey.snk
    ```

    <span data-ttu-id="99e9f-244">如果您使用 Visual Studio，請使用專案 [屬性]  對話方塊的 [簽署]  索引標籤來產生金鑰檔。</span><span class="sxs-lookup"><span data-stu-id="99e9f-244">If you are using Visual Studio, use the **Signing** tab of the project **Properties** dialog box to generate the key file.</span></span>

2. <span data-ttu-id="99e9f-245">使用下列[強式名稱工具 (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) 命令來建立名為 PublicKey.snk 的公用金鑰檔案：</span><span class="sxs-lookup"><span data-stu-id="99e9f-245">Use the following [Strong Name Tool (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) command to create a public key file named PublicKey.snk:</span></span>

    ```console
    sn –p ResKey.snk PublicKey.snk
    ```

3. <span data-ttu-id="99e9f-246">建立名為 Strings.resx 的資源檔，以包含預設文化特性的資源。</span><span class="sxs-lookup"><span data-stu-id="99e9f-246">Create a resource file named Strings.resx to contain the resource for the default culture.</span></span> <span data-ttu-id="99e9f-247">將名為 `Greeting` 且其值為 "How do you do?" 的單一字串儲存</span><span class="sxs-lookup"><span data-stu-id="99e9f-247">Store a single string named `Greeting` whose value is "How do you do?"</span></span> <span data-ttu-id="99e9f-248">在該檔案中。</span><span class="sxs-lookup"><span data-stu-id="99e9f-248">in that file.</span></span>

4. <span data-ttu-id="99e9f-249">若要指出 "en" 是應用程式的預設文化特性，請將下列 <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> 屬性新增至應用程式的 AssemblyInfo 檔案或將編譯為應用程式主要組件的主要原始程式碼檔案：</span><span class="sxs-lookup"><span data-stu-id="99e9f-249">To indicate that "en" is the application's default culture, add the following <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> attribute to the application's AssemblyInfo file or to the main source code file that will be compiled into the application's main assembly:</span></span>

    [!code-csharp[Conceptual.Resources.Satellites#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/stringlibrary.cs#2)]
    [!code-vb[Conceptual.Resources.Satellites#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/stringlibrary.vb#2)]

5. <span data-ttu-id="99e9f-250">將其他文化特性 (en-US、fr-FR 和 ru-RU 文化特性) 的支援新增至應用程式，如下所示：</span><span class="sxs-lookup"><span data-stu-id="99e9f-250">Add support for additional cultures (the en-US, fr-FR, and ru-RU cultures) to the application as follows:</span></span>

    - <span data-ttu-id="99e9f-251">若要支援 "en-US" 或英文 (美國) 文化特性，請建立名為 Strings.en-US.resx 或 Strings.en-US.txt 的資源檔，並在其中儲存名為 `Greeting` 且其值為 "Hello!" 的單一字串。</span><span class="sxs-lookup"><span data-stu-id="99e9f-251">To support the "en-US" or English (United States) culture, create a resource file named Strings.en-US.resx or Strings.en-US.txt, and store in it a single string named `Greeting` whose value is "Hello!".</span></span>

    - <span data-ttu-id="99e9f-252">若要支援 "fr-FR" 或法文 (法國) 文化特性，請建立名為 Strings.fr-FR.resx 或 Strings.fr-FR.txt 的資源檔，並在其中儲存名為 `Greeting` 且其值為 "Bon jour!" 的單一字串。</span><span class="sxs-lookup"><span data-stu-id="99e9f-252">To support the "fr-FR" or French (France) culture, create a resource file named Strings.fr-FR.resx or Strings.fr-FR.txt and store in it a single string named `Greeting` whose value is "Bon jour!"</span></span>

    - <span data-ttu-id="99e9f-253">若要支援 "ru-RU" 或俄文 (俄國) 文化特性，請建立名為 Strings.ru-RU.resx 或 Strings.ru-RU.txt 的資源檔，並在其中儲存名為 `Greeting` 且其值為 "Привет!" 的單一字串。</span><span class="sxs-lookup"><span data-stu-id="99e9f-253">To support the "ru-RU" or Russian (Russia) culture, create a resource file named Strings.ru-RU.resx or Strings.ru-RU.txt and store in it a single string named `Greeting` whose value is "Привет!"</span></span>

6. <span data-ttu-id="99e9f-254">使用 [Resgen.exe](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)，將每一個文字或 XML 資源檔編譯成二進位 .resources 檔案。</span><span class="sxs-lookup"><span data-stu-id="99e9f-254">Use [Resgen.exe](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) to compile each text or XML resource file to a binary .resources file.</span></span> <span data-ttu-id="99e9f-255">輸出是根檔案名稱與 .resx 或 .txt 檔案相同的一組檔案，但副檔名為 .resources。</span><span class="sxs-lookup"><span data-stu-id="99e9f-255">The output is a set of files that have the same root file name as the .resx or .txt files, but a .resources extension.</span></span> <span data-ttu-id="99e9f-256">如果您使用 Visual Studio 建立範例，則會自動處理編譯程序。</span><span class="sxs-lookup"><span data-stu-id="99e9f-256">If you create the example with Visual Studio, the compilation process is handled automatically.</span></span> <span data-ttu-id="99e9f-257">如果您不要使用 Visual Studio，請執行下列命令將 .resx 檔案編譯為 .resources 檔案：</span><span class="sxs-lookup"><span data-stu-id="99e9f-257">If you aren't using Visual Studio, run the following command to compile the .resx files into .resources files:</span></span>

    ```console
    resgen filename
    ```

    <span data-ttu-id="99e9f-258">其中 <檔案名稱>  是 .resx 或文字檔的選擇性路徑、檔案名稱和副檔名。</span><span class="sxs-lookup"><span data-stu-id="99e9f-258">where *filename* is the optional path, file name, and extension of the .resx or text file.</span></span>

7. <span data-ttu-id="99e9f-259">將 StringLibrary.vb 或 StringLibrary.cs 的下列原始程式碼以及預設文化特性的資源編譯為名為 StringLibrary.dll 的延遲簽署程式庫組件：</span><span class="sxs-lookup"><span data-stu-id="99e9f-259">Compile the following source code for StringLibrary.vb or StringLibrary.cs along with the resources for the default culture into a delay signed library assembly named StringLibrary.dll:</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="99e9f-260">如果您使用命令列而非 Visual Studio 來建立範例，則應該將 <xref:System.Resources.ResourceManager> 類別建構函式的呼叫修改為 `ResourceManager rm = new ResourceManager("Strings",` `typeof(Example).Assembly);`。</span><span class="sxs-lookup"><span data-stu-id="99e9f-260">If you are using the command line rather than Visual Studio to create the example, you should modify the call to the <xref:System.Resources.ResourceManager> class constructor to `ResourceManager rm = new ResourceManager("Strings",` `typeof(Example).Assembly);`.</span></span>

    [!code-csharp[Conceptual.Resources.Satellites#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/stringlibrary.cs#1)]
    [!code-vb[Conceptual.Resources.Satellites#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/stringlibrary.vb#1)]

    <span data-ttu-id="99e9f-261">C# 編譯器的命令是：</span><span class="sxs-lookup"><span data-stu-id="99e9f-261">The command for the C# compiler is:</span></span>

    ```console
    csc -t:library -resource:Strings.resources -delaysign+ -keyfile:publickey.snk StringLibrary.cs
    ```

    <span data-ttu-id="99e9f-262">對應的 Visual Basic 編譯器命令為：</span><span class="sxs-lookup"><span data-stu-id="99e9f-262">The corresponding Visual Basic compiler command is:</span></span>

    ```console
    vbc -t:library -resource:Strings.resources -delaysign+ -keyfile:publickey.snk StringLibrary.vb
    ```

8. <span data-ttu-id="99e9f-263">在應用程式所支援之每個當地語系化文化特性的主要應用程式目錄中，建立子目錄。</span><span class="sxs-lookup"><span data-stu-id="99e9f-263">Create a subdirectory in the main application directory for each localized culture supported by the application.</span></span> <span data-ttu-id="99e9f-264">您應該建立 en-US、fr-FR 和 ru-RU 子目錄。</span><span class="sxs-lookup"><span data-stu-id="99e9f-264">You should create an en-US, an fr-FR, and an ru-RU subdirectory.</span></span> <span data-ttu-id="99e9f-265">Visual Studio 會在編譯程序時自動建立這些子目錄。</span><span class="sxs-lookup"><span data-stu-id="99e9f-265">Visual Studio creates these subdirectories automatically as part of the compilation process.</span></span> <span data-ttu-id="99e9f-266">因為所有附屬組件都有相同的檔案名稱，所以使用子目錄來儲存個別文化特性特定附屬組件，直到使用公開/私密金鑰組簽署它們為止。</span><span class="sxs-lookup"><span data-stu-id="99e9f-266">Because all satellite assemblies have the same file name, the subdirectories are used to store individual culture-specific satellite assemblies until they are signed with a public/private key pair.</span></span>

9. <span data-ttu-id="99e9f-267">將個別文化特性特定 .resources 檔案內嵌到延遲簽署的附屬組件，並將它們儲存到適當的目錄。</span><span class="sxs-lookup"><span data-stu-id="99e9f-267">Embed the individual culture-specific .resources files into delay signed satellite assemblies and save them to the appropriate directory.</span></span> <span data-ttu-id="99e9f-268">針對每個 .resources 檔案執行這項作業的命令為：</span><span class="sxs-lookup"><span data-stu-id="99e9f-268">The command to do this for each .resources file is:</span></span>

    ```console
    al -target:lib -embed:Strings.culture.resources -culture:culture -out:culture\StringLibrary.resources.dll -delay+ -keyfile:publickey.snk
    ```

    <span data-ttu-id="99e9f-269">其中 *culture* 是文化特性的名稱。</span><span class="sxs-lookup"><span data-stu-id="99e9f-269">where *culture* is the name of a culture.</span></span> <span data-ttu-id="99e9f-270">在此範例中，文化特性名稱是 en-US、fr-FR 和 ru-RU。</span><span class="sxs-lookup"><span data-stu-id="99e9f-270">In this example, the culture names are en-US, fr-FR, and ru-RU.</span></span>

10. <span data-ttu-id="99e9f-271">使用[強式名稱工具 (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) 來重新簽署 StringLibrary.dll，如下所示：</span><span class="sxs-lookup"><span data-stu-id="99e9f-271">Re-sign StringLibrary.dll by using the [Strong Name Tool (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) as follows:</span></span>

    ```console
    sn –R StringLibrary.dll RealKeyPair.snk
    ```

11. <span data-ttu-id="99e9f-272">重新簽署個別附屬組件。</span><span class="sxs-lookup"><span data-stu-id="99e9f-272">Re-sign the individual satellite assemblies.</span></span> <span data-ttu-id="99e9f-273">若要這樣做，請使用每個附屬組件的[強式名稱工具 (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)，如下所示：</span><span class="sxs-lookup"><span data-stu-id="99e9f-273">To do this, use the [Strong Name Tool (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) as follows for each satellite assembly:</span></span>

    ```console
    sn –R StringLibrary.resources.dll RealKeyPair.snk
    ```

12. <span data-ttu-id="99e9f-274">使用下列命令，在全域組件快取中註冊 StringLibrary.dll 和其每個附屬組件：</span><span class="sxs-lookup"><span data-stu-id="99e9f-274">Register StringLibrary.dll and each of its satellite assemblies in the global assembly cache by using the following command:</span></span>

    ```console
    gacutil -i filename
    ```

    <span data-ttu-id="99e9f-275">其中 <檔案名稱>  是要註冊之檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="99e9f-275">where *filename* is the name of the file to register.</span></span>

13. <span data-ttu-id="99e9f-276">如果您使用 Visual Studio，請建立名為 `Example` 的新**主控台應用程式**專案，並在其中新增 StringLibrary.dll 參考和下列原始程式碼，然後進行編譯。</span><span class="sxs-lookup"><span data-stu-id="99e9f-276">If you are using Visual Studio, create a new **Console Application** project named `Example`, add a reference to StringLibrary.dll and the following source code to it, and compile.</span></span>

    [!code-csharp[Conceptual.Resources.Satellites#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/example.cs#3)]
    [!code-vb[Conceptual.Resources.Satellites#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/example.vb#3)]

    <span data-ttu-id="99e9f-277">若要從命令列進行編譯，請針對 C# 編譯器使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="99e9f-277">To compile from the command line, use the following command for the C# compiler:</span></span>

    ```console
    csc Example.cs -r:StringLibrary.dll
    ```

    <span data-ttu-id="99e9f-278">Visual Basic 編譯器的命令列為：</span><span class="sxs-lookup"><span data-stu-id="99e9f-278">The command line for the Visual Basic compiler is:</span></span>

    ```console
    vbc Example.vb -r:StringLibrary.dll
    ```

14. <span data-ttu-id="99e9f-279">執行 Example.exe。</span><span class="sxs-lookup"><span data-stu-id="99e9f-279">Run Example.exe.</span></span>

## <a name="see-also"></a><span data-ttu-id="99e9f-280">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99e9f-280">See also</span></span>

- [<span data-ttu-id="99e9f-281">封裝和部署資源</span><span class="sxs-lookup"><span data-stu-id="99e9f-281">Packaging and Deploying Resources</span></span>](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [<span data-ttu-id="99e9f-282">延遲簽署組件</span><span class="sxs-lookup"><span data-stu-id="99e9f-282">Delay Signing an Assembly</span></span>](../../../docs/framework/app-domains/delay-sign-assembly.md)
- [<span data-ttu-id="99e9f-283">Al.exe (組件連結器)</span><span class="sxs-lookup"><span data-stu-id="99e9f-283">Al.exe (Assembly Linker)</span></span>](../../../docs/framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="99e9f-284">Sn.exe (強式名稱工具)</span><span class="sxs-lookup"><span data-stu-id="99e9f-284">Sn.exe (Strong Name Tool)</span></span>](../../../docs/framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="99e9f-285">Gacutil.exe (全域組件快取工具)</span><span class="sxs-lookup"><span data-stu-id="99e9f-285">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
- [<span data-ttu-id="99e9f-286">桌面應用程式中的資源</span><span class="sxs-lookup"><span data-stu-id="99e9f-286">Resources in Desktop Apps</span></span>](../../../docs/framework/resources/index.md)
