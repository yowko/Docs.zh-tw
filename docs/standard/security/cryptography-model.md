---
title: .NET 密碼編譯模型
description: 在 .NET 中審視一般密碼編譯演算法的實作為。 瞭解物件繼承、串流設計、& 設定的可延伸加密模型。
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [.NET], model
- encryption [.NET], model
ms.assetid: 12fecad4-fbab-432a-bade-2f05976a2971
ms.openlocfilehash: f9ec08992cb8db8f81f11de661612e1b7d15131c
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94831113"
---
# <a name="net-cryptography-model"></a><span data-ttu-id="cc58e-104">.NET 密碼編譯模型</span><span class="sxs-lookup"><span data-stu-id="cc58e-104">.NET Cryptography Model</span></span>

<span data-ttu-id="cc58e-105">.NET 提供許多標準密碼編譯演算法的執行，而 .NET 加密模型則是可擴充的。</span><span class="sxs-lookup"><span data-stu-id="cc58e-105">.NET provides implementations of many standard cryptographic algorithms, and the .NET cryptography model is extensible.</span></span>

## <a name="object-inheritance"></a><span data-ttu-id="cc58e-106">物件繼承</span><span class="sxs-lookup"><span data-stu-id="cc58e-106">Object Inheritance</span></span>

<span data-ttu-id="cc58e-107">.NET 密碼編譯系統會實作為衍生類別繼承的可擴充模式。</span><span class="sxs-lookup"><span data-stu-id="cc58e-107">The .NET cryptography system implements an extensible pattern of derived class inheritance.</span></span> <span data-ttu-id="cc58e-108">階層如下所述：</span><span class="sxs-lookup"><span data-stu-id="cc58e-108">The hierarchy is as follows:</span></span>

- <span data-ttu-id="cc58e-109">演算法型別類別，例如 <xref:System.Security.Cryptography.SymmetricAlgorithm> 、  <xref:System.Security.Cryptography.AsymmetricAlgorithm> 或 <xref:System.Security.Cryptography.HashAlgorithm> 。</span><span class="sxs-lookup"><span data-stu-id="cc58e-109">Algorithm type class, such as <xref:System.Security.Cryptography.SymmetricAlgorithm>,  <xref:System.Security.Cryptography.AsymmetricAlgorithm>, or <xref:System.Security.Cryptography.HashAlgorithm>.</span></span> <span data-ttu-id="cc58e-110">這個層級是抽象的。</span><span class="sxs-lookup"><span data-stu-id="cc58e-110">This level is abstract.</span></span>

- <span data-ttu-id="cc58e-111">繼承自演算法類型類別的演算法類別；例如，<xref:System.Security.Cryptography.Aes><xref:System.Security.Cryptography.RSA> 或 <xref:System.Security.Cryptography.ECDiffieHellman>。</span><span class="sxs-lookup"><span data-stu-id="cc58e-111">Algorithm class that inherits from an algorithm type class; for example, <xref:System.Security.Cryptography.Aes>, <xref:System.Security.Cryptography.RSA>, or <xref:System.Security.Cryptography.ECDiffieHellman>.</span></span> <span data-ttu-id="cc58e-112">這個層級是抽象的。</span><span class="sxs-lookup"><span data-stu-id="cc58e-112">This level is abstract.</span></span>

- <span data-ttu-id="cc58e-113">繼承自演算法類別的演算法類別實作；例如，<xref:System.Security.Cryptography.AesManaged><xref:System.Security.Cryptography.RC2CryptoServiceProvider> 或 <xref:System.Security.Cryptography.ECDiffieHellmanCng>。</span><span class="sxs-lookup"><span data-stu-id="cc58e-113">Implementation of an algorithm class that inherits from an algorithm class; for example, <xref:System.Security.Cryptography.AesManaged>, <xref:System.Security.Cryptography.RC2CryptoServiceProvider>, or <xref:System.Security.Cryptography.ECDiffieHellmanCng>.</span></span> <span data-ttu-id="cc58e-114">這個層級已完全實作。</span><span class="sxs-lookup"><span data-stu-id="cc58e-114">This level is fully implemented.</span></span>

<span data-ttu-id="cc58e-115">這種衍生類別的模式可讓您加入新的演算法，或現有演算法的新實作為。</span><span class="sxs-lookup"><span data-stu-id="cc58e-115">This pattern of derived classes lets you add a new algorithm or a new implementation of an existing algorithm.</span></span> <span data-ttu-id="cc58e-116">例如，若要建立新的公開金鑰演算法，您會繼承自 <xref:System.Security.Cryptography.AsymmetricAlgorithm> 類別。</span><span class="sxs-lookup"><span data-stu-id="cc58e-116">For example, to create a new public-key algorithm, you would inherit from the <xref:System.Security.Cryptography.AsymmetricAlgorithm> class.</span></span> <span data-ttu-id="cc58e-117">若要建立特定演算法的新實作，您會建立該演算法的非抽象衍生類別。</span><span class="sxs-lookup"><span data-stu-id="cc58e-117">To create a new implementation of a specific algorithm, you would create a non-abstract derived class of that algorithm.</span></span>

## <a name="how-algorithms-are-implemented-in-net"></a><span data-ttu-id="cc58e-118">如何在 .NET 中執行演算法</span><span class="sxs-lookup"><span data-stu-id="cc58e-118">How Algorithms Are Implemented in .NET</span></span>

<span data-ttu-id="cc58e-119">做為可供演算法使用的不同實作方式範例，請考慮對稱演算法。</span><span class="sxs-lookup"><span data-stu-id="cc58e-119">As an example of the different implementations available for an algorithm, consider symmetric algorithms.</span></span> <span data-ttu-id="cc58e-120">所有對稱演算法的基底是 <xref:System.Security.Cryptography.SymmetricAlgorithm> 由 <xref:System.Security.Cryptography.Aes> 、 <xref:System.Security.Cryptography.TripleDES> 和其他不再建議的所繼承。</span><span class="sxs-lookup"><span data-stu-id="cc58e-120">The base for all symmetric algorithms is <xref:System.Security.Cryptography.SymmetricAlgorithm>, which is inherited by <xref:System.Security.Cryptography.Aes>, <xref:System.Security.Cryptography.TripleDES>, and others that are no longer recommended.</span></span>

<span data-ttu-id="cc58e-121"><xref:System.Security.Cryptography.Aes> 繼承自 <xref:System.Security.Cryptography.AesCryptoServiceProvider> 、 <xref:System.Security.Cryptography.AesCng> 和 <xref:System.Security.Cryptography.AesManaged> 。</span><span class="sxs-lookup"><span data-stu-id="cc58e-121"><xref:System.Security.Cryptography.Aes> is inherited by <xref:System.Security.Cryptography.AesCryptoServiceProvider>, <xref:System.Security.Cryptography.AesCng>, and <xref:System.Security.Cryptography.AesManaged>.</span></span>

<span data-ttu-id="cc58e-122">在 Windows 上的 .NET Framework：</span><span class="sxs-lookup"><span data-stu-id="cc58e-122">In .NET Framework on Windows:</span></span>

* <span data-ttu-id="cc58e-123">`*CryptoServiceProvider` 演算法類別（例如 <xref:System.Security.Cryptography.AesCryptoServiceProvider> ）是在 Windows 密碼編譯 API 周圍的包裝函式， (CAPI) 的演算法執行。</span><span class="sxs-lookup"><span data-stu-id="cc58e-123">`*CryptoServiceProvider` algorithm classes, such as <xref:System.Security.Cryptography.AesCryptoServiceProvider>, are wrappers around the Windows Cryptography API (CAPI) implementation of an algorithm.</span></span>
* <span data-ttu-id="cc58e-124">`*Cng` 演算法類別（例如 <xref:System.Security.Cryptography.ECDiffieHellmanCng> ）是 Windows 新一代密碼編譯 (CNG) 實作為包裝函式。</span><span class="sxs-lookup"><span data-stu-id="cc58e-124">`*Cng` algorithm classes, such as <xref:System.Security.Cryptography.ECDiffieHellmanCng>, are wrappers around the Windows Cryptography Next Generation (CNG) implementation.</span></span>
* <span data-ttu-id="cc58e-125">`*Managed` 類別（例如 <xref:System.Security.Cryptography.AesManaged> ）完全以 managed 程式碼撰寫。</span><span class="sxs-lookup"><span data-stu-id="cc58e-125">`*Managed` classes, such as <xref:System.Security.Cryptography.AesManaged>, are written entirely in managed code.</span></span> <span data-ttu-id="cc58e-126">`*Managed` (FIPS) 的聯邦資訊處理標準尚未認證，而且可能會比和包裝函式 `*CryptoServiceProvider` 類別更慢 `*Cng` 。</span><span class="sxs-lookup"><span data-stu-id="cc58e-126">`*Managed` implementations are not certified by the Federal Information Processing Standards (FIPS), and may be slower than the `*CryptoServiceProvider` and `*Cng` wrapper classes.</span></span>

<span data-ttu-id="cc58e-127">在 .NET Core 和 .NET 5 和更新版本中，所有的實類別 (`*CryptoServiceProvider` 、 `*Managed` 和 `*Cng`) 都是作業系統 (OS) 演算法的包裝函式。</span><span class="sxs-lookup"><span data-stu-id="cc58e-127">In .NET Core and .NET 5 and later versions, all implementation classes (`*CryptoServiceProvider`, `*Managed`, and `*Cng`) are wrappers for the operating system (OS) algorithms.</span></span> <span data-ttu-id="cc58e-128">如果 OS 演算法是經過 FIPS 認證，則 .NET 會使用 FIPS 認證的演算法。</span><span class="sxs-lookup"><span data-stu-id="cc58e-128">If the OS algorithms are FIPS-certified, then .NET uses FIPS-certified algorithms.</span></span> <span data-ttu-id="cc58e-129">如需詳細資訊，請參閱 [跨平臺密碼](cross-platform-cryptography.md)編譯。</span><span class="sxs-lookup"><span data-stu-id="cc58e-129">For more information, see [Cross-Platform Cryptography](cross-platform-cryptography.md).</span></span>

<span data-ttu-id="cc58e-130">在大多數情況下，您不需要直接參考演算法實類別，例如 `AesCryptoServiceProvider` 。</span><span class="sxs-lookup"><span data-stu-id="cc58e-130">In most cases, you don't need to directly reference an algorithm implementation class, such as `AesCryptoServiceProvider`.</span></span> <span data-ttu-id="cc58e-131">您通常需要的方法和屬性位於基底演算法類別，例如 `Aes` 。</span><span class="sxs-lookup"><span data-stu-id="cc58e-131">The methods and properties you typically need are on the base algorithm class, such as `Aes`.</span></span> <span data-ttu-id="cc58e-132">使用基底演算法類別上的 factory 方法建立預設實類別的實例，並參考基底演算法類別。</span><span class="sxs-lookup"><span data-stu-id="cc58e-132">Create an instance of a default implementation class by using a factory method on the base algorithm class, and refer to the base algorithm class.</span></span> <span data-ttu-id="cc58e-133">例如，請參閱下列範例中反白顯示的程式程式碼：</span><span class="sxs-lookup"><span data-stu-id="cc58e-133">For example, see the highlighted line of code in the following example:</span></span>

:::code language="csharp" source="snippets/encrypting-data/csharp/aes-encrypt.cs" highlight="16":::
:::code language="vb" source="snippets/encrypting-data/vb/aes-encrypt.vb" highlight="12":::

## <a name="cryptographic-configuration"></a><span data-ttu-id="cc58e-134">密碼編譯組態</span><span class="sxs-lookup"><span data-stu-id="cc58e-134">Cryptographic Configuration</span></span>

<span data-ttu-id="cc58e-135">密碼編譯設定可讓您將演算法的特定執行解析為演算法名稱，允許 .NET 密碼編譯類別的擴充性。</span><span class="sxs-lookup"><span data-stu-id="cc58e-135">Cryptographic configuration lets you resolve a specific implementation of an algorithm to an algorithm name, allowing extensibility of the .NET cryptography classes.</span></span> <span data-ttu-id="cc58e-136">您可以加入自己的演算法硬體或軟體實作，並將實作對應到您選擇的演算法名稱。</span><span class="sxs-lookup"><span data-stu-id="cc58e-136">You can add your own hardware or software implementation of an algorithm and map the implementation to the algorithm name of your choice.</span></span> <span data-ttu-id="cc58e-137">如果在組態檔中未指定演算法，會使用預設設定。</span><span class="sxs-lookup"><span data-stu-id="cc58e-137">If an algorithm is not specified in the configuration file, the default settings are used.</span></span>

## <a name="choosing-an-algorithm"></a><span data-ttu-id="cc58e-138">選擇演算法</span><span class="sxs-lookup"><span data-stu-id="cc58e-138">Choosing an Algorithm</span></span>

<span data-ttu-id="cc58e-139">您選取演算法時可能有不同的原因：例如，為了資料完整性、為了資料隱私權，或是為了產生金鑰。</span><span class="sxs-lookup"><span data-stu-id="cc58e-139">You can select an algorithm for different reasons: for example, for data integrity, for data privacy, or to generate a key.</span></span> <span data-ttu-id="cc58e-140">對稱和雜湊演算法是要用來出於完整性的原因 (防止變更) 或隱私權的原因 (防止檢視) 保護資料。</span><span class="sxs-lookup"><span data-stu-id="cc58e-140">Symmetric and hash algorithms are intended for protecting data for either integrity reasons (protect from change) or privacy reasons (protect from viewing).</span></span> <span data-ttu-id="cc58e-141">雜湊演算法主要用於資料完整性。</span><span class="sxs-lookup"><span data-stu-id="cc58e-141">Hash algorithms are used primarily for data integrity.</span></span>

<span data-ttu-id="cc58e-142">以下是依應用程式的建議演算法清單：</span><span class="sxs-lookup"><span data-stu-id="cc58e-142">Here is a list of recommended algorithms by application:</span></span>

- <span data-ttu-id="cc58e-143">資料隱私權：</span><span class="sxs-lookup"><span data-stu-id="cc58e-143">Data privacy:</span></span>
  - <xref:System.Security.Cryptography.Aes>
- <span data-ttu-id="cc58e-144">資料完整性：</span><span class="sxs-lookup"><span data-stu-id="cc58e-144">Data integrity:</span></span>
  - <xref:System.Security.Cryptography.HMACSHA256>
  - <xref:System.Security.Cryptography.HMACSHA512>
- <span data-ttu-id="cc58e-145">數位簽章：</span><span class="sxs-lookup"><span data-stu-id="cc58e-145">Digital signature:</span></span>
  - <xref:System.Security.Cryptography.ECDsa>
  - <xref:System.Security.Cryptography.RSA>
- <span data-ttu-id="cc58e-146">金鑰交換：</span><span class="sxs-lookup"><span data-stu-id="cc58e-146">Key exchange:</span></span>
  - <xref:System.Security.Cryptography.ECDiffieHellman>
  - <xref:System.Security.Cryptography.RSA>
- <span data-ttu-id="cc58e-147">亂數產生：</span><span class="sxs-lookup"><span data-stu-id="cc58e-147">Random number generation:</span></span>
  - <xref:System.Security.Cryptography.RandomNumberGenerator.Create%2A?displayProperty=nameWithType>
- <span data-ttu-id="cc58e-148">從密碼產生金鑰：</span><span class="sxs-lookup"><span data-stu-id="cc58e-148">Generating a key from a password:</span></span>
  - <xref:System.Security.Cryptography.Rfc2898DeriveBytes>

## <a name="see-also"></a><span data-ttu-id="cc58e-149">請參閱</span><span class="sxs-lookup"><span data-stu-id="cc58e-149">See also</span></span>

- [<span data-ttu-id="cc58e-150">密碼編譯服務</span><span class="sxs-lookup"><span data-stu-id="cc58e-150">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="cc58e-151">跨平臺密碼編譯</span><span class="sxs-lookup"><span data-stu-id="cc58e-151">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="cc58e-152">ASP.NET Core 資料保護</span><span class="sxs-lookup"><span data-stu-id="cc58e-152">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
