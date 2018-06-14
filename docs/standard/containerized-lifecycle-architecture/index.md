---
title: 容器和 Docker 簡介
description: Microsoft 平台和工具的容器化 Docker 應用程式生命週期
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 8d1062aaea85cf810fa07b36252974eceb227c43
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32768277"
---
# <a name="introduction-to-containers-and-docker"></a>容器和 Docker 簡介

容器化是一種軟體開發方法，在此方法中，應用程式或服務、其相依性及其組態 (抽象化為部署資訊清單檔) 會封裝在一起，成為一個容器映像。 您可以將容器化應用程式當作一個單位來測試，並將它以容器映像執行個體形式部署至主機作業系統。

就像運輸業使用標準化貨櫃以透過船隻、火車或貨車移動貨物，而不論其內的貨物，軟體容器都是標準軟體單位，可包含不同的程式碼和相依性。 將軟體放置到容器可讓開發人員和 IT 專業人員只需要一點修改或不需要任何修改，就能跨環境部署這些容器。

容器也可讓不同的應用程式在共用作業系統 (OS) 上彼此隔離。 容器化應用程式會在容器主機上執行，再於 OS (Linux 或 Windows) 上執行。 因此，容器所需空間明顯小於虛擬機器 (VM) 映像。

每個容器都可以執行整個 Web 應用程式或服務，如圖 1-1 所示。

![](./media/image1.png)

圖 1-1：在容器主機上執行的多個容器

在此範例中，Docker 主機是容器主機，而 App 1、App 2、Svc 1 和 Svc 2 是容器化應用程式或服務。

您可以從容器化衍生的另一個優點是延展性。 針對短期工作建立新的容器，即可更快速地擴充。 從應用程式的觀點來看，「具現化映像」(建立容器) 類似於具現化處理序 (例如服務或 Web 應用程式)。 不過，為了可靠起見，當您在多部主機伺服器之間執行相同映像的多個執行個體時，您通常需要在不同的主機伺服器或 VM 中，或是不同的容錯網域中，執行各個容器 (映像執行個體)。

簡單來說，容器在整個應用程式生命週期工作流程中，提供隔離、可攜性、彈性、延展性和控制能力等優點。 最重要的優點是為開發與作業提供隔離。


>[!div class="step-by-step"]
[下一個] (what-is-docker.md)
