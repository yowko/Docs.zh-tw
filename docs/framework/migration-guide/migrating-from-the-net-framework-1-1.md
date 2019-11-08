---
title: 從 .NET Framework 1.1 移轉
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 4.5, migrating from 1.1
- .NET Framework 1.1, migrating to .NET Framework 4.5
ms.assetid: 7ead0cb3-3b19-414a-8417-a1c1fa198d9e
ms.openlocfilehash: a553d24a12b7ea227325a76d255e2ad53ada716f
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739617"
---
# <a name="migrate-from-the-net-framework-11"></a><span data-ttu-id="07e24-102">從 .NET Framework 1.1 遷移</span><span class="sxs-lookup"><span data-stu-id="07e24-102">Migrate from the .NET Framework 1.1</span></span>

<span data-ttu-id="07e24-103">Windows 7 和更新版本的 Windows 作業系統不支援 .NET Framework 1.1。</span><span class="sxs-lookup"><span data-stu-id="07e24-103">Windows 7 and later versions of the Windows operating system do not support the .NET Framework 1.1.</span></span> <span data-ttu-id="07e24-104">因此，以 .NET Framework 1.1 為目標的應用程式不需要在 Windows 7 或更新版本的作業系統版本上進行修改，就不會執行。</span><span class="sxs-lookup"><span data-stu-id="07e24-104">As a result, applications that target the .NET Framework 1.1 will not run without modification on Windows 7 or later operating system versions.</span></span> <span data-ttu-id="07e24-105">本主題討論在 Windows 7 和更新版本的 Windows 作業系統下執行以 .NET Framework 1.1 為目標的應用程式所需的步驟。</span><span class="sxs-lookup"><span data-stu-id="07e24-105">This topic discusses the steps required to run an application that targets the .NET Framework 1.1 under Windows 7 and later versions of the Windows operating system.</span></span> <span data-ttu-id="07e24-106">如需 .NET Framework 1.1 和 Windows 8 的詳細資訊，請參閱[在 Windows 8 和更新版本上執行 .NET Framework 1.1 應用程式](../install/run-net-framework-1-1-apps.md)。</span><span class="sxs-lookup"><span data-stu-id="07e24-106">For more information about the .NET Framework 1.1 and Windows 8, see [Run .NET Framework 1.1 Apps on Windows 8 and later versions](../install/run-net-framework-1-1-apps.md).</span></span>

## <a name="retarget-or-recompile"></a><span data-ttu-id="07e24-107">重定目標或重新編譯</span><span class="sxs-lookup"><span data-stu-id="07e24-107">Retarget or recompile</span></span>

<span data-ttu-id="07e24-108">有兩種方式可取得使用 .NET Framework 1.1 編譯的應用程式，以在 Windows 7 或更新版本的 Windows 作業系統上執行：</span><span class="sxs-lookup"><span data-stu-id="07e24-108">There are two ways to get an application that was compiled using the .NET Framework 1.1 to run on Windows 7 or a later Windows operating system:</span></span>

- <span data-ttu-id="07e24-109">將應用程式的目標重定為在 .NET Framework 4 和更新版本下執行。</span><span class="sxs-lookup"><span data-stu-id="07e24-109">Retarget the application to run under .NET Framework 4 and later versions.</span></span> <span data-ttu-id="07e24-110">重新設定目標需要您將 [\<supportedRuntime>](../configure-apps/file-schema/startup/supportedruntime-element.md) 元素新增至應用程式的組態檔，使它可以在 .NET Framework 4 和更新版本之下執行。</span><span class="sxs-lookup"><span data-stu-id="07e24-110">Retargeting requires that you add a [\<supportedRuntime>](../configure-apps/file-schema/startup/supportedruntime-element.md) element to the application's configuration file that allows it to run under .NET Framework 4 and later versions.</span></span> <span data-ttu-id="07e24-111">這類組態檔的形式如下：</span><span class="sxs-lookup"><span data-stu-id="07e24-111">Such a configuration file takes the following form:</span></span>

    ```xml
    <configuration>
       <startup>
          <supportedRuntime version="v4.0"/>
       </startup>
    </configuration>
    ```

- <span data-ttu-id="07e24-112">使用以 .NET Framework 4 或更新版本為目標的編譯器來重新編譯應用程式。</span><span class="sxs-lookup"><span data-stu-id="07e24-112">Recompile the application with a compiler that targets the .NET Framework 4 or a later version.</span></span> <span data-ttu-id="07e24-113">如果您原本使用 Visual Studio 2003 來開發及編譯解決方案，您可以在 Visual Studio 2010 (更新版本也可以) 中開啟此解決方案，並且使用 [專案相容性] 對話方塊來將此解決方案和專案檔從 Visual Studio 2003 使用的格式轉換成 Microsoft Build Engine (MSBuild) 格式。</span><span class="sxs-lookup"><span data-stu-id="07e24-113">If you originally used Visual Studio 2003 to develop and compile your solution, you can open the solution in Visual Studio 2010 (and possibly later versions too) and use the **Project Compatibility** dialog box to convert the solution and project files from the formats used by Visual Studio 2003 to the Microsoft Build Engine (MSBuild) format.</span></span>

<span data-ttu-id="07e24-114">不論您偏好重新編譯應用程式還是重新設定應用程式的目標，您都必須決定您的應用程式是否會受到較新 .NET Framework 版本中引入的任何變更所影響。</span><span class="sxs-lookup"><span data-stu-id="07e24-114">Regardless of whether you prefer to recompile or retarget your application, you must determine whether your application is affected by any changes introduced in later versions of the .NET Framework.</span></span> <span data-ttu-id="07e24-115">這些變更有兩種：</span><span class="sxs-lookup"><span data-stu-id="07e24-115">These changes are of two kinds:</span></span>

- <span data-ttu-id="07e24-116">在 .NET Framework 1.1 與較新版 .NET Framework 之間發生的重大變更。</span><span class="sxs-lookup"><span data-stu-id="07e24-116">Breaking changes that occurred between the .NET Framework 1.1 and later versions of the .NET Framework.</span></span>

- <span data-ttu-id="07e24-117">在 .NET Framework 1.1 與較新版 .NET Framework 之間，標示為已取代或已過時的型別和型別成員。</span><span class="sxs-lookup"><span data-stu-id="07e24-117">Types and type members that have been marked as deprecated or obsolete between the .NET Framework 1.1 and later versions of the .NET Framework.</span></span>

<span data-ttu-id="07e24-118">無論您是重新設定應用程式的目標還是重新編譯，您都應該針對 .NET Framework 1.1 之後發行的每一個 .NET Framework 版本來檢閱重大變更及過時的型別和成員。</span><span class="sxs-lookup"><span data-stu-id="07e24-118">Whether you retarget your application or recompile it, you should review both the breaking changes and the obsolete types and members for each version of the .NET Framework that was released after .NET Framework 1.1.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="07e24-119">重大變更</span><span class="sxs-lookup"><span data-stu-id="07e24-119">Breaking changes</span></span>

<span data-ttu-id="07e24-120">當發生重大變更時，重新設定目標及重新編譯的應用程式可能會有替代解決辦法可用 (視特定變更而定)。</span><span class="sxs-lookup"><span data-stu-id="07e24-120">When a breaking change occurs, depending on the specific change, a workaround may be available both for retargeted and recompiled applications.</span></span> <span data-ttu-id="07e24-121">在某些情況下，您可以將子元素加入至應用程式組態檔的 [\<runtime>](../configure-apps/file-schema/startup/supportedruntime-element.md) 元素，以還原舊版的行為。</span><span class="sxs-lookup"><span data-stu-id="07e24-121">In some cases, you can add a child element to the [\<runtime>](../configure-apps/file-schema/startup/supportedruntime-element.md) element of your application's configuration file to restore the previous behavior.</span></span> <span data-ttu-id="07e24-122">例如，下列組態檔會還原 .NET Framework 1.1 中使用的字串排序和比較行為，而且可以搭配重新設定目標或重新編譯的應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="07e24-122">For example, the following configuration file restores the string sorting and comparison behavior used in the .NET Framework 1.1 and can be used either with a retargeted or a recompiled application.</span></span>

```xml
<configuration>
   <runtime>
      <CompatSortNLSVersion enabled="4096"/>
   </runtime>
</configuration>
```

<span data-ttu-id="07e24-123">但是在某些情況下，您可能必須修改原始程式碼及重新編譯應用程式。</span><span class="sxs-lookup"><span data-stu-id="07e24-123">However, in some cases, you may have to modify your source code and recompile your application.</span></span>

<span data-ttu-id="07e24-124">若要評估可能的重大變更對您的應用程式的影響，您必須檢閱以下變更清單：</span><span class="sxs-lookup"><span data-stu-id="07e24-124">To assess the impact of possible breaking changes on your application, you must review the following lists of changes:</span></span>

- <span data-ttu-id="07e24-125">[.NET Framework 2.0 中的重大變更](https://go.microsoft.com/fwlink/?LinkId=125263)記錄可能會影響以 .NET Framework 1.1 為目標之應用程式的 .NET Framework 2.0 SP1 變更。</span><span class="sxs-lookup"><span data-stu-id="07e24-125">[Breaking Changes in .NET Framework 2.0](https://go.microsoft.com/fwlink/?LinkId=125263) documents changes in .NET Framework 2.0 SP1 that can affect an application that targets .NET Framework 1.1.</span></span>

- <span data-ttu-id="07e24-126">[.NET Framework 3.5 SP1 中的變更](https://go.microsoft.com/fwlink/?LinkID=186989)記錄在 .NET Framework 3.5 和 .NET Framework 3.5 SP1 之間的變更。</span><span class="sxs-lookup"><span data-stu-id="07e24-126">[Changes in .NET Framework 3.5 SP1](https://go.microsoft.com/fwlink/?LinkID=186989) documents changes between the .NET Framework 3.5 and the .NET Framework 3.5 SP1.</span></span>

- <span data-ttu-id="07e24-127">[.NET Framework 4 移轉問題](net-framework-4-migration-issues.md)中記載 .NET Framework 3.5 SP1 和 .NET Framework 4 之間的變更。</span><span class="sxs-lookup"><span data-stu-id="07e24-127">[.NET Framework 4 Migration Issues](net-framework-4-migration-issues.md) documents changes between the .NET Framework 3.5 SP1 and the .NET Framework 4.</span></span>

## <a name="obsolete-types-and-members"></a><span data-ttu-id="07e24-128">過時的類型和成員</span><span class="sxs-lookup"><span data-stu-id="07e24-128">Obsolete types and members</span></span>

<span data-ttu-id="07e24-129">對於重新設定目標的應用程式和重新編譯的應用程式而言，已被取代的型別和成員的影響有些不同。</span><span class="sxs-lookup"><span data-stu-id="07e24-129">The impact of deprecated types and members is somewhat different for retargeted applications and recompiled applications.</span></span> <span data-ttu-id="07e24-130">使用過時的型別和成員將不會影響重新設定目標的應用程式，除非已經從其組件中實際移除過時的型別或成員。</span><span class="sxs-lookup"><span data-stu-id="07e24-130">The use of obsolete types and members will not affect a retargeted application unless the obsolete type or member has been physically removed from its assembly.</span></span> <span data-ttu-id="07e24-131">重新編譯使用過時型別或成員的應用程式通常會產生編譯器警告，而不是編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="07e24-131">Recompiling an application that uses obsolete types or members usually produces a compiler warning rather than a compiler error.</span></span> <span data-ttu-id="07e24-132">但是在某些情況下，它會產生編譯器錯誤，而且使用過時型別或成員的程式碼無法成功編譯。</span><span class="sxs-lookup"><span data-stu-id="07e24-132">However, in some cases, it produces a compiler error, and code that uses the obsolete type or member does not compile successfully.</span></span> <span data-ttu-id="07e24-133">在此情況下，您必須重新撰寫呼叫過時型別或成員的原始程式碼，然後重新編譯應用程式。</span><span class="sxs-lookup"><span data-stu-id="07e24-133">In this case, you must rewrite the source code that calls the obsolete type or member before you recompile your application.</span></span> <span data-ttu-id="07e24-134">如需過時類型和成員的詳細資訊，請參閱[類別庫中的過時功能](../whats-new/whats-obsolete.md)。</span><span class="sxs-lookup"><span data-stu-id="07e24-134">For more information about obsolete types and members, see [What's Obsolete in the Class Library](../whats-new/whats-obsolete.md).</span></span>

<span data-ttu-id="07e24-135">若要評估自從 .NET Framework 2.0 SP1 發行之後已被取代之型別和成員的影響，請參閱[類別庫中的過時功能](../whats-new/whats-obsolete.md)。</span><span class="sxs-lookup"><span data-stu-id="07e24-135">To assess the impact of types and members that have been deprecated since the release of the .NET Framework 2.0 SP1, see [What's Obsolete in the Class Library](../whats-new/whats-obsolete.md).</span></span> <span data-ttu-id="07e24-136">針對 .NET Framework 2.0 SP1、.NET Framework 3.5 和 .NET Framework 4，檢閱淘汰的型別和成員清單。</span><span class="sxs-lookup"><span data-stu-id="07e24-136">Review the lists of obsolete types and member for the .NET Framework 2.0 SP1, the .NET Framework 3.5, and the .NET Framework 4.</span></span>
