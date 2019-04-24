---
title: 設計和開發多容器和微服務 .NET 應用程式
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 了解設計和開發多容器與微服務型 .NET 應用程式的外部架構。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/02/2018
ms.openlocfilehash: 3bbf746aa9c0b66a097b8c4df2964b5679342fd0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973624"
---
# <a name="designing-and-developing-multi-container-and-microservice-based-net-applications"></a>設計和開發多容器和微服務 .NET 應用程式

開發容器化微服務應用程式表示您要建置多容器應用程式。不過，多容器應用程式也可能更簡單 (例如三層應用程式)，而且不一定是使用微服務架構所建置。

我們之前問到「建置微服務架構是否需要 Docker？」 答案顯然是不需要。 Docker 是啟用器並可提供顯著的優點，但微服務不一定需要容器和 Docker。 例如，使用 Azure Service Fabric 時，由於它支援微服務以簡單處理序或 Docker 容器執行，因此您不一定會使用 Docker 來建立微服務應用程式。

不過，如果您知道如何設計和開發同時以 Docker 容器為基礎的微服務應用程式，您將能夠設計和開發任何其他更簡單的應用程式模型。 例如，您可以設計同時需要多容器方法的三層應用程式。 基於此理由，以及由於微服務架構是容器世界中的重要趨勢，本節會著重於使用 Docker 容器的微服務架構實作。

>[!div class="step-by-step"]
>[上一頁](../docker-application-development-process/docker-app-development-workflow.md)
>[下一頁](microservice-application-design.md)