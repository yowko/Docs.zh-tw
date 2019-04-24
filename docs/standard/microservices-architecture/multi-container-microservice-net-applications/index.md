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
# <a name="designing-and-developing-multi-container-and-microservice-based-net-applications"></a><span data-ttu-id="10a25-103">設計和開發多容器和微服務 .NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="10a25-103">Designing and Developing Multi-Container and Microservice-Based .NET Applications</span></span>

<span data-ttu-id="10a25-104">開發容器化微服務應用程式表示您要建置多容器應用程式。不過，多容器應用程式也可能更簡單 (例如三層應用程式)，而且不一定是使用微服務架構所建置。</span><span class="sxs-lookup"><span data-stu-id="10a25-104">*Developing containerized microservice applications means you are building multi-container applications. However, a multi-container application could also be simpler—for example, a three-tier application—and might not be built using a microservice architecture.*</span></span>

<span data-ttu-id="10a25-105">我們之前問到「建置微服務架構是否需要 Docker？」</span><span class="sxs-lookup"><span data-stu-id="10a25-105">Earlier we raised the question "Is Docker necessary when building a microservice architecture?"</span></span> <span data-ttu-id="10a25-106">答案顯然是不需要。</span><span class="sxs-lookup"><span data-stu-id="10a25-106">The answer is a clear no.</span></span> <span data-ttu-id="10a25-107">Docker 是啟用器並可提供顯著的優點，但微服務不一定需要容器和 Docker。</span><span class="sxs-lookup"><span data-stu-id="10a25-107">Docker is an enabler and can provide significant benefits, but containers and Docker are not a hard requirement for microservices.</span></span> <span data-ttu-id="10a25-108">例如，使用 Azure Service Fabric 時，由於它支援微服務以簡單處理序或 Docker 容器執行，因此您不一定會使用 Docker 來建立微服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="10a25-108">As an example, you could create a microservices-based application with or without Docker when using Azure Service Fabric, which supports microservices running as simple processes or as Docker containers.</span></span>

<span data-ttu-id="10a25-109">不過，如果您知道如何設計和開發同時以 Docker 容器為基礎的微服務應用程式，您將能夠設計和開發任何其他更簡單的應用程式模型。</span><span class="sxs-lookup"><span data-stu-id="10a25-109">However, if you know how to design and develop a microservices-based application that is also based on Docker containers, you will be able to design and develop any other, simpler application model.</span></span> <span data-ttu-id="10a25-110">例如，您可以設計同時需要多容器方法的三層應用程式。</span><span class="sxs-lookup"><span data-stu-id="10a25-110">For example, you might design a three-tier application that also requires a multi-container approach.</span></span> <span data-ttu-id="10a25-111">基於此理由，以及由於微服務架構是容器世界中的重要趨勢，本節會著重於使用 Docker 容器的微服務架構實作。</span><span class="sxs-lookup"><span data-stu-id="10a25-111">Because of that, and because microservice architectures are an important trend within the container world, this section focuses on a microservice architecture implementation using Docker containers.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="10a25-112">[上一頁](../docker-application-development-process/docker-app-development-workflow.md)
>[下一頁](microservice-application-design.md)</span><span class="sxs-lookup"><span data-stu-id="10a25-112">[Previous](../docker-application-development-process/docker-app-development-workflow.md)
[Next](microservice-application-design.md)</span></span>