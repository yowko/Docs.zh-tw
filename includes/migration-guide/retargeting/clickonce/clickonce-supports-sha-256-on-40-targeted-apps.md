---
ms.openlocfilehash: c967a5b09b5e9ffeee7bff046f0c96469bc7fb02
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615619"
---
### <a name="clickonce-supports-sha-256-on-40-targeted-apps"></a><span data-ttu-id="e1465-101">ClickOnce 在 4.0 為目標的應用程式上支援 SHA-256</span><span class="sxs-lookup"><span data-stu-id="e1465-101">ClickOnce supports SHA-256 on 4.0-targeted apps</span></span>

#### <a name="details"></a><span data-ttu-id="e1465-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e1465-102">Details</span></span>

<span data-ttu-id="e1465-103">先前，具有使用 SHA-256 簽署之憑證的 ClickOnce 應用程式，需要有 .NET Framework 4.5 或更新版本存在，即使應用程式是以 4.0 為目標。</span><span class="sxs-lookup"><span data-stu-id="e1465-103">Previously, a ClickOnce app with a certificate signed with SHA-256 would require .NET Framework 4.5 or later to be present, even if the app targeted 4.0.</span></span> <span data-ttu-id="e1465-104">現在，即使使用 SHA-256 簽署，以 .NET Framework 4.0 為目標的 ClickOnce 應用程式也可以在 .NET Framework 4.0 上執行。</span><span class="sxs-lookup"><span data-stu-id="e1465-104">Now, .NET Framework 4.0-targeted ClickOnce apps can run on .NET Framework 4.0, even if signed with SHA-256.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e1465-105">建議</span><span class="sxs-lookup"><span data-stu-id="e1465-105">Suggestion</span></span>

<span data-ttu-id="e1465-106">這項變更移除了該相依性，並允許使用 SHA-256 憑證來簽署以 .NET Framework 4 和更早版本為目標的 ClickOnce 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e1465-106">This change removes that dependency and allows SHA-256 certificates to be used to sign ClickOnce apps that target .NET Framework 4 and earlier versions.</span></span>

| <span data-ttu-id="e1465-107">名稱</span><span class="sxs-lookup"><span data-stu-id="e1465-107">Name</span></span>    | <span data-ttu-id="e1465-108">值</span><span class="sxs-lookup"><span data-stu-id="e1465-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e1465-109">影響範圍</span><span class="sxs-lookup"><span data-stu-id="e1465-109">Scope</span></span>   | <span data-ttu-id="e1465-110">Minor</span><span class="sxs-lookup"><span data-stu-id="e1465-110">Minor</span></span>       |
| <span data-ttu-id="e1465-111">版本</span><span class="sxs-lookup"><span data-stu-id="e1465-111">Version</span></span> | <span data-ttu-id="e1465-112">4.6</span><span class="sxs-lookup"><span data-stu-id="e1465-112">4.6</span></span>         |
| <span data-ttu-id="e1465-113">類型</span><span class="sxs-lookup"><span data-stu-id="e1465-113">Type</span></span>    | <span data-ttu-id="e1465-114">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="e1465-114">Retargeting</span></span> |
