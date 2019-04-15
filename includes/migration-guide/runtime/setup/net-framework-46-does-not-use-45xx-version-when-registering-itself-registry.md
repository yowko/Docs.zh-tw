---
ms.openlocfilehash: ee5070a1a4c58d6c1282ba47c921436ca22722ff
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234165"
---
### <a name="the-net-framework-46-does-not-use-a-45xx-version-when-registering-itself-in-the-registry"></a><span data-ttu-id="43582-101">.NET Framework 4.6 在登錄中註冊本身時不使用 4.5.x.x 版本</span><span class="sxs-lookup"><span data-stu-id="43582-101">The .NET Framework 4.6 does not use a 4.5.x.x version when registering itself in the registry</span></span>

|   |   |
|---|---|
|<span data-ttu-id="43582-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="43582-102">Details</span></span>|<span data-ttu-id="43582-103">如預期一般，.NET Framework 4.6 在登錄中的版本機碼設定 (位於 <code>HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4\Full</code>) 開頭為 '4.6'，而不是 '4.5'。</span><span class="sxs-lookup"><span data-stu-id="43582-103">As one might expect, the version key set in the registry (at <code>HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4\Full</code>) for the .NET Framework 4.6 begins with '4.6', not '4.5'.</span></span> <span data-ttu-id="43582-104">相依於這些登錄機碼以得知電腦上所安裝之 .NET Framework 版本的應用程式應該加以更新，才能了解 4.6 是新的可能版本，以及其與先前的 4.5.x 版相容。</span><span class="sxs-lookup"><span data-stu-id="43582-104">Apps that depend on these registry keys to know which .NET Framework versions are installed on a machine should be updated to understand that 4.6 is a new possible version, and one that is compatible with previous 4.5.x releases.</span></span>|
|<span data-ttu-id="43582-105">建議</span><span class="sxs-lookup"><span data-stu-id="43582-105">Suggestion</span></span>|<span data-ttu-id="43582-106">藉由尋找 4.5 登錄機碼來更新 .NET Framework 4.5 安裝的應用程式探查，使其也接受 4.6。</span><span class="sxs-lookup"><span data-stu-id="43582-106">Update apps probing for a .NET Framework 4.5 install by looking for 4.5 registry keys to also accept 4.6.</span></span>|
|<span data-ttu-id="43582-107">範圍</span><span class="sxs-lookup"><span data-stu-id="43582-107">Scope</span></span>|<span data-ttu-id="43582-108">Edge</span><span class="sxs-lookup"><span data-stu-id="43582-108">Edge</span></span>|
|<span data-ttu-id="43582-109">版本</span><span class="sxs-lookup"><span data-stu-id="43582-109">Version</span></span>|<span data-ttu-id="43582-110">4.6</span><span class="sxs-lookup"><span data-stu-id="43582-110">4.6</span></span>|
|<span data-ttu-id="43582-111">類型</span><span class="sxs-lookup"><span data-stu-id="43582-111">Type</span></span>|<span data-ttu-id="43582-112">執行階段</span><span class="sxs-lookup"><span data-stu-id="43582-112">Runtime</span></span>|
