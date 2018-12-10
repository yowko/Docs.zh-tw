---
title: 容器和 Docker 簡介
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 容器和 Docker 簡介
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 08/31/2018
ms.openlocfilehash: cf86640456af03d4c44f537fe1ff3282521f2200
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53147935"
---
# <a name="introduction-to-containers-and-docker"></a>容器和 Docker 簡介

容器化是一種軟體開發方法，在此方法中，應用程式或服務、其相依性及其組態 (抽象化為部署資訊清單檔) 會封裝在一起，成為一個容器映像。 容器化應用程式可以當作一個單位來測試，並以容器映像執行個體形式部署至主機作業系統 (OS)。

就像是貨櫃允許利用船隻、火車或貨車運輸貨物，而不論內含哪種貨物，軟體容器是軟體部署的標準單位，可包含不同的程式碼和相依性。 以此方式容器化軟體可讓開發人員和 IT 專業人員只需要一點修改或不需要任何修改，就能跨環境進行部署。

容器也可讓不同的應用程式在共用 OS 上彼此隔離。 容器化應用程式會在容器主機上執行，再於 OS (Linux 或 Windows) 上執行。 因此，容器所需空間明顯小於虛擬機器 (VM) 映像。

每個容器可以執行整個 Web 應用程式或服務，如圖 2-1 所示。 在此範例中，Docker 主機是容器主機，而 App1、App2、Svc 1 和 Svc 2 是容器化應用程式或服務。

![在 VM 或實體伺服器的作業系統上執行的兩個應用程式和兩個服務](./media/image1.png)

**圖 2-1**. 在容器主機上執行的多個容器

容器化的另一個優點是延展性。 您可以針對短期工作建立新的容器，以更快擴充。 從應用程式的觀點來看，具現化映像 (建立容器) 類似於具現化處理序 (例如服務或 Web 應用程式)。 不過，為了可靠起見，當您在多部主機伺服器之間執行相同映像的多個執行個體時，您通常需要在不同的主機伺服器或 VM 中，或是不同的容錯網域中，執行各個容器 (映像執行個體)。

簡單來說，容器在整個應用程式生命週期工作流程中，提供隔離、可攜性、彈性、延展性和控制能力等優點。 最重要的優點是可為開發與作業提供環境的隔離。

>[!div class="step-by-step"]
>[上一頁](../index.md)
>[下一頁](docker-defined.md)