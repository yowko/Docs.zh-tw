---
title: "服務導向架構"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |服務導向架構"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 970ff86c77100077d4c7710c0a697d1745d35819
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="service-oriented-architecture"></a>服務導向架構 

服務導向架構 (SOA) 是過度的詞彙，且有不同的項目對不同的人。 但為共同點，SOA 表示您將應用程式結構由分解 （通常為 HTTP 服務） 都能夠分類為不同的型別，如子系統或層級的多個服務。

這些服務現在可以部署為 Docker 容器，它可以解決部署問題，因為容器映像內含的所有相依性。 不過，當您需要向上延展 SOA 應用程式，您可能需要延展性和可用性挑戰，如果您要部署單一的 Docker 主機。 這是 Docker 叢集軟體或 orchestrator 將會幫助您，我們用來描述 microservices 的部署方法的後續章節中所述。

Docker 容器是很有用 （但非必要） 的傳統服務導向架構和更進階的 microservices 架構。

Microservices 衍生自 SOA，但 SOA microservices 架構不同。 像大中央 broker 的功能，在組織層級中，中央 orchestrators 和[企業服務匯流排 (ESB)](https://en.wikipedia.org/wiki/Enterprise_service_bus) SOA 中一般。 但在大部分情況下，這些是微服務社群中的反向模式。 事實上，有些人認為 「 微服務架構是 SOA 正確完成。 」

本指南主要著重在 microservices，因為 SOA 方法是較不精準比需求和在微服務架構中使用的技術。 如果您知道如何建置微服務為基礎的應用程式，您也知道如何建置簡單的服務導向應用程式。




>[!div class="step-by-step"]
[上一個](docker-應用程式的狀態-data.md) [下一步] (microservices architecture.md)
