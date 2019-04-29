---
title: 整合型應用程式
description: 了解容器化整合型應用程式的核心概念。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: e7454100b09f602e1e103c38685609e1dab62fe9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61644941"
---
# <a name="monolithic-applications"></a>整合型應用程式

在此案例中，您要建置單一的整合型 web 應用程式或服務，並將它部署為容器。 在應用程式中，結構可能不是單體式;它可能包含數個程式庫、 元件或甚至是階層 （應用程式層、 領域層、 資料存取層等等）。 在外部，它是單一容器，像是單一處理序、 單一 web 應用程式或單一服務。

為了管理此模型，您會部署單一容器來代表應用程式。 調整其規模，只新增幾個使用負載平衡器前端的多個複本。 管理單一部署中的單一容器或虛擬機器 (VM) 很簡單。

之後，容器會執行一個動作，並在其中一個處理序的主體，整合型模式處於衝突狀態。 您可以包含多個元件/程式庫或內部層級中每個容器，如所示的 圖 4-1。

![單體式應用程式有其功能在單一處理序或容器內的全部或大部分，它元件化的內部層或程式庫中。](./media/image1.png)

**圖 4-1.** 整合型應用程式架構的範例

這種方法的缺點是，如果或應用程式成長而需要擴充。 若整個應用程式都擴充，則不成問題。 不過，在大部分情況下，應用程式的一些組件會阻礙，需要調整，而不使用其他元件。

使用一般的電子商務範例時，您可能需要的功能是擴充產品資訊元件。 瀏覽產品的客戶比購買的人多。 比起使用付款管道，會有更多客戶使用其購物籃。 新增留言或檢視其購買歷程記錄的客戶較少。 而且您可能擁有只有少數幾個員工，在單一區域中，需要管理內容和行銷活動。 藉由調整整合型設計，所有的程式碼會多次部署。

除了 「 小數位數-所有項目 」 問題，單一元件的變更需要完整重新測試整個應用程式，以及完整的重新部署的所有執行個體。

整合型方法很常見，和許多組織正在開發使用此架構的方法。 許多享有良好足夠的結果，而其他人遇到的限制。 許多設計其應用程式在此模型中的工具和基礎結構很難建置完成 Soa，因此他們也看需要-直到應用程式成長。

基礎結構的觀點而言，每一部伺服器可以執行相同的主控件中的許多應用程式，並在您的資源使用量，有的效率可接受的比例，如所示 圖 4-2。

![單一主機可以在不同的容器中執行多個應用程式。](./media/image2.png)

**圖 4-2.** 執行多個應用程式/容器的主機

最後，從可用性的觀點而言，整合型應用程式必須部署整個;這表示如果您必須*停止和啟動*，在部署期間，則會影響所有的功能和所有使用者。 在某些情況下，使用 Azure 和容器可以最小化這些情況下，並降低您的應用程式的停機的可能性，如您所見 圖 4-3。

您可以針對每個執行個體使用專用的 Vm 部署在 Azure 中的整合型應用程式。 使用[Azure VM 擴展集](https://docs.microsoft.com/azure/virtual-machine-scale-sets/)，您可以輕鬆地調整 Vm。

您也可以使用[Azure App Service](https://azure.microsoft.com/services/app-service/)執行整合型應用程式，並輕鬆地調整執行個體，而不需要管理 Vm。 Azure App Service 可以執行 Docker 容器，以及，單一執行的個體，以簡化部署。

您可以部署為 Docker 主機的多個 Vm，並執行任意數目的每個 VM 的容器。 然後，藉由使用 Azure Load Balancer，如所示在圖 4-3，您可以管理調整。

![單體式應用程式可以向外延展到不同的主機，其中每個時，會在容器中執行應用程式。](./media/image3.png)

**圖 4-3**： 多部主機向外擴充單一 Docker 應用程式的應用程式/容器

您可以管理主機本身透過傳統部署技術的部署。

您也可以使用類似的命令從命令列管理 Docker 容器`docker run`和`docker-compose up`，而且您可以將其自動化持續傳遞 (CD) 管線中，並將部署到 Docker 主機 Azure DevOps 服務，從執行個體。

## <a name="monolithic-application-deployed-as-a-container"></a>整合型應用程式部署為容器

有許多使用容器來管理整合型部署的優點。 調整容器執行個體遠比部署額外的 VM 更輕鬆快速。

以 Docker 映像來部署更新會更快且網路效率更高。 以秒為單位，因此可加速推出通常啟動 docker 容器。 卸除 Docker 容器很簡單，只要叫用`docker stop`命令，通常少於一秒內完成。

因為容器是原本就是不可變的根據設計，您永遠不必擔心 Vm 損毀，因為更新指令碼忘記處理部分特定設定或是磁碟上剩餘的檔案。

雖然整合型應用程式可以從 Docker 獲益，我們要碰觸的優點的祕訣上。 部署與管理各種不同的執行個體和每個容器執行個體的生命週期的容器 orchestrator 來自管理容器的較大的優勢。 將整合型應用程式分成可個別擴充、開發及部署的多個子系統，是您開始使用微服務的不錯起點。

若要深入了解如何使用容器的 「 隨即轉移 」 整合型應用程式，以及如何將現代化您的應用程式，您可以讀取此其他的 Microsoft 指南，[現代化現有的.NET 應用程式與 Azure 雲端和 Windows 容器](../../modernize-with-azure-and-containers/index.md)，，您也可以下載為 PDF 從<https://aka.ms/LiftAndShiftWithContainersEbook>。

## <a name="publish-a-single-docker-container-app-to-azure-app-service"></a>將單一 Docker 容器應用程式發佈至 Azure App Service

可能是因為您想要取得的容器部署至 Azure 的快速驗證或因為應用程式只是單一容器應用程式，Azure App Service 提供適合用來提供可調整的單一容器服務。

使用 Azure App Service 是直覺式，您可以啟動並快速執行，因為它提供絕佳的 Git 整合，以取得程式碼，建置在 Microsoft Visual Studio 中，並直接將它部署至 Azure。 但傳統上 （使用任何 Docker)，視其他的功能、 架構或相依性，不支援的應用程式服務，您需要等待直到 Azure 團隊更新 App Service 中的這些相依性或切換到其他服務，例如Service Fabric、 雲端服務或甚至純文字的 Vm，您還有其他控制項和可以為您的應用程式安裝的必要的元件或架構。

現在，當顯示在 圖 4-4，當使用 Visual Studio 2017 時，Azure App Service 中的容器支援可讓您以包含您想在您的應用程式環境中的任何內容。 如果因為您在容器中執行，您可以新增至您的應用程式的相依性，您會取得您的 Dockerfile 或 Docker 映像中包括這些相依性的功能。

![Visual Studio 精靈發行至 Azure app service 中，反白顯示容器登錄的選取器的檢視。](./media/image4.png)

**圖 4-4**： 發佈至 Azure App Service 的容器，從 Visual Studio 應用程式/容器

圖 4-4 也會顯示發行流程將透過容器登錄庫，它可以是 Azure Container Registry （登錄接近您在 Azure 中的部署和受保護的 Azure Active Directory 群組和帳戶） 或任何其他的 Docker 登錄的映像推送像是 Docker Hub 或內部部署的登錄。

>[!div class="step-by-step"]
>[上一頁](common-container-design-principles.md)
>[下一頁](state-and-data-in-docker-applications.md)
