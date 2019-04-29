---
title: 容器和 Docker 簡介
description: 取得使用 Docker 的主要優點的高層級概觀。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: aa3ead1cb184e23dd091822368e62f580ed73ee5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785618"
---
# <a name="introduction-to-containers-and-docker"></a>容器和 Docker 簡介

*容器化是在其中應用程式或服務、 其相依性和及其組態 （抽象化為部署資訊清單檔案） 會封裝在一起成為容器映像的軟體開發方法。然後可以測試當做一個單位的容器化應用程式並將它部署為主機作業系統 (OS) 的容器映像執行個體。*

就像是貨櫃允許利用船隻、火車或貨車運輸貨物，而不論內含哪種貨物，軟體容器是軟體部署的標準單位，可包含不同的程式碼和相依性。 以此方式容器化軟體可讓開發人員和 IT 專業人員只需要一點修改或不需要任何修改，就能跨環境進行部署。

容器也可讓不同的應用程式在共用 OS 上彼此隔離。 容器化應用程式會在容器主機上執行，再於 OS (Linux 或 Windows) 上執行。 因此，容器所小使用量虛擬機器 (VM) 映像。

每個容器可以執行整個 web 應用程式或服務，如所示的圖 1-1。 在此範例中，Docker 主機是容器主機，而 App1、 App2、 Svc1 和 Svc2 是容器化應用程式或服務。

![在 VM 或實體伺服器的作業系統上執行的兩個應用程式和兩個服務](./media/image1.png)

**圖 1-1**。 在容器主機上執行的多個容器

您可以從容器化衍生的另一個優點是延展性。 您可以針對短期工作建立新的容器，以更快擴充。 從應用程式的觀點來看，具現化映像 (建立容器) 類似於具現化處理序 (例如服務或 Web 應用程式)。 不過，為了可靠起見，當您在多部主機伺服器之間執行相同映像的多個執行個體時，您通常需要在不同的主機伺服器或 VM 中，或是不同的容錯網域中，執行各個容器 (映像執行個體)。

簡單來說，容器會提供隔離、 可攜性、 靈活性、 延展性和控制的優點，在整個應用程式生命週期工作流程。 最重要的優點是開發與營運部門提供環境隔離。

>[!div class="step-by-step"]
>[下一步](what-is-docker.md)
