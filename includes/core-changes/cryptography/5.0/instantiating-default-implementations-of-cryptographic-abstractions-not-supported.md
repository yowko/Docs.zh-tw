---
ms.openlocfilehash: 8198eca5b9c63d9717260b71ac6687dbf7245f35
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159546"
---
### <a name="instantiating-default-implementations-of-cryptographic-abstractions-is-not-supported"></a><span data-ttu-id="f98c7-101">不支援具現化密碼編譯抽象概念的預設實值</span><span class="sxs-lookup"><span data-stu-id="f98c7-101">Instantiating default implementations of cryptographic abstractions is not supported</span></span>

<span data-ttu-id="f98c7-102">密碼編譯抽象概念上的無參數多載， `Create()` 會因為 .net 5.0 的警告而淘汰。</span><span class="sxs-lookup"><span data-stu-id="f98c7-102">The parameterless `Create()` overloads on cryptographic abstractions are obsolete as warning as of .NET 5.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="f98c7-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="f98c7-103">Change description</span></span>

<span data-ttu-id="f98c7-104">在 .NET Framework 2.0-4.8 中，可以將抽象密碼編譯基本 factory （例如） <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> 設定為傳回不同的演算法。</span><span class="sxs-lookup"><span data-stu-id="f98c7-104">In .NET Framework 2.0 - 4.8, abstract cryptographic primitive factories such as <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> can be configured to return different algorithms.</span></span> <span data-ttu-id="f98c7-105">例如，在預設的 .NET Framework 4.8 安裝上，無參數的靜態方法會傳回 <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> SHA1 演算法的實例，如下列程式碼片段所示。</span><span class="sxs-lookup"><span data-stu-id="f98c7-105">For example, on a default install of .NET Framework 4.8, the parameterless, static method <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> returns an instance of the SHA1 algorithm, as shown in the following snippet.</span></span>

<span data-ttu-id="f98c7-106">**僅 .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="f98c7-106">**.NET Framework only**</span></span>

```csharp
// Return an instance of the default hash algorithm (SHA1).
HashAlgorithm alg = HashAlgorithm.Create();
// Prints 'System.Security.Cryptography.SHA1CryptoServiceProvider'.
Console.WriteLine(alg.GetType());

// Change the default algorithm to be SHA256, not SHA1.
CryptoConfig.AddAlgorithm(typeof(SHA256CryptoServiceProvider), typeof(HashAlgorithm).FullName);
alg = HashAlgorithm.Create();
// Prints 'System.Security.Cryptography.SHA256CryptoServiceProvider'.
Console.WriteLine(alg.GetType());
```

<span data-ttu-id="f98c7-107">您也可以使用 [全電腦](../../../../docs/framework/configure-apps/map-algorithm-names-to-cryptography-classes.md) 設定來變更預設演算法，而不需要以程式設計的 `CryptoConfig` 方式呼叫。</span><span class="sxs-lookup"><span data-stu-id="f98c7-107">You can also use [machine-wide configuration](../../../../docs/framework/configure-apps/map-algorithm-names-to-cryptography-classes.md) to change the default algorithm without needing to call into `CryptoConfig` programmatically.</span></span>

<span data-ttu-id="f98c7-108">在 .NET Core 2.0-3.1 中，抽象密碼編譯基本 factory，例如 <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> 一律擲回 <xref:System.PlatformNotSupportedException> 。</span><span class="sxs-lookup"><span data-stu-id="f98c7-108">In .NET Core 2.0 - 3.1, abstract cryptographic primitive factories such as <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> always throw a <xref:System.PlatformNotSupportedException>.</span></span>

```csharp
// Throws PlatformNotSupportedException on .NET Core.
HashAlgorithm alg = HashAlgorithm.Create();
```

<span data-ttu-id="f98c7-109">在 .NET 5.0 和更新版本中，抽象密碼編譯基本處理站（例如） <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> 會標示為已淘汰，並產生識別碼為的編譯時間警告 `SYSLIB0007` 。</span><span class="sxs-lookup"><span data-stu-id="f98c7-109">In .NET 5.0 and later versions, abstract cryptographic primitive factories such as <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> are marked obsolete and produce a compile-time warning with ID `SYSLIB0007`.</span></span> <span data-ttu-id="f98c7-110">在執行時間，這些方法會繼續擲回 <xref:System.PlatformNotSupportedException> 。</span><span class="sxs-lookup"><span data-stu-id="f98c7-110">At run time, these methods continue to throw a <xref:System.PlatformNotSupportedException>.</span></span>

```csharp
// Throws PlatformNotSupportedException.
// Also produces compile-time warning SYSLIB0007 on .NET 5+.
HashAlgorithm alg = HashAlgorithm.Create();
```

<span data-ttu-id="f98c7-111">這是僅限編譯時期的變更。</span><span class="sxs-lookup"><span data-stu-id="f98c7-111">This is a compile-time only change.</span></span> <span data-ttu-id="f98c7-112">舊版 .NET Core 沒有任何執行時間變更。</span><span class="sxs-lookup"><span data-stu-id="f98c7-112">There is no run-time change from previous versions of .NET Core.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="f98c7-113">只有方法的無參數多載 `Create()` 已過時。</span><span class="sxs-lookup"><span data-stu-id="f98c7-113">Only the parameterless overloads of the `Create()` methods are obsolete.</span></span> <span data-ttu-id="f98c7-114">參數化多載尚未過時，且仍如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="f98c7-114">Parameterized overloads are not obsolete and still function as expected.</span></span>
>
>   ```csharp
>   // Call Create(string), providing an explicit algorithm family name.
>   // Works in .NET Framework, .NET Core, and .NET 5.0+.
>   HashAlgorithm hashAlg = HashAlgorithm.Create("SHA256");
>   ```
>
> - <span data-ttu-id="f98c7-115">*特定*演算法系列的無參數多載 (不是抽象) 不會過時，且將繼續如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="f98c7-115">Parameterless overloads of *specific* algorithm families (not abstractions) are not obsolete, and will continue to function as expected.</span></span>
>
>   ```csharp
>   // Call a specific algorithm family's parameterless Create() ctor.
>   // Works in .NET Framework, .NET Core, and .NET 5.0+.
>   Aes aesAlg = Aes.Create();
>   ```

#### <a name="reason-for-change"></a><span data-ttu-id="f98c7-116">變更的原因</span><span class="sxs-lookup"><span data-stu-id="f98c7-116">Reason for change</span></span>

<span data-ttu-id="f98c7-117">.NET Framework 中的密碼編譯設定系統不再存在於 .NET Core 和 .NET 5.0 + 中，因為舊版系統不允許適當的密碼編譯靈活性。</span><span class="sxs-lookup"><span data-stu-id="f98c7-117">The cryptographic configuration system present in .NET Framework is no longer present in .NET Core and .NET 5.0+, since that legacy system doesn't allow for proper cryptographic agility.</span></span> <span data-ttu-id="f98c7-118">.NET 的回溯相容性需求也會禁止架構更新特定的密碼編譯 Api，以保持密碼編譯的進展。</span><span class="sxs-lookup"><span data-stu-id="f98c7-118">.NET's backward-compatibility requirements also prohibit the framework from updating certain cryptographic APIs to keep up with advances in cryptography.</span></span> <span data-ttu-id="f98c7-119">例如， <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> 當 sha-1 雜湊演算法為最新狀態時，方法就會在 .NET Framework 1.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="f98c7-119">For example, the <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> method was introduced in .NET Framework 1.0, when the SHA-1 hash algorithm was state-of-the-art.</span></span> <span data-ttu-id="f98c7-120">經過二十年後，現在會將 SHA-1 視為已中斷，但我們無法變更 <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> 來傳回不同的演算法。</span><span class="sxs-lookup"><span data-stu-id="f98c7-120">Twenty years have passed, and now SHA-1 is considered broken, but we cannot change <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> to return a different algorithm.</span></span> <span data-ttu-id="f98c7-121">這麼做會導致取用應用程式中的不可接受中斷性變更。</span><span class="sxs-lookup"><span data-stu-id="f98c7-121">Doing so would introduce an unacceptable breaking change in consuming applications.</span></span>

<span data-ttu-id="f98c7-122">最佳做法規定，使用密碼編譯基本類型 (例如 AES、SHA-1 和 RSA) 的程式庫，應能完全掌控它們使用這些基本專案的方式。</span><span class="sxs-lookup"><span data-stu-id="f98c7-122">Best practice dictates that libraries that consume cryptographic primitives (such as AES, SHA-\*, and RSA) should be in full control over how they consume these primitives.</span></span> <span data-ttu-id="f98c7-123">需要後續校對的應用程式應該使用更高層級的程式庫，這些程式庫會包裝這些基本專案，並新增金鑰管理和密碼編譯靈活性功能。</span><span class="sxs-lookup"><span data-stu-id="f98c7-123">Applications that require future-proofing should utilize higher-level libraries that wrap these primitives and add key management and cryptographic agility capabilities.</span></span> <span data-ttu-id="f98c7-124">裝載環境通常會提供這些程式庫。</span><span class="sxs-lookup"><span data-stu-id="f98c7-124">These libraries are often provided by the hosting environment.</span></span> <span data-ttu-id="f98c7-125">其中一個範例是 [ASP。NET 的資料保護程式庫](/aspnet/core/security/data-protection/)，代表呼叫的應用程式處理這些問題。</span><span class="sxs-lookup"><span data-stu-id="f98c7-125">One example is [ASP.NET's Data Protection library](/aspnet/core/security/data-protection/), which handles these concerns on behalf of the calling application.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f98c7-126">引進的版本</span><span class="sxs-lookup"><span data-stu-id="f98c7-126">Version introduced</span></span>

<span data-ttu-id="f98c7-127">5.0 RC1</span><span class="sxs-lookup"><span data-stu-id="f98c7-127">5.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f98c7-128">建議的動作</span><span class="sxs-lookup"><span data-stu-id="f98c7-128">Recommended action</span></span>

- <span data-ttu-id="f98c7-129">建議的動作是將對已淘汰 Api 的呼叫取代為特定演算法的 factory 方法呼叫，例如 <xref:System.Security.Cryptography.Aes.Create?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="f98c7-129">The recommended course of action is to replace calls to the now-obsolete APIs with calls to factory methods for specific algorithms, for example, <xref:System.Security.Cryptography.Aes.Create?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f98c7-130">這可讓您完全掌控要具現化的演算法。</span><span class="sxs-lookup"><span data-stu-id="f98c7-130">This gives you full control over which algorithms are instantiated.</span></span>

- <span data-ttu-id="f98c7-131">如果您需要維持與使用已過時 Api 的 .NET Framework 應用程式所產生之現有承載的相容性，請使用下表中建議的取代。</span><span class="sxs-lookup"><span data-stu-id="f98c7-131">If you need to maintain compatibility with existing payloads generated by .NET Framework apps that use the now-obsolete APIs, use the replacements suggested in the following table.</span></span> <span data-ttu-id="f98c7-132">下表提供從 .NET Framework 預設演算法到其 .NET 5 + 對等專案的對應。</span><span class="sxs-lookup"><span data-stu-id="f98c7-132">The table provides a mapping from .NET Framework default algorithms to their .NET 5+ equivalents.</span></span>

  | <span data-ttu-id="f98c7-133">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="f98c7-133">.NET Framework</span></span> | <span data-ttu-id="f98c7-134">.NET Core/.NET 5.0 + 相容取代</span><span class="sxs-lookup"><span data-stu-id="f98c7-134">.NET Core / .NET 5.0+ compatible replacement</span></span> | <span data-ttu-id="f98c7-135">備註</span><span class="sxs-lookup"><span data-stu-id="f98c7-135">Remarks</span></span> |
  | - | - | - |
  | <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.RSA.Create?displayProperty=nameWithType> | |
  | <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.SHA1.Create?displayProperty=nameWithType> | <span data-ttu-id="f98c7-136">SHA-1 演算法會被視為已中斷。</span><span class="sxs-lookup"><span data-stu-id="f98c7-136">The SHA-1 algorithm is considered broken.</span></span> <span data-ttu-id="f98c7-137">如果可能的話，請考慮使用較強的演算法。</span><span class="sxs-lookup"><span data-stu-id="f98c7-137">Consider using a stronger algorithm if possible.</span></span> <span data-ttu-id="f98c7-138">如需進一步指引，請參閱您的安全性顧問。</span><span class="sxs-lookup"><span data-stu-id="f98c7-138">Consult your security advisor for further guidance.</span></span> |
  | <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.HMACSHA1.%23ctor> | <span data-ttu-id="f98c7-139">大部分新式應用程式不建議採用 HMACSHA1 演算法。</span><span class="sxs-lookup"><span data-stu-id="f98c7-139">The HMACSHA1 algorithm is discouraged for most modern applications.</span></span> <span data-ttu-id="f98c7-140">如果可能的話，請考慮使用較強的演算法。</span><span class="sxs-lookup"><span data-stu-id="f98c7-140">Consider using a stronger algorithm if possible.</span></span> <span data-ttu-id="f98c7-141">如需進一步指引，請參閱您的安全性顧問。</span><span class="sxs-lookup"><span data-stu-id="f98c7-141">Consult your security advisor for further guidance.</span></span> |
  | <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.HMACSHA1.%23ctor> | <span data-ttu-id="f98c7-142">大部分新式應用程式不建議採用 HMACSHA1 演算法。</span><span class="sxs-lookup"><span data-stu-id="f98c7-142">The HMACSHA1 algorithm is discouraged for most modern applications.</span></span> <span data-ttu-id="f98c7-143">如果可能的話，請考慮使用較強的演算法。</span><span class="sxs-lookup"><span data-stu-id="f98c7-143">Consider using a stronger algorithm if possible.</span></span> <span data-ttu-id="f98c7-144">如需進一步指引，請參閱您的安全性顧問。</span><span class="sxs-lookup"><span data-stu-id="f98c7-144">Consult your security advisor for further guidance.</span></span> |
  | <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.Aes.Create?displayProperty=nameWithType> |

- <span data-ttu-id="f98c7-145">如果您必須繼續呼叫過時的無參數多載 `Create()` ，您可以 `SYSLIB0007` 在程式碼中隱藏警告。</span><span class="sxs-lookup"><span data-stu-id="f98c7-145">If you must continue to call the obsolete parameterless `Create()` overloads, you can suppress the `SYSLIB0007` warning in code.</span></span>

  ```csharp
  #pragma warning disable SYSLIB0007 // Disable the warning.
  HashAlgorithm alg = HashAlgorithm.Create(); // Still throws PNSE.
  #pragma warning restore SYSLIB0007 // Re-enable the warning.
  ```

  <span data-ttu-id="f98c7-146">您也可以隱藏專案檔中的警告。</span><span class="sxs-lookup"><span data-stu-id="f98c7-146">You can also suppress the warning in your project file.</span></span> <span data-ttu-id="f98c7-147">這麼做會停用專案內所有原始程式檔的警告。</span><span class="sxs-lookup"><span data-stu-id="f98c7-147">Doing so disables the warning for all source files within the project.</span></span>

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- NoWarn below suppresses SYSLIB0007 project-wide -->
     <NoWarn>$(NoWarn);SYSLIB0007</NoWarn>
    </PropertyGroup>
  </Project>
  ```

  > [!NOTE]
  > <span data-ttu-id="f98c7-148">隱藏 `SYSLIB0007` 只會停用此處所列之密碼編譯 api 的 obsoletion 警告。</span><span class="sxs-lookup"><span data-stu-id="f98c7-148">Suppressing `SYSLIB0007` disables only the obsoletion warnings for the cryptography APIs listed here.</span></span> <span data-ttu-id="f98c7-149">它不會停用任何其他警告。</span><span class="sxs-lookup"><span data-stu-id="f98c7-149">It does not disable any other warnings.</span></span> <span data-ttu-id="f98c7-150">此外，即使您隱藏警告，這些過時的 Api 仍然會 <xref:System.PlatformNotSupportedException> 在執行時間擲回。</span><span class="sxs-lookup"><span data-stu-id="f98c7-150">Additionally, even if you suppress the warning, these obsoleted APIs will still throw a <xref:System.PlatformNotSupportedException> at run time.</span></span>

#### <a name="category"></a><span data-ttu-id="f98c7-151">類別</span><span class="sxs-lookup"><span data-stu-id="f98c7-151">Category</span></span>

- <span data-ttu-id="f98c7-152">密碼編譯</span><span class="sxs-lookup"><span data-stu-id="f98c7-152">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f98c7-153">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="f98c7-153">Affected APIs</span></span>

- <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.HMAC.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.AsymmetricAlgorithm.Create`
- `M:System.Security.Cryptography.HashAlgorithm.Create`
- `M:System.Security.Cryptography.HMAC.Create`
- `M:System.Security.Cryptography.KeyedHashAlgorithm.Create`
- `M:System.Security.Cryptography.SymmetricAlgorithm.Create`

-->
