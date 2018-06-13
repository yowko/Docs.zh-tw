---
title: 下載驗證簽發者名稱登錄套件
ms.date: 03/30/2017
ms.assetid: ff8b0014-c5d4-4614-90f0-13fcc0ba777a
ms.openlocfilehash: 03b68f4b9dc6fde02c951968067e0311e4981d33
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33398745"
---
# <a name="downloading-the-validating-issuer-name-registry-package"></a><span data-ttu-id="801f9-102">下載驗證簽發者名稱登錄套件</span><span class="sxs-lookup"><span data-stu-id="801f9-102">Downloading the Validating Issuer Name Registry Package</span></span>
<span data-ttu-id="801f9-103">本主題討論如何在您的專案中下載與使用驗證簽發者名稱登錄 (VINR)。</span><span class="sxs-lookup"><span data-stu-id="801f9-103">This topic discusses how to download and use the Validating Issuer Name Registry (VINR) in your project.</span></span>  
  
## <a name="downloading-the-validating-issuer-name-registry"></a><span data-ttu-id="801f9-104">下載驗證簽發者名稱登錄</span><span class="sxs-lookup"><span data-stu-id="801f9-104">Downloading the Validating Issuer Name Registry</span></span>  
 <span data-ttu-id="801f9-105">VINR 以 NuGet 套件的形式供您使用，會將必要的組件和參考新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="801f9-105">The VINR is available as a NuGet package, which adds the necessary assemblies and references to your project.</span></span> <span data-ttu-id="801f9-106">如果尚未安裝 NuGet，請移至 [nuget.org](http://nuget.org) 安裝它。</span><span class="sxs-lookup"><span data-stu-id="801f9-106">If you do not already have NuGet installed, go to [nuget.org](http://nuget.org) to install it.</span></span> <span data-ttu-id="801f9-107">您可以在 NuGet 前往其頁面，查看延伸模組的版本控制記錄：[Microsoft Validating Issuer Name Registry on NuGet](https://nuget.org/packages/System.IdentityModel.Tokens.ValidatingIssuerNameRegistry/) (NuGet 上的 Microsoft 驗證簽發者名稱登錄)。</span><span class="sxs-lookup"><span data-stu-id="801f9-107">You can see the versioning history for the extension by visiting its page on NuGet: [Microsoft Validating Issuer Name Registry on NuGet](https://nuget.org/packages/System.IdentityModel.Tokens.ValidatingIssuerNameRegistry/)</span></span>  
  
#### <a name="downloading-the-validating-issuer-name-registry-by-using-the-package-manager-gui"></a><span data-ttu-id="801f9-108">使用套件管理員 GUI 下載驗證簽發者名稱登錄</span><span class="sxs-lookup"><span data-stu-id="801f9-108">Downloading the Validating Issuer Name Registry by using the Package Manager GUI</span></span>  
  
1.  <span data-ttu-id="801f9-109">在 Visual Studio 中，以滑鼠右鍵按一下方案總管中的專案，然後選取 [管理 NuGet 套件]。</span><span class="sxs-lookup"><span data-stu-id="801f9-109">In Visual Studio, right-click your project in **Solution Explorer**, and then select **Manage NuGet Packages**.</span></span>  
  
2.  <span data-ttu-id="801f9-110">在 [管理 NuGet 套件] 視窗中，按一下搜尋方塊並輸入 `ValidatingIssuerNameRegistry`，然後按 **Enter**。</span><span class="sxs-lookup"><span data-stu-id="801f9-110">In the **Manage NuGet Packages** window, click the search box and enter `ValidatingIssuerNameRegistry` and press **Enter**.</span></span>  
  
3.  <span data-ttu-id="801f9-111">從 [結果] 窗格中，按一下第一個結果的 [安裝] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="801f9-111">From the results pane, click the **Install** button for the first result.</span></span>  
  
4.  <span data-ttu-id="801f9-112">即開始下載套件。</span><span class="sxs-lookup"><span data-stu-id="801f9-112">The package will begin downloading.</span></span> <span data-ttu-id="801f9-113">在它新增至您的專案之前，[接受授權] 對話方塊會先出現。</span><span class="sxs-lookup"><span data-stu-id="801f9-113">Before it is added to your project, the License Acceptance dialog will appear.</span></span> <span data-ttu-id="801f9-114">如果您同意授權條款，請按一下 [接受]。</span><span class="sxs-lookup"><span data-stu-id="801f9-114">If you agree to the license terms, click **I Accept**.</span></span>  
  
5.  <span data-ttu-id="801f9-115">最新的 VINR 組件會下載並新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="801f9-115">The latest VINR assemblies will be downloaded and added to your project.</span></span>  
  
#### <a name="downloading-the-validating-issuer-name-registry-by-using-the-package-manager-console"></a><span data-ttu-id="801f9-116">使用套件管理器主控台下載驗證簽發者名稱登錄</span><span class="sxs-lookup"><span data-stu-id="801f9-116">Downloading the Validating Issuer Name Registry by using the Package Manager Console</span></span>  
  
1.  <span data-ttu-id="801f9-117">在 Visual Studio 中，依序按一下 [工具]、[程式庫套件管理員] 和 [套件管理器主控台]。</span><span class="sxs-lookup"><span data-stu-id="801f9-117">In Visual Studio, click **Tools**, **Library Package Manager**, and then **Package Manager Console**.</span></span>  
  
2.  <span data-ttu-id="801f9-118">[套件管理器主控台] 視窗隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="801f9-118">The **Package Manager Console** appears.</span></span> <span data-ttu-id="801f9-119">輸入下列文字，然後按 **ENTER**：</span><span class="sxs-lookup"><span data-stu-id="801f9-119">Enter the following text and press **Enter**:</span></span>  
  
    ```powershell  
    Install-Package System.IdentityModel.Tokens.ValidatingIssuerNameRegistry  
    ```  
  
3.  <span data-ttu-id="801f9-120">最新的 VINR 組件會下載並新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="801f9-120">The latest VINR assemblies will be downloaded and added to your project.</span></span>
