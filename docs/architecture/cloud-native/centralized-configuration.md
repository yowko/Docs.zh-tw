---
title: 集中式設定
description: 使用 Azure 應用程式組態和 AzureKey 保存庫集中設定雲端原生應用程式的設定。
ms.date: 05/13/2020
ms.openlocfilehash: d389d29dcdb1db5162d95370d181ab5a85d72dc8
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614223"
---
# <a name="centralized-configuration"></a>集中式設定

與在單一實例內執行所有專案的整合型應用程式不同，雲端原生應用程式是由分散在虛擬機器、容器和地理區域的獨立服務所組成。 管理數十個相互依存服務的設定，可能是一項挑戰。 不同位置間的重複設定複本會發生錯誤，而且很容易管理。 集中式設定是分散式雲端原生應用程式的關鍵需求。

如[第1章](introduction.md)所述，十二個要素的應用程式建議需要在程式碼與設定之間進行嚴格的分隔。 設定必須從應用程式外部儲存，並視需要進行讀取。 在程式碼中將設定值儲存為常數或常值，是一項違規。 相同的應用程式中的許多服務通常會使用相同的設定值。 此外，我們必須跨多個環境（例如開發、測試和生產）支援相同的值。 最佳做法是將它們儲存在集中式設定存放區中。

Azure 雲端提供幾個絕佳的選項。

## <a name="azure-app-configuration"></a>Azure 應用程式組態

[Azure 應用程式組態](https://docs.microsoft.com/azure/azure-app-configuration/overview)是完全受控的 Azure 服務，可將非秘密設定儲存在安全、集中的位置。 儲存的值可以在多個服務和應用程式之間共用。

此服務很容易使用，並提供數個優點：

- 彈性的索引鍵/值標記法和對應
- 使用 Azure 標籤標記
- 管理專用的 UI
- 機密資訊的加密
- 查詢和批次抓取

Azure 應用程式組態會維護7天對索引鍵/值設定所做的變更。 「時間點快照集」功能可讓您重建設定的歷程記錄，甚至是復原失敗的部署。

應用程式組態會自動快取每個設定，以避免過多的設定存放區呼叫。 重新整理作業會等到設定的快取值過期，才會更新該設定，即使其值在設定存放區中有所變更也一樣。 預設讀快取到期時間為 30 秒。 您可以覆寫到期時間。

應用程式組態會加密傳輸中和待用的所有設定值。 金鑰名稱和標籤會用來做為抓取設定資料的索引，而且不會加密。

雖然應用程式組態提供強化的安全性，但 Azure Key Vault 仍然是儲存應用程式秘密的最佳位置。 Key Vault 提供硬體層級加密、細微存取原則和管理作業（例如憑證輪替）。 您可以建立應用程式組態值來參考儲存在 Key Vault 中的秘密。

## <a name="azure-key-vault"></a>Azure 金鑰保存庫

Key Vault 是一種受控服務，可安全地儲存和存取秘密。 祕密是指任何需受到嚴密存取控制的項目，例如 API 金鑰、密碼或憑證。 保存庫是秘密的邏輯群組。

Key Vault 可大幅降低不小心洩露祕密的風險。 使用 Key Vault 時，應用程式開發人員不再需要在其應用程式中儲存安全性資訊。 這種做法不需要將此資訊儲存在您的程式碼中。 例如，應用程式可能需要連線到資料庫。 您可以在 Key Vault 中妥善儲存連接字串，而不用在應用程式程式碼中儲存連接字串。

您的應用程式可以使用 URI 安全地存取其所需的資訊。 這些 URI 可讓應用程式擷取特定版本的祕密。 不需要撰寫自訂程式碼來保護儲存在 Key Vault 中的任何秘密資訊。

存取 Key Vault 需要適當的呼叫端驗證和授權。 一般來說，每個雲端原生微服務都會使用 ClientId/ClientSecret 組合。 請務必將這些認證保留在原始檔控制之外。 最佳做法是在應用程式的環境中設定它們。 您可以使用[Key Vault FlexVolume](https://github.com/Azure/kubernetes-keyvault-flexvol)，直接存取 AKS 的 Key Vault。

## <a name="configuration-in-eshop"></a>EShop 中的設定

EShopOnContainers 應用程式包含每個微服務的本機應用程式佈建檔案。 這些檔案會簽入原始檔控制中，但不包含生產秘密，例如連接字串或 API 金鑰。 在生產環境中，個別的設定可能會以每個服務的環境變數來覆寫。 在環境變數中插入秘密是裝載應用程式的常見作法，但不提供中央設定存放區。 為了支援集中式的設定管理，每個微服務都包含一個設定，可在使用本機設定或 Azure Key Vault 設定之間切換。

## <a name="references"></a>參考

- [EShopOnContainers 架構](https://github.com/dotnet-architecture/eShopOnContainers/wiki/Architecture)
- [協調微服務和多容器應用程式的高延展性和可用性](https://docs.microsoft.com/dotnet/architecture/microservices/architect-microservice-container-applications/scalable-available-multi-container-microservice-applications)
- [Azure API 管理](https://docs.microsoft.com/azure/api-management/api-management-key-concepts)
- [Azure SQL Database 總覽](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview)
- [Azure Cache for Redis](https://azure.microsoft.com/services/cache/)
- [適用於 MongoDB 的 Azure Cosmos DB API](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction)
- [Azure 服務匯流排](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview)
- [Azure 監視器概觀](https://docs.microsoft.com/azure/azure-monitor/overview)
- [eShopOnContainers：在 AKS 中建立 Kubernetes 叢集](https://github.com/dotnet-architecture/eShopOnContainers/wiki/Deploy-to-Azure-Kubernetes-Service-(AKS)#create-kubernetes-cluster-in-aks)
- [eShopOnContainers： Azure Dev Spaces](https://github.com/dotnet-architecture/eShopOnContainers/wiki/Azure-Dev-Spaces)
- [Azure 開發人員空間](https://docs.microsoft.com/azure/dev-spaces/about)

>[!div class="step-by-step"]
>[上一個](deploy-eshoponcontainers-azure.md) 
>[下一步](scale-applications.md)
