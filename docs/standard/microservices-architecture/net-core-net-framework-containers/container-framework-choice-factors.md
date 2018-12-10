---
title: 決策資料表。 用於 Docker 的 .NET Frameworks
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 決策資料表，用於 Docker 的 .NET Frameworks
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/11/2018
ms.openlocfilehash: 8044e3064ac372750c174d8b47c3f7a63d6bbd0b
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53149051"
---
# <a name="decision-table-net-frameworks-to-use-for-docker"></a><span data-ttu-id="04999-104">決策資料表：用於 Docker 的 .NET Frameworks</span><span class="sxs-lookup"><span data-stu-id="04999-104">Decision table: .NET frameworks to use for Docker</span></span>

<span data-ttu-id="04999-105">以下決策資料表摘述要使用 .NET Framework 或 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="04999-105">The following decision table summarizes whether to use .NET Framework or .NET Core.</span></span> <span data-ttu-id="04999-106">請記住，Linux 容器需要以 Linux 為架構的 Docker 主機 (VM 或伺服器)，而 Windows 容器需要以 Windows Server 為架構的 Docker 主機 (VM 或伺服器)。</span><span class="sxs-lookup"><span data-stu-id="04999-106">Remember that for Linux containers, you need Linux-based Docker hosts (VMs or servers) and that for Windows Containers you need Windows Server based Docker hosts (VMs or servers).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="04999-107">您的開發電腦會執行一部 Docker 主機，Linux 或 Windows。</span><span class="sxs-lookup"><span data-stu-id="04999-107">Your development machines will run one Docker host, either Linux or Windows.</span></span> <span data-ttu-id="04999-108">您想要在一個解決方案中執行並測試的相關微服務，都需要在相同的容器平台上執行。</span><span class="sxs-lookup"><span data-stu-id="04999-108">Related microservices that you want to run and test together in one solution will all need to run on the same container platform.</span></span>

<table>
<thead>
<tr class="header">
<th><span data-ttu-id="04999-109"><strong>架構/應用程式類型</strong></span><span class="sxs-lookup"><span data-stu-id="04999-109"><strong>Architecture / App Type</strong></span></span></th>
<th><span data-ttu-id="04999-110"><strong>Linux 容器</strong></span><span class="sxs-lookup"><span data-stu-id="04999-110"><strong>Linux containers</strong></span></span></th>
<th><span data-ttu-id="04999-111"><strong>Windows 容器</strong></span><span class="sxs-lookup"><span data-stu-id="04999-111"><strong>Windows Containers</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="04999-112">容器上的微服務</span><span class="sxs-lookup"><span data-stu-id="04999-112">Microservices on containers</span></span></td>
<td><span data-ttu-id="04999-113">.NET Core</span><span class="sxs-lookup"><span data-stu-id="04999-113">.NET Core</span></span></td>
<td><span data-ttu-id="04999-114">.NET Core</span><span class="sxs-lookup"><span data-stu-id="04999-114">.NET Core</span></span></td>
</tr>
<tr class="even">
<td><span data-ttu-id="04999-115">整合型應用程式</span><span class="sxs-lookup"><span data-stu-id="04999-115">Monolithic app</span></span></td>
<td><span data-ttu-id="04999-116">.NET Core</span><span class="sxs-lookup"><span data-stu-id="04999-116">.NET Core</span></span></td>
<td><p><span data-ttu-id="04999-117">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="04999-117">.NET Framework</span></span></p>
<p><span data-ttu-id="04999-118">.NET Core</span><span class="sxs-lookup"><span data-stu-id="04999-118">.NET Core</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="04999-119">同級最佳效能和延展性</span><span class="sxs-lookup"><span data-stu-id="04999-119">Best-in-class performance and scalability</span></span></td>
<td><span data-ttu-id="04999-120">.NET Core</span><span class="sxs-lookup"><span data-stu-id="04999-120">.NET Core</span></span></td>
<td><span data-ttu-id="04999-121">.NET Core</span><span class="sxs-lookup"><span data-stu-id="04999-121">.NET Core</span></span></td>
</tr>
<tr class="even">
<td><span data-ttu-id="04999-122">Windows Server 舊版應用程式 (「棕地」) 移轉至容器</span><span class="sxs-lookup"><span data-stu-id="04999-122">Windows Server legacy app ("brown-field") migration to containers</span></span></td>
<td>--</td>
<td><span data-ttu-id="04999-123">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="04999-123">.NET Framework</span></span></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="04999-124">新的容器型開發 (「綠燈區」)</span><span class="sxs-lookup"><span data-stu-id="04999-124">New container-based development ("green-field")</span></span></td>
<td><span data-ttu-id="04999-125">.NET Core</span><span class="sxs-lookup"><span data-stu-id="04999-125">.NET Core</span></span></td>
<td><span data-ttu-id="04999-126">.NET Core</span><span class="sxs-lookup"><span data-stu-id="04999-126">.NET Core</span></span></td>
</tr>
<tr class="even">
<td><span data-ttu-id="04999-127">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="04999-127">ASP.NET Core</span></span></td>
<td><span data-ttu-id="04999-128">.NET Core</span><span class="sxs-lookup"><span data-stu-id="04999-128">.NET Core</span></span></td>
<td><p><span data-ttu-id="04999-129">.NET Core (建議)</span><span class="sxs-lookup"><span data-stu-id="04999-129">.NET Core (recommended)</span></span></p>
<p><span data-ttu-id="04999-130">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="04999-130">.NET Framework</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="04999-131">ASP.NET 4 (MVC 5、Web API 2 和 Web Form)</span><span class="sxs-lookup"><span data-stu-id="04999-131">ASP.NET 4 (MVC 5, Web API 2, and Web Forms)</span></span></td>
<td>--</td>
<td><span data-ttu-id="04999-132">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="04999-132">.NET Framework</span></span></td>
</tr>
<tr class="even">
<td><span data-ttu-id="04999-133">SignalR 服務</span><span class="sxs-lookup"><span data-stu-id="04999-133">SignalR services</span></span></td>
<td><span data-ttu-id="04999-134">.NET Core 2.1 或更新版本</span><span class="sxs-lookup"><span data-stu-id="04999-134">.NET Core 2.1 or higher version</span></span></td>
<td><p><span data-ttu-id="04999-135">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="04999-135">.NET Framework</span></span></p>
<p><span data-ttu-id="04999-136">.NET Core 2.1 或更新版本</span><span class="sxs-lookup"><span data-stu-id="04999-136">.NET Core 2.1 or higher version</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="04999-137">WCF、WF 和其他舊版架構</span><span class="sxs-lookup"><span data-stu-id="04999-137">WCF, WF, and other legacy frameworks</span></span></td>
<td><span data-ttu-id="04999-138">.NET Core 中的 WCF (僅 WCF 用戶端程式庫)</span><span class="sxs-lookup"><span data-stu-id="04999-138">WCF in .NET Core (only the WCF client library)</span></span></td>
<td><p><span data-ttu-id="04999-139">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="04999-139">.NET Framework</span></span></p>
<p><span data-ttu-id="04999-140">.NET Core 中的 WCF (僅 WCF 用戶端程式庫)</span><span class="sxs-lookup"><span data-stu-id="04999-140">WCF in .NET Core (only the WCF client library)</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="04999-141">Azure 服務的使用量</span><span class="sxs-lookup"><span data-stu-id="04999-141">Consumption of Azure services</span></span></td>
<td><p><span data-ttu-id="04999-142">.NET Core</span><span class="sxs-lookup"><span data-stu-id="04999-142">.NET Core</span></span></p>
<p><span data-ttu-id="04999-143">(最終所有 Azure 服務都會提供適用於 .NET Core 的用戶端 SDK)</span><span class="sxs-lookup"><span data-stu-id="04999-143">(eventually all Azure services will provide client SDKs for .NET Core)</span></span></p></td>
<td><p><span data-ttu-id="04999-144">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="04999-144">.NET Framework</span></span></p>
<p><span data-ttu-id="04999-145">.NET Core</span><span class="sxs-lookup"><span data-stu-id="04999-145">.NET Core</span></span></p>
<p><span data-ttu-id="04999-146">(最終所有 Azure 服務都會提供適用於 .NET Core 的用戶端 SDK)</span><span class="sxs-lookup"><span data-stu-id="04999-146">(eventually all Azure services will provide client SDKs for .NET Core)</span></span></p></td>
</tr>
</tbody>
</table>

>[!div class="step-by-step"]
><span data-ttu-id="04999-147">[上一頁](net-framework-container-scenarios.md)
>[下一頁](net-container-os-targets.md)</span><span class="sxs-lookup"><span data-stu-id="04999-147">[Previous](net-framework-container-scenarios.md)
[Next](net-container-os-targets.md)</span></span>