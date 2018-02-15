---
title: "不要將部署到 Windows 容器的時機"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |不要將部署到 Windows 容器的時機"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c74b71f9c80ab51cabe0e3c4abf32f292da30763
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="when-not-to-deploy-to-windows-containers"></a><span data-ttu-id="ceb85-103">不要將部署到 Windows 容器的時機</span><span class="sxs-lookup"><span data-stu-id="ceb85-103">When not to deploy to Windows Containers</span></span>

<span data-ttu-id="ceb85-104">Windows 容器不支援某些 Windows 技術。</span><span class="sxs-lookup"><span data-stu-id="ceb85-104">Some Windows technologies are not supported by Windows Containers.</span></span> <span data-ttu-id="ceb85-105">在這些情況下，您仍然要移轉到標準的 Vm，通常只以 Windows 和 IIS。</span><span class="sxs-lookup"><span data-stu-id="ceb85-105">In those cases, you still need to migrate to standards VMs, usually with just Windows and IIS.</span></span>

<span data-ttu-id="ceb85-106">不支援在 Windows 容器中，為準，mid 2017 案例：</span><span class="sxs-lookup"><span data-stu-id="ceb85-106">Cases not supported in Windows Containers, as of mid-2017:</span></span>

-   <span data-ttu-id="ceb85-107">Microsoft Message Queuing (MSMQ) 目前不支援在 Windows 容器中。</span><span class="sxs-lookup"><span data-stu-id="ceb85-107">Microsoft Message Queuing (MSMQ) currently is not supported in Windows Containers.</span></span>

    -   [<span data-ttu-id="ceb85-108">UserVoice 要求論壇</span><span class="sxs-lookup"><span data-stu-id="ceb85-108">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

    -   [<span data-ttu-id="ceb85-109">討論區論壇</span><span class="sxs-lookup"><span data-stu-id="ceb85-109">Discussion forum</span></span>](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

-   <span data-ttu-id="ceb85-110">Microsoft Distributed Transaction Coordinator (MSDTC) 目前不支援在 Windows 容器中</span><span class="sxs-lookup"><span data-stu-id="ceb85-110">Microsoft Distributed Transaction Coordinator (MSDTC) currently is not supported in Windows Containers</span></span>

    -   [<span data-ttu-id="ceb85-111">GitHub 問題</span><span class="sxs-lookup"><span data-stu-id="ceb85-111">GitHub issue</span></span>](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

-   <span data-ttu-id="ceb85-112">Microsoft Office 目前不支援容器</span><span class="sxs-lookup"><span data-stu-id="ceb85-112">Microsoft Office currently does not support containers</span></span>

    -   [<span data-ttu-id="ceb85-113">UserVoice 要求論壇</span><span class="sxs-lookup"><span data-stu-id="ceb85-113">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

<span data-ttu-id="ceb85-114">其他不支援的案例及社群中的要求，請參閱 UserVoice 論壇 Windows 容器： <https://windowsserver.uservoice.com/forums/304624-containers>。</span><span class="sxs-lookup"><span data-stu-id="ceb85-114">For additional not-supported scenarios and requests from the community, see the UserVoice forum for Windows Containers: <https://windowsserver.uservoice.com/forums/304624-containers>.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="ceb85-115">其他資源</span><span class="sxs-lookup"><span data-stu-id="ceb85-115">Additional resources</span></span>

-   <span data-ttu-id="ceb85-116">**虛擬機器和 Azure 中的容器**</span><span class="sxs-lookup"><span data-stu-id="ceb85-116">**Virtual machines and containers in Azure**</span></span>

    [<span data-ttu-id="ceb85-117">https://docs.microsoft.com/azure/virtual-machines/windows/containers</span><span class="sxs-lookup"><span data-stu-id="ceb85-117">https://docs.microsoft.com/azure/virtual-machines/windows/containers</span></span>](https://docs.microsoft.com/azure/virtual-machines/windows/containers)

>[!div class="step-by-step"]
<span data-ttu-id="ceb85-118">[上一頁](deploy-existing-net-apps-as-windows-containers.md)
[下一頁](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="ceb85-118">[Previous](deploy-existing-net-apps-as-windows-containers.md)
[Next](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span></span>
