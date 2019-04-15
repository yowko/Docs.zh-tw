---
ms.openlocfilehash: 0358450024607a985f38564ec9743ba964949e8f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234406"
---
### <a name="clickonce-supports-sha-256-on-40-targeted-apps"></a><span data-ttu-id="90237-101">ClickOnce 在 4.0 為目標的應用程式上支援 SHA-256</span><span class="sxs-lookup"><span data-stu-id="90237-101">ClickOnce supports SHA-256 on 4.0-targeted apps</span></span>

|   |   |
|---|---|
|<span data-ttu-id="90237-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="90237-102">Details</span></span>|<span data-ttu-id="90237-103">先前，具有使用 SHA-256 簽署之憑證的 ClickOnce 應用程式，需要有 .NET Framework 4.5 或更新版本存在，即使應用程式是以 4.0 為目標。</span><span class="sxs-lookup"><span data-stu-id="90237-103">Previously, a ClickOnce app with a certificate signed with SHA-256 would require .NET Framework 4.5 or later to be present, even if the app targeted 4.0.</span></span> <span data-ttu-id="90237-104">現在，即使使用 SHA-256 簽署，以 .NET Framework 4.0 為目標的 ClickOnce 應用程式也可以在 .NET Framework 4.0 上執行。</span><span class="sxs-lookup"><span data-stu-id="90237-104">Now, .NET Framework 4.0-targeted ClickOnce apps can run on .NET Framework 4.0, even if signed with SHA-256.</span></span>|
|<span data-ttu-id="90237-105">建議</span><span class="sxs-lookup"><span data-stu-id="90237-105">Suggestion</span></span>|<span data-ttu-id="90237-106">這項變更移除了該相依性，並允許使用 SHA-256 憑證來簽署以 .NET Framework 4 和更早版本為目標的 ClickOnce 應用程式。</span><span class="sxs-lookup"><span data-stu-id="90237-106">This change removes that dependency and allows SHA-256 certificates to be used to sign ClickOnce apps that target .NET Framework 4 and earlier versions.</span></span>|
|<span data-ttu-id="90237-107">範圍</span><span class="sxs-lookup"><span data-stu-id="90237-107">Scope</span></span>|<span data-ttu-id="90237-108">次要</span><span class="sxs-lookup"><span data-stu-id="90237-108">Minor</span></span>|
|<span data-ttu-id="90237-109">版本</span><span class="sxs-lookup"><span data-stu-id="90237-109">Version</span></span>|<span data-ttu-id="90237-110">4.6</span><span class="sxs-lookup"><span data-stu-id="90237-110">4.6</span></span>|
|<span data-ttu-id="90237-111">類型</span><span class="sxs-lookup"><span data-stu-id="90237-111">Type</span></span>|<span data-ttu-id="90237-112">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="90237-112">Retargeting</span></span>|
