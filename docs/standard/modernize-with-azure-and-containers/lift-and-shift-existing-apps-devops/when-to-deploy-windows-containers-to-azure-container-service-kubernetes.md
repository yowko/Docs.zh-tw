---
title: "當 Azure 容器服務 (也就是 Kubernetes) 部署 Windows 容器"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |當 Azure 容器服務 (也就是 Kubernetes) 部署 Windows 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.prod: .net
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f0a096712e14e506403961f0b9283ca4b707cbda
ms.sourcegitcommit: d3cfda0943364aaf6ccd574f55f584576c8a4fee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2018
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a>當 Azure 容器服務 (也就是 Kubernetes) 部署 Windows 容器

Azure 容器服務進行最佳化的熱門的開放原始碼工具和技術的組態，特別針對 Azure。 您會取得開啟的方案，提供可攜性適用於您的容器和應用程式組態。 您選取大小、 主機、 數目和 orchestrator 工具。 Azure 容器服務會為您處理基礎結構。

如果您已經使用開放原始碼 orchestrators Kubernetes、 Docker Swarm，或 DC/OS 等，您不需要變更您現有的管理作法，若要將容器的工作負載移到雲端。 使用您已經熟悉的而且您選擇的 orchestrator 透過標準的應用程式開發介面端點連線時，應用程式管理工具。

如果您使用 Linux Docker 容器，但它們也支援 Windows 容器 （部分前面，一些還要新，取決於 orchestrator） 時，所有這些 orchestrators 是 2017 的成熟的環境。

例如，在 Kubernetes，對支援容器是原生 （第一級棒），所以使用 Windows 容器上 Kubernetes 也是非常有效且可靠 （直到預覽中及早切換 2017年）。

>[!div class="step-by-step"]
[上一頁](when-to-deploy-windows-containers-to-service-fabric.md)
[下一頁](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
