---
title: 強式命名和.NET 程式庫
description: 強式命名的.NET 程式庫的最佳作法建議。
author: jamesnk
ms.author: mairaw
ms.date: 10/16/2018
ms.openlocfilehash: e3f7d443eb9acc84c800ea2611b803733085391c
ms.sourcegitcommit: e42d09e5966dd9fd02847d3e7eeb4ec0877069f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2018
ms.locfileid: "49372801"
---
# <a name="strong-naming"></a><span data-ttu-id="235a2-103">強式命名</span><span class="sxs-lookup"><span data-stu-id="235a2-103">Strong naming</span></span>

<span data-ttu-id="235a2-104">強式命名簽署金鑰，產生的組件是指[強式名稱組件](../../framework/app-domains/strong-named-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="235a2-104">Strong naming refers to signing an assembly with a key, producing a [strong-named assembly](../../framework/app-domains/strong-named-assemblies.md).</span></span> <span data-ttu-id="235a2-105">當強式名稱組件，它會建立唯一的名稱和組件版本號碼為基礎的身分識別，它可以協助防止組件衝突。</span><span class="sxs-lookup"><span data-stu-id="235a2-105">When an assembly is strong-named, it creates a unique identity based on the name and assembly version number, and it can help prevent assembly conflicts.</span></span>

<span data-ttu-id="235a2-106">強式命名的缺點是 Windows 上的.NET Framework 可讓組件具有強式名稱之後嚴格方式載入組件。</span><span class="sxs-lookup"><span data-stu-id="235a2-106">The downside to strong naming is that the .NET Framework on Windows enables strict loading of assemblies once an assembly is strong named.</span></span> <span data-ttu-id="235a2-107">強式名稱組件的參考必須完全符合的組件中，然後再強制開發人員所參考的版本[設定繫結重新導向](../../framework/configure-apps/redirect-assembly-versions.md)時使用的組件：</span><span class="sxs-lookup"><span data-stu-id="235a2-107">A strong-named assembly reference must exactly match the version referenced by an assembly, forcing developers to [configure binding redirects](../../framework/configure-apps/redirect-assembly-versions.md) when using the assembly:</span></span>

```xml
<configuration>
   <runtime>
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
         <dependentAssembly>
            <assemblyIdentity name="myAssembly" publicKeyToken="32ab4ba45e0a69a1" culture="neutral" />
            <bindingRedirect oldVersion="1.0.0.0" newVersion="2.0.0.0"/>
         </dependentAssembly>
      </assemblyBinding>
   </runtime>
</configuration>
```

<span data-ttu-id="235a2-108">當強式命名抱怨.NET 開發人員時，什麼它們通常抱怨是嚴格的組件載入。</span><span class="sxs-lookup"><span data-stu-id="235a2-108">When .NET developers complain about strong naming, what they're usually complaining about is strict assembly loading.</span></span> <span data-ttu-id="235a2-109">幸運的是，這是問題隔離至.NET Framework。</span><span class="sxs-lookup"><span data-stu-id="235a2-109">Fortunately, this issue is isolated to the .NET Framework.</span></span> <span data-ttu-id="235a2-110">.NET core、 Xamarin、 UWP 和其他大部分的.NET 實作不需要嚴格的組件載入，並移除強式命名的主要缺點。</span><span class="sxs-lookup"><span data-stu-id="235a2-110">.NET Core, Xamarin, UWP, and most other .NET implementations don't have strict assembly loading and removes the main downside of strong naming.</span></span>

<span data-ttu-id="235a2-111">強式命名的一個重要層面是它是病毒式： 強式命名組件可以只參考其他強式名稱組件。</span><span class="sxs-lookup"><span data-stu-id="235a2-111">One important aspect of strong naming is that it's viral: a strong named assembly can only reference other strong named assemblies.</span></span> <span data-ttu-id="235a2-112">如果您的程式庫不強式命名，您已排除的開發人員所建置的應用程式庫需要使用它的強式命名。</span><span class="sxs-lookup"><span data-stu-id="235a2-112">If your library isn't strong named, then you have excluded developers who are building an application or library that needs strong naming from using it.</span></span>

<span data-ttu-id="235a2-113">強式命名的優點為：</span><span class="sxs-lookup"><span data-stu-id="235a2-113">The benefits of strong naming are:</span></span>

1. <span data-ttu-id="235a2-114">組件可參考，並由其他強式名稱組件中。</span><span class="sxs-lookup"><span data-stu-id="235a2-114">The assembly can be referenced and used by other strong-named assemblies.</span></span>
2. <span data-ttu-id="235a2-115">組件可以儲存在全域組件快取 (GAC) 中。</span><span class="sxs-lookup"><span data-stu-id="235a2-115">The assembly can be stored in the Global Assembly Cache (GAC).</span></span>
3. <span data-ttu-id="235a2-116">組件可以載入組件的其他版本並存。</span><span class="sxs-lookup"><span data-stu-id="235a2-116">The assembly can be loaded side by side with other versions of the assembly.</span></span> <span data-ttu-id="235a2-117">使用外掛程式架構的應用程式通常需要並排顯示的組件載入。</span><span class="sxs-lookup"><span data-stu-id="235a2-117">Side-by-side assembly loading is commonly required by applications with plug-in architectures.</span></span>

## <a name="create-strong-named-net-libraries"></a><span data-ttu-id="235a2-118">建立強式命名的.NET 程式庫</span><span class="sxs-lookup"><span data-stu-id="235a2-118">Create strong named .NET libraries</span></span>

<span data-ttu-id="235a2-119">您應該強式命名您的開放原始碼.NET 程式庫。</span><span class="sxs-lookup"><span data-stu-id="235a2-119">You should strong name your open-source .NET libraries.</span></span> <span data-ttu-id="235a2-120">強式命名組件可確保大部分的人可以使用它，並嚴格的組件載入僅會影響在.NET Framework。</span><span class="sxs-lookup"><span data-stu-id="235a2-120">Strong naming an assembly ensures the most people can use it, and strict assembly loading only affects the .NET Framework.</span></span>

> [!NOTE]
> <span data-ttu-id="235a2-121">本指南旨在公開分散式的.NET 程式庫，例如在 NuGet.org 上發行的.NET 程式庫。大部分的.NET 應用程式不需要強式命名，並不應該根據預設。</span><span class="sxs-lookup"><span data-stu-id="235a2-121">This guidance is specific to publicly distributed .NET libraries, such as .NET libraries published on NuGet.org. Strong naming is not required by most .NET applications and should not be done by default.</span></span>

<span data-ttu-id="235a2-122">**請考慮 ✔️**強式命名您的程式庫組件。</span><span class="sxs-lookup"><span data-stu-id="235a2-122">**✔️ CONSIDER** strong naming your library's assemblies.</span></span>

<span data-ttu-id="235a2-123">**請考慮 ✔️**簽入到原始檔控制系統使用的強式名稱的金鑰。</span><span class="sxs-lookup"><span data-stu-id="235a2-123">**✔️ CONSIDER** checking in the key used to strong name into your source control system.</span></span>

> <span data-ttu-id="235a2-124">公開可用的金鑰可讓開發人員修改及編譯您的程式庫程式碼使用相同的金鑰。</span><span class="sxs-lookup"><span data-stu-id="235a2-124">A publicly available key lets developers modify and recompile your library source code with the same key.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="235a2-125">時需要密碼編譯的身分識別，則[Authenticode](/windows-hardware/drivers/install/authenticode)並[NuGet 套件簽署](/nuget/create-packages/sign-a-package)建議。</span><span class="sxs-lookup"><span data-stu-id="235a2-125">When a cryptographic identity is desired, [Authenticode](/windows-hardware/drivers/install/authenticode) and [NuGet Package Signing](/nuget/create-packages/sign-a-package) are recommended.</span></span> <span data-ttu-id="235a2-126">強式命名不應該使用的安全性考量。</span><span class="sxs-lookup"><span data-stu-id="235a2-126">Strong naming should not be used for security considerations.</span></span>

<span data-ttu-id="235a2-127">**請考慮 ✔️**遞增組件版本，只有主要版本變更，以協助使用者減少繫結重新導向，以及要更新的頻率。</span><span class="sxs-lookup"><span data-stu-id="235a2-127">**✔️ CONSIDER** incrementing the assembly version on only major version changes to help users reduce binding redirects, and how often they're updated.</span></span>

> <span data-ttu-id="235a2-128">深入了解[版本控制和組件版本](./versioning.md#assembly-version)。</span><span class="sxs-lookup"><span data-stu-id="235a2-128">Read more about [versioning and the assembly version](./versioning.md#assembly-version).</span></span>

<span data-ttu-id="235a2-129">**不這麼做 ❌**新增、 移除或變更的強式命名的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="235a2-129">**❌ DO NOT** add, remove, or change the strong naming key.</span></span>

> <span data-ttu-id="235a2-130">修改組件的強式命名金鑰變更組件的識別，並且中斷編譯的程式碼使用它。</span><span class="sxs-lookup"><span data-stu-id="235a2-130">Modifying an assembly's strong naming key changes the assembly's identity and breaks compiled code that uses it.</span></span> <span data-ttu-id="235a2-131">如需詳細資訊，請參閱 <<c0> [ 二進位的重大變更](./breaking-changes.md#binary-breaking-change)。</span><span class="sxs-lookup"><span data-stu-id="235a2-131">For more information, see [binary breaking changes](./breaking-changes.md#binary-breaking-change).</span></span>

<span data-ttu-id="235a2-132">**不這麼做 ❌**發佈您的媒體櫃的強式名稱，且非強式名稱版本。</span><span class="sxs-lookup"><span data-stu-id="235a2-132">**❌ DO NOT** publish strong-named and non-strong-named versions of your library.</span></span> <span data-ttu-id="235a2-133">例如，`Contoso.Api` 和 `Contoso.Api.StrongNamed`。</span><span class="sxs-lookup"><span data-stu-id="235a2-133">For example, `Contoso.Api` and `Contoso.Api.StrongNamed`.</span></span>

> <span data-ttu-id="235a2-134">發佈兩個套件分岔程式開發人員最系統。</span><span class="sxs-lookup"><span data-stu-id="235a2-134">Publishing two packages forks your developer eco-system.</span></span> <span data-ttu-id="235a2-135">此外，如果應用程式最後會根據這兩個封裝開發人員可能會遇到類型名稱衝突。</span><span class="sxs-lookup"><span data-stu-id="235a2-135">Also, if an application ends up depending on both packages the developer can encounter type name conflicts.</span></span> <span data-ttu-id="235a2-136">.NET 是而言它們是不同的組件中的不同類型。</span><span class="sxs-lookup"><span data-stu-id="235a2-136">As far as .NET is concerned they are different types in different assemblies.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="235a2-137">[上一頁](./cross-platform-targeting.md)
[下一頁](./nuget.md)</span><span class="sxs-lookup"><span data-stu-id="235a2-137">[Previous](./cross-platform-targeting.md)
[Next](./nuget.md)</span></span>
