---
title: 強式命名與 .NET 程式庫
description: .NET 程式庫強式命名的最佳做法建議。
author: jamesnk
ms.author: mairaw
ms.date: 10/16/2018
ms.openlocfilehash: 3a623f65d95d776e45af245a1fe241cc5ee25b93
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2019
ms.locfileid: "70968975"
---
# <a name="strong-naming"></a><span data-ttu-id="c0159-103">強式命名</span><span class="sxs-lookup"><span data-stu-id="c0159-103">Strong naming</span></span>

<span data-ttu-id="c0159-104">強式命名是指使用金鑰對組件進行簽名，進而產生[強式名稱組件](../assembly/strong-named.md)。</span><span class="sxs-lookup"><span data-stu-id="c0159-104">Strong naming refers to signing an assembly with a key, producing a [strong-named assembly](../assembly/strong-named.md).</span></span> <span data-ttu-id="c0159-105">當組件具有強式名稱時，它會根據名稱與組件版本號碼建立唯一身分識別，而且它可以協助防止組件衝突。</span><span class="sxs-lookup"><span data-stu-id="c0159-105">When an assembly is strong-named, it creates a unique identity based on the name and assembly version number, and it can help prevent assembly conflicts.</span></span>

<span data-ttu-id="c0159-106">強式命名的缺點是，一旦組件具有強式名稱，Windows 上的 .NET Framework 就會啟用嚴格的組件載入。</span><span class="sxs-lookup"><span data-stu-id="c0159-106">The downside to strong naming is that the .NET Framework on Windows enables strict loading of assemblies once an assembly is strong named.</span></span> <span data-ttu-id="c0159-107">強式名稱組件參考必須與組件參考的版本完全符合，以強制開發人員在使用組件時[設定繫結重新導向](../../framework/configure-apps/redirect-assembly-versions.md)：</span><span class="sxs-lookup"><span data-stu-id="c0159-107">A strong-named assembly reference must exactly match the version referenced by an assembly, forcing developers to [configure binding redirects](../../framework/configure-apps/redirect-assembly-versions.md) when using the assembly:</span></span>

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

<span data-ttu-id="c0159-108">當 .NET 開發人員抱怨強式命名時，他們通常抱怨的是嚴格的組件載入。</span><span class="sxs-lookup"><span data-stu-id="c0159-108">When .NET developers complain about strong naming, what they're usually complaining about is strict assembly loading.</span></span> <span data-ttu-id="c0159-109">幸運的是，只有 .NET Framework 會有此問題。</span><span class="sxs-lookup"><span data-stu-id="c0159-109">Fortunately, this issue is isolated to the .NET Framework.</span></span> <span data-ttu-id="c0159-110">.NET core、Xamarin、UWP 與其他大部分的 .NET 實作沒有嚴格的組件載入，且移除了強式命名的主要缺點。</span><span class="sxs-lookup"><span data-stu-id="c0159-110">.NET Core, Xamarin, UWP, and most other .NET implementations don't have strict assembly loading and removes the main downside of strong naming.</span></span>

<span data-ttu-id="c0159-111">強式命名的一個重要層面是它是病毒式：強式命名組件只能參考其他強式名稱組件。</span><span class="sxs-lookup"><span data-stu-id="c0159-111">One important aspect of strong naming is that it's viral: a strong named assembly can only reference other strong named assemblies.</span></span> <span data-ttu-id="c0159-112">如果您的程式庫不是強式命名，那麼您已經排除了正在建置需要進行強式命名之應用程式或程式庫的開發人員，使其無法使用它。</span><span class="sxs-lookup"><span data-stu-id="c0159-112">If your library isn't strong named, then you have excluded developers who are building an application or library that needs strong naming from using it.</span></span>

<span data-ttu-id="c0159-113">強式命名的優點為：</span><span class="sxs-lookup"><span data-stu-id="c0159-113">The benefits of strong naming are:</span></span>

1. <span data-ttu-id="c0159-114">組件可以被其他強式名稱組件參考及使用。</span><span class="sxs-lookup"><span data-stu-id="c0159-114">The assembly can be referenced and used by other strong-named assemblies.</span></span>
2. <span data-ttu-id="c0159-115">組件可以儲存於全域組件快取 (GAC)。</span><span class="sxs-lookup"><span data-stu-id="c0159-115">The assembly can be stored in the Global Assembly Cache (GAC).</span></span>
3. <span data-ttu-id="c0159-116">組件可以組件的其他版本並存載入。</span><span class="sxs-lookup"><span data-stu-id="c0159-116">The assembly can be loaded side by side with other versions of the assembly.</span></span> <span data-ttu-id="c0159-117">具有外掛程式架構的應用程式通常需要並存組件載入。</span><span class="sxs-lookup"><span data-stu-id="c0159-117">Side-by-side assembly loading is commonly required by applications with plug-in architectures.</span></span>

## <a name="create-strong-named-net-libraries"></a><span data-ttu-id="c0159-118">建立強式命名的 .NET 程式庫</span><span class="sxs-lookup"><span data-stu-id="c0159-118">Create strong named .NET libraries</span></span>

<span data-ttu-id="c0159-119">您應該為您的開放原始碼 .NET 程式庫進行強式命名。</span><span class="sxs-lookup"><span data-stu-id="c0159-119">You should strong name your open-source .NET libraries.</span></span> <span data-ttu-id="c0159-120">強式命名組件可確保大部分的人可以使用它，而嚴格的組件載入只會影響 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="c0159-120">Strong naming an assembly ensures the most people can use it, and strict assembly loading only affects the .NET Framework.</span></span>

> [!NOTE]
> <span data-ttu-id="c0159-121">此指南僅適用於公開的分散式 .NET 程式庫，例如在 NuGet.org 上發行的 .NET 程式庫。大部分的 .NET 應用程式都不需要強式命名，根據預設不應該這樣做。</span><span class="sxs-lookup"><span data-stu-id="c0159-121">This guidance is specific to publicly distributed .NET libraries, such as .NET libraries published on NuGet.org. Strong naming is not required by most .NET applications and should not be done by default.</span></span>

<span data-ttu-id="c0159-122">**✔️ 考慮**為您的程式庫組件進行強式命名。</span><span class="sxs-lookup"><span data-stu-id="c0159-122">**✔️ CONSIDER** strong naming your library's assemblies.</span></span>

<span data-ttu-id="c0159-123">**✔️ 考慮**將強式命名金鑰新增至您的原始檔控制系統。</span><span class="sxs-lookup"><span data-stu-id="c0159-123">**✔️ CONSIDER** adding the strong naming key to your source control system.</span></span>

> <span data-ttu-id="c0159-124">公開可用的金鑰可讓開發人員使用相同的金鑰修改及編譯您的程式庫原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="c0159-124">A publicly available key lets developers modify and recompile your library source code with the same key.</span></span>
> 
> <span data-ttu-id="c0159-125">如果過去曾使用強式命名金鑰在[部分信任案例](/dotnet/framework/misc/using-libraries-from-partially-trusted-code)中授與特殊權限，則不應將它公開。</span><span class="sxs-lookup"><span data-stu-id="c0159-125">You shouldn't make the strong naming key public if it has been used in the past to give special permissions in [partial-trust scenarios](/dotnet/framework/misc/using-libraries-from-partially-trusted-code).</span></span> <span data-ttu-id="c0159-126">否則，您可能會危及現有的環境。</span><span class="sxs-lookup"><span data-stu-id="c0159-126">Otherwise, you might compromise existing environments.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c0159-127">當需要程式碼發行者的身分識別時，建議使用 [Authenticode](/windows-hardware/drivers/install/authenticode) 與 [NuGet 套件簽署](/nuget/create-packages/sign-a-package)。</span><span class="sxs-lookup"><span data-stu-id="c0159-127">When the identity of the publisher of the code is desired, [Authenticode](/windows-hardware/drivers/install/authenticode) and [NuGet Package Signing](/nuget/create-packages/sign-a-package) are recommended.</span></span> <span data-ttu-id="c0159-128">程式碼存取安全性 (CAS) 不應作為安全性風險降低機制使用。</span><span class="sxs-lookup"><span data-stu-id="c0159-128">Code Access Security (CAS) should not be used as a security mitigation.</span></span>

<span data-ttu-id="c0159-129">**✔️ 考慮**僅在主要版本變更時遞增組件版本，以協助使用者減少繫結重新導向，以及更新它們的頻率。</span><span class="sxs-lookup"><span data-stu-id="c0159-129">**✔️ CONSIDER** incrementing the assembly version on only major version changes to help users reduce binding redirects, and how often they're updated.</span></span>

> <span data-ttu-id="c0159-130">深入了解[版本控制與組件版本](./versioning.md#assembly-version)。</span><span class="sxs-lookup"><span data-stu-id="c0159-130">Read more about [versioning and the assembly version](./versioning.md#assembly-version).</span></span>

<span data-ttu-id="c0159-131">**❌ 請不要**新增、移除或變更強式命名金鑰。</span><span class="sxs-lookup"><span data-stu-id="c0159-131">**❌ DO NOT** add, remove, or change the strong naming key.</span></span>

> <span data-ttu-id="c0159-132">修改組件的強式命名金鑰會變更組件的身分識別，並且中斷使用它的編譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="c0159-132">Modifying an assembly's strong naming key changes the assembly's identity and breaks compiled code that uses it.</span></span> <span data-ttu-id="c0159-133">如需詳細資訊，請參閱[二進位中斷性變更](./breaking-changes.md#binary-breaking-change)。</span><span class="sxs-lookup"><span data-stu-id="c0159-133">For more information, see [binary breaking changes](./breaking-changes.md#binary-breaking-change).</span></span>

<span data-ttu-id="c0159-134">**❌ 禁止**發行程式庫的強式名稱和非強式名稱版本。</span><span class="sxs-lookup"><span data-stu-id="c0159-134">**❌ DO NOT** publish strong-named and non-strong-named versions of your library.</span></span> <span data-ttu-id="c0159-135">例如，`Contoso.Api` 和 `Contoso.Api.StrongNamed`。</span><span class="sxs-lookup"><span data-stu-id="c0159-135">For example, `Contoso.Api` and `Contoso.Api.StrongNamed`.</span></span>

> <span data-ttu-id="c0159-136">發佈兩個套件會派生您的開發人員生態系統。</span><span class="sxs-lookup"><span data-stu-id="c0159-136">Publishing two packages forks your developer eco-system.</span></span> <span data-ttu-id="c0159-137">此外，如果應用程式最後根據這兩個套件，開發人員可能會遇到類型名稱衝突。</span><span class="sxs-lookup"><span data-stu-id="c0159-137">Also, if an application ends up depending on both packages the developer can encounter type name conflicts.</span></span> <span data-ttu-id="c0159-138">就 .NET 而言，它們在不同的組件中是不同的類型。</span><span class="sxs-lookup"><span data-stu-id="c0159-138">As far as .NET is concerned they are different types in different assemblies.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c0159-139">[上一頁](cross-platform-targeting.md)
>[下一頁](nuget.md)</span><span class="sxs-lookup"><span data-stu-id="c0159-139">[Previous](cross-platform-targeting.md)
[Next](nuget.md)</span></span>
