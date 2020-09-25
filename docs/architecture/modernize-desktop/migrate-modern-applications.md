---
title: 遷移新式桌面應用程式
description: 針對新式桌面應用程式的遷移程式，您需要知道的一切。
ms.date: 05/12/2020
ms.openlocfilehash: f7862d6379eeeb737c386b5ffeaab938d258b046
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173329"
---
# <a name="migrating-modern-desktop-applications"></a><span data-ttu-id="2ca8c-103">遷移新式桌面應用程式</span><span class="sxs-lookup"><span data-stu-id="2ca8c-103">Migrating Modern Desktop applications</span></span>

<span data-ttu-id="2ca8c-104">在本章中，我們將探討將現有應用程式從 .NET Framework 遷移至 .NET Core 時，最常見的問題和挑戰。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-104">In this chapter, we're exploring the most common issues and challenges you can face when migrating an existing application from .NET Framework to .NET Core.</span></span>

<span data-ttu-id="2ca8c-105">複雜的桌面應用程式不會獨立運作，而且需要與可能位於本機電腦或遠端伺服器上之子系統的某種互動。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-105">A complex desktop application doesn't work in isolation and needs some kind of interaction with subsystems that may reside on the local machine or on a remote server.</span></span> <span data-ttu-id="2ca8c-106">可能需要某種類型的資料庫，才能在本機或遠端連線為持續性儲存區。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-106">It will probably need some kind of database to connect as a persistence storage either locally or remotely.</span></span> <span data-ttu-id="2ca8c-107">隨著網際網路和服務導向架構的引發，您的應用程式通常會連線到位於遠端伺服器或雲端中的某種服務。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-107">With the raise of Internet and service-oriented architectures, it's common to have your application connected to some sort of service residing on a remote server or in the cloud.</span></span> <span data-ttu-id="2ca8c-108">您可能需要存取電腦檔案系統，才能執行一些功能。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-108">You may need to access the machine file system to implement some functionality.</span></span> <span data-ttu-id="2ca8c-109">或者，您可能使用的功能是位於應用程式外部的 COM 物件內，如果您是在應用程式中整合 Office 元件，這是常見的情況。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-109">Alternatively, maybe you're using a piece of functionality that resides inside a COM object outside your application, which is a common scenario if, for example, you're integrating Office assemblies in your app.</span></span>

<span data-ttu-id="2ca8c-110">此外，.NET Framework 和 .NET Core 公開的 API 介面有一些差異，而 .NET Framework 上可用的部分功能則無法在 .NET Core 上使用。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-110">Besides, there are differences in the API surface that is exposed by .NET Framework and .NET Core, and some features that are available on .NET Framework aren't available on .NET Core.</span></span> <span data-ttu-id="2ca8c-111">因此，在規劃遷移時，請務必瞭解並納入考慮。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-111">So, it's important for you to know and take them into account when planning a migration.</span></span>

## <a name="configuration-files"></a><span data-ttu-id="2ca8c-112">組態檔</span><span class="sxs-lookup"><span data-stu-id="2ca8c-112">Configuration files</span></span>

<span data-ttu-id="2ca8c-113">設定檔可讓您儲存在執行時間讀取的屬性集，並影響應用程式的行為，例如尋找資料庫的位置，或執行迴圈的次數。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-113">Configuration files offer the possibility to store sets of properties that are read at run time and affect the behavior of our apps, such as where to locate a database or how many times to execute a loop.</span></span> <span data-ttu-id="2ca8c-114">這項技術的優點是您可以修改應用程式的某些層面，而不需要重新編碼和重新編譯。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-114">The beauty of this technique is that you can modify some aspects of the application without the need to recode and recompile.</span></span> <span data-ttu-id="2ca8c-115">比方說，當相同的應用程式程式碼在具有一組特定設定值的開發環境中執行，且在生產環境中使用不同的應用程式程式碼時，這會很有用。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-115">This comes in handy when, for example, the same app code runs on a development environment with a certain set of configuration values and in production with a different one.</span></span>

### <a name="configuration-on-net-framework"></a><span data-ttu-id="2ca8c-116">.NET Framework 上的設定</span><span class="sxs-lookup"><span data-stu-id="2ca8c-116">Configuration on .NET Framework</span></span>

<span data-ttu-id="2ca8c-117">如果您有工作 .NET Framework 桌面應用程式，您可能會有*app.config* <xref:System.Configuration.AppSettingsSection> 從命名空間透過類別存取的app.config檔案 `System.Configuration` 。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-117">If you have a working .NET Framework desktop application, chances are you have an *app.config* file accessed through the <xref:System.Configuration.AppSettingsSection> class from the `System.Configuration` namespace.</span></span>

<span data-ttu-id="2ca8c-118">在 .NET Framework 基礎結構中，有一階層的設定檔會繼承其父代的屬性。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-118">Within the .NET Framework infrastructure, there's a hierarchy of configuration files that inherit properties from its parents.</span></span> <span data-ttu-id="2ca8c-119">您可以找到 *machine.config* 檔案，該檔案會定義可以在任何子系設定檔中使用或覆寫的許多屬性和設定區段。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-119">You can find a *machine.config* file that defines many properties and configuration sections that can be used or overridden in any descendant configuration file.</span></span>

### <a name="configuration-on-net-core"></a><span data-ttu-id="2ca8c-120">.NET Core 上的設定</span><span class="sxs-lookup"><span data-stu-id="2ca8c-120">Configuration on .NET Core</span></span>

<span data-ttu-id="2ca8c-121">在 .NET Core 世界中，沒有 *machine.config* 的檔案。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-121">In the .NET Core world, there's no *machine.config* file.</span></span> <span data-ttu-id="2ca8c-122">雖然您可以繼續使用舊的舊 <xref:System.Configuration> 命名空間，但您還是可以考慮改用新式，以 <xref:Microsoft.Extensions.Configuration> 提供很多的增強功能。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-122">And even though you can continue to use the old fashioned <xref:System.Configuration> namespace, you may consider switching to the modern <xref:Microsoft.Extensions.Configuration>, which offers a good number of enhancements.</span></span>

<span data-ttu-id="2ca8c-123">設定 API 支援設定提供者的概念，其定義要用來載入設定的資料來源。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-123">The configuration API supports the concept of configuration provider, which defines the data source to be used to load the configuration.</span></span> <span data-ttu-id="2ca8c-124">有不同類型的內建提供者，例如：</span><span class="sxs-lookup"><span data-stu-id="2ca8c-124">There are different kinds of built-in providers, such as:</span></span>

- <span data-ttu-id="2ca8c-125">記憶體內部 .NET 物件</span><span class="sxs-lookup"><span data-stu-id="2ca8c-125">In-memory .NET objects</span></span>
- <span data-ttu-id="2ca8c-126">INI 檔案</span><span class="sxs-lookup"><span data-stu-id="2ca8c-126">INI files</span></span>
- <span data-ttu-id="2ca8c-127">JSON 檔案</span><span class="sxs-lookup"><span data-stu-id="2ca8c-127">JSON files</span></span>
- <span data-ttu-id="2ca8c-128">XML 檔案</span><span class="sxs-lookup"><span data-stu-id="2ca8c-128">XML files</span></span>
- <span data-ttu-id="2ca8c-129">命令列引數</span><span class="sxs-lookup"><span data-stu-id="2ca8c-129">Command-line arguments</span></span>
- <span data-ttu-id="2ca8c-130">環境變數</span><span class="sxs-lookup"><span data-stu-id="2ca8c-130">Environment variables</span></span>
- <span data-ttu-id="2ca8c-131">加密的使用者存放區</span><span class="sxs-lookup"><span data-stu-id="2ca8c-131">Encrypted user store</span></span>

 <span data-ttu-id="2ca8c-132">您也可以建立自己的版本。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-132">Or you can build your own.</span></span>

<span data-ttu-id="2ca8c-133">新的設定允許可分組為多層級階層的成對名稱/值組清單。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-133">The new configuration allows a list of name-value pairs that can be grouped into a multi-level hierarchy.</span></span> <span data-ttu-id="2ca8c-134">任何儲存的值會對應至字串，且有內建的系結支援，可讓您將設定還原序列化為自訂的簡單 CLR 物件， (POCO) 物件。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-134">Any stored value maps to a string, and there's built-in binding support that allows you to deserialize settings into a custom plain old CLR object (POCO) object.</span></span>

<span data-ttu-id="2ca8c-135"><xref:Microsoft.Extensions.Configuration.ConfigurationBuilder>物件可讓您新增應用程式所需數量的設定提供者，並使用優先順序規則來解析喜好設定。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-135">The <xref:Microsoft.Extensions.Configuration.ConfigurationBuilder> object lets you add as many configuration providers you may need for your application, using a precedence rule to resolve preference.</span></span> <span data-ttu-id="2ca8c-136">因此，您在程式碼中加入的最後一個提供者會覆寫其他提供者。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-136">So, the last provider you add in your code will override the others.</span></span> <span data-ttu-id="2ca8c-137">由於您可以針對開發、測試和生產環境定義不同的設定，並在程式碼內的單一函式上管理它們，因此這是管理不同環境來執行的絕佳功能。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-137">This is a great feature for managing different environments for execution since you can define different configurations for development, testing and production environments, and manage them on a single function inside your code.</span></span>

### <a name="migrating-configuration-files"></a><span data-ttu-id="2ca8c-138">正在遷移設定檔</span><span class="sxs-lookup"><span data-stu-id="2ca8c-138">Migrating Configuration files</span></span>

<span data-ttu-id="2ca8c-139">您可以繼續使用現有的 app.config XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-139">You can continue to use your existing app.config XML file.</span></span> <span data-ttu-id="2ca8c-140">不過，您可以利用這個機會來遷移您的設定，以受益于 .NET Core 上的數個增強功能。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-140">However, you could take this opportunity to migrate your configuration to benefit from the several enhancements made on .NET Core.</span></span>

<span data-ttu-id="2ca8c-141">若要從舊樣式的 *app.config* 遷移至新的設定檔，您應該選擇 XML 格式和 JSON 格式。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-141">To migrate from an old-style *app.config* to a new configuration file, you should choose between an XML format and a JSON format.</span></span>

<span data-ttu-id="2ca8c-142">如果您選擇 XML，則轉換很簡單。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-142">If you choose XML, the conversion is straightforward.</span></span> <span data-ttu-id="2ca8c-143">因為內容相同，所以只需將 *app.config* 檔案重新命名為具有 XML 副檔名的檔案即可。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-143">Since the content is the same, just rename the *app.config* file to a file with XML extension.</span></span> <span data-ttu-id="2ca8c-144">然後，將參考 AppSettings 的程式碼變更為使用 `ConfigurationBuilder` 類別。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-144">Then, change the code that references AppSettings to use the `ConfigurationBuilder` class.</span></span> <span data-ttu-id="2ca8c-145">這種變更應該很簡單。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-145">This change should be easy.</span></span>

<span data-ttu-id="2ca8c-146">如果您想要使用 JSON 格式，而不想要手動遷移，可在 .NET Core 上使用稱為 [dotnet config2json](https://www.nuget.org/packages/dotnet-config2json/) 的工具，可將 *app.config* 檔案轉換成 JSON 設定檔。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-146">If you want to use a JSON format and you don't want to migrate by hand, there's a tool called [dotnet-config2json](https://www.nuget.org/packages/dotnet-config2json/) available on .NET Core that can convert an *app.config* file to a JSON configuration file.</span></span>

<span data-ttu-id="2ca8c-147">使用 *machine.config* 檔中定義的設定區段時，您也可能會遇到一些問題。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-147">You may also come across some issues when using configuration sections that were defined in the *machine.config* file.</span></span> <span data-ttu-id="2ca8c-148">例如，請考慮下列設定：</span><span class="sxs-lookup"><span data-stu-id="2ca8c-148">For example, consider the following configuration:</span></span>

```xml
<configuration>
    <system.diagnostics>
        <switches>
            <add name="General" value="4" />
        </switches>
        <trace autoflush="true" indentsize="2">
            <listeners>
                <add name="myListener"
                     type="System.Diagnostics.TextWriterTraceListener,
                           System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
                     initializeData="MyListener.log"
                     traceOutputOptions="ProcessId, LogicalOperationStack, Timestamp, ThreadId, Callstack, DateTime" />
            </listeners>
        </trace>
    </system.diagnostics>
</configuration>
```

<span data-ttu-id="2ca8c-149">如果您將此設定設定為 .NET Core，您將會收到例外狀況：</span><span class="sxs-lookup"><span data-stu-id="2ca8c-149">If you take this configuration to a .NET Core, you'll get an exception:</span></span>

<span data-ttu-id="2ca8c-150">無法辨識的設定區段系統診斷</span><span class="sxs-lookup"><span data-stu-id="2ca8c-150">Unrecognized configuration section system.diagnostics</span></span>

<span data-ttu-id="2ca8c-151">發生此例外狀況是因為該區段和負責處理該區段的元件已定義于 *machine.config* 檔案中，但目前不存在。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-151">This exception occurs because that section and the assembly responsible for handling that section was defined in the *machine.config* file, which now doesn't exist.</span></span>

<span data-ttu-id="2ca8c-152">若要輕鬆地修正此問題，您可以從舊的 *machine.config* 將區段定義複製到新的設定檔：</span><span class="sxs-lookup"><span data-stu-id="2ca8c-152">To easily fix the issue, you can copy the section definition from your old *machine.config* to your new configuration file:</span></span>

```xml
<configSections>
    <section name="system.diagnostics"
             type="System.Diagnostics.SystemDiagnosticsSection,
                   System, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>
</configSections>
```

## <a name="accessing-databases"></a><span data-ttu-id="2ca8c-153">存取資料庫</span><span class="sxs-lookup"><span data-stu-id="2ca8c-153">Accessing databases</span></span>

<span data-ttu-id="2ca8c-154">幾乎所有的桌面應用程式都需要某種類型的資料庫。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-154">Almost every desktop application needs some kind of database.</span></span> <span data-ttu-id="2ca8c-155">針對桌面，通常會在桌面應用程式和 database engine 之間直接連線來尋找用戶端-伺服器架構。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-155">For desktop, it's common to find client-server architectures with a direct connection between the desktop app and the database engine.</span></span> <span data-ttu-id="2ca8c-156">這些資料庫可以是本機或遠端，視需要在不同使用者之間共用資訊的需求而定。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-156">These databases can be local or remote depending on the need to share information between different users.</span></span>

<span data-ttu-id="2ca8c-157">從程式碼的觀點來看，有許多技術和架構可讓開發人員連接、查詢及更新資料庫。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-157">From the code perspective, there have been many technologies and frameworks to give the developer the possibility to connect, query, and update a database.</span></span>

<span data-ttu-id="2ca8c-158">在談到 Windows 傳統型應用程式時，最常見的資料庫範例是 Microsoft Access 和 Microsoft SQL Server。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-158">The most common examples of database you can find when talking about Windows Desktop application are Microsoft Access and Microsoft SQL Server.</span></span> <span data-ttu-id="2ca8c-159">如果您在桌上型電腦上擁有20年以上的體驗程式設計，則會很熟悉 ODBC、OLEDB、RDO、ADO、ADO.NET、LINQ 和 Entity Framework 等名稱。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-159">If you have more than 20 years of experience programming for the desktop, names like ODBC, OLEDB, RDO, ADO, ADO.NET, LINQ, and Entity Framework will sound familiar.</span></span>

### <a name="odbc"></a><span data-ttu-id="2ca8c-160">ODBC</span><span class="sxs-lookup"><span data-stu-id="2ca8c-160">ODBC</span></span>

<span data-ttu-id="2ca8c-161">您可以繼續使用 .NET Core 上的 ODBC，因為 Microsoft 會提供 `System.Data.Odbc` 與 .NET Standard 2.0 相容的程式庫。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-161">You can continue to use ODBC on .NET Core since Microsoft is providing the `System.Data.Odbc` library compatible with .NET Standard 2.0.</span></span>

### <a name="ole-db"></a><span data-ttu-id="2ca8c-162">OLE DB</span><span class="sxs-lookup"><span data-stu-id="2ca8c-162">OLE DB</span></span>

<span data-ttu-id="2ca8c-163">[OLE DB](/previous-versions/windows/desktop/ms722784(v=vs.85))  已經是以一致的方式存取各種資料來源的絕佳方式。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-163">[OLE DB](/previous-versions/windows/desktop/ms722784(v=vs.85)) has been a great way to access various data sources in a uniform manner.</span></span> <span data-ttu-id="2ca8c-164">但它是以 COM 為基礎，這是一種僅限 Windows 的技術，因此不是最適合跨平臺技術（例如 .NET Core）。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-164">But it was based on COM, which is a Windows-only technology, and as such wasn't the best fit for a cross-platform technology such as .NET Core.</span></span> <span data-ttu-id="2ca8c-165">SQL Server 版本2014和更新版本也不支援此功能。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-165">It's also unsupported in SQL Server versions 2014 and later.</span></span> <span data-ttu-id="2ca8c-166">基於這些原因，.NET Core 將不支援 OLE DB。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-166">For those reasons, OLE DB won't be supported by .NET Core.</span></span>

### <a name="adonet"></a><span data-ttu-id="2ca8c-167">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2ca8c-167">ADO.NET</span></span>

<span data-ttu-id="2ca8c-168">您仍然可以在 .NET Core 上使用現有的桌面程式碼中的 ADO.NET。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-168">You can still use ADO.NET from your existing desktop code on .NET Core.</span></span> <span data-ttu-id="2ca8c-169">您只需要更新一些 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-169">You just need to update some NuGet packages.</span></span>

### <a name="ef-core-vs-ef6"></a><span data-ttu-id="2ca8c-170">EF Core 與 EF6</span><span class="sxs-lookup"><span data-stu-id="2ca8c-170">EF Core vs. EF6</span></span>

<span data-ttu-id="2ca8c-171">目前支援兩種版本的 Entity Framework (EF) ，Entity Framework 6 (EF6) 和 EF Core。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-171">There are two currently supported versions of Entity Framework (EF), Entity Framework 6 (EF6) and EF Core.</span></span>

<span data-ttu-id="2ca8c-172">在 .NET Framework 世界中發行的最新技術是 Entity Framework，6.4 是最新版本。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-172">The latest technology released as part of the .NET Framework world is Entity Framework, with 6.4 being the latest version.</span></span> <span data-ttu-id="2ca8c-173">隨著 .NET Core 的推出，Microsoft 也會根據 Entity Framework 發行新的資料存取堆疊，並呼叫 Entity Framework Core。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-173">With the launch of .NET Core, Microsoft also released a new data access stack based on Entity Framework and called Entity Framework Core.</span></span>

<span data-ttu-id="2ca8c-174">您可以從 .NET Framework 和 .NET Core 使用 EF 6.4 和 EF Core。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-174">You can use EF 6.4 and EF Core from both .NET Framework and .NET Core.</span></span> <span data-ttu-id="2ca8c-175">那麼，有哪些決策驅動程式有助於決定兩者之間？</span><span class="sxs-lookup"><span data-stu-id="2ca8c-175">So, what are the decision drivers to help to decide between the two?</span></span>

<span data-ttu-id="2ca8c-176">EF 6.3 是 EF6 的第一個版本，可在 .NET Core 上執行並跨平臺運作。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-176">EF 6.3 is the first version of EF6 that can run on .NET Core and work cross-platform.</span></span> <span data-ttu-id="2ca8c-177">事實上，這個版本的主要目標是要讓您更輕鬆地將使用 EF6 的現有應用程式遷移至 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-177">In fact, the main goal of this release was to make it easier to migrate existing applications that use EF6 to .NET Core.</span></span>

<span data-ttu-id="2ca8c-178">EF Core 旨在提供類似於 EF6 的開發人員體驗。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-178">EF Core was designed to provide a developer experience similar to EF6.</span></span> <span data-ttu-id="2ca8c-179">大部分的頂層 API 都維持不變，因此使用過 EF6 的開發人員會對 EF Core 感到熟悉。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-179">Most of the top-level APIs remain the same, so EF Core will feel familiar to developers who have used EF6.</span></span>

<span data-ttu-id="2ca8c-180">雖然是相容的，但在進行決策之前，您應該檢查的實作為差異。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-180">Although compatible, there are differences on the implementation you should check before making a decision.</span></span>
<span data-ttu-id="2ca8c-181">如需詳細資訊，請參閱 [比較 EF Core & EF6](/ef/efcore-and-ef6/)。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-181">For more information, see [Compare EF Core & EF6](/ef/efcore-and-ef6/).</span></span>

<span data-ttu-id="2ca8c-182">建議您在下列情況中使用 EF Core：</span><span class="sxs-lookup"><span data-stu-id="2ca8c-182">The recommendation is to use EF Core if:</span></span>

* <span data-ttu-id="2ca8c-183">該應用程式需要 .NET Core 的功能。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-183">The app needs the capabilities of .NET Core.</span></span>
* <span data-ttu-id="2ca8c-184">EF Core 支援應用程式所需的所有功能。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-184">EF Core supports all of the features that the app requires.</span></span>

<span data-ttu-id="2ca8c-185">如果下列兩個條件成立，請考慮使用 EF6：</span><span class="sxs-lookup"><span data-stu-id="2ca8c-185">Consider using EF6 if both of the following conditions are true:</span></span>

* <span data-ttu-id="2ca8c-186">應用程式將在 Windows 上執行，並 .NET Framework 4.0 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-186">The app will run on Windows and .NET Framework 4.0 or later.</span></span>
* <span data-ttu-id="2ca8c-187">EF6 支援應用程式所需的所有功能。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-187">EF6 supports all of the features that the app requires.</span></span>

### <a name="relational-databases"></a><span data-ttu-id="2ca8c-188">關聯式資料庫</span><span class="sxs-lookup"><span data-stu-id="2ca8c-188">Relational databases</span></span>

#### <a name="sql-server"></a><span data-ttu-id="2ca8c-189">SQL Server</span><span class="sxs-lookup"><span data-stu-id="2ca8c-189">SQL Server</span></span>

<span data-ttu-id="2ca8c-190">如果您在幾年前開發桌上型電腦，SQL Server 就是其中一個選擇的資料庫。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-190">SQL Server has been one of the databases of choice if you were developing for the desktop some years ago.</span></span> <span data-ttu-id="2ca8c-191">使用 <xref:System.Data.SqlClient> .NET Framework 中的，您可以存取封裝的 SQL Server 版本，以封裝資料庫特定的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-191">With the use of <xref:System.Data.SqlClient> in .NET Framework, you could access versions of SQL Server, which encapsulates database-specific protocols.</span></span>

<span data-ttu-id="2ca8c-192">在 .NET Core 中，您可以找到新的 `SqlClient` 類別，與 .NET Framework 中現有的類別完全相容，但位於連結 <xref:Microsoft.Data.SqlClient> 庫中。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-192">In .NET Core, you can find a new `SqlClient` class, fully compatible with the one existing in the .NET Framework but located in the <xref:Microsoft.Data.SqlClient> library.</span></span> <span data-ttu-id="2ca8c-193">您只需要新增 [SqlClient](https://www.nuget.org/packages/Microsoft.Data.SqlClient/) NuGet 套件的參考，並對命名空間進行一些重新命名，一切應該都能如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-193">You just have to add a reference to the [Microsoft.Data.SqlClient](https://www.nuget.org/packages/Microsoft.Data.SqlClient/) NuGet package and do some renaming for the namespaces and everything should work as expected.</span></span>

#### <a name="microsoft-access"></a><span data-ttu-id="2ca8c-194">Microsoft Access</span><span class="sxs-lookup"><span data-stu-id="2ca8c-194">Microsoft Access</span></span>

<span data-ttu-id="2ca8c-195">當您不需要精密且可擴充的 SQL Server 時，會使用 Microsoft Access。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-195">Microsoft Access has been used for years when the sophisticated and more scalable SQL Server wasn't needed.</span></span> <span data-ttu-id="2ca8c-196">您仍然可以使用程式庫連接到 Microsoft Access <xref:System.Data.Odbc> 。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-196">You can still connect to Microsoft Access using the <xref:System.Data.Odbc> library.</span></span>

## <a name="consuming-services"></a><span data-ttu-id="2ca8c-197">使用服務</span><span class="sxs-lookup"><span data-stu-id="2ca8c-197">Consuming services</span></span>

<span data-ttu-id="2ca8c-198">隨著服務導向架構的引發，桌面應用程式會從用戶端-伺服器模型開始發展到三層式的方法。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-198">With the raise of service-oriented architectures, desktop applications began to evolve from a client-server model to the three-layer approach.</span></span> <span data-ttu-id="2ca8c-199">在用戶端伺服器的方法中，直接資料庫連線是從保存商務邏輯的用戶端建立，通常是在單一 EXE 檔案內。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-199">In the client-server approach, a direct database connection is established from the client holding the business logic usually inside a single EXE file.</span></span> <span data-ttu-id="2ca8c-200">另一方面，三層式方法會建立一個中繼服務層，以實行商務邏輯和資料庫存取，以提供更佳的安全性、可調整性和重複使用性。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-200">On the other hand, the three-layer approach establishes an intermediate service layer implementing business logic and database access allowing for better security, scalability, and reusability.</span></span> <span data-ttu-id="2ca8c-201">該層方法不會直接使用資料的資料集，而是依賴一組執行合約和類型物件的服務來執行資料傳輸。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-201">Instead of working directly with datasets of data, the layer approach relies in a set of services implementing contracts and types objects as a way to implement data transfer.</span></span>

<span data-ttu-id="2ca8c-202">如果您有使用 WCF 服務的桌面應用程式，而您想要將它遷移至 .NET Core，則需要考慮一些事項。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-202">If you have a desktop application using a WCF service and you want to migrate it to .NET Core, there are some things to consider.</span></span>

<span data-ttu-id="2ca8c-203">第一件事是如何解決設定以存取服務。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-203">The first thing is how to resolve the configuration to access the service.</span></span> <span data-ttu-id="2ca8c-204">因為 .NET Core 上的設定不同，所以您必須在設定檔中進行一些更新。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-204">Because the configuration is different on .NET Core, you'll need to make some updates in your configuration file.</span></span>

<span data-ttu-id="2ca8c-205">其次，您必須使用 Visual Studio 2019 上的新工具，重新產生服務用戶端。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-205">Second, you'll need to regenerate the service client with the new tools present on Visual Studio 2019.</span></span> <span data-ttu-id="2ca8c-206">在此步驟中，您必須考慮啟用同步作業的產生，使用戶端與您現有的程式碼相容。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-206">In this step, you must consider activating the generation of the synchronous operations to make the client compatible with your existing code.</span></span>

<span data-ttu-id="2ca8c-207">在遷移之後，如果您發現 .NET Core 上有您需要的程式庫，您可以新增對 [Microsoft 的相容性](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) NuGet 套件的參考，並查看是否有遺漏的函式。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-207">After the migration, if you find that there are libraries you need that aren't present on .NET Core, you can add a reference to the [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) NuGet package and see if the missing functions are there.</span></span>

<span data-ttu-id="2ca8c-208">如果您使用 <xref:System.Net.WebRequest> 類別來執行 web 服務呼叫，您可能會發現 .Net Core 有一些差異。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-208">If you're using the <xref:System.Net.WebRequest> class to perform web service calls, you may find some differences on .NET Core.</span></span> <span data-ttu-id="2ca8c-209">建議您改為使用 HttpClient。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-209">The recommendation is to use the System.Net.Http.HttpClient instead.</span></span>

## <a name="consuming-a-com-object"></a><span data-ttu-id="2ca8c-210">使用 COM 物件</span><span class="sxs-lookup"><span data-stu-id="2ca8c-210">Consuming a COM Object</span></span>

<span data-ttu-id="2ca8c-211">目前沒有任何方法可將參考加入至 Visual Studio 2019 的 COM 物件，以與 .NET Core 搭配使用。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-211">Currently, there's no way to add a reference to a COM object from Visual Studio 2019 to use with .NET Core.</span></span> <span data-ttu-id="2ca8c-212">因此，您必須手動修改專案檔。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-212">So, you have to manually modify the project file.</span></span>

<span data-ttu-id="2ca8c-213">`COMReference`在專案檔內插入結構，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="2ca8c-213">Insert a `COMReference` structure inside the project file like in the following example:</span></span>

```xml
<ItemGroup>
    <COMReference Include="MSHTML">
        <Guid>{3050F1C5-98B5-11CF-BB82-00AA00BDCE0B}\</Guid>
        <VersionMajor>4</VersionMajor>
        <VersionMinor>0</VersionMinor>
        <Lcid>0</Lcid>
        <WrapperTool>primary</WrapperTool>
        <Isolated>false</Isolated>
    </COMReference>
</ItemGroup>
```

## <a name="more-things-to-consider"></a><span data-ttu-id="2ca8c-214">其他應考慮的事項</span><span class="sxs-lookup"><span data-stu-id="2ca8c-214">More things to consider</span></span>

<span data-ttu-id="2ca8c-215">適用于 .NET Core 的 .NET Framework 程式庫可以使用數種技術。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-215">Several technologies available to .NET Framework libraries aren't available for .NET Core.</span></span> <span data-ttu-id="2ca8c-216">如果您的程式碼相依于這些技術，請考慮本節所述的替代方法。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-216">If your code relies on some of these technologies, consider the alternative approaches outlined in this section.</span></span>

<span data-ttu-id="2ca8c-217">[Windows 相容性套件](../../core/porting/windows-compat-pack.md)可讓您存取先前僅供 .NET Framework 使用的 api。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-217">The [Windows Compatibility Pack](../../core/porting/windows-compat-pack.md) provides access to APIs that were previously available only for .NET Framework.</span></span> <span data-ttu-id="2ca8c-218">它可以在 .NET Core 和 .NET Standard 專案上使用。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-218">It can be used on .NET Core and .NET Standard projects.</span></span>

<span data-ttu-id="2ca8c-219">如需 API 相容性的詳細資訊，您可以在中找到有關重大變更和已淘汰/舊版 Api 的檔 <https://docs.microsoft.com/dotnet/core/compatibility/fx-core> 。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-219">For more information on API compatibility, you can find documentation about breaking changes and deprecated/legacy APIs at <https://docs.microsoft.com/dotnet/core/compatibility/fx-core>.</span></span>

### <a name="appdomains"></a><span data-ttu-id="2ca8c-220">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2ca8c-220">AppDomains</span></span>

<span data-ttu-id="2ca8c-221">應用程式定義域 (AppDomain) 可將應用程式互相隔離。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-221">Application domains (AppDomains) isolate apps from one another.</span></span> <span data-ttu-id="2ca8c-222">Appdomain 需要執行時間支援，而且很昂貴。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-222">AppDomains require runtime support and are expensive.</span></span> <span data-ttu-id="2ca8c-223">不支援建立其他應用程式網域。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-223">Creating additional app domains isn't supported.</span></span> <span data-ttu-id="2ca8c-224">若要隔離程式碼，建議使用不同的處理序或使用容器作為替代方法。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-224">For code isolation, we recommend separate processes or using containers as an alternative.</span></span> <span data-ttu-id="2ca8c-225">針對動態載入元件，我們建議新的  <xref:System.Runtime.Loader.AssemblyLoadContext> 類別。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-225">For the dynamic loading of assemblies, we recommend the new <xref:System.Runtime.Loader.AssemblyLoadContext> class.</span></span>

<span data-ttu-id="2ca8c-226">為了讓您更輕鬆地從 .NET Framework 進行程式碼遷移，.NET Core 會公開一些 AppDomain API 介面。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-226">To make code migration from .NET Framework easier, .NET Core exposes some of the AppDomain API surface.</span></span> <span data-ttu-id="2ca8c-227">某些 Api 會正常運作 (例如  <xref:System.AppDomain.UnhandledException?displayProperty=nameWithType>) 、某些成員不會執行任何動作 (例如  <xref:System.AppDomain.SetCachePath%2A>) ，而某些成員會擲回 <xref:System.PlatformNotSupportedException> (例如  <xref:System.AppDomain.CreateDomain%2A>) 。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-227">Some of the APIs function normally (for example, <xref:System.AppDomain.UnhandledException?displayProperty=nameWithType>), some members do nothing (for example, <xref:System.AppDomain.SetCachePath%2A>), and some of them throw <xref:System.PlatformNotSupportedException> (for example, <xref:System.AppDomain.CreateDomain%2A>).</span></span>

### <a name="remoting"></a><span data-ttu-id="2ca8c-228">遠端</span><span class="sxs-lookup"><span data-stu-id="2ca8c-228">Remoting</span></span>

<span data-ttu-id="2ca8c-229">.NET 遠端處理是用於跨 AppDomain 通訊，但已不再支援。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-229">.NET Remoting was used for cross-AppDomain communication, which is no longer supported.</span></span> <span data-ttu-id="2ca8c-230">此外，遠端處理需要執行階段支援，因此維護成本相當高昂。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-230">Also, Remoting requires runtime support, which is expensive to maintain.</span></span> <span data-ttu-id="2ca8c-231">基於這些理由，.NET Core 不支援 .NET 遠端處理。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-231">For these reasons, .NET Remoting isn't supported on .NET Core.</span></span>

<span data-ttu-id="2ca8c-232">針對跨進程的通訊，您應該考慮 (IPC) 機制的處理序間通訊，作為遠端的替代方式，例如 <xref:System.IO.Pipes?displayProperty=nameWithType> 或 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> 類別。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-232">For communication across processes, you should consider inter-process communication (IPC) mechanisms as an alternative to Remoting, such as the <xref:System.IO.Pipes?displayProperty=nameWithType> or the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> class.</span></span>

<span data-ttu-id="2ca8c-233">針對跨機器通訊，請使用以網路為基礎的替代方案。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-233">Across machines, use a network-based solution as an alternative.</span></span> <span data-ttu-id="2ca8c-234">最好是使用低額外負荷的純文字通訊協定，例如 HTTP。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-234">Preferably, use a low-overhead plaintext protocol, such as HTTP.</span></span> <span data-ttu-id="2ca8c-235">Kestrel Web 伺服器 \(英文\) 是 ASP.NET Core 所使用的 Web 伺服器，也是此情況下可考慮使用的選項。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-235">The Kestrel web server, the web server used by ASP.NET Core, is an option here.</span></span>

### <a name="code-access-security-cas"></a><span data-ttu-id="2ca8c-236">程式碼存取安全性 (CAS)</span><span class="sxs-lookup"><span data-stu-id="2ca8c-236">Code Access Security (CAS)</span></span>

<span data-ttu-id="2ca8c-237">.NET Core 不支援沙箱（依賴執行時間或架構來限制受管理應用程式或程式庫所使用或執行的資源）。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-237">Sandboxing, which relies on the runtime or the framework to constrain which resources a managed application or library uses or runs, isn't supported on .NET Core.</span></span>

<span data-ttu-id="2ca8c-238">使用作業系統所提供的安全性界限（例如虛擬化、容器或使用者帳戶），以最少的許可權集執行處理常式。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-238">Use security boundaries that are provided by the operating system, such as virtualization, containers, or user accounts for running processes with the minimum set of privileges.</span></span>

### <a name="security-transparency"></a><span data-ttu-id="2ca8c-239">安全性透明度</span><span class="sxs-lookup"><span data-stu-id="2ca8c-239">Security Transparency</span></span>

<span data-ttu-id="2ca8c-240">與 CAS 類似，安全性透明度會以宣告方式區隔沙箱化程式碼和安全性關鍵程式碼，但已不再支援作為安全性界限。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-240">Similar to CAS, Security Transparency separates sandboxed code from security critical code in a declarative fashion but is no longer supported as a security boundary.</span></span>

<span data-ttu-id="2ca8c-241">使用作業系統所提供的安全性界限（例如虛擬化、容器或使用者帳戶），以最少的許可權來執行進程。</span><span class="sxs-lookup"><span data-stu-id="2ca8c-241">Use security boundaries that are provided by the operating system, such as virtualization, containers, or user accounts for running processes with the least set of privileges.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="2ca8c-242">[上一個](whats-new-dotnet-core.md ) 
>[下一步](windows-migration.md)</span><span class="sxs-lookup"><span data-stu-id="2ca8c-242">[Previous](whats-new-dotnet-core.md )
[Next](windows-migration.md)</span></span>
