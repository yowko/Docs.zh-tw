---
title: 當 Azure 容器服務 (也就是 Kubernetes) 部署 Windows 容器
description: 現代化現有的.NET 應用程式與 Azure 雲端和 Windows 容器 |當 Azure 容器服務 (也就是 Kubernetes) 部署 Windows 容器
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: b7f106e2b79a2c6bb24733debf7f4828505d66a6
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a>當 Azure 容器服務 (也就是 Kubernetes) 部署 Windows 容器

Azure 容器服務進行最佳化的熱門的開放原始碼工具和技術的組態，特別針對 Azure。 您會取得開啟的方案，提供可攜性適用於您的容器和應用程式組態。 您選取大小、 主機、 數目和 orchestrator 工具。 Azure 容器服務會為您處理基礎結構。

如果您已經使用開放原始碼 orchestrators Kubernetes、 Docker Swarm，或 DC/OS 等，您不需要變更您現有的管理作法，若要將容器的工作負載移到雲端。 使用您已熟悉的應用程式管理工具，並透過標準的應用程式開發介面端點連線，您所選擇的 orchestrator。

所有這些 orchestrators 是成熟的環境，如果您使用 Linux Docker 容器，但可能只會在 Windows 容器的預覽狀態。

例如，在 Kubernetes，對支援容器是原生 （第一級棒），所以使用 Windows 容器上 Kubernetes 也很有效 （在從早期 2018年開始在 ACS 中預覽）。

重要事項： 進化和 「 多個 PaaS"Kubernetes ACS （Azure 容器服務） 的版本是 AKS （Azure Kubernetes 服務）、 Windows 容器仍不支援為準，Q2 2018，不過，將立即支援。

>[!div class="step-by-step"]
[上一頁](when-to-deploy-windows-containers-to-service-fabric.md)
[下一頁](choosing-azure-compute-options-for-container-based-applications.md)
