---
title: 服務導向架構
description: 了解微服務和服務導向架構 (SOA) 的基本差異。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/20/2018
ms.openlocfilehash: d19053d8296dbe75ac1e0ce037d6a713d9f5687c
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53148609"
---
# <a name="service-oriented-architecture"></a>服務導向架構

服務導向架構 (SOA) 是過度使用的詞彙，而且對不同的人有不同的意義。 但作為共同點，SOA 表示您透過將應用程式分解為多個服務 (通常是 HTTP 服務) 來建構應用程式，而服務可以分類為不同的型別 (例如子系統或層級)。

這些服務現在可以部署為 Docker 容器以解決部署問題，因為容器映像包含所有相依性。 不過，當您需要相應增加 SOA 應用程式時，如果以單一 Docker 主機為基礎部署，可能會有延展性和可用性挑戰。 Docker 叢集軟體或協調器可在這方面幫助您，後續各節所述之微服務部署方法會加以說明。

Docker 容器十分適用 (但不是必要) 於傳統服務導向架構和更進階的微服務架構。

微服務衍生自 SOA，但 SOA 與微服務架構不同。 SOA 一般會提供大型的中央訊息代理程式、組織層級的中央協調器和[企業服務匯流排 (ESB)](https://en.wikipedia.org/wiki/Enterprise_service_bus) 這類功能。 但在大部分情況下，這些是微服務社群中的反向模式。 事實上，有些人認為「微服務架構就是 SOA。」

本指南著重在微服務，因為 SOA 方法與微服務架構中所使用的需求和技術相較之下較不精準。 如果您知道如何建置微服務應用程式，則也會知道如何建置較簡單的服務導向應用程式。

>[!div class="step-by-step"]
>[上一頁](docker-application-state-data.md)
>[下一頁](microservices-architecture.md)