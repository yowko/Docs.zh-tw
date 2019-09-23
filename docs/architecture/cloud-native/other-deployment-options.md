---
title: 其他容器部署選項
description: 使用 Azure 的其他容器部署選項
ms.date: 06/30/2019
ms.openlocfilehash: 892514417cb8650c28b7491315f767758278ad6e
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184880"
---
# <a name="other-container-deployment-options"></a>其他容器部署選項

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

除了部署至 AKS，您也可以將容器部署到容器和 Azure 容器實例的 Azure App Service。

## <a name="when-does-it-make-sense-to-deploy-to-app-service-for-containers"></a>部署至容器的 App Service 有何意義？

不需要協調流程的簡單生產應用程式很適合用於容器 Azure App Service。

## <a name="how-to-deploy-to-app-service-for-containers"></a>如何部署至容器的 App Service

若要部署至[容器的 Azure App Service](https://azure.microsoft.com/services/app-service/containers/)，您必須已設定 AZURE CONTAINER REGISTRY （ACR）和認證來進行存取。 將您想要裝載的容器推送至登錄，使其可供提取到您的 Azure App Service。 建立之後，您可以設定應用程式進行持續部署，每當您更新 ACR 中的對應映射時，它就會自動將更新部署至應用程式。

## <a name="when-does-it-make-sense-to-deploy-to-azure-container-instances"></a>部署至 Azure 容器實例的時機為何？

Azure 容器實例最適合用於測試案例。 它們提供快速且簡單的方法，將應用程式部署至雲端裝載的容器實例。 當您不需要 Azure Kubernetes Service 所提供的調整和協調流程功能時，可使用它們來測試或示範應用程式。

## <a name="how-to-deploy-an-app-to-azure-container-instances"></a>如何將應用程式部署至 Azure 容器實例

若要部署至[Azure 容器實例（ACI）](https://docs.microsoft.com/azure/container-instances/)，您必須已設定 AZURE CONTAINER REGISTRY （ACR）和認證來進行存取。 您也必須先將容器映射推送至登錄，才能將它提取到 ACI 中。 您可以使用 Azure CLI 或透過入口網站來處理 ACI。 Azure Container registry 可讓您輕鬆地直接從登錄內將個別容器實例部署至 ACI，如圖3-14 所示。

![Azure Container Registry 執行實例](./media/acr-runinstance-contextmenu.png)

**圖 3-14**。 Azure Container Registry 執行實例

從登錄建立容器實例只需要您指定一般的 Azure 設定（名稱、訂用帳戶、資源群組和位置）、要配置給容器的記憶體數量，以及應該接聽的埠。 本[快速入門說明如何使用 Azure 入口網站將容器實例部署至 ACI](https://docs.microsoft.com/azure/container-instances/container-instances-quickstart-portal)。

部署完成之後，尋找新部署容器的 IP 位址，並透過您指定的埠與其通訊。

Azure 容器實例提供最快速且最簡單的方式，讓您在 Azure 中執行容器。 不需要設定 app service 或 orchestrator，或處理虛擬機器。 不過，由於簡單起見，ACI 主要應該用於測試用途。 如果您的應用程式需要自動調整、多個設定為一起運作的容器，或任何其他複雜的功能，則可使用其他更適合的 Azure 服務來裝載您的應用程式。

## <a name="references"></a>reference

- [Azure 容器實例檔](https://docs.microsoft.com/azure/container-instances/)
- [從 ACR 部署容器實例](https://docs.microsoft.com/azure/container-instances/container-instances-using-azure-container-registry#deploy-with-azure-portal)

>[!div class="step-by-step"]
>[上一頁](scale-containers-serverless.md)
>[下一頁](communication-patterns.md) <!-- Next Chapter -->
