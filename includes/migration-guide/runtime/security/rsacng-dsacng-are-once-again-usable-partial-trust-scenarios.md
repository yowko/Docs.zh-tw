---
ms.openlocfilehash: 4788f5b80306116e63ee56584d65b862ce0606ee
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497396"
---
### <a name="rsacng-and-dsacng-are-once-again-usable-in-partial-trust-scenarios"></a><span data-ttu-id="2c87f-101">RSACng 和 DSACng 再次可在部分信任案例中使用</span><span class="sxs-lookup"><span data-stu-id="2c87f-101">RSACng and DSACng are once again usable in Partial Trust scenarios</span></span>

#### <a name="details"></a><span data-ttu-id="2c87f-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="2c87f-102">Details</span></span>

<span data-ttu-id="2c87f-103">CngLightup (用於數個較高層級的加密 API，例如 <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=nameWithType>) 和 <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> 在某些情況下依賴完全信任。</span><span class="sxs-lookup"><span data-stu-id="2c87f-103">CngLightup (used in several higher-level crypto apis, such as <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=nameWithType>) and <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> in some cases rely on full trust.</span></span> <span data-ttu-id="2c87f-104">這些包括沒有主張 <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode?displayProperty=nameWithType> 權限的 P/Invoke，以及 <xref:System.Security.Cryptography.CngKey?displayProperty=nameWithType> 具有 <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode?displayProperty=nameWithType> 之權限要求的程式碼路徑。</span><span class="sxs-lookup"><span data-stu-id="2c87f-104">These include P/Invokes without asserting <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode?displayProperty=nameWithType> permissions, and code paths where <xref:System.Security.Cryptography.CngKey?displayProperty=nameWithType> has permission demands for <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode?displayProperty=nameWithType>.</span></span> <span data-ttu-id="2c87f-105">從 .NET Framework 4.6.2 開始，盡量使用 CngLightup 來切換至 <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="2c87f-105">Starting with the .NET Framework 4.6.2, CngLightup was used to switch to <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> wherever possible.</span></span> <span data-ttu-id="2c87f-106">因此，成功使用 <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=nameWithType> 的部分信任應用程式開始失敗，並擲回 <xref:System.Security.SecurityException> 例外狀況。這項變更將新增所需的主張，讓所有使用 CngLightup 的函式具有必要權限。</span><span class="sxs-lookup"><span data-stu-id="2c87f-106">As a result, partial trust apps that successfully used <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=nameWithType> began to fail and throw <xref:System.Security.SecurityException> exceptions.This change adds the required asserts so that all functions using CngLightup have the required permissions.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="2c87f-107">建議</span><span class="sxs-lookup"><span data-stu-id="2c87f-107">Suggestion</span></span>

<span data-ttu-id="2c87f-108">如果 .NET Framework 4.6.2 中的這項變更已對部分信任應用程式產生負面影響，請升級至 .NET Framework 4.7.1。</span><span class="sxs-lookup"><span data-stu-id="2c87f-108">If this change in the .NET Framework 4.6.2 has negatively impacted your partial trust apps, upgrade to the .NET Framework 4.7.1.</span></span>

| <span data-ttu-id="2c87f-109">名稱</span><span class="sxs-lookup"><span data-stu-id="2c87f-109">Name</span></span>    | <span data-ttu-id="2c87f-110">值</span><span class="sxs-lookup"><span data-stu-id="2c87f-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="2c87f-111">範圍</span><span class="sxs-lookup"><span data-stu-id="2c87f-111">Scope</span></span>   |<span data-ttu-id="2c87f-112">Edge</span><span class="sxs-lookup"><span data-stu-id="2c87f-112">Edge</span></span>|
|<span data-ttu-id="2c87f-113">版本</span><span class="sxs-lookup"><span data-stu-id="2c87f-113">Version</span></span>|<span data-ttu-id="2c87f-114">4.6.2</span><span class="sxs-lookup"><span data-stu-id="2c87f-114">4.6.2</span></span>|
|<span data-ttu-id="2c87f-115">類型</span><span class="sxs-lookup"><span data-stu-id="2c87f-115">Type</span></span>|<span data-ttu-id="2c87f-116">執行階段</span><span class="sxs-lookup"><span data-stu-id="2c87f-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="2c87f-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="2c87f-117">Affected APIs</span></span>

- <xref:System.Security.Cryptography.DSACng.%23ctor(System.Security.Cryptography.CngKey)>
- <xref:System.Security.Cryptography.DSACng.Key?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.DSACng.LegalKeySizes?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.DSACng.CreateSignature(System.Byte[])?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.DSACng.VerifySignature(System.Byte[],System.Byte[])?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSACng.%23ctor(System.Security.Cryptography.CngKey)>
- <xref:System.Security.Cryptography.RSACng.Key?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSACng.Decrypt(System.Byte[],System.Security.Cryptography.RSAEncryptionPadding)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSACng.SignHash(System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.DSACng.#ctor(System.Security.Cryptography.CngKey)`
- `P:System.Security.Cryptography.DSACng.Key`
- `P:System.Security.Cryptography.DSACng.LegalKeySizes`
- `M:System.Security.Cryptography.DSACng.CreateSignature(System.Byte[])`
- `M:System.Security.Cryptography.DSACng.VerifySignature(System.Byte[],System.Byte[])`
- `M:System.Security.Cryptography.RSACng.#ctor(System.Security.Cryptography.CngKey)`
- `P:System.Security.Cryptography.RSACng.Key`
- `M:System.Security.Cryptography.RSACng.Decrypt(System.Byte[],System.Security.Cryptography.RSAEncryptionPadding)`
- `M:System.Security.Cryptography.RSACng.SignHash(System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)`

-->
