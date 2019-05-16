---
title: 下載 JSON Web 語彙基元處理常式套件
ms.date: 10/10/2018
ms.assetid: d12b3f5b-f1f1-4a9d-a159-0c13e5976c90
ms.openlocfilehash: a8685a71d46778d932595965f32c0041b176bd83
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633531"
---
# <a name="download-the-json-web-token-handler-package"></a><span data-ttu-id="79b32-102">下載 JSON Web 權杖處理常式套件</span><span class="sxs-lookup"><span data-stu-id="79b32-102">Download the JSON Web Token Handler Package</span></span>

<span data-ttu-id="79b32-103">本主題討論如何在您的專案中下載並使用 JSON Web 權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="79b32-103">This topic discusses how to download and use the JSON Web Token Handler in your project.</span></span>

<span data-ttu-id="79b32-104">JSON Web 權杖處理常式延伸模組以 NuGet 套件的形式供您使用，會將必要的組件和參考新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="79b32-104">The JSON Web Token Handler extension is available as a NuGet package, which adds the necessary assemblies and references to your project.</span></span> <span data-ttu-id="79b32-105">如果尚未安裝 NuGet，請移至 [nuget.org](https://nuget.org) 安裝它。</span><span class="sxs-lookup"><span data-stu-id="79b32-105">If you do not already have NuGet installed, go to [nuget.org](https://nuget.org) to install it.</span></span> <span data-ttu-id="79b32-106">在 NuGet 前往其頁面，您可以看到延伸模組的版本歷程記錄：[JSON Web 權杖處理常式在 NuGet 上](https://www.nuget.org/packages/System.IdentityModel.Tokens.Jwt/)</span><span class="sxs-lookup"><span data-stu-id="79b32-106">You can see the versioning history for the extension by visiting its page on NuGet: [JSON Web Token Handler on NuGet](https://www.nuget.org/packages/System.IdentityModel.Tokens.Jwt/)</span></span>

## <a name="use-the-package-manager-gui"></a><span data-ttu-id="79b32-107">使用套件管理員 GUI</span><span class="sxs-lookup"><span data-stu-id="79b32-107">Use the Package Manager GUI</span></span>

1. <span data-ttu-id="79b32-108">在 Visual Studio 中，以滑鼠右鍵按一下方案總管中的專案，然後選取 [管理 NuGet 套件]。</span><span class="sxs-lookup"><span data-stu-id="79b32-108">In Visual Studio, right-click your project in **Solution Explorer**, and then select **Manage NuGet Packages**.</span></span>

2. <span data-ttu-id="79b32-109">在 [管理 NuGet 套件] 視窗中，按一下搜尋方塊並輸入 `JWT Token Handler`，然後按 **Enter**。</span><span class="sxs-lookup"><span data-stu-id="79b32-109">In the **Manage NuGet Packages** window, click the search box and enter `JWT Token Handler` and press **Enter**.</span></span>

3. <span data-ttu-id="79b32-110">從 [結果] 窗格中，按一下第一個結果的 [安裝] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="79b32-110">From the results pane, click the **Install** button for the first result.</span></span>

4. <span data-ttu-id="79b32-111">即開始下載套件。</span><span class="sxs-lookup"><span data-stu-id="79b32-111">The package will begin downloading.</span></span> <span data-ttu-id="79b32-112">在它新增至您的專案之前，[接受授權] 對話方塊會先出現。</span><span class="sxs-lookup"><span data-stu-id="79b32-112">Before it is added to your project, the License Acceptance dialog will appear.</span></span> <span data-ttu-id="79b32-113">如果您同意授權條款，請按一下 [接受]。</span><span class="sxs-lookup"><span data-stu-id="79b32-113">If you agree to the license terms, click **I Accept**.</span></span>

5. <span data-ttu-id="79b32-114">最新的 JSON Web 權杖處理常式會下載並新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="79b32-114">The latest JSON Web Token Handler assemblies will be downloaded and added to your project.</span></span>

## <a name="use-the-package-manager-console"></a><span data-ttu-id="79b32-115">使用套件管理員主控台</span><span class="sxs-lookup"><span data-stu-id="79b32-115">Use the Package Manager Console</span></span>

1. <span data-ttu-id="79b32-116">在 Visual Studio 中，按一下**工具** > **NuGet 套件管理員** > **Package Manager Console**。</span><span class="sxs-lookup"><span data-stu-id="79b32-116">In Visual Studio, click **Tools** > **NuGet Package Manager** > **Package Manager Console**.</span></span>

2. <span data-ttu-id="79b32-117">[套件管理器主控台] 視窗隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="79b32-117">The **Package Manager Console** appears.</span></span> <span data-ttu-id="79b32-118">輸入下列文字，然後按 **ENTER**：</span><span class="sxs-lookup"><span data-stu-id="79b32-118">Enter the following text and press **Enter**:</span></span>

    ```powershell
    Install-Package System.IdentityModel.Tokens.Jwt
    ```

3. <span data-ttu-id="79b32-119">最新的 JSON Web 權杖處理常式會下載並新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="79b32-119">The latest JSON Web Token Handler assemblies will be downloaded and added to your project.</span></span>
