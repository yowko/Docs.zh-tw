---
title: 何時將 Windows 容器部署到 Azure 容器服務(即庫伯奈斯)
description: 使用 Azure 雲和 Windows 容器對現有 .NET 應用程式進行現代化 |何時將 Windows 容器部署到 Azure 容器服務(即庫伯奈斯)
ms.date: 04/30/2018
ms.openlocfilehash: 3ff51a70d4e158b831155ab4992ec32f5d98cedb
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2020
ms.locfileid: "80987760"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a>何時將 Windows 容器部署到 Azure 容器服務(即庫伯奈斯)

Azure 容器服務優化了專為 Azure 提供的熱門開源工具和技術的配置。 您將獲得一個開放的解決方案,該解決方案既可為容器提供便攜性,也可提供應用程式配置。 您可以選擇大小、主機數和協調器工具。 Azure 容器服務可為您處理基礎結構。

如果您已經在使用開源協調器(如 Kubernetes、Docker Swarm 或 DC/OS),則無需更改現有管理實踐將容器工作負載移動到雲。 使用您已經熟悉的應用程式管理工具,並通過您選擇的協調器的標準 API 終結點進行連接。

如果使用 Linux Docker 容器,但可能僅處於 Windows 容器的預覽狀態,則所有這些協調器都是成熟的環境。

例如,在 Kubernetes 中,對容器的支援是本機(一級公民),因此在 Kubernetes 上使用 Windows 容器也有效(在 2018 年初的 ACS 預覽版中)。

重要提示:Kubernetes 的 ACS(Azure 容器服務)的已演變和「更多 PaaS」版本是 AKS(Azure Kubernetes 服務),但是,截至 2018 年第 2 季度,Windows 容器仍然不受支援,但很快就會得到支援。

>[!div class="step-by-step"]
>[前一個](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
>[下一個](choosing-azure-compute-options-for-container-based-applications.md)
