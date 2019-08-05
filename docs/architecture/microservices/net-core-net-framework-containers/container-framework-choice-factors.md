---
title: 決策資料表。 用於 Docker 的 .NET Frameworks
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 決策資料表，用於 Docker 的 .NET Frameworks
ms.date: 09/11/2018
ms.openlocfilehash: 96b2750e52d64b06444b7f87dea624879f37d3d7
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68675815"
---
# <a name="decision-table-net-frameworks-to-use-for-docker"></a>決策資料表：用於 Docker 的 .NET Frameworks

以下決策資料表摘述要使用 .NET Framework 或 .NET Core。 請記住，Linux 容器需要以 Linux 為架構的 Docker 主機 (VM 或伺服器)，而 Windows 容器需要以 Windows Server 為架構的 Docker 主機 (VM 或伺服器)。

> [!IMPORTANT]
> 您的開發電腦會執行一部 Docker 主機，Linux 或 Windows。 您想要在一個解決方案中執行並測試的相關微服務，都需要在相同的容器平台上執行。

<table>
<thead>
<tr class="header">
<th><strong>架構/應用程式類型</strong></th>
<th><strong>Linux 容器</strong></th>
<th><strong>Windows 容器</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>容器上的微服務</td>
<td>.NET Core</td>
<td>.NET Core</td>
</tr>
<tr class="even">
<td>整合型應用程式</td>
<td>.NET Core</td>
<td><p>.NET Framework</p>
<p>.NET Core</p></td>
</tr>
<tr class="odd">
<td>同級最佳效能和延展性</td>
<td>.NET Core</td>
<td>.NET Core</td>
</tr>
<tr class="even">
<td>Windows Server 舊版應用程式 (「棕地」) 移轉至容器</td>
<td>--</td>
<td>.NET Framework</td>
</tr>
<tr class="odd">
<td>新的容器型開發 (「綠燈區」)</td>
<td>.NET Core</td>
<td>.NET Core</td>
</tr>
<tr class="even">
<td>ASP.NET Core</td>
<td>.NET Core</td>
<td><p>.NET Core (建議)</p>
<p>.NET Framework</p></td>
</tr>
<tr class="odd">
<td>ASP.NET 4 (MVC 5、Web API 2 和 Web Form)</td>
<td>--</td>
<td>.NET Framework</td>
</tr>
<tr class="even">
<td>SignalR 服務</td>
<td>.NET Core 2.1 或更新版本</td>
<td><p>.NET Framework</p>
<p>.NET Core 2.1 或更新版本</p></td>
</tr>
<tr class="odd">
<td>WCF、WF 和其他舊版架構</td>
<td>.NET Core 中的 WCF (僅 WCF 用戶端程式庫)</td>
<td><p>.NET Framework</p>
<p>.NET Core 中的 WCF (僅 WCF 用戶端程式庫)</p></td>
</tr>
<tr class="even">
<td>Azure 服務的使用量</td>
<td><p>.NET Core</p>
<p>(最終所有 Azure 服務都會提供適用於 .NET Core 的用戶端 SDK)</p></td>
<td><p>.NET Framework</p>
<p>.NET Core</p>
<p>(最終所有 Azure 服務都會提供適用於 .NET Core 的用戶端 SDK)</p></td>
</tr>
</tbody>
</table>

>[!div class="step-by-step"]
>[上一頁](net-framework-container-scenarios.md)
>[下一頁](net-container-os-targets.md)
