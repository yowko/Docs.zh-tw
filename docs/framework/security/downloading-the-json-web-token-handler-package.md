---
title: "下載 JSON Web 語彙基元處理常式套件"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d12b3f5b-f1f1-4a9d-a159-0c13e5976c90
caps.latest.revision: "3"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: d3821ff1da945df7c6e07e5baf69730173eacc87
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="downloading-the-json-web-token-handler-package"></a><span data-ttu-id="cb229-102">下載 JSON Web 語彙基元處理常式套件</span><span class="sxs-lookup"><span data-stu-id="cb229-102">Downloading the JSON Web Token Handler Package</span></span>
<span data-ttu-id="cb229-103">本主題討論如何在您的專案中下載並使用 JSON Web 權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="cb229-103">This topic discusses how to download and use the JSON Web Token Handler in your project.</span></span>  
  
## <a name="downloading-the-json-web-token-handler"></a><span data-ttu-id="cb229-104">下載 JSON Web 語彙基元處理常式</span><span class="sxs-lookup"><span data-stu-id="cb229-104">Downloading the JSON Web Token Handler</span></span>  
 <span data-ttu-id="cb229-105">JSON Web 權杖處理常式延伸模組以 NuGet 套件的形式供您使用，會將必要的組件和參考新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="cb229-105">The JSON Web Token Handler extension is available as a NuGet package, which adds the necessary assemblies and references to your project.</span></span> <span data-ttu-id="cb229-106">如果尚未安裝 NuGet，請移至 [nuget.org](http://nuget.org) 安裝它。</span><span class="sxs-lookup"><span data-stu-id="cb229-106">If you do not already have NuGet installed, go to [nuget.org](http://nuget.org) to install it.</span></span> <span data-ttu-id="cb229-107">您可以在 NuGet 前往其頁面，查看延伸模組的版本控制記錄：[JSON Web Token Handler on NuGet](http://www.nuget.org/packages/System.IdentityModel.Tokens.Jwt/) (NuGet 上的 JSON Web 權杖處理常式)。</span><span class="sxs-lookup"><span data-stu-id="cb229-107">You can see the versioning history for the extension by visiting its page on NuGet: [JSON Web Token Handler on NuGet](http://www.nuget.org/packages/System.IdentityModel.Tokens.Jwt/)</span></span>  
  
#### <a name="downloading-the-json-web-token-handler-by-using-the-package-manager-gui"></a><span data-ttu-id="cb229-108">使用套件管理員 GUI 下載 JSON Web 權杖處理常式</span><span class="sxs-lookup"><span data-stu-id="cb229-108">Downloading the JSON Web Token Handler by using the Package Manager GUI</span></span>  
  
1.  <span data-ttu-id="cb229-109">在 Visual Studio 中，以滑鼠右鍵按一下方案總管中的專案，然後選取 [管理 NuGet 套件]。</span><span class="sxs-lookup"><span data-stu-id="cb229-109">In Visual Studio, right-click your project in **Solution Explorer**, and then select **Manage NuGet Packages**.</span></span>  
  
2.  <span data-ttu-id="cb229-110">在 [管理 NuGet 套件] 視窗中，按一下搜尋方塊並輸入 `JWT Token Handler`，然後按 **Enter**。</span><span class="sxs-lookup"><span data-stu-id="cb229-110">In the **Manage NuGet Packages** window, click the search box and enter `JWT Token Handler` and press **Enter**.</span></span>  
  
3.  <span data-ttu-id="cb229-111">從 [結果] 窗格中，按一下第一個結果的 [安裝] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="cb229-111">From the results pane, click the **Install** button for the first result.</span></span>  
  
4.  <span data-ttu-id="cb229-112">即開始下載套件。</span><span class="sxs-lookup"><span data-stu-id="cb229-112">The package will begin downloading.</span></span> <span data-ttu-id="cb229-113">在它新增至您的專案之前，[接受授權] 對話方塊會先出現。</span><span class="sxs-lookup"><span data-stu-id="cb229-113">Before it is added to your project, the License Acceptance dialog will appear.</span></span> <span data-ttu-id="cb229-114">如果您同意授權條款，請按一下 [接受]。</span><span class="sxs-lookup"><span data-stu-id="cb229-114">If you agree to the license terms, click **I Accept**.</span></span>  
  
5.  <span data-ttu-id="cb229-115">最新的 JSON Web 權杖處理常式會下載並新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="cb229-115">The latest JSON Web Token Handler assemblies will be downloaded and added to your project.</span></span>  
  
#### <a name="downloading-the-json-web-token-handler-by-using-the-package-manager-console"></a><span data-ttu-id="cb229-116">使用套件管理員主控台下載 JSON Web 權杖處理常式</span><span class="sxs-lookup"><span data-stu-id="cb229-116">Downloading the JSON Web Token Handler by using the Package Manager Console</span></span>  
  
1.  <span data-ttu-id="cb229-117">在 Visual Studio 中，依序按一下 [工具]、[程式庫套件管理員] 和 [套件管理器主控台]。</span><span class="sxs-lookup"><span data-stu-id="cb229-117">In Visual Studio, click **Tools**, **Library Package Manager**, and then **Package Manager Console**.</span></span>  
  
2.  <span data-ttu-id="cb229-118">[套件管理器主控台] 視窗隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="cb229-118">The **Package Manager Console** appears.</span></span> <span data-ttu-id="cb229-119">輸入下列文字，然後按 **ENTER**：</span><span class="sxs-lookup"><span data-stu-id="cb229-119">Enter the following text and press **Enter**:</span></span>  
  
    ```powershell  
    Install-Package System.IdentityModel.Tokens.Jwt  
    ```  
  
3.  <span data-ttu-id="cb229-120">最新的 JSON Web 權杖處理常式會下載並新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="cb229-120">The latest JSON Web Token Handler assemblies will be downloaded and added to your project.</span></span>
