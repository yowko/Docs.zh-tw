---
title: 針對雲端原生服務合併容器和無伺服器方法
description: 結合容器與 Kubernetes 與無伺服器方法
ms.date: 05/13/2020
ms.openlocfilehash: b1b85519ce02ddd1d69735d872cf24fadcc81ef7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91160888"
---
# <a name="combining-containers-and-serverless-approaches"></a>結合容器和無伺服器方法

雲端原生應用程式通常會利用容器和協調流程來執行服務。 通常會有機會將部分應用程式的服務公開為 Azure Functions。 不過，在將雲端原生應用程式部署至 Kubernetes 時，在相同的工具組中充分利用 Azure Functions 是很好的方法。 幸好，您可以在 Docker 容器內包裝 Azure Functions，並使用與 Kubernetes 應用程式其餘部分相同的程式和工具來部署它們。

## <a name="when-does-it-make-sense-to-use-containers-with-serverless"></a>使用無伺服器的容器有什麼意義？

您的 Azure 函數不知道其部署所在的平臺。 在某些案例中，您可能會有特定需求，而且需要自訂您的函式程式碼將在其上執行的環境。 您需要支援相依性的自訂映射，或預設映射不支援的設定。 在這些情況下，將您的函式部署在自訂 Docker 容器中是合理的。

## <a name="when-should-you-avoid-using-containers-with-azure-functions"></a>何時應避免使用 Azure Functions 的容器？

如果您想要使用耗用量計費，您將無法在容器中執行您的函式。 此外，如果您將函式部署至 Kubernetes 叢集，您將不再受益于 Azure Functions 所提供的內建擴充功能。 您必須使用 Kubernetes 的調整功能，如本章節稍早所述。

## <a name="how-to-combine-serverless-and-docker-containers"></a>如何結合無伺服器和 Docker 容器

若要將 Azure 函數包裝在 Docker 容器中，請安裝 [Azure Functions Core Tools](https://github.com/Azure/azure-functions-core-tools) ，然後執行下列命令：

```console
func init ProjectName --worker-runtime dotnet --docker
```

建立專案時，它會包含 Dockerfile 和設定為的背景工作執行時間 `dotnet` 。 現在，您可以在本機建立及測試您的函式。 使用和命令來建立並執行它  `docker build` `docker run` 。 如需開始使用 Docker 支援建立 Azure Functions 的詳細步驟，請參閱 [使用自訂映射在 Linux 上建立](/azure/azure-functions/functions-create-function-linux-custom-image) 函式教學課程。

## <a name="how-to-combine-serverless-and-kubernetes-with-keda"></a>如何結合無伺服器和 Kubernetes 與 KEDA

在本章中，您已瞭解 Azure Functions 的平臺會自動相應放大以符合需求。 不過，將容器化函式部署至 AKS 時，您會失去內建的調整功能。 為了解決這個 [情況，Kubernetes 型事件導向 (KEDA) ](/azure/azure-functions/functions-kubernetes-keda)。 它可讓您更精細地自動調整，以 `event-driven Kubernetes workloads,` 包含容器化函數。

KEDA 可為 Docker 容器中的函數執行時間提供事件驅動的調整功能。 KEDA 可以從零 (的實例進行調整，而不會因為負載而發生) 的事件 `n instances` 。 它會將自訂計量公開給 Kubernetes 自動調整程式 (水準 Pod 自動調整程式) ，藉此啟用自動調整。 將 Functions 容器與 KEDA 搭配使用，可讓您在任何 Kubernetes 叢集中複寫無伺服器函式功能。

值得注意的是，KEDA 專案現在是由雲端原生運算基礎 (CNCF) 來管理。

>[!div class="step-by-step"]
>[上一個](leverage-serverless-functions.md) 
>[下一步](deploy-containers-azure.md)
