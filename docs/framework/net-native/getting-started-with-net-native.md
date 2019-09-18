---
title: .NET Native 使用者入門
ms.date: 03/30/2017
ms.assetid: fc9e04e8-2d05-4870-8cd6-5bd276814afc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: de887f73a5cc3968dda7e0e4dd14493883485d2b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049742"
---
# <a name="getting-started-with-net-native"></a><span data-ttu-id="4edb2-102">.NET Native 使用者入門</span><span class="sxs-lookup"><span data-stu-id="4edb2-102">Getting Started with .NET Native</span></span>

<span data-ttu-id="4edb2-103">不論是為了 Windows 10 撰寫新的 Windows 應用程式，或是移轉現有的 Windows 市集應用程式，都可遵循一組相同的程序進行。</span><span class="sxs-lookup"><span data-stu-id="4edb2-103">Whether you are writing a new Windows app for Windows 10 or you are migrating an existing Windows Store app, you can follow the same set of procedures.</span></span> <span data-ttu-id="4edb2-104">若要建立 .NET Native 應用程式，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="4edb2-104">To create a .NET Native app, follow these steps:</span></span>

1. <span data-ttu-id="4edb2-105">[開發以 Windows 10 為目標的通用 Windows 平台 (UWP) 應用程式](#Step1)，並測試應用程式的偵錯組建，以確保運作正常。</span><span class="sxs-lookup"><span data-stu-id="4edb2-105">[Develop a Universal Windows Platform (UWP) app that targets Windows 10](#Step1), and test the debug builds of your app to ensure that it works properly.</span></span>

2. <span data-ttu-id="4edb2-106">[處理其他反映和序列化使用](#Step2)。</span><span class="sxs-lookup"><span data-stu-id="4edb2-106">[Handle additional reflection and serialization usage](#Step2).</span></span>

3. <span data-ttu-id="4edb2-107">[部署並測試應用程式的發行組建](#Step3)。</span><span class="sxs-lookup"><span data-stu-id="4edb2-107">[Deploy and test the release builds of your app](#Step3).</span></span>

4. <span data-ttu-id="4edb2-108">[手動解決遺漏中繼資料的問題](#Step4)，然後重複 [步驟 3](#Step3) 直到所有問題解決為止。</span><span class="sxs-lookup"><span data-stu-id="4edb2-108">[Manually resolve missing metadata](#Step4), and repeat [step 3](#Step3) until all issues are resolved.</span></span>

> [!NOTE]
> <span data-ttu-id="4edb2-109">如果您要將現有的 Windows Store 應用程式遷移至 .NET Native，請務必檢查將[您的 Windows Store 應用程式遷移至 .NET Native](migrating-your-windows-store-app-to-net-native.md)。</span><span class="sxs-lookup"><span data-stu-id="4edb2-109">If you are migrating an existing Windows Store app to .NET Native, be sure to review [Migrating Your Windows Store App to .NET Native](migrating-your-windows-store-app-to-net-native.md).</span></span>

<a name="Step1"></a>

## <a name="step-1-develop-and-test-debug-builds-of-your-uwp-app"></a><span data-ttu-id="4edb2-110">步驟 1：開發和測試 UWP 應用程式的 debug 組建</span><span class="sxs-lookup"><span data-stu-id="4edb2-110">Step 1: Develop and test debug builds of your UWP app</span></span>

<span data-ttu-id="4edb2-111">不論您要開發新的應用程式，或移轉現有的應用程式，都會遵循與所有 Windows 應用程式相同的程序。</span><span class="sxs-lookup"><span data-stu-id="4edb2-111">Whether you are developing a new app or migrating an existing one, you follow the same process as for any Windows app.</span></span>

1. <span data-ttu-id="4edb2-112">使用適用於 Visual C# 或 Visual Basic 的通用 Windows 應用程式範本，在 Visual Studio 中建立新的 UWP 專案。</span><span class="sxs-lookup"><span data-stu-id="4edb2-112">Create a new UWP project in Visual Studio by using the Universal Windows app template for Visual C# or Visual Basic.</span></span> <span data-ttu-id="4edb2-113">根據預設，所有 UWP 應用程式都會以 CoreCLR 為目標，而其發行組建則使用 .NET Native 工具鏈進行編譯。</span><span class="sxs-lookup"><span data-stu-id="4edb2-113">By default, all UWP applications target the CoreCLR and their release builds are compiled by using the .NET Native tool chain.</span></span>

2. <span data-ttu-id="4edb2-114">請注意，使用 .NET Native 工具鏈編譯 UWP 應用程式專案與不使用此工具進行編譯之間有一些已知的相容性問題。</span><span class="sxs-lookup"><span data-stu-id="4edb2-114">Note that there are some known compatibility issues between compiling UWP app projects with the .NET Native tool chain and without it.</span></span> <span data-ttu-id="4edb2-115">如需詳細資訊，請參閱 [移轉指南](migrating-your-windows-store-app-to-net-native.md) 。</span><span class="sxs-lookup"><span data-stu-id="4edb2-115">Refer to the [migration guide](migrating-your-windows-store-app-to-net-native.md) for more information.</span></span>

<span data-ttu-id="4edb2-116">您現在可以針對C#在本機系統上執行的 .NET Native 介面區（或在模擬器中），撰寫或 Visual Basic 程式碼。</span><span class="sxs-lookup"><span data-stu-id="4edb2-116">You can now write C# or Visual Basic code against the .NET Native surface area that runs on the local system (or in the simulator).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4edb2-117">當您開發應用程式時，請記下在程式碼中使用的任何序列化或反映。</span><span class="sxs-lookup"><span data-stu-id="4edb2-117">As you develop your app, note any use of serialization or reflection in your code.</span></span>

<span data-ttu-id="4edb2-118">根據預設，會以 JIT 編譯的方式建立偵錯工具，以啟用快速 F5 部署，而發行組建則是使用 .NET Native 預先編譯技術來編譯。</span><span class="sxs-lookup"><span data-stu-id="4edb2-118">By default, debug builds are JIT-compiled to enable rapid F5 deployment, while release builds are compiled by using the .NET Native pre-compilation technology.</span></span> <span data-ttu-id="4edb2-119">這表示您應該建置並測試應用程式的偵錯組建以確保運作正常，再使用 .NET Native 工具鏈進行編譯。</span><span class="sxs-lookup"><span data-stu-id="4edb2-119">This means you should build and test the debug builds of your app to ensure that they work normally before compiling them with the .NET Native tool chain.</span></span>

<a name="Step2"></a>

## <a name="step-2-handle-additional-reflection-and-serialization-usage"></a><span data-ttu-id="4edb2-120">步驟 2：處理其他反映和序列化使用方式</span><span class="sxs-lookup"><span data-stu-id="4edb2-120">Step 2: Handle additional reflection and serialization usage</span></span>

<span data-ttu-id="4edb2-121">當您建立專案時會自動將執行階段指示詞檔 Default.rd.xml 加入您的專案。</span><span class="sxs-lookup"><span data-stu-id="4edb2-121">A runtime directives file, Default.rd.xml, is automatically added to your project when you create it.</span></span> <span data-ttu-id="4edb2-122">如果您以 C# 進行開發，它位於您專案的 [屬性] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="4edb2-122">If you develop in C#, it is found in your project's **Properties** folder.</span></span> <span data-ttu-id="4edb2-123">如果您以 Visual Basic 進行開發，它位於您專案的 [我的專案] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="4edb2-123">If you develop in Visual Basic, it is found in your project's **My Project** folder.</span></span>

> [!NOTE]
> <span data-ttu-id="4edb2-124">如需 .NET 原生編譯程序的概觀 (其提供需要執行階段指示詞檔案的背景資訊)，請參閱 [.NET 原生和編譯](net-native-and-compilation.md)。</span><span class="sxs-lookup"><span data-stu-id="4edb2-124">For an overview of the .NET Native compilation process that provides background on why a runtime directives file is needed, see [.NET Native and Compilation](net-native-and-compilation.md).</span></span>

<span data-ttu-id="4edb2-125">執行階段指示詞檔案會用來定義您的應用程式在執行階段所需的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="4edb2-125">The runtime directives file is used to define the metadata that your app needs at run time.</span></span> <span data-ttu-id="4edb2-126">在某些情況下，檔案的預設版本應已足夠。</span><span class="sxs-lookup"><span data-stu-id="4edb2-126">In some cases, the default version of the file may be adequate.</span></span> <span data-ttu-id="4edb2-127">不過，某些相依於序列化或反映的程式碼可能需要執行階段指示詞檔案中的其他項目。</span><span class="sxs-lookup"><span data-stu-id="4edb2-127">However, some code that relies on serialization or reflection may require additional entries in the runtime directives file.</span></span>

<span data-ttu-id="4edb2-128">**序列化**</span><span class="sxs-lookup"><span data-stu-id="4edb2-128">**Serialization**</span></span>

<span data-ttu-id="4edb2-129">序列化程式可分為兩種類別，這兩種類別都需要執行階段指示詞檔案中的其他項目：</span><span class="sxs-lookup"><span data-stu-id="4edb2-129">There are two categories of serializers, and both may require additional entries in the runtime directives file:</span></span>

- <span data-ttu-id="4edb2-130">非反映型序列化程式。</span><span class="sxs-lookup"><span data-stu-id="4edb2-130">Non-reflection based serializers.</span></span> <span data-ttu-id="4edb2-131">.NET Framework 類別庫中不依賴反映的序列化程式，例如 <xref:System.Runtime.Serialization.DataContractSerializer>、 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>和 <xref:System.Xml.Serialization.XmlSerializer> 類別。</span><span class="sxs-lookup"><span data-stu-id="4edb2-131">The serializers found in the .NET Framework class library, such as the <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer> classes, do not rely on reflection.</span></span> <span data-ttu-id="4edb2-132">不過，這些序列化程式需要依據所要序列化或還原序列化的物件來產生程式碼。</span><span class="sxs-lookup"><span data-stu-id="4edb2-132">However, they do require that code be generated based on the object to be serialized or deserialized.</span></span>  <span data-ttu-id="4edb2-133">如需詳細資訊，請參閱 [Serialization and Metadata](serialization-and-metadata.md)中的＜Microsoft 序列化程式＞一節。</span><span class="sxs-lookup"><span data-stu-id="4edb2-133">For more information, see the "Microsoft Serializers" section in [Serialization and Metadata](serialization-and-metadata.md).</span></span>

- <span data-ttu-id="4edb2-134">協力廠商序列化程式。</span><span class="sxs-lookup"><span data-stu-id="4edb2-134">Third-party serializers.</span></span> <span data-ttu-id="4edb2-135">協力廠商序列化程式庫是最常見的 Newtonsoft JSON 序列化程式，通常是以反映為基礎，而且需要在. .xml \*檔案中的專案，才能支持對象序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="4edb2-135">Third-party serialization libraries, the most common of which is the Newtonsoft JSON serializer, are generally reflection-based and require entries in the \*.rd.xml file to support object serialization and deserialization.</span></span> <span data-ttu-id="4edb2-136">如需詳細資訊，請參閱 [Serialization and Metadata](serialization-and-metadata.md)中的＜協力廠商序列化程式＞一節。</span><span class="sxs-lookup"><span data-stu-id="4edb2-136">For more information, see the "Third-Party Serializers" section in [Serialization and Metadata](serialization-and-metadata.md).</span></span>

<span data-ttu-id="4edb2-137">**依賴反映的方法**</span><span class="sxs-lookup"><span data-stu-id="4edb2-137">**Methods that rely on reflection**</span></span>

<span data-ttu-id="4edb2-138">在某些情況下，很難察覺程式碼中是否有使用反映。</span><span class="sxs-lookup"><span data-stu-id="4edb2-138">In some cases, the use of reflection in code is not obvious.</span></span> <span data-ttu-id="4edb2-139">某些常見的 API 或程式設計模式不是反映 API 的一部分，但依賴反映才能順利執行。</span><span class="sxs-lookup"><span data-stu-id="4edb2-139">Some common APIs or programming patterns aren't considered part of the reflection API but rely on reflection to execute successfully.</span></span> <span data-ttu-id="4edb2-140">其中包括下列類型具現化和方法建構方法：</span><span class="sxs-lookup"><span data-stu-id="4edb2-140">This includes the following type instantiation and method construction methods:</span></span>

- <span data-ttu-id="4edb2-141"><xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> 方法</span><span class="sxs-lookup"><span data-stu-id="4edb2-141">The <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method</span></span>

- <span data-ttu-id="4edb2-142"><xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> 和 <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> 方法</span><span class="sxs-lookup"><span data-stu-id="4edb2-142">The <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> and <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> methods</span></span>

- <span data-ttu-id="4edb2-143"><xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> 方法</span><span class="sxs-lookup"><span data-stu-id="4edb2-143">The <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="4edb2-144">如需詳細資訊，請參閱 [APIs That Rely on Reflection](apis-that-rely-on-reflection.md)。</span><span class="sxs-lookup"><span data-stu-id="4edb2-144">For more information, see [APIs That Rely on Reflection](apis-that-rely-on-reflection.md).</span></span>

> [!NOTE]
> <span data-ttu-id="4edb2-145">執行階段指示詞檔案中使用的類型名稱必須是完整名稱。</span><span class="sxs-lookup"><span data-stu-id="4edb2-145">Type names used in runtime directives files must be fully qualified.</span></span> <span data-ttu-id="4edb2-146">例如，檔案必須指定 "System.String"，而不是 "String"。</span><span class="sxs-lookup"><span data-stu-id="4edb2-146">For example, the file must specify "System.String" instead of "String".</span></span>

<a name="Step3"></a>

## <a name="step-3-deploy-and-test-the-release-builds-of-your-app"></a><span data-ttu-id="4edb2-147">步驟 3：部署和測試應用程式的發行組建</span><span class="sxs-lookup"><span data-stu-id="4edb2-147">Step 3: Deploy and test the release builds of your app</span></span>

<span data-ttu-id="4edb2-148">更新執行階段指示詞檔案之後，您可以重建並部署應用程式的發行組建。</span><span class="sxs-lookup"><span data-stu-id="4edb2-148">After you’ve updated the runtime directives file, you can rebuild and deploy release builds of your app.</span></span> <span data-ttu-id="4edb2-149">.NET 原生二進位碼檔案會放在 [建置輸出路徑] 文字方塊 (位於專案之 [屬性] 對話方塊的 [編譯] 索引標籤中) 所指定之目錄的 ILC.out 子目錄中。不在這個資料夾中的二進位碼檔案尚未使用 .NET 原生編譯。</span><span class="sxs-lookup"><span data-stu-id="4edb2-149">.NET Native binaries are placed in the ILC.out subdirectory of the directory specified in the **Build output path** text box of  the project's **Properties** dialog box, **Compile** tab. Binaries that aren't in this folder haven't been compiled with .NET Native.</span></span> <span data-ttu-id="4edb2-150">請在其目標平台上完整測試您的應用程式，並測試所有情況，包括失敗情況。</span><span class="sxs-lookup"><span data-stu-id="4edb2-150">Test your app thoroughly, and test all scenarios, including failure scenarios, on each of its target platforms.</span></span>

<span data-ttu-id="4edb2-151">如果您的應用程式無法正常運作（特別是在執行時間擲回[MissingMetadataException](missingmetadataexception-class-net-native.md)或[MissingInteropDataException](missinginteropdataexception-class-net-native.md)例外狀況的情況下），請遵循[下一節步驟4：手動解決遺漏的](#Step4)中繼資料。</span><span class="sxs-lookup"><span data-stu-id="4edb2-151">If your app doesn’t work properly (particularly in cases where it throws [MissingMetadataException](missingmetadataexception-class-net-native.md) or [MissingInteropDataException](missinginteropdataexception-class-net-native.md) exceptions at run time), follow the instructions in the next section, [Step 4: Manually resolve missing metadata](#Step4).</span></span> <span data-ttu-id="4edb2-152">啟用第一個可能發生的例外狀況可協助您尋找這些錯誤。</span><span class="sxs-lookup"><span data-stu-id="4edb2-152">Enabling first-chance exceptions may help you find these bugs.</span></span>

<span data-ttu-id="4edb2-153">當您已測試並調試應用程式的 debug 組建，並確信您已消除[MissingMetadataException](missingmetadataexception-class-net-native.md)和[MissingInteropDataException](missinginteropdataexception-class-net-native.md)例外狀況時，您應該以優化的 .NET Native 應用程式來測試您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="4edb2-153">When you’ve tested and debugged the debug builds of your app and you’re confident that you’ve eliminated the [MissingMetadataException](missingmetadataexception-class-net-native.md) and [MissingInteropDataException](missinginteropdataexception-class-net-native.md) exceptions, you should test your app as an optimized .NET Native app.</span></span> <span data-ttu-id="4edb2-154">若要執行這項操作，請將使用中的專案組態從 [偵錯] 變更為 [發行]。</span><span class="sxs-lookup"><span data-stu-id="4edb2-154">To do this, change your active project configuration from **Debug** to **Release**.</span></span>

<a name="Step4"></a>

## <a name="step-4-manually-resolve-missing-metadata"></a><span data-ttu-id="4edb2-155">步驟 4：手動解決遺失的中繼資料</span><span class="sxs-lookup"><span data-stu-id="4edb2-155">Step 4: Manually resolve missing metadata</span></span>

<span data-ttu-id="4edb2-156">您在桌面上不會遇到的 .NET Native 最常見的失敗，就是執行時間[MissingMetadataException](missingmetadataexception-class-net-native.md)、 [MissingInteropDataException](missinginteropdataexception-class-net-native.md)或[MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md)例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4edb2-156">The most common failure you'll encounter with .NET Native that you don't encounter on the desktop is a runtime [MissingMetadataException](missingmetadataexception-class-net-native.md), [MissingInteropDataException](missinginteropdataexception-class-net-native.md), or [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exception.</span></span> <span data-ttu-id="4edb2-157">在某些情況下，缺少中繼資料會發生未預期的行為，甚至導致應用程式失敗。</span><span class="sxs-lookup"><span data-stu-id="4edb2-157">In some cases, the absence of metadata can manifest itself in unpredictable behavior or even in app failures.</span></span> <span data-ttu-id="4edb2-158">本節討論如何將指示詞加入至執行階段指示詞檔案，來偵錯及解決這些例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4edb2-158">This section discusses how you can debug and resolve these exceptions by adding directives to the runtime directives file.</span></span> <span data-ttu-id="4edb2-159">如需執行階段指示詞格式的資訊，請參閱[執行階段指示詞 (rd.xml) 組態檔參考](runtime-directives-rd-xml-configuration-file-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="4edb2-159">For information about the format of runtime directives, see [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md).</span></span> <span data-ttu-id="4edb2-160">新增執行階段指示詞之後，您應該重新[部署和測試應用程式](#Step3)，並解決任何新的 [MissingMetadataException](missingmetadataexception-class-net-native.md)、[MissingInteropDataException](missinginteropdataexception-class-net-native.md) 和 [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) 例外狀況，直到未遇到其他任何例外狀況為止。</span><span class="sxs-lookup"><span data-stu-id="4edb2-160">After you’ve added runtime directives, you should [deploy and test your app](#Step3) again and resolve any new [MissingMetadataException](missingmetadataexception-class-net-native.md), [MissingInteropDataException](missinginteropdataexception-class-net-native.md), and  [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exceptions until you encounter no more exceptions.</span></span>

> [!TIP]
> <span data-ttu-id="4edb2-161">在較高層級指定執行階段指示詞，可讓應用程式彈性地回應程式碼變更。</span><span class="sxs-lookup"><span data-stu-id="4edb2-161">Specify the runtime directives at a high level to enable your app to be resilient to code changes.</span></span>  <span data-ttu-id="4edb2-162">建議在命名空間和類型層級加入執行階段指示詞，而不是在成員層級加入執行階段指示詞。</span><span class="sxs-lookup"><span data-stu-id="4edb2-162">We recommend adding runtime directives at the namespace and type levels rather than the member level.</span></span> <span data-ttu-id="4edb2-163">請注意，您可能需要在彈性與較大二進位檔案需要更長編譯時間之間進行取捨。</span><span class="sxs-lookup"><span data-stu-id="4edb2-163">Note that there may be a tradeoff between resiliency and larger binaries with longer compile times.</span></span>

<span data-ttu-id="4edb2-164">解決遺漏中繼資料的例外狀況時，請考慮下列問題：</span><span class="sxs-lookup"><span data-stu-id="4edb2-164">When addressing a missing metadata exception, consider these issues:</span></span>

- <span data-ttu-id="4edb2-165">發生例外狀況之前，應用程式正嘗試執行哪項作業？</span><span class="sxs-lookup"><span data-stu-id="4edb2-165">What was the app trying to do before the exception?</span></span>

  - <span data-ttu-id="4edb2-166">例如，應用程式正在執行資料繫結、序列化或還原序列化資料，還是直接使用反映 API？</span><span class="sxs-lookup"><span data-stu-id="4edb2-166">For example, was it data binding, serializing or deserializing data, or directly using the reflection API?</span></span>

- <span data-ttu-id="4edb2-167">這是獨立案例，還是您認為其他類型也會遇到相同問題？</span><span class="sxs-lookup"><span data-stu-id="4edb2-167">Is this an isolated case, or do you believe you'll encounter the same issue for other types?</span></span>

  - <span data-ttu-id="4edb2-168">例如，當序列化應用程式物件模型中的類型時，擲回 [MissingMetadataException](missingmetadataexception-class-net-native.md) 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4edb2-168">For example, a [MissingMetadataException](missingmetadataexception-class-net-native.md) exception is thrown when serializing a type in the app’s object model.</span></span>  <span data-ttu-id="4edb2-169">如果您知道即將序列化其他類型，您可以同時針對這些類型 (視程式碼組織程度而定也可能針對其包含命名空間) 加入執行階段指示詞。</span><span class="sxs-lookup"><span data-stu-id="4edb2-169">If you know other types that will be serialized, you can add runtime directives for those types (or for their containing namespaces, depending on how well the code is organized) at the same time.</span></span>

- <span data-ttu-id="4edb2-170">是否可以重寫程式碼使其不使用反映？</span><span class="sxs-lookup"><span data-stu-id="4edb2-170">Can you rewrite the code so it doesn’t use reflection?</span></span>

  - <span data-ttu-id="4edb2-171">例如，當您知道預期類型時，程式碼是否使用 `dynamic` 關鍵字？</span><span class="sxs-lookup"><span data-stu-id="4edb2-171">For example, does the code use the `dynamic` keyword when you know what type to expect?</span></span>

  - <span data-ttu-id="4edb2-172">程式碼是否在有一些更佳的替代方案時，呼叫相依於反映的方法？</span><span class="sxs-lookup"><span data-stu-id="4edb2-172">Does the code call a method that depends on reflection when some better alternative is available?</span></span>

> [!NOTE]
> <span data-ttu-id="4edb2-173">如需處理源自于桌面應用程式和 .NET Native 中的反映和中繼資料可用性差異之問題的詳細資訊，請參閱[依賴反映的 api](apis-that-rely-on-reflection.md)。</span><span class="sxs-lookup"><span data-stu-id="4edb2-173">For additional information about handling problems that stem from differences in reflection and the availability of metadata in desktop apps and .NET Native, see [APIs That Rely on Reflection](apis-that-rely-on-reflection.md).</span></span>

<span data-ttu-id="4edb2-174">如需處理測試應用程式時所發生之例外狀況和其他問題的一些特定範例，請參閱：</span><span class="sxs-lookup"><span data-stu-id="4edb2-174">For some specific examples of handling exceptions and other issues that occur when testing your app, see:</span></span>

- [<span data-ttu-id="4edb2-175">範例：在系結資料時處理例外狀況</span><span class="sxs-lookup"><span data-stu-id="4edb2-175">Example: Handling Exceptions When Binding Data</span></span>](example-handling-exceptions-when-binding-data.md)

- [<span data-ttu-id="4edb2-176">範例：針對動態程式設計進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="4edb2-176">Example: Troubleshooting Dynamic Programming</span></span>](example-troubleshooting-dynamic-programming.md)

- [<span data-ttu-id="4edb2-177">.NET Native 應用程式中的執行階段例外狀況</span><span class="sxs-lookup"><span data-stu-id="4edb2-177">Runtime Exceptions in .NET Native Apps</span></span>](runtime-exceptions-in-net-native-apps.md)

## <a name="see-also"></a><span data-ttu-id="4edb2-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4edb2-178">See also</span></span>

- [<span data-ttu-id="4edb2-179">執行階段指示詞 (rd.xml) 組態檔參考</span><span class="sxs-lookup"><span data-stu-id="4edb2-179">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- <span data-ttu-id="4edb2-180">[.NET Native 安裝和設定](https://docs.microsoft.com/previous-versions/dn600164(v=vs.110))</span><span class="sxs-lookup"><span data-stu-id="4edb2-180">[.NET Native Setup and Configuration](https://docs.microsoft.com/previous-versions/dn600164(v=vs.110))</span></span>
- [<span data-ttu-id="4edb2-181">.NET Native 和編譯</span><span class="sxs-lookup"><span data-stu-id="4edb2-181">.NET Native and Compilation</span></span>](net-native-and-compilation.md)
- [<span data-ttu-id="4edb2-182">反映和 .NET Native</span><span class="sxs-lookup"><span data-stu-id="4edb2-182">Reflection and .NET Native</span></span>](reflection-and-net-native.md)
- [<span data-ttu-id="4edb2-183">依賴反映的 API</span><span class="sxs-lookup"><span data-stu-id="4edb2-183">APIs That Rely on Reflection</span></span>](apis-that-rely-on-reflection.md)
- [<span data-ttu-id="4edb2-184">序列化和中繼資料</span><span class="sxs-lookup"><span data-stu-id="4edb2-184">Serialization and Metadata</span></span>](serialization-and-metadata.md)
- [<span data-ttu-id="4edb2-185">將您的 Windows 市集應用程式移轉至 .NET Native</span><span class="sxs-lookup"><span data-stu-id="4edb2-185">Migrating Your Windows Store App to .NET Native</span></span>](migrating-your-windows-store-app-to-net-native.md)
