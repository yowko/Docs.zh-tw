---
ms.openlocfilehash: 9a747d8fc15ca8fa2b915f89291f118d7344d172
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325248"
---
### <a name="httpsys-client-certificate-renegotiation-disabled-by-default"></a><span data-ttu-id="f5998-101">HttpSys：預設會停用用戶端憑證重新協商</span><span class="sxs-lookup"><span data-stu-id="f5998-101">HttpSys: Client certificate renegotiation disabled by default</span></span>

<span data-ttu-id="f5998-102">預設會停用重新協商連接和要求用戶端憑證的選項。</span><span class="sxs-lookup"><span data-stu-id="f5998-102">The option to renegotiate a connection and request a client certificate has been disabled by default.</span></span> <span data-ttu-id="f5998-103">如需討論，請參閱 issue [dotnet/aspnetcore # 23181](https://github.com/dotnet/aspnetcore/issues/23181)。</span><span class="sxs-lookup"><span data-stu-id="f5998-103">For discussion, see issue [dotnet/aspnetcore#23181](https://github.com/dotnet/aspnetcore/issues/23181).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f5998-104">引進的版本</span><span class="sxs-lookup"><span data-stu-id="f5998-104">Version introduced</span></span>

<span data-ttu-id="f5998-105">ASP.NET Core 5。0</span><span class="sxs-lookup"><span data-stu-id="f5998-105">ASP.NET Core 5.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="f5998-106">舊的行為</span><span class="sxs-lookup"><span data-stu-id="f5998-106">Old behavior</span></span>

<span data-ttu-id="f5998-107">連接可以重新協商以要求用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="f5998-107">The connection can be renegotiated to request a client certificate.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="f5998-108">新的行為</span><span class="sxs-lookup"><span data-stu-id="f5998-108">New behavior</span></span>

<span data-ttu-id="f5998-109">只有在初始連線交握期間，才可要求用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="f5998-109">Client certificates can only be requested during the initial connection handshake.</span></span> <span data-ttu-id="f5998-110">如需詳細資訊，請參閱 pull request [dotnet/aspnetcore # 23162](https://github.com/dotnet/aspnetcore/pull/23162)。</span><span class="sxs-lookup"><span data-stu-id="f5998-110">For more information, see pull request [dotnet/aspnetcore#23162](https://github.com/dotnet/aspnetcore/pull/23162).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="f5998-111">變更的原因</span><span class="sxs-lookup"><span data-stu-id="f5998-111">Reason for change</span></span>

<span data-ttu-id="f5998-112">重新協商會造成一些效能和鎖死問題。</span><span class="sxs-lookup"><span data-stu-id="f5998-112">Renegotiation caused a number of performance and deadlock issues.</span></span> <span data-ttu-id="f5998-113">HTTP/2 也不支援。</span><span class="sxs-lookup"><span data-stu-id="f5998-113">It's also not supported in HTTP/2.</span></span> <span data-ttu-id="f5998-114">如需控制此行為的選項在 ASP.NET Core 3.1 中引進的其他內容，請參閱 issue [dotnet/aspnetcore # 14806](https://github.com/dotnet/aspnetcore/issues/14806)。</span><span class="sxs-lookup"><span data-stu-id="f5998-114">For additional context from when the option to control this behavior was introduced in ASP.NET Core 3.1, see issue [dotnet/aspnetcore#14806](https://github.com/dotnet/aspnetcore/issues/14806).</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f5998-115">建議的動作</span><span class="sxs-lookup"><span data-stu-id="f5998-115">Recommended action</span></span>

<span data-ttu-id="f5998-116">需要用戶端憑證的應用程式應該使用*netsh.exe*將 `clientcertnegotiation` 選項設定為 `enabled` 。</span><span class="sxs-lookup"><span data-stu-id="f5998-116">Apps that require client certificates should use *netsh.exe* to set the `clientcertnegotiation` option to `enabled`.</span></span> <span data-ttu-id="f5998-117">如需詳細資訊，請參閱[netsh HTTP 命令](/windows-server/networking/technologies/netsh/netsh-http)。</span><span class="sxs-lookup"><span data-stu-id="f5998-117">For more information, see [netsh http commands](/windows-server/networking/technologies/netsh/netsh-http).</span></span>

<span data-ttu-id="f5998-118">如果您只想針對應用程式的某些部分啟用用戶端憑證，請參閱[選用用戶端憑證](/aspnet/core/security/authentication/certauth?view=aspnetcore-3.1#optional-client-certificates)的指引。</span><span class="sxs-lookup"><span data-stu-id="f5998-118">If you want client certificates enabled for only some parts of your app, see the guidance at [Optional client certificates](/aspnet/core/security/authentication/certauth?view=aspnetcore-3.1#optional-client-certificates).</span></span>

<span data-ttu-id="f5998-119">如果您需要舊的重新協商行為，請將設定 `HttpSysOptions.ClientCertificateMethod` 為舊的值 `ClientCertificateMethod.AllowRenegotiate` 。</span><span class="sxs-lookup"><span data-stu-id="f5998-119">If you need the old renegotiate behavior, set `HttpSysOptions.ClientCertificateMethod` to the old value `ClientCertificateMethod.AllowRenegotiate`.</span></span> <span data-ttu-id="f5998-120">這不建議用於上述和連結的指引中所述的原因。</span><span class="sxs-lookup"><span data-stu-id="f5998-120">This isn't recommended for the reasons outlined above and in the linked guidance.</span></span>

#### <a name="category"></a><span data-ttu-id="f5998-121">類別</span><span class="sxs-lookup"><span data-stu-id="f5998-121">Category</span></span>

<span data-ttu-id="f5998-122">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f5998-122">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f5998-123">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="f5998-123">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Http.ConnectionInfo.ClientCertificate%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.ConnectionInfo.GetClientCertificateAsync%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Server.HttpSys.HttpSysOptions.ClientCertificateMethod%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:Microsoft.AspNetCore.Http.ConnectionInfo.ClientCertificate`
- `Overload:Microsoft.AspNetCore.Http.ConnectionInfo.GetClientCertificateAsync`
- `Overload:Microsoft.AspNetCore.Server.HttpSys.HttpSysOptions.ClientCertificateMethod`

-->
