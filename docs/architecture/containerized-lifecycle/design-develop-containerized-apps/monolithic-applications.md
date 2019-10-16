---
title: 整合型應用程式
description: 了解如何將整合型應用程式容器化的核心概念。
ms.date: 02/15/2019
ms.openlocfilehash: 1d4b54017e431bd9775bf2aee8c88f56e0489367
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394687"
---
# <a name="monolithic-applications"></a>整合型應用程式

在本案例中，您會建置單一且整合型的 Web 應用程式或服務，並將它部署為容器。 從應用程式內部來看，其結構可能不是整合型，而是由數個程式庫、元件，甚至層級 (應用程式層、網域層、資料存取層等) 所組成。 從外部來看，它是單一容器，像是單一處理序、單一 Web 應用程式或單一服務。

為了管理此模型，您會部署單一容器來代表應用程式。 若要進行擴充，只要透過前端負載平衡器多新增幾個複本即可。 由於您可以在單一容器或虛擬機器 (VM) 中管理單一部署，因此相對簡單。

當您遵循「容器僅執行一項動作並在一個處理序中執行該動作」的原則時，整合型模式可能會產生衝突。 您可以在每個容器中包含多個元件/程式庫或內部層級，如圖 4-1 所示。

![此圖顯示透過複製應用程式相應放大的整合型應用程式。](./media/monolithic-applications/monolithic-application-architecture-example.png)

**圖 4-1.** 整合型應用程式的架構範例

整合型應用程式的單一處理序或容器內即具有其全部或大部分功能，且在內部層或程式庫中經元件化處理。 如果應用程式因成長而需要擴充，則此方法的缺點便會浮現。 若整個應用程式都擴充，則不成問題。 不過，在大多數情況下，應用程式只需要擴充幾個造成阻礙的部分，其他元件則較少使用。

若是一般的電子商務範例，您可能需要調整的是產品資訊元件。 瀏覽產品的客戶比購買的人多。 比起使用付款管道，會有更多客戶使用其購物籃。 新增留言或檢視其購買歷程記錄的客戶較少。 而且在單一區域中，您可能只有少數幾個員工來管理內容和行銷活動。 藉由擴充整合型設計，即可多次部署所有程式碼。

除了「全部調整」的問題之外，當您變更單一元件時，必須徹底重新測試整個應用程式，並重新部署所有執行個體。

整合型方法很常見，許多組織也開始使用這個架構方法進行開發。 其中有許多組織獲得良好的結果，但其他組織卻遭遇到限制。 由於工具和基礎結構太難建置 SOA，因此許多組織按照此模型來設計應用程式，但是在應用程式成長之後需求才會顯現出來。

從基礎結構的觀點來看，每部伺服器都可以在相同主機內執行許多應用程式，並具備可接受的資源使用效率比，如圖 4-2 所示。

![圖表，顯示在不同的容器中有多個應用程式的主控制項。](./media/monolithic-applications/host-with-multiple-apps-containers.png)

**圖 4-2.** 執行多個應用程式/容器的主機

最後，從可用性的觀點來看，整合型應用程式必須以整體方式部署；這表示萬一您必須「停止和啟動」時，會影響部署期間的所有功能和所有使用者。 在某些情況下，使用 Azure 和容器可以盡量避免這些情況，並降低應用程式停機的可能性，如圖 4-3 所示。

您可以針對每個執行個體使用專用 VM，在 Azure 中部署整合型應用程式。 您可以使用 [Azure VM 擴展集](https://docs.microsoft.com/azure/virtual-machine-scale-sets/)來調整 VM。

您也可以使用 [Azure App Service](https://azure.microsoft.com/services/app-service/) 來執行整合型應用程式並輕鬆調整執行個體，而不必管理 VM。 Azure App Service 也可以執行 Docker 容器的單一執行個體，以簡化部署。

您可以將多個 VM 部署為 Docker 主機，並在每個 VM 執行任意數目的容器。 然後，您可以使用 Azure Load Balancer 來管理調整，如圖 4-3 所示。

![圖表，顯示相應放大至不同主機的整合型應用程式。](./media/monolithic-applications/multiple-hosts-from-single-docker-container.png)

**圖 4-3**： 多部主機相應放大單一 Docker 應用程式

您可以透過傳統部署技術來管理主機本身的部署。

您可以使用 `docker run` 和 `docker-compose up` 等命令，從命令列管理 Docker 容器；您也可以在持續傳遞 (CD) 管線中將其自動化，並從 Azure DevOps Services 部署到 Docker 主機。

## <a name="monolithic-application-deployed-as-a-container"></a>整合型應用程式部署為容器

使用容器來管理整合型部署有許多優點。 調整容器執行個體遠比部署額外的 VM 更輕鬆快速。

以 Docker 映像來部署更新會更快且網路效率更高。 Docker 容器通常只要幾秒鐘就能啟動，因此可加速推出。 您只要叫用 `docker stop` 命令即可輕鬆卸除 Docker 容器，且通常不到一秒就會完成。

容器的設計原本即為固定，因此您永遠不需要擔心會因為更新指令碼忘記處理部分特定設定或是檔案殘留在磁碟上而導致 VM 損毀。

雖然整合型應用程式可以從 Docker 獲益，但這只是一小部分優點。 管理容器的主要優點來自於使用容器協調器進行部署，透過此方式來管理各種執行個體和每個容器執行個體的生命週期。 將整合型應用程式分成可個別擴充、開發及部署的多個子系統，是您開始使用微服務的不錯起點。

若要深入了解如何「隨即轉移」整合型應用程式與容器，以及如何將應用程式現代化，您可以另外參閱[使用 Azure 雲端及 Windows 容器將現有 .NET 應用程式轉換成現代化的應用程式](../../modernize-with-azure-containers/index.md)此 Microsoft 指南，您也可以從 <https://aka.ms/LiftAndShiftWithContainersEbook> 下載 PDF。

## <a name="publish-a-single-docker-container-app-to-azure-app-service"></a>將單一 Docker 容器應用程式發佈至 Azure App Service

不論您是為了想要快速取得部署至 Azure 的容器驗證，還是基於應用程式只是單一容器應用程式等原因，Azure App Service 都有絕佳方法來提供可擴充的單一容器服務。

Azure App Service 提供與 Git 的絕佳整合，讓您可以輕鬆地取得程式碼、在 Microsoft Visual Studio 中建置，並將它直接部署至 Azure，其使用方式為直覺式，因此您可以快速啟動並執行。 但是，以傳統方式來說 (不含任何 Docker)，如果您需要 Azure App Service 不支援的其他功能、架構或相依性，您必須等 Azure 小組更新 Azure App Service 中的這些相依性或切換到其他服務 (例如 Service Fabric、雲端服務，甚至單純的 VM)，才能進一步控制並為應用程式安裝必要的元件或架構。

現在，當您使用 Visual Studio 2017 時，Azure App Service 的容器支援可讓您在應用程式環境中包含所想要任何項目，如圖 4-4 所示。 如果您已將相依性新增至應用程式，並在容器中加以執行，即可在 Dockerfile 或 Docker 映像中包括這些相依性。

![顯示容器登錄的 [建立 App Service] 對話方塊的螢幕擷取畫面。](./media/monolithic-applications/publish-azure-app-service-container.png)

**圖 4-4**： 將容器從 Visual Studio 應用程式/容器發佈至 Azure App Service

如圖 4-4 所示，發佈流程會透過容器登錄推送映像，而這可能是 Azure Container Registry (接近您 Azure 部署並受到 Azure Active Directory 群組和帳戶保護的登錄)，或任何其他 Docker 登錄，例如 Docker Hub 或內部部署登錄。

>[!div class="step-by-step"]
>[上一頁](common-container-design-principles.md)
>[下一頁](state-and-data-in-docker-applications.md)
