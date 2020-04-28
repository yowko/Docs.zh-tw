---
title: 為雲端原生服務結合容器和無伺服器方法
description: 結合容器和 Kubernetes 與無伺服器方法
ms.date: 04/23/2020
ms.openlocfilehash: fe9e9fd5d07132971d64bc6433a762fb7bd22048
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2020
ms.locfileid: "82199660"
---
# <a name="combining-containers-and-serverless-approaches"></a>結合容器和無伺服器方法

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

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

建立專案時，會包含 Dockerfile，以及設定為`dotnet`的背景工作執行時間。 現在，您可以在本機建立及測試您的函式。 使用`docker build`和`docker run`命令來建立並執行它。 如需開始使用 Docker 支援來建立 Azure Functions 的詳細步驟，請參閱[使用自訂映射在 Linux 上建立](https://docs.microsoft.com/azure/azure-functions/functions-create-function-linux-custom-image)函式教學課程。

## <a name="how-to-combine-serverless-and-kubernetes-with-keda"></a>如何結合無伺服器和 Kubernetes 與 KEDA

Azure 函式會根據以其為目標的事件速率，自動調整以滿足需求。 您一律可以利用 AKS 來裝載您的函式，並使用以 Kubernetes 為基礎的事件驅動自動調整，或 KEDA。 當沒有發生任何事件時，KEDA 可以相應減少為零個實例。 [深入瞭解如何使用 KEDA 調整 Azure](https://docs.microsoft.com/azure/azure-functions/functions-kubernetes-keda)函式。

>[!div class="step-by-step"]
>[上一頁](leverage-serverless-functions.md)
>[下一頁](deploy-containers-azure.md)
