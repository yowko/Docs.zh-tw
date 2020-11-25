---
title: 重大變更：使用非預設診斷識別碼的 API obsoletions
description: 瞭解核心 .NET 程式庫中的 .NET 5.0 重大變更，其中某些 Api 已使用自訂診斷識別碼標示為過時。
ms.date: 11/01/2020
ms.openlocfilehash: 9bd7ce18aed38955f9abc91e0c8b09e827c401d6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760753"
---
# <a name="api-obsoletions-with-non-default-diagnostic-ids"></a><span data-ttu-id="d9ffd-103">使用非預設診斷識別碼的 API obsoletions</span><span class="sxs-lookup"><span data-stu-id="d9ffd-103">API obsoletions with non-default diagnostic IDs</span></span>

<span data-ttu-id="d9ffd-104">某些 Api 已標示為過時，從 .NET 5.0 開始。</span><span class="sxs-lookup"><span data-stu-id="d9ffd-104">Some APIs have been marked as obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="d9ffd-105">這項重大變更是 *使用自訂診斷識別碼* 標示為已淘汰的 api 所特有。</span><span class="sxs-lookup"><span data-stu-id="d9ffd-105">This breaking change is specific to APIs that have been marked as obsolete *with a custom diagnostic ID*.</span></span> <span data-ttu-id="d9ffd-106">隱藏 c # 編譯器所 [CS0618](../../../../csharp/language-reference/compiler-messages/cs0618.md) 的預設 OBSOLETION 診斷識別碼，不會隱藏編譯器在使用這些 api 時所產生的警告。</span><span class="sxs-lookup"><span data-stu-id="d9ffd-106">Suppressing the default obsoletion diagnostic ID, which is [CS0618](../../../../csharp/language-reference/compiler-messages/cs0618.md) for the C# compiler, does not suppress the warnings that the compiler generates when these APIs are used.</span></span>

## <a name="change-description"></a><span data-ttu-id="d9ffd-107">變更描述</span><span class="sxs-lookup"><span data-stu-id="d9ffd-107">Change description</span></span>

<span data-ttu-id="d9ffd-108">在舊版的 .NET 中，您可以使用這些 Api，而不需要任何組建警告。</span><span class="sxs-lookup"><span data-stu-id="d9ffd-108">In previous .NET versions, these APIs can be used without any build warning.</span></span> <span data-ttu-id="d9ffd-109">在 .NET 5.0 和更新版本中，使用這些 API 會產生具有自訂診斷識別碼的編譯時期警告或錯誤。</span><span class="sxs-lookup"><span data-stu-id="d9ffd-109">In .NET 5.0 and later versions, use of these APIS produces a compile-time warning or error with a custom diagnostic ID.</span></span> <span data-ttu-id="d9ffd-110">使用自訂診斷識別碼可讓您個別隱藏 obsoletion 警告，而非全面隱藏所有 obsoletion 警告。</span><span class="sxs-lookup"><span data-stu-id="d9ffd-110">The use of custom diagnostic IDs allows you to suppress the obsoletion warnings individually instead of blanket-suppressing all obsoletion warnings.</span></span>

<span data-ttu-id="d9ffd-111">下表列出已過時 Api 的自訂診斷識別碼及其對應的警告訊息。</span><span class="sxs-lookup"><span data-stu-id="d9ffd-111">The following table lists the custom diagnostic IDs and their corresponding warning messages for obsoleted APIs.</span></span>

| <span data-ttu-id="d9ffd-112">診斷識別碼</span><span class="sxs-lookup"><span data-stu-id="d9ffd-112">Diagnostic ID</span></span> | <span data-ttu-id="d9ffd-113">描述</span><span class="sxs-lookup"><span data-stu-id="d9ffd-113">Description</span></span> | <span data-ttu-id="d9ffd-114">Severity</span><span class="sxs-lookup"><span data-stu-id="d9ffd-114">Severity</span></span> |
| - | - |
| `SYSLIB0001` | <span data-ttu-id="d9ffd-115">UTF-7 編碼並不安全，因此不應該使用。</span><span class="sxs-lookup"><span data-stu-id="d9ffd-115">The UTF-7 encoding is insecure and should not be used.</span></span> <span data-ttu-id="d9ffd-116">請考慮改為使用 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="d9ffd-116">Consider using UTF-8 instead.</span></span> | <span data-ttu-id="d9ffd-117">警告</span><span class="sxs-lookup"><span data-stu-id="d9ffd-117">Warning</span></span> |
| `SYSLIB0002` | <span data-ttu-id="d9ffd-118"><xref:System.Security.Permissions.PrincipalPermissionAttribute> 執行時間不接受，而且不得使用。</span><span class="sxs-lookup"><span data-stu-id="d9ffd-118"><xref:System.Security.Permissions.PrincipalPermissionAttribute> is not honored by the runtime and must not be used.</span></span> | <span data-ttu-id="d9ffd-119">Error</span><span class="sxs-lookup"><span data-stu-id="d9ffd-119">Error</span></span> |
| `SYSLIB0003` | <span data-ttu-id="d9ffd-120">執行時間不支援或不接受代碼啟用安全性 (CAS) 。</span><span class="sxs-lookup"><span data-stu-id="d9ffd-120">Code access security (CAS) is not supported or honored by the runtime.</span></span> | <span data-ttu-id="d9ffd-121">警告</span><span class="sxs-lookup"><span data-stu-id="d9ffd-121">Warning</span></span> |
| `SYSLIB0004` | <span data-ttu-id="d9ffd-122">不支援 (CER) 功能的限制執列區域。</span><span class="sxs-lookup"><span data-stu-id="d9ffd-122">The constrained execution region (CER) feature is not supported.</span></span> | <span data-ttu-id="d9ffd-123">警告</span><span class="sxs-lookup"><span data-stu-id="d9ffd-123">Warning</span></span> |
| `SYSLIB0005` | <span data-ttu-id="d9ffd-124">不支援全域組件快取 (GAC) 。</span><span class="sxs-lookup"><span data-stu-id="d9ffd-124">The global assembly cache (GAC) is not supported.</span></span> | <span data-ttu-id="d9ffd-125">警告</span><span class="sxs-lookup"><span data-stu-id="d9ffd-125">Warning</span></span> |
| `SYSLIB0006` | <span data-ttu-id="d9ffd-126"><xref:System.Threading.Thread.Abort?displayProperty=nameWithType> 不受支援，而且會擲回 <xref:System.PlatformNotSupportedException> 。</span><span class="sxs-lookup"><span data-stu-id="d9ffd-126"><xref:System.Threading.Thread.Abort?displayProperty=nameWithType> is not supported and throws <xref:System.PlatformNotSupportedException>.</span></span> | <span data-ttu-id="d9ffd-127">警告</span><span class="sxs-lookup"><span data-stu-id="d9ffd-127">Warning</span></span> |
| `SYSLIB0007` | <span data-ttu-id="d9ffd-128">不支援此密碼編譯演算法的預設執行。</span><span class="sxs-lookup"><span data-stu-id="d9ffd-128">The default implementation of this cryptography algorithm is not supported.</span></span> | <span data-ttu-id="d9ffd-129">警告</span><span class="sxs-lookup"><span data-stu-id="d9ffd-129">Warning</span></span> |
| `SYSLIB0008` | <span data-ttu-id="d9ffd-130"><xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator>不支援並擲回 API <xref:System.PlatformNotSupportedException> 。</span><span class="sxs-lookup"><span data-stu-id="d9ffd-130">The <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator> API is not supported and throws <xref:System.PlatformNotSupportedException>.</span></span> | <span data-ttu-id="d9ffd-131">警告</span><span class="sxs-lookup"><span data-stu-id="d9ffd-131">Warning</span></span> |
| `SYSLIB0009` | <span data-ttu-id="d9ffd-132"><xref:System.Net.AuthenticationManager.Authenticate%2A?displayProperty=nameWithType>和 <xref:System.Net.AuthenticationManager.PreAuthenticate%2A?displayProperty=nameWithType> 方法不受支援，而且會擲回 <xref:System.PlatformNotSupportedException> 。</span><span class="sxs-lookup"><span data-stu-id="d9ffd-132">The <xref:System.Net.AuthenticationManager.Authenticate%2A?displayProperty=nameWithType> and <xref:System.Net.AuthenticationManager.PreAuthenticate%2A?displayProperty=nameWithType> methods are not supported and throw <xref:System.PlatformNotSupportedException>.</span></span> | <span data-ttu-id="d9ffd-133">警告</span><span class="sxs-lookup"><span data-stu-id="d9ffd-133">Warning</span></span> |
| `SYSLIB0010`| <span data-ttu-id="d9ffd-134">某些遠端 Api 不受支援且會擲回 <xref:System.PlatformNotSupportedException> 。</span><span class="sxs-lookup"><span data-stu-id="d9ffd-134">Some remoting APIs are not supported and throw <xref:System.PlatformNotSupportedException>.</span></span> | <span data-ttu-id="d9ffd-135">警告</span><span class="sxs-lookup"><span data-stu-id="d9ffd-135">Warning</span></span> |
| `SYSLIB0011` | <span data-ttu-id="d9ffd-136"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 序列化已過時，不應該使用。</span><span class="sxs-lookup"><span data-stu-id="d9ffd-136"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> serialization is obsolete and should not be used.</span></span> | <span data-ttu-id="d9ffd-137">警告</span><span class="sxs-lookup"><span data-stu-id="d9ffd-137">Warning</span></span> |
| `SYSLIB0012` | <span data-ttu-id="d9ffd-138"><xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType> 和 <xref:System.Reflection.Assembly.EscapedCodeBase?displayProperty=nameWithType> 只包含 .NET Framework 相容性。</span><span class="sxs-lookup"><span data-stu-id="d9ffd-138"><xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType> and <xref:System.Reflection.Assembly.EscapedCodeBase?displayProperty=nameWithType> are only included for .NET Framework compatibility.</span></span> <span data-ttu-id="d9ffd-139">請改用 <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="d9ffd-139">Use <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> instead.</span></span> | <span data-ttu-id="d9ffd-140">警告</span><span class="sxs-lookup"><span data-stu-id="d9ffd-140">Warning</span></span> |

## <a name="version-introduced"></a><span data-ttu-id="d9ffd-141">引進的版本</span><span class="sxs-lookup"><span data-stu-id="d9ffd-141">Version introduced</span></span>

<span data-ttu-id="d9ffd-142">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="d9ffd-142">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="d9ffd-143">建議的動作</span><span class="sxs-lookup"><span data-stu-id="d9ffd-143">Recommended action</span></span>

- <span data-ttu-id="d9ffd-144">使用警告上提供的 URL 連結，遵循針對每個診斷識別碼所提供的特定指引。</span><span class="sxs-lookup"><span data-stu-id="d9ffd-144">Follow the specific guidance provided for the each diagnostic ID using the URL link provided on the warning.</span></span>

- <span data-ttu-id="d9ffd-145">針對過時的類型或成員，無法使用標準診斷識別碼來抑制這些 obsoletions 的警告或錯誤;請改用自訂 `SYSLIBxxxx` 診斷識別碼值。</span><span class="sxs-lookup"><span data-stu-id="d9ffd-145">Warnings or errors for these obsoletions can't be suppressed using the standard diagnostic ID for obsolete types or members; use the custom `SYSLIBxxxx` diagnostic ID value instead.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="d9ffd-146">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="d9ffd-146">Affected APIs</span></span>

### <a name="syslib0001"></a><span data-ttu-id="d9ffd-147">SYSLIB0001</span><span class="sxs-lookup"><span data-stu-id="d9ffd-147">SYSLIB0001</span></span>

- <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType>
- <xref:System.Text.UTF7Encoding.%23ctor%2A>

### <a name="syslib0002"></a><span data-ttu-id="d9ffd-148">SYSLIB0002</span><span class="sxs-lookup"><span data-stu-id="d9ffd-148">SYSLIB0002</span></span>

- <xref:System.Security.Permissions.PrincipalPermissionAttribute.%23ctor(System.Security.Permissions.SecurityAction)>

### <a name="syslib0003"></a><span data-ttu-id="d9ffd-149">SYSLIB0003</span><span class="sxs-lookup"><span data-stu-id="d9ffd-149">SYSLIB0003</span></span>

<span data-ttu-id="d9ffd-150">命名空間中的類別 `System.Security.Permissions` ：</span><span class="sxs-lookup"><span data-stu-id="d9ffd-150">Classes in the `System.Security.Permissions` namespace:</span></span>

- <xref:System.Security.Permissions.CodeAccessSecurityAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.DataProtectionPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.DataProtectionPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.EnvironmentPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.EnvironmentPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.FileDialogPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.FileDialogPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.FileIOPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.FileIOPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.GacIdentityPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.GacIdentityPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.IsolatedStorageFilePermission?displayProperty=fullName>
- <xref:System.Security.Permissions.IsolatedStorageFilePermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.IsolatedStoragePermission?displayProperty=fullName>
- <xref:System.Security.Permissions.IsolatedStoragePermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.KeyContainerPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.KeyContainerPermissionAccessEntry?displayProperty=fullName>
- <xref:System.Security.Permissions.KeyContainerPermissionAccessEntryCollection?displayProperty=fullName>
- <xref:System.Security.Permissions.KeyContainerPermissionAccessEntryEnumerator?displayProperty=fullName>
- <xref:System.Security.Permissions.KeyContainerPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.MediaPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.MediaPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.PermissionSetAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.PrincipalPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.PrincipalPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.PublisherIdentityPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.PublisherIdentityPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.ReflectionPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.ReflectionPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.RegistryPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.RegistryPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.ResourcePermissionBase?displayProperty=fullName>
- <xref:System.Security.Permissions.ResourcePermissionBaseEntry?displayProperty=fullName>
- <xref:System.Security.Permissions.SecurityAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.SecurityPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.SecurityPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.SiteIdentityPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.SiteIdentityPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.StorePermission?displayProperty=fullName>
- <xref:System.Security.Permissions.StorePermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.StrongNameIdentityPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.StrongNamePublicKeyBlob?displayProperty=fullName>
- <xref:System.Security.Permissions.TypeDescriptorPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.TypeDescriptorPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.UIPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.UIPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.UrlIdentityPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.UrlIdentityPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.WebBrowserPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.WebBrowserPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.ZoneIdentityPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.ZoneIdentityPermissionAttribute?displayProperty=fullName>

<span data-ttu-id="d9ffd-151">衍生自的類別 `CodeAccessSecurityAttribute` ：</span><span class="sxs-lookup"><span data-stu-id="d9ffd-151">Classes that derive from `CodeAccessSecurityAttribute`:</span></span>

- <xref:System.Configuration.ConfigurationPermissionAttribute?displayProperty=fullName>
- <xref:System.Data.Common.DBDataPermissionAttribute?displayProperty=fullName>
- <xref:System.Data.Odbc.OdbcPermissionAttribute?displayProperty=fullName>
- <xref:System.Data.OleDb.OleDbPermissionAttribute?displayProperty=fullName>
- <xref:System.Data.OracleClient.OraclePermissionAttribute?displayProperty=fullName>
- <xref:System.Data.SqlClient.SqlClientPermissionAttribute?displayProperty=fullName>
- <xref:System.Diagnostics.EventLogPermissionAttribute?displayProperty=fullName>
- <xref:System.Diagnostics.PerformanceCounterPermissionAttribute?displayProperty=fullName>
- <xref:System.DirectoryServices.DirectoryServicesPermissionAttribute?displayProperty=fullName>
- <xref:System.Drawing.Printing.PrintingPermissionAttribute?displayProperty=fullName>
- <xref:System.Net.DnsPermissionAttribute?displayProperty=fullName>
- <xref:System.Net.SocketPermissionAttribute?displayProperty=fullName>
- <xref:System.Net.WebPermissionAttribute?displayProperty=fullName>
- <xref:System.Net.Mail.SmtpPermissionAttribute?displayProperty=fullName>
- <xref:System.Net.NetworkInformation.NetworkInformationPermissionAttribute?displayProperty=fullName>
- <xref:System.Net.PeerToPeer.PnrpPermissionAttribute?displayProperty=fullName>
- <xref:System.Net.PeerToPeer.Collaboration.PeerCollaborationPermissionAttribute?displayProperty=fullName>
- <xref:System.ServiceProcess.ServiceControllerPermissionAttribute?displayProperty=fullName>
- <xref:System.Transactions.DistributedTransactionPermissionAttribute?displayProperty=fullName>
- <xref:System.Web.AspNetHostingPermissionAttribute?displayProperty=fullName>

<span data-ttu-id="d9ffd-152">介面：</span><span class="sxs-lookup"><span data-stu-id="d9ffd-152">Interfaces:</span></span>

- <xref:System.Security.Permissions.IUnrestrictedPermission?displayProperty=fullName>
- <xref:System.Security.IPermission?displayProperty=fullName>
- <xref:System.Security.IStackWalk?displayProperty=fullName>
- <xref:System.Security.Policy.IIdentityPermissionFactory?displayProperty=fullName>

<span data-ttu-id="d9ffd-153">執行的類別 `IStackWalk` ：</span><span class="sxs-lookup"><span data-stu-id="d9ffd-153">Classes that implement `IStackWalk`:</span></span>

- <xref:System.Security.NamedPermissionSet?displayProperty=fullName>
- <xref:System.Security.PermissionSet?displayProperty=fullName>

<span data-ttu-id="d9ffd-154">執行的類別 `IPermission` ：</span><span class="sxs-lookup"><span data-stu-id="d9ffd-154">Classes that implement `IPermission`:</span></span>

- <xref:System.Security.CodeAccessPermission?displayProperty=fullName>

<span data-ttu-id="d9ffd-155">衍生自的類別 `CodeAccessPermission` ：</span><span class="sxs-lookup"><span data-stu-id="d9ffd-155">Classes that derive from `CodeAccessPermission`:</span></span>

- <xref:System.Configuration.ConfigurationPermission?displayProperty=fullName>
- <xref:System.Data.Common.DBDataPermission?displayProperty=fullName>
- <xref:System.Data.Odbc.OdbcPermission?displayProperty=fullName>
- <xref:System.Data.OleDb.OleDbPermission?displayProperty=fullName>
- <xref:System.Data.SqlClient.SqlClientPermission?displayProperty=fullName>
- <xref:System.Data.OracleClient.OraclePermission?displayProperty=fullName>
- <xref:System.Drawing.Printing.PrintingPermission?displayProperty=fullName>
- <xref:System.Net.DnsPermission?displayProperty=fullName>
- <xref:System.Net.SocketPermission?displayProperty=fullName>
- <xref:System.Net.WebPermission?displayProperty=fullName>
- <xref:System.Net.Mail.SmtpPermission?displayProperty=fullName>
- <xref:System.Net.NetworkInformation.NetworkInformationPermission?displayProperty=fullName>
- <xref:System.Net.PeerToPeer.PnrpPermission?displayProperty=fullName>
- <xref:System.Net.PeerToPeer.Collaboration.PeerCollaborationPermission?displayProperty=fullName>
- <xref:System.Transactions.DistributedTransactionPermission?displayProperty=fullName>
- <xref:System.Web.AspNetHostingPermission?displayProperty=fullName>
- <xref:System.Xaml.Permissions.XamlLoadPermission?displayProperty=fullName>

<span data-ttu-id="d9ffd-156">衍生自的類別 `ResourcePermissionBase` ：</span><span class="sxs-lookup"><span data-stu-id="d9ffd-156">Classes that derive from `ResourcePermissionBase`:</span></span>

- <xref:System.Diagnostics.EventLogPermission?displayProperty=fullName>
- <xref:System.Diagnostics.PerformanceCounterPermission?displayProperty=fullName>
- <xref:System.DirectoryServices.DirectoryServicesPermission?displayProperty=fullName>
- <xref:System.ServiceProcess.ServiceControllerPermission?displayProperty=fullName>

<span data-ttu-id="d9ffd-157">命名空間中的列舉 `System.Security.Permissions` ：</span><span class="sxs-lookup"><span data-stu-id="d9ffd-157">Enums in the `System.Security.Permissions` namespace:</span></span>

- <xref:System.Security.Permissions.DataProtectionPermissionFlags?displayProperty=fullName>
- <xref:System.Security.Permissions.EnvironmentPermissionAccess?displayProperty=fullName>
- <xref:System.Security.Permissions.FileDialogPermissionAccess?displayProperty=fullName>
- <xref:System.Security.Permissions.FileIOPermissionAccess?displayProperty=fullName>
- <xref:System.Security.Permissions.HostProtectionResource?displayProperty=fullName>
- <xref:System.Security.Permissions.IsolatedStorageContainment?displayProperty=fullName>
- <xref:System.Security.Permissions.KeyContainerPermissionFlags?displayProperty=fullName>
- <xref:System.Security.Permissions.MediaPermissionAudio?displayProperty=fullName>
- <xref:System.Security.Permissions.MediaPermissionImage?displayProperty=fullName>
- <xref:System.Security.Permissions.MediaPermissionVideo?displayProperty=fullName>
- <xref:System.Security.Permissions.PermissionState?displayProperty=fullName>
- <xref:System.Security.Permissions.ReflectionPermissionFlag?displayProperty=fullName>
- <xref:System.Security.Permissions.RegistryPermissionAccess?displayProperty=fullName>
- <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName>
- <xref:System.Security.Permissions.SecurityPermissionFlag?displayProperty=fullName>
- <xref:System.Security.Permissions.StorePermissionFlags?displayProperty=fullName>
- <xref:System.Security.Permissions.TypeDescriptorPermissionFlags?displayProperty=fullName>
- <xref:System.Security.Permissions.UIPermissionClipboard?displayProperty=fullName>
- <xref:System.Security.Permissions.UIPermissionWindow?displayProperty=fullName>
- <xref:System.Security.Permissions.WebBrowserPermissionLevel?displayProperty=fullName>

<span data-ttu-id="d9ffd-158">相依于代碼啟用安全性類型的類別和成員：</span><span class="sxs-lookup"><span data-stu-id="d9ffd-158">Classes and members that depend on code access security types:</span></span>

- <xref:System.AppDomain.PermissionSet?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.AllowReversePInvokeCallsAttribute?displayProperty=fullName>
- <xref:System.Security.HostProtectionException?displayProperty=fullName>
- <xref:System.Security.Policy.FileCodeGroup?displayProperty=fullName>
- <xref:System.Security.Policy.StrongName?displayProperty=fullName>
- <xref:System.Security.Policy.StrongNameMembershipCondition?displayProperty=fullName>
- [<span data-ttu-id="d9ffd-159">ApplicationTrust. ApplicationTrust (PermissionSet，IEnumerable \<StrongName>) </span><span class="sxs-lookup"><span data-stu-id="d9ffd-159">System.Security.Policy.ApplicationTrust.ApplicationTrust(PermissionSet, IEnumerable\<StrongName>)</span></span>](/dotnet/api/system.security.policy.applicationtrust.-ctor#System_Security_Policy_ApplicationTrust__ctor_System_Security_PermissionSet_System_Collections_Generic_IEnumerable_System_Security_Policy_StrongName__)
- <xref:System.Security.Policy.ApplicationTrust.FullTrustAssemblies?displayProperty=fullName>
- <xref:System.Security.Policy.GacInstalled?displayProperty=fullName>
- <xref:System.Security.Policy.PolicyStatement.%23ctor%2A?displayProperty=fullName>
- <xref:System.Security.Policy.PolicyLevel.AddNamedPermissionSet(System.Security.NamedPermissionSet)?displayProperty=fullName>
- <xref:System.Security.Policy.PolicyLevel.ChangeNamedPermissionSet(System.String,System.Security.PermissionSet)?displayProperty=fullName>
- <xref:System.Security.Policy.PolicyLevel.GetNamedPermissionSet(System.String)?displayProperty=fullName>
- <xref:System.Security.Policy.PolicyLevel.RemoveNamedPermissionSet(System.String)?displayProperty=fullName>
- <xref:System.Security.Policy.PolicyLevel.RemoveNamedPermissionSet(System.Security.NamedPermissionSet)?displayProperty=nameWithType>
- <xref:System.Security.Policy.PolicyStatement.PermissionSet?displayProperty=fullName>
- <xref:System.Security.Policy.Publisher?displayProperty=fullName>
- <xref:System.Security.Policy.Site?displayProperty=fullName>
- <xref:System.Security.Policy.Url?displayProperty=fullName>
- <xref:System.Security.Policy.Zone?displayProperty=fullName>
- <xref:System.Security.SecurityManager?displayProperty=fullName>

### <a name="syslib0004"></a><span data-ttu-id="d9ffd-160">SYSLIB0004</span><span class="sxs-lookup"><span data-stu-id="d9ffd-160">SYSLIB0004</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup(System.Runtime.CompilerServices.RuntimeHelpers.TryCode,System.Runtime.CompilerServices.RuntimeHelpers.CleanupCode,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegionsNoOP?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareContractedDelegate(System.Delegate)?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.ProbeForSufficientStack?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.Cer?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.Consistency?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.PrePrepareMethodAttribute?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute?displayProperty=nameWithType>

### <a name="syslib0005"></a><span data-ttu-id="d9ffd-161">SYSLIB0005</span><span class="sxs-lookup"><span data-stu-id="d9ffd-161">SYSLIB0005</span></span>

- <xref:System.Reflection.Assembly.GlobalAssemblyCache?displayProperty=nameWithType>

### <a name="syslib0006"></a><span data-ttu-id="d9ffd-162">SYSLIB0006</span><span class="sxs-lookup"><span data-stu-id="d9ffd-162">SYSLIB0006</span></span>

- <xref:System.Threading.Thread.Abort?displayProperty=nameWithType>
- <xref:System.Threading.Thread.Abort(System.Object)?displayProperty=nameWithType>

### <a name="syslib0007"></a><span data-ttu-id="d9ffd-163">SYSLIB0007</span><span class="sxs-lookup"><span data-stu-id="d9ffd-163">SYSLIB0007</span></span>

- <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.HMAC.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=fullName>

### <a name="syslib0008"></a><span data-ttu-id="d9ffd-164">SYSLIB0008</span><span class="sxs-lookup"><span data-stu-id="d9ffd-164">SYSLIB0008</span></span>

- <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType>

### <a name="syslib0009"></a><span data-ttu-id="d9ffd-165">SYSLIB0009</span><span class="sxs-lookup"><span data-stu-id="d9ffd-165">SYSLIB0009</span></span>

- <xref:System.Net.AuthenticationManager.Authenticate%2A?displayProperty=nameWithType>
- <xref:System.Net.AuthenticationManager.PreAuthenticate%2A?displayProperty=nameWithType>

### <a name="syslib0010"></a><span data-ttu-id="d9ffd-166">SYSLIB0010</span><span class="sxs-lookup"><span data-stu-id="d9ffd-166">SYSLIB0010</span></span>

- <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType>
- <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType>

### <a name="syslib0011"></a><span data-ttu-id="d9ffd-167">SYSLIB0011</span><span class="sxs-lookup"><span data-stu-id="d9ffd-167">SYSLIB0011</span></span>

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>

### <a name="syslib0012"></a><span data-ttu-id="d9ffd-168">SYSLIB0012</span><span class="sxs-lookup"><span data-stu-id="d9ffd-168">SYSLIB0012</span></span>

- <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.EscapedCodeBase?displayProperty=nameWithType>
