---
title: 為雲端原生服務結合容器和無伺服器方法
description: 結合容器和 Kubernetes 與無伺服器方法
ms.date: 05/13/2020
ms.openlocfilehash: 67eee89659026db06eb16ef6f1154ab6935725a4
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614197"
---
# <a name="combining-containers-and-serverless-approaches"></a>結合容器和無伺服器方法

雲端原生應用程式通常會利用容器和協調流程來執行服務。 通常會有機會將部分應用程式的服務公開為 Azure Functions。 不過，在部署至 Kubernetes 的雲端原生應用程式中，利用此相同工具組中的 Azure Functions 是很好的做法。 幸好，您可以將 Azure Functions 包裝在 Docker 容器內，並使用與 Kubernetes 應用程式其餘部分相同的進程和工具進行部署。

## <a name="when-does-it-make-sense-to-use-containers-with-serverless"></a>使用無伺服器的容器有何意義？

您的 Azure 函數不知道其部署所在的平臺。 在某些情況下，您可能會有特定需求，而且需要自訂您的函式程式碼將在其上執行的環境。 您需要支援相依性的自訂映射，或預設映射不支援的設定。 在這些情況下，在自訂的 Docker 容器中部署您的函式是合理的。

## <a name="when-should-you-avoid-using-containers-with-azure-functions"></a>何時應避免使用 Azure Functions 的容器？

如果您想要使用取用計費，就無法在容器中執行您的函式。 此外，如果您將函式部署至 Kubernetes 叢集，將不再受益于 Azure Functions 所提供的內建調整。 您將需要使用 Kubernetes 的調整功能，如本章稍早所述。

## <a name="how-to-combine-serverless-and-docker-containers"></a>如何結合無伺服器和 Docker 容器

若要將 Azure 函式包裝在 Docker 容器中，請安裝[Azure Functions Core Tools](https://github.com/Azure/azure-functions-core-tools) ，然後執行下列命令：

```console
func init ProjectName --worker-runtime dotnet --docker
```

建立專案時，會包含 Dockerfile，以及設定為的背景工作執行時間 `dotnet` 。 現在，您可以在本機建立及測試您的函式。 使用和命令來建立並執行它 `docker build` `docker run` 。 如需開始使用 Docker 支援來建立 Azure Functions 的詳細步驟，請參閱[使用自訂映射在 Linux 上建立](https://docs.microsoft.com/azure/azure-functions/functions-create-function-linux-custom-image)函式教學課程。

## <a name="how-to-combine-serverless-and-kubernetes-with-keda"></a>如何結合無伺服器和 Kubernetes 與 KEDA

在本章中，您已瞭解 Azure Functions 的平臺會自動相應放大以符合需求。 不過，將容器化函式部署到 AKS 時，您會失去內建的調整功能。 若要解決這種情況，就會產生以[Kubernetes 為基礎的事件驅動（KEDA）](https://docs.microsoft.com/azure/azure-functions/functions-kubernetes-keda)。 它可為包含容器化函式提供更細緻的自動調整 `event-driven Kubernetes workloads,` 功能。

KEDA 提供事件驅動的調整功能給 Docker 容器中的函式執行時間。 KEDA 可以根據負載，從零個實例（沒有發生的事件）相應縮小至 `n instances` 。 它會將自訂計量公開至 Kubernetes 自動調整程式（水準 Pod 自動調整程式）來啟用自動調整。 將函式容器與 KEDA 搭配使用，可讓您在任何 Kubernetes 叢集中複寫無伺服器函式功能。

值得注意的是，KEDA 專案現在是由雲端原生運算基礎（由 CNCF）所管理。

>[!div class="step-by-step"]
>[上一個](leverage-serverless-functions.md) 
>[下一步](deploy-containers-azure.md)
