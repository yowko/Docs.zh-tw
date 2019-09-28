---
title: 疑難排解「無法啟動此應用程式」
description: 如果您看到 [無法啟動此應用程式] 對話方塊，請瞭解該怎麼辦。
author: rpetrusha
ms.author: ronpet
ms.date: 09/05/2019
ms.openlocfilehash: 2534979e8dea886c2d7298c57e12b66d7a962c69
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71401701"
---
# <a name="troubleshooting-a-this-application-could-not-be-started-error-message"></a><span data-ttu-id="19861-103">疑難排解「此應用程式無法啟動」錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="19861-103">Troubleshooting a 'This application could not be started' error message</span></span>

<span data-ttu-id="19861-104">針對 .NET Framework 所開發的應用程式通常需要在您的系統上安裝特定版本的 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="19861-104">Applications that are developed for the .NET Framework typically require that a specific version of the .NET Framework be installed on your system.</span></span> <span data-ttu-id="19861-105">在某些情況下，您可能會嘗試執行應用程式，而不需要有已安裝的版本或所需的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="19861-105">In some cases, you may attempt to run an application without either an installed version or the expected version of the .NET Framework present.</span></span> <span data-ttu-id="19861-106">這通常會產生如下的錯誤對話方塊：</span><span class="sxs-lookup"><span data-stu-id="19861-106">This often produces an error dialog box like the following:</span></span>

![無法啟動這個應用程式](media/application-not-started/app-could-not-be-started.png)

<span data-ttu-id="19861-108">這通常表示下列其中一種情況：</span><span class="sxs-lookup"><span data-stu-id="19861-108">This typically indicates one of the following conditions:</span></span>

- <span data-ttu-id="19861-109">系統上的 .NET Framework 安裝已損毀。</span><span class="sxs-lookup"><span data-stu-id="19861-109">A .NET Framework installation on your system has become corrupted.</span></span>

- <span data-ttu-id="19861-110">無法偵測到您的應用程式所需的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="19861-110">The version of the .NET Framework needed by your application cannot be detected.</span></span>

<span data-ttu-id="19861-111">若要解決此問題，讓您能夠執行應用程式，請執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="19861-111">To address this issue so that you can run your application, do the following:</span></span>

1. <span data-ttu-id="19861-112">下載[.NET Framework Repair Tool （NetFxRepairTool）](https://www.microsoft.com/download/details.aspx?id=30135)。</span><span class="sxs-lookup"><span data-stu-id="19861-112">Download the [.NET Framework Repair Tool (NetFxRepairTool.exe)](https://www.microsoft.com/download/details.aspx?id=30135).</span></span> <span data-ttu-id="19861-113">此工具會在下載完成時自動執行。</span><span class="sxs-lookup"><span data-stu-id="19861-113">The tool runs automatically when the download completes.</span></span>

1. <span data-ttu-id="19861-114">如果 .NET Framework 修復工具建議任何其他動作（例如下圖所示的動作），請選取 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="19861-114">If the .NET Framework Repair Tool recommends any additional action, such as those shown in the following figure, select **Next**.</span></span>

   ![建議變更](media/application-not-started/repair-tool-recommended-changes.png)

1. <span data-ttu-id="19861-116">[.NET Framework 修復工具] 會顯示如下圖所示的對話方塊，指出變更已完成。</span><span class="sxs-lookup"><span data-stu-id="19861-116">The .NET Framework Repair Tools displays a dialog box shown in the following figure to indicate that changes are complete.</span></span> <span data-ttu-id="19861-117">在您嘗試重新執行應用程式時，讓對話方塊保持開啟。</span><span class="sxs-lookup"><span data-stu-id="19861-117">Leave the dialog box open while you to try rerun your application.</span></span> <span data-ttu-id="19861-118">如果 .NET Framework 修復工具已識別並更正損毀的 .NET Framework 安裝，這應該會成功。</span><span class="sxs-lookup"><span data-stu-id="19861-118">This should succeed if the .NET Framework Repair Tool has identified and corrected a corrupted .NET Framework installation.</span></span>

   ![建議變更](media/application-not-started/repair-tool-changes-complete.png)

1. <span data-ttu-id="19861-120">如果您的應用程式順利執行，請選取 [**完成]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="19861-120">If your application runs successfully, select the **Finish** button.</span></span> <span data-ttu-id="19861-121">否則，請選取 [**下一步]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="19861-121">Otherwise, select the **Next** button.</span></span>

1. <span data-ttu-id="19861-122">如果您選取 [**下一步]** 按鈕，[.NET Framework Repair] 工具會顯示如下的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="19861-122">If you selected the **Next** button, the .NET Framework Repair Tool displays a a dialog box like the following.</span></span> <span data-ttu-id="19861-123">選取 [**完成]** 按鈕，將診斷資訊傳送給 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="19861-123">Select the **Finish** button to send diagnostic information to Microsoft.</span></span>

   ![無法解決問題](media/application-not-started/repair-tool-no-resolution.png)

1. <span data-ttu-id="19861-125">如果您仍然無法執行應用程式，請安裝您的 Windows 版本所支援的最新版本 .NET Framework，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="19861-125">If you still cannot run the application, install the latest version of the .NET Framework supported by your version of Windows, as shown in the following table.</span></span>

   |<span data-ttu-id="19861-126">Windows 版本</span><span class="sxs-lookup"><span data-stu-id="19861-126">Windows version</span></span>|<span data-ttu-id="19861-127">.NET Framework 安裝</span><span class="sxs-lookup"><span data-stu-id="19861-127">.NET Framework installation</span></span>|
   |---|---|
   |<span data-ttu-id="19861-128">Windows 10 年度更新版和更新版本</span><span class="sxs-lookup"><span data-stu-id="19861-128">Windows 10 Anniversary Update and later versions</span></span>|[<span data-ttu-id="19861-129">.NET Framework 4.8 執行時間</span><span class="sxs-lookup"><span data-stu-id="19861-129">.NET Framework 4.8 Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |<span data-ttu-id="19861-130">Windows 10，Windows 10 11 月更新</span><span class="sxs-lookup"><span data-stu-id="19861-130">Windows 10, Windows 10 November Update</span></span>|[<span data-ttu-id="19861-131">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="19861-131">.NET Framework 4.6.2</span></span>](https://www.microsoft.com/download/details.aspx?id=53345)|
   |<span data-ttu-id="19861-132">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="19861-132">Windows 8.1</span></span>|[<span data-ttu-id="19861-133">.NET Framework 4.8 執行時間</span><span class="sxs-lookup"><span data-stu-id="19861-133">.NET Framework 4.8 Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |<span data-ttu-id="19861-134">Windows 8</span><span class="sxs-lookup"><span data-stu-id="19861-134">Windows 8</span></span>|[<span data-ttu-id="19861-135">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="19861-135">.NET Framework 4.6.1</span></span>](https://www.microsoft.com/download/details.aspx?id=49981)|
   |<span data-ttu-id="19861-136">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="19861-136">Windows 7 SP1</span></span>|[<span data-ttu-id="19861-137">.NET Framework 4.8 執行時間</span><span class="sxs-lookup"><span data-stu-id="19861-137">.NET Framework 4.8 Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |<span data-ttu-id="19861-138">Windows Vista SP2</span><span class="sxs-lookup"><span data-stu-id="19861-138">Windows Vista SP2</span></span>|[<span data-ttu-id="19861-139">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="19861-139">.NET Framework 4.6</span></span>](https://www.microsoft.com/download/details.aspx?id=48130)|

   > [!NOTE]
   >  <span data-ttu-id="19861-140">.NET Framework 4.8 已預先安裝在 Windows 10 5 月2019更新。</span><span class="sxs-lookup"><span data-stu-id="19861-140">.NET Framework 4.8 is preinstalled on Windows 10 May 2019 Update.</span></span>

1. <span data-ttu-id="19861-141">嘗試啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="19861-141">Attempt to launch the application.</span></span>

1. <span data-ttu-id="19861-142">在某些情況下，您可能會看到如下所示的對話方塊，這會要求您安裝 .NET Framework 3.5。</span><span class="sxs-lookup"><span data-stu-id="19861-142">In some cases, you may see a dialog box like the following, which asks you to install the .NET Framework 3.5.</span></span> <span data-ttu-id="19861-143">選取 [**下載並安裝此功能**] 以安裝 .NET Framework 3.5，然後再次啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="19861-143">Select **Download and install this feature** to install the .NET Framework 3.5, then launch the application again.</span></span>

   ![無法解決問題](media/application-not-started/install-3-5.png)

## <a name="see-also"></a><span data-ttu-id="19861-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19861-145">See also</span></span>

- [<span data-ttu-id="19861-146">.NET Framework 系統需求</span><span class="sxs-lookup"><span data-stu-id="19861-146">.NET Framework System Requirements</span></span>](../get-started/system-requirements.md)
- [<span data-ttu-id="19861-147">.NET Framework 安裝指南</span><span class="sxs-lookup"><span data-stu-id="19861-147">.NET Framework installation guide</span></span>](index.md)
- [<span data-ttu-id="19861-148">疑難排解 .NET Framework 安裝和解除安裝遭封鎖的問題</span><span class="sxs-lookup"><span data-stu-id="19861-148">Troubleshoot blocked .NET Framework installations and uninstallations</span></span>](troubleshoot-blocked-installations-and-uninstallations.md)
