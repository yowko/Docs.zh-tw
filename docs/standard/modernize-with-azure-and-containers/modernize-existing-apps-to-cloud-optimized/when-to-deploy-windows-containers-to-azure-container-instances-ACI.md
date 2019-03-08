---
title: 將 Windows 容器部署至 Azure Container Instances (ACI) 中的時機
description: 將現有的.NET 應用程式使用 Azure 雲端和 Windows 容器現代化 |將 Windows 容器部署至 Azure Container Instances (ACI) 中的時機
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/29/2018
ms.openlocfilehash: 03ee7c8b65e1a92dcc7fd40b44e9ba081f571487
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2019
ms.locfileid: "57674402"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a>將 Windows 容器部署至 Azure Container Instances (ACI) 中的時機

Azure 容器執行個體的主要價值主張是立即，您可以將容器部署到它，而且您不需要維護該環境，您不需要升級/修補基礎作業系統或所有的而言是透明的 Vm，並只需將部署準備使用環境的容器。

原因，以及在您想要使用 ACI 案例中的主要案例類似當您使用 Azure Vm 與容器，所以基本上，使用 Azure Container Instances 的主要案例包括：

- **開發/測試案例**
- **工作自動化**
- **CI/CD 代理程式**
- **小型/擴展批次處理**
- **簡單 web 應用程式**

簡單的 web 應用程式案例 ACI 公平案例，但請考慮在 ACI 中只能有單一的容器執行個體，每個容器映像，因為您不需要高可用性，並只會有有限延展性。

不過，即使在 ACI 被視為基礎結構，因為它只是提供單一容器執行個體，是相較於一般的 Azure 虛擬機器與 Windows Server 是一大福音。 使用 ACI，只需將容器部署到自我維護的環境，並只支付這些容器。 您不需要維護/更新/修補的 Vm，所以大部分的情況下，您也可以使用 Vm 與容器的太多的完美平台。 使用 ACI 很簡單，您只是將容器部署，則不需要建立 VM 環境，您只需將容器部署。

Azure Container Instances (ACI) 的主要優點為：

- 執行容器而不必管理伺服器
- 隨選容器增加彈性
- 將容器部署至雲端，前所未有的簡潔且高速 — 使用單一命令。
- 利用 hypervisor 隔離保護應用程式

簡單地說，透過 ACI 中，您可以開發應用程式快速而不需要管理虛擬機器或不必學習新工具。 它是只是您的應用程式，在容器中，在雲端中執行。

> [!div class="step-by-step"]
> [上一頁](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
> [下一頁](when-to-deploy-windows-containers-to-service-fabric.md)
