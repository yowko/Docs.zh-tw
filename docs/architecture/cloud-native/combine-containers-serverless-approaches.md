---
title: 結合容器和無伺服器方法
description: 結合容器和 Kubernetes 與無伺服器方法
ms.date: 06/30/2019
ms.openlocfilehash: 58aff43adbdd2e629370cc685f32c7b61c25f85e
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183431"
---
# <a name="combining-containers-and-serverless-approaches"></a>結合容器和無伺服器方法

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

微服務為基礎的應用程式經常依賴容器、協調流程和訊息傳遞，來進行節點之間的通訊。 這項訊息是 Azure Functions 的理想工作，但在使用 Kubernetes 和相關工具設定及部署應用程式的其餘部分時，最好能夠在這個相同的工具組中利用 Azure Functions。 幸好，您可以將 Azure Functions 包裝在 Docker 容器中，並使用與 Kubernetes 應用程式其餘部分相同的進程和工具進行部署。

## <a name="when-does-it-make-sense-to-use-containers-with-serverless"></a>使用無伺服器的容器有何意義？

根據預設，您的無伺服器函式不知道其執行所在的平臺。 不過，在某些情況下，您可能會有特定需求，讓您自訂程式碼將在其中執行的容器映射很重要。 您可能想要使用自訂映射，因為您的函式依賴特定語言版本，或是預設映射不支援的相依性或設定需求。 在這些情況下，自訂您自己的容器，並在自訂的 Docker 容器中部署您的函式可能是合理的做法。

## <a name="when-should-you-avoid-using-containers-with-azure-functions"></a>何時應避免使用 Azure Functions 的容器？

如果您預期會受益于您函式的耗用量方案計費，如果您使用自己的容器，就無法這麼做。 此外，如果您不只是使用 Docker 容器，並將您的函式部署到您自己的 Kubernetes 叢集，就無法再受益于 Azure Functions 所提供的內建調整。 您必須使用 Kubernetes 的調整功能，如下所述。

## <a name="how-to-combine-serverless-and-docker-containers"></a>如何結合無伺服器和 Docker 容器

若要將 Azure 函式包裝在 Docker 容器中，請安裝 Azure Functions Core Tools，然後執行下列命令：

```console
func init ProjectName --docker
```

從下列選項中選擇您要的背景工作執行時間：

- `dotnet` (C#)
- `node` (JavaScript)
- `python`

建立專案時，會包含 Dockerfile。 現在，您可以在本機建立及測試您的函式。 使用`docker build` 和`docker run`命令來建立並執行它。 如需開始使用 Docker 支援來建立 Azure Functions 的詳細步驟，請參閱[使用自訂映射在 Linux 上建立](https://docs.microsoft.com/azure/azure-functions/functions-create-function-linux-custom-image)函式教學課程。

## <a name="how-to-combine-serverless-and-kubernetes-with-keda"></a>如何結合無伺服器和 Kubernetes 與 KEDA

Azure 函式會根據以指定函式為目標的事件速率，自動調整以滿足需求。 此外，您可以利用 Kubernetes 來裝載您的函式，並使用以 Kubernetes 為基礎的事件驅動自動調整，或 KEDA。 當沒有發生任何事件時，KEDA 可以相應減少為0個實例，然後為了回應事件，它可以使用其水準 pod 自動調整程式來相應增加容器的數目，以符合需求。 [深入瞭解如何使用 KEDA 調整 Azure](https://docs.microsoft.com/azure/azure-functions/functions-kubernetes-keda)函式。

## <a name="references"></a>reference

- [在 Docker 容器中執行 Azure Functions](https://markheath.net/post/azure-functions-docker)
- [使用自訂映射在 Linux 上建立函式](https://docs.microsoft.com/azure/azure-functions/functions-create-function-linux-custom-image)
- [具有 Kubernetes 事件驅動自動調整的 Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-kubernetes-keda)

>[!div class="step-by-step"]
>[上一頁](leverage-serverless-functions.md)
>[下一頁](deploy-containers-azure.md)
