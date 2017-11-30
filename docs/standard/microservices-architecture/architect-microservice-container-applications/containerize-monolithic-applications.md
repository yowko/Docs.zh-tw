---
title: "Containerizing 整合的應用程式"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |Containerizing 整合的應用程式"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 11e2c24403b9b61584e424696c844e00e5d34b03
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="containerizing-monolithic-applications"></a>Containerizing 整合的應用程式

您可以建立單一、 monolithically 已部署 web 應用程式或服務，並將它部署為容器。 應用程式本身可能不會在內部龐大，但結構化以多個程式庫、 元件或甚至是圖層 （應用程式層級、 網域層級、 資料存取層等等）。 不過，外部，它會是在單一容器 — 在單一處理序中，單一的 web 應用程式或單一服務。

若要管理此模型，您可以部署單一容器來表示應用程式。 若要向上延展，只要加入前方負載平衡器與多個複本。 管理單一容器或 VM 中的單一部署來自簡易性。

![](./media/image1.png)

**圖 4-1**。 容器化的整合應用程式架構的範例

您可以包含多個元件、 程式庫或內部層中每個容器，在圖 4-1 中所述。 不過，此整合模式可能會與"容器沒有一件事，和一個處理序中運作"，但可能容器原則衝突會在某些情況下 [確定]。

這種方法的缺點變得顯而易見，如果應用程式成長，需要調整。 如果可以調整整個應用程式，它並非真正的問題。 不過，在大部分情況下，應用程式只需要幾個部分都需要調整其他元件時使用小於淺壓深點。

例如，在典型的電子商務應用程式中，您可能需要調整產品資訊子系統中，因為比購買更多其他客戶瀏覽產品。 更多的客戶使用及其購物籃，比使用付款管線。 較少的客戶加入註解或檢視其採購歷程記錄。 因此，您可能必須少數幾個需要管理內容與行銷活動的員工。 如果您調整規模龐大的設計，請針對這些不同工作的所有程式碼是多次部署和縮放比例為相同的等級。

有多種方式可以調整應用程式 — 分割不同的應用程式和資料分割類似的商務概念或資料區域的水平重複。 但是，除了縮放所有元件的問題，變更單一元件需要完整測試整個應用程式，以及完整的重新部署的所有執行個體。

但是，整合的方法是不常見，因為應用程式開發一開始更為 microservices 方法。 因此，許多組織開發使用這個架構的方法。 某些組織有良好足夠的結果，而其他人到達限制。 許多組織設計其應用程式，因為工具與基礎結構並不容易太建置服務導向架構 (SOA) 年前，及它們不會看到需要使用此模型，直到應用程式成長。

從基礎結構的觀點而言，每一部伺服器可以執行相同的主控件中的許多應用程式，並有一個可接受比效率的資源使用量，如圖 4-2 所示。

![](./media/image2.png)

**圖 4-2**。 整合的方法： 裝載執行多個應用程式，做為容器執行每個應用程式

Microsoft Azure 中的整合應用程式可以使用每個執行個體的專用的 Vm 部署。 此外，使用[Azure VM 規模集](https://docs.microsoft.com/azure/virtual-machine-scale-sets/)，您可以輕鬆地調整 Vm。 [Azure App Service](https://azure.microsoft.com/services/app-service/)可以也執行整合的應用程式並輕鬆擴充執行個體，而不需要您管理的 Vm。 自 2016，Azure 應用程式服務可以執行單一執行個體，Docker 容器簡化部署。

QA 環境或有限的生產環境，您可以部署多個 Docker 主機 Vm 並平衡它們使用 Azure 的平衡器，如下圖 4-3。 這可讓您管理調整以粗略的方法，因為整個應用程式都位於單一容器內。

![](./media/image3.png)

**圖 4-3**。 向上擴充單一容器應用程式的多部主機的範例

部署到不同主機都可以使用傳統部署技術來管理。 使用類似的命令可以管理 docker 主機`docker run`或`docker-compose`執行手動方式或透過自動化，例如持續傳遞 (CD) 管線。

## <a name="deploying-a-monolithic-application-as-a-container"></a>部署整合的應用程式，做為容器

有許多優點，若要使用容器來管理整合的應用程式部署。 調整容器執行個體是遠比快速而且容易部署額外的 Vm。 即使您使用 VM 規模集時，Vm 會需要啟動的時間。 當部署為傳統的應用程式執行個體，而不是容器，應用程式的組態管理一部分 VM，這並不理想。

部署更新的 Docker 映像的速度遠和有效率的網路。 Docker 映像一開始通常以秒為單位，這會加速首度發行。 破壞的 Docker 映像執行個體非常簡單，只要發出`docker stop`命令，然後通常少於一秒內完成。

容器是不變，根據設計，因為您永遠不需要擔心損毀的 Vm。 相反地，VM 的更新指令碼可能會忘記某些特定的設定或磁碟上剩餘的檔案。

整合的應用程式可以從 Docker 獲益，雖然我們接觸只在優點。 管理容器的其他優點來自部署容器 orchestrators，管理不同的執行個體和每個容器執行個體的生命週期。 整合應用程式子系統，可調整、 開發，而且個別部署成重大是 microservices 的領域您進入點。

## <a name="publishing-a-single-container-based-application-to-azure-app-service"></a>單一容器基礎應用程式發行至 Azure App Service

您是否想要取得的容器，部署至 Azure 的驗證，或只是單一容器應用程式的應用程式時，Azure 應用程式服務會提供以提供單一容器基礎的可延展服務的好方法。 使用 Azure App Service 很簡單。 它提供絕佳的整合，使用 Git，讓您輕鬆取得您的程式碼、 建置在 Visual Studio 中，並將它部署直接部署至 Azure。

![](./media/image4.png)

**圖 4-4**。 單一容器應用程式發行至 Azure 應用程式服務從 Visual Studio

Docker，沒有如果您需要其他的功能、 架構或相依性，不支援在 Azure 應用程式服務中，您必須等到 Azure 團隊更新 App Service 中的相依性。 或者，您必須切換到其他服務，例如 Azure Service Fabric、 Azure 雲端服務或甚至 Vm，其中，您必須進一步控制，您無法安裝必要的元件或架構應用程式。

在 Visual Studio 2017 容器支援可讓您包含任何您想要在應用程式環境中，如圖 4-4 所示。 因為您已經執行在容器中，如果您將相依性加入至您的應用程式，您可以在 Dockerfile 或 Docker 映像中包含相依性。

也所示圖 4-4，發行流程推送透過容器登錄中的映像。 這可以是 Azure 容器登錄中 （登錄關閉您在 Azure 中的部署和保護 Azure Active Directory 群組和帳戶） 或任何其他 Docker 登錄，像是 Docker Hub 或內部登錄。


>[!div class="step-by-step"]
[上一個](index.md) [下一步] (docker-應用程式的狀態-data.md)
