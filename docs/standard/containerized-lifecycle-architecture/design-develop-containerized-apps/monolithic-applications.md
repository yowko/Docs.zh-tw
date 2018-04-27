---
title: 整合應用程式
description: Microsoft 平台和工具的容器化 Docker 應用程式生命週期
ms.prod: .net
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 1a9969930f5d57bdc66207b7c4a9d43ea43b56f7
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="monolithic-applications"></a>整合應用程式

在此案例中，您會建置單一且整合的 web 應用程式或服務和部署的容器。 在應用程式結構可能不是整合;它可能由數個程式庫、 元件或甚至是圖層 （應用程式層級、 網域層級、 資料存取層等等） 所組成。 在外部，它是單一的容器，例如單一處理程序、 單一 web 應用程式或單一服務。

為了管理此模型，您會部署單一容器來代表應用程式。 若要調整它，只要加入與負載平衡器在前面的一些多個複本。 管理單一容器或虛擬機器 (VM) 中的單一部署來自簡易性。

容器未一件事，而且沒有一個處理序中的主體，在整合模式處於衝突狀態。 圖 4-1 的說明，您可以包含多個元件/程式庫或每個容器，在內部層級。

![](./media/image1.png)

圖 4-1: 的範例應用程式整合架構

這種方法的缺點是如果或當應用程式成長時，需要調整。 若整個應用程式都擴充，則不成問題。 不過，在大部分情況下，應用程式的某些部分是淺壓深點需要調整，而較不使用其他元件的。

使用一般的電子商務範例，您可能需要什麼是調整的產品資訊的元件。 瀏覽產品的客戶比購買的人多。 比起使用付款管道，會有更多客戶使用其購物籃。 新增留言或檢視其購買歷程記錄的客戶較少。 而且，您可能需要在少數幾個員工，在單一區域中，需要管理內容和行銷活動。 藉由調整僵化設計，所有的程式碼是多次部署。

除了"小數位數的所有項目 」 問題，整個應用程式，以及完整的重新部署的所有執行個體的完整重新測試後必須變更單一元件。

是很常見，整合的方法，許多組織正在開發使用這個架構的方法。 許多享受良好足夠的結果，而其他人遇到的限制。 許多設計其應用程式在此模型，因為工具與基礎結構太難建置 SOAs，所以他們看不需要，直到應用程式成長。

從基礎結構的觀點而言，每一部伺服器執行相同的主控件中的許多應用程式與您的資源使用量中, 有一個可接受比效率的如圖 4-2 所示。

![](./media/image2.png)

圖 4-2： 執行多個應用程式/容器的主機

您可以使用專用的 Vm，每個執行個體部署在 Azure 中的整合應用程式。 使用[Azure VM 規模集](https://docs.microsoft.com/azure/virtual-machine-scale-sets/)，您可以輕鬆地調整 Vm。 [Azure App Service](https://azure.microsoft.com/en-us/services/app-service/) 可以執行整合型應用程式並輕鬆地調整執行個體，而不必管理 VM。 自 2016，Azure 應用程式服務可以執行單一執行個體的 Docker 容器，以及，簡化部署。 然後使用 Docker 時，您可以部署單一 VM 做為 Docker 主機並執行多個執行個體。 在圖 4-3 的說明，請使用 Azure 的平衡器，，您可以管理縮放比例。

![](./media/image3.png)

圖 4-3： 多部主機向外擴充具有單一 Docker 應用程式的應用程式/容器

您可以管理各種不同的主機，透過傳統部署技術的部署。 您可以使用類似的命令，以管理 Docker 主機`docker run`手動、 透過自動化，例如持續傳遞 (CD) 管線，我們說明稍後在本電子書。

## <a name="monolithic-application-deployed-as-a-container"></a>整合型應用程式部署為容器

有許多優點，若要使用容器來管理整合的部署。 調整容器執行個體遠比部署額外的 VM 更輕鬆快速。 VM 規模集是很棒的功能，來調整 Vm，裝載所需 Docker 容器，但是它們會花時間設定。 當部署為應用程式執行個體時，應用程式的設定是作為 VM 的一部分管理。

以 Docker 映像來部署更新會更快且網路效率更高。 Vn 執行個體可以設定相同主機上為您的 Vn 1 執行個體，因而不加入其他 Vm 所產生的成本。 Docker 映像一開始通常以秒為單位，加速首度發行。 破壞的 Docker 執行個體非常簡單，只要叫用`docker stop`命令，通常少於一秒內完成。

由於容器本身不變的根據設計，永遠不需要擔心損毀的 Vm，因為某些特定的組態或檔案保留在磁碟上忘記更新指令碼。

雖然整合的應用程式可受益於 Docker，我們要碰觸上好處的秘訣。 部署與管理不同的執行個體和每個容器執行個體的生命週期的容器 orchestrators 來自管理容器的較大的優勢。 將整合型應用程式分成可個別擴充、開發及部署的多個子系統，是您開始使用微服務的不錯起點。

## <a name="publishing-a-single-docker-container-app-to-azure-app-service"></a>單一的 Docker 容器應用程式發行到 Azure 應用程式服務

可能是因為您想要取得快速部署至 Azure 容器驗證或因為應用程式只是單一容器應用程式，Azure 應用程式服務會提供以提供可擴充的單一容器服務的好方法。

使用 Azure App Service 是直覺式可以啟動，且快速地執行，因為它提供絕佳的 Git 整合，以取得您的程式碼建置在 Microsoft Visual Studio 中，並直接將它部署至 Azure。 但是，傳統 （使用任何 Docker)，如果您需要其他的功能、 架構或不支援的應用程式服務的相依性需要等候直到 Azure 團隊更新 App Service 中的相依性或切換到其他服務，例如Service Fabric、 雲端服務或甚至一般的 Vm，您有進一步的控制和可以安裝必要的元件或架構應用程式。

現在，不過 （Microsoft Connect 2016 在 2016 年 11 月宣佈） 和使用 Visual Studio 2017 時，圖 4‑4 中所示，Azure App Service 中的容器支援可讓您以包含您要在應用程式環境中的任何。 如果因為您已經在容器中執行，您可以加入至您的應用程式的相依性，您會取得的功能包括 Dockerfile 或 Docker 映像中的這些相依性。

![](./media/image4.png)

圖 4-4： 從 Visual Studio 應用程式/容器將容器發行至 Azure App Service

圖 4-4 也會顯示發行流程將推送透過容器登錄中，它可以是 Azure 容器登錄中 （登錄接近您在 Azure 中的部署和保護 Azure Active Directory 群組和帳戶） 或任何其他 Docker 登錄映像像 Docker Hub 或內部部署的登錄。


>[!div class="step-by-step"]
[上一個] (常見的容器-設計-principles.md) [下一步] (state-and-data-in-docker-applications.md)
