---
title: 故障排除"無法啟動此應用程式"
description: 瞭解如果看到"無法啟動此應用程式"對話方塊該怎麼辦。
ms.date: 09/05/2019
ms.openlocfilehash: 864c6ea23e9a048f060eee39d904bd4377be5084
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "76965902"
---
# <a name="troubleshooting-a-this-application-could-not-be-started-error-message"></a><span data-ttu-id="7c7a2-103">排除"無法啟動此應用程式"錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="7c7a2-103">Troubleshooting a 'This application could not be started' error message</span></span>

<span data-ttu-id="7c7a2-104">為 .NET 框架開發的應用程式通常需要在系統上安裝 .NET 框架的特定版本。</span><span class="sxs-lookup"><span data-stu-id="7c7a2-104">Applications that are developed for the .NET Framework typically require that a specific version of the .NET Framework be installed on your system.</span></span> <span data-ttu-id="7c7a2-105">在某些情況下，您可能嘗試在沒有已安裝版本或 .NET Framework 的預期版本的情況下運行應用程式。</span><span class="sxs-lookup"><span data-stu-id="7c7a2-105">In some cases, you may attempt to run an application without either an installed version or the expected version of the .NET Framework present.</span></span> <span data-ttu-id="7c7a2-106">這通常會生成如下所示的錯誤對話方塊：</span><span class="sxs-lookup"><span data-stu-id="7c7a2-106">This often produces an error dialog box like the following:</span></span>

![無法啟動這個應用程式](media/application-not-started/app-could-not-be-started.png)

<span data-ttu-id="7c7a2-108">這通常表示以下條件之一：</span><span class="sxs-lookup"><span data-stu-id="7c7a2-108">This typically indicates one of the following conditions:</span></span>

- <span data-ttu-id="7c7a2-109">系統上的 .NET 框架安裝已損壞。</span><span class="sxs-lookup"><span data-stu-id="7c7a2-109">A .NET Framework installation on your system has become corrupted.</span></span>

- <span data-ttu-id="7c7a2-110">無法檢測到應用程式所需的 .NET 框架版本。</span><span class="sxs-lookup"><span data-stu-id="7c7a2-110">The version of the .NET Framework needed by your application cannot be detected.</span></span>

<span data-ttu-id="7c7a2-111">要解決此問題，以便運行應用程式，請執行以下操作：</span><span class="sxs-lookup"><span data-stu-id="7c7a2-111">To address this issue so that you can run your application, do the following:</span></span>

1. <span data-ttu-id="7c7a2-112">下載[.NET 框架修復工具 （NetFx 修復工具.exe）。](https://www.microsoft.com/download/details.aspx?id=30135)</span><span class="sxs-lookup"><span data-stu-id="7c7a2-112">Download the [.NET Framework Repair Tool (NetFxRepairTool.exe)](https://www.microsoft.com/download/details.aspx?id=30135).</span></span> <span data-ttu-id="7c7a2-113">下載完成後，該工具將自動運行。</span><span class="sxs-lookup"><span data-stu-id="7c7a2-113">The tool runs automatically when the download completes.</span></span>

1. <span data-ttu-id="7c7a2-114">如果 .NET 框架修復工具建議執行任何其他操作（如下圖所示的操作），請選擇"**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="7c7a2-114">If the .NET Framework Repair Tool recommends any additional action, such as those shown in the following figure, select **Next**.</span></span>

   ![建議變更](media/application-not-started/repair-tool-recommended-changes.png)

1. <span data-ttu-id="7c7a2-116">.NET 框架修復工具顯示下圖中顯示的對話方塊，以指示更改已完成。</span><span class="sxs-lookup"><span data-stu-id="7c7a2-116">The .NET Framework Repair Tools displays a dialog box shown in the following figure to indicate that changes are complete.</span></span> <span data-ttu-id="7c7a2-117">嘗試重新運行應用程式時，請保持對話方塊打開狀態。</span><span class="sxs-lookup"><span data-stu-id="7c7a2-117">Leave the dialog box open while you to try rerun your application.</span></span> <span data-ttu-id="7c7a2-118">如果 .NET 框架修復工具已識別並更正損壞的 .NET 框架安裝，則此成功。</span><span class="sxs-lookup"><span data-stu-id="7c7a2-118">This should succeed if the .NET Framework Repair Tool has identified and corrected a corrupted .NET Framework installation.</span></span>

   ![建議變更](media/application-not-started/repair-tool-changes-complete.png)

1. <span data-ttu-id="7c7a2-120">如果應用程式成功運行，請選擇 **"完成"** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="7c7a2-120">If your application runs successfully, select the **Finish** button.</span></span> <span data-ttu-id="7c7a2-121">否則，選擇"**下一步**"按鈕。</span><span class="sxs-lookup"><span data-stu-id="7c7a2-121">Otherwise, select the **Next** button.</span></span>

1. <span data-ttu-id="7c7a2-122">如果選擇了"**下一步"** 按鈕，.NET 框架修復工具將顯示一個對話方塊，如下所示。</span><span class="sxs-lookup"><span data-stu-id="7c7a2-122">If you selected the **Next** button, the .NET Framework Repair Tool displays a dialog box like the following.</span></span> <span data-ttu-id="7c7a2-123">選擇 **"完成"** 按鈕以向 Microsoft 發送診斷資訊。</span><span class="sxs-lookup"><span data-stu-id="7c7a2-123">Select the **Finish** button to send diagnostic information to Microsoft.</span></span>

   ![無法解決問題](media/application-not-started/repair-tool-no-resolution.png)

1. <span data-ttu-id="7c7a2-125">如果仍然無法運行該應用程式，請安裝 Windows 版本支援的 .NET 框架的最新版本，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="7c7a2-125">If you still cannot run the application, install the latest version of the .NET Framework supported by your version of Windows, as shown in the following table.</span></span>

   |<span data-ttu-id="7c7a2-126">Windows 版本</span><span class="sxs-lookup"><span data-stu-id="7c7a2-126">Windows version</span></span>|<span data-ttu-id="7c7a2-127">.NET 框架安裝</span><span class="sxs-lookup"><span data-stu-id="7c7a2-127">.NET Framework installation</span></span>|
   |---|---|
   |<span data-ttu-id="7c7a2-128">Windows 10 周年更新和更高版本</span><span class="sxs-lookup"><span data-stu-id="7c7a2-128">Windows 10 Anniversary Update and later versions</span></span>|[<span data-ttu-id="7c7a2-129">.NET 框架 4.8 運行時</span><span class="sxs-lookup"><span data-stu-id="7c7a2-129">.NET Framework 4.8 Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |<span data-ttu-id="7c7a2-130">視窗 10， Windows 10 11 月更新</span><span class="sxs-lookup"><span data-stu-id="7c7a2-130">Windows 10, Windows 10 November Update</span></span>|[<span data-ttu-id="7c7a2-131">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="7c7a2-131">.NET Framework 4.6.2</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net462)|
   |<span data-ttu-id="7c7a2-132">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="7c7a2-132">Windows 8.1</span></span>|[<span data-ttu-id="7c7a2-133">.NET 框架 4.8 運行時</span><span class="sxs-lookup"><span data-stu-id="7c7a2-133">.NET Framework 4.8 Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |<span data-ttu-id="7c7a2-134">Windows 8</span><span class="sxs-lookup"><span data-stu-id="7c7a2-134">Windows 8</span></span>|[<span data-ttu-id="7c7a2-135">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="7c7a2-135">.NET Framework 4.6.1</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net461)|
   |<span data-ttu-id="7c7a2-136">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="7c7a2-136">Windows 7 SP1</span></span>|[<span data-ttu-id="7c7a2-137">.NET 框架 4.8 運行時</span><span class="sxs-lookup"><span data-stu-id="7c7a2-137">.NET Framework 4.8 Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |<span data-ttu-id="7c7a2-138">Windows Vista SP2</span><span class="sxs-lookup"><span data-stu-id="7c7a2-138">Windows Vista SP2</span></span>|[<span data-ttu-id="7c7a2-139">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="7c7a2-139">.NET Framework 4.6</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net46)|

   > [!NOTE]
   > <span data-ttu-id="7c7a2-140">.NET 框架 4.8 預先安裝在 2019 年 5 月 10 日的 Windows 更新中。</span><span class="sxs-lookup"><span data-stu-id="7c7a2-140">.NET Framework 4.8 is preinstalled on Windows 10 May 2019 Update.</span></span>

1. <span data-ttu-id="7c7a2-141">嘗試啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="7c7a2-141">Attempt to launch the application.</span></span>

1. <span data-ttu-id="7c7a2-142">在某些情況下，您可能會看到如下所示的對話方塊，該對話方塊要求您安裝 .NET 框架 3.5。</span><span class="sxs-lookup"><span data-stu-id="7c7a2-142">In some cases, you may see a dialog box like the following, which asks you to install the .NET Framework 3.5.</span></span> <span data-ttu-id="7c7a2-143">選擇 **"下載並安裝此功能**"以安裝 .NET 框架 3.5，然後再次啟動該應用程式。</span><span class="sxs-lookup"><span data-stu-id="7c7a2-143">Select **Download and install this feature** to install the .NET Framework 3.5, then launch the application again.</span></span>

   ![無法解決問題](media/application-not-started/install-3-5.png)

## <a name="see-also"></a><span data-ttu-id="7c7a2-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c7a2-145">See also</span></span>

- [<span data-ttu-id="7c7a2-146">.NET Framework 系統需求</span><span class="sxs-lookup"><span data-stu-id="7c7a2-146">.NET Framework System Requirements</span></span>](../get-started/system-requirements.md)
- [<span data-ttu-id="7c7a2-147">.NET Framework 安裝指南</span><span class="sxs-lookup"><span data-stu-id="7c7a2-147">.NET Framework installation guide</span></span>](index.md)
- [<span data-ttu-id="7c7a2-148">疑難排解 .NET Framework 安裝和解除安裝遭封鎖的問題</span><span class="sxs-lookup"><span data-stu-id="7c7a2-148">Troubleshoot blocked .NET Framework installations and uninstallations</span></span>](troubleshoot-blocked-installations-and-uninstallations.md)
