---
title: 集中式設定
description: 使用 Azure 應用程式組態與 AzureKey 保存庫集中設定雲端原生應用程式。
ms.date: 05/13/2020
ms.openlocfilehash: 0d40c5b2d70f30beb17489dfd55900f7c5fc1a75
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91160875"
---
# <a name="centralized-configuration"></a>集中式設定

不同于在單一實例中執行所有專案的整合型應用程式，雲端原生應用程式是由分散在虛擬機器、容器和地理區域的獨立服務所組成。 管理數十個互相依存服務的設定，可能是一項挑戰。 跨不同位置的設定複本複本重複，是容易發生錯誤且難以管理。 集中式設定是分散式雲端原生應用程式的重要需求。

如 [第1章](introduction.md)所述，十二要素應用程式建議需要在程式碼與設定之間進行嚴格的分隔。 設定必須從應用程式外部儲存，並視需要進行讀取。 在程式碼中將設定值儲存為常數或常值是一項違規。 相同的設定值通常會由相同應用程式中的許多服務使用。 此外，我們必須跨多個環境（例如開發、測試和生產環境）支援相同的值。 最佳做法是將它們儲存在集中式設定存放區。

Azure 雲端提供數個絕佳的選項。

## <a name="azure-app-configuration"></a>Azure 應用程式組態

[Azure 應用程式組態](/azure/azure-app-configuration/overview) 是完全受控的 Azure 服務，可將非秘密設定設定儲存在安全且集中的位置。 您可以在多個服務和應用程式之間共用儲存的值。

這項服務很容易使用，並提供幾項優點：

- 彈性的索引鍵/值標記法和對應
- 使用 Azure 標籤標記
- 用於管理的專用 UI
- 機密資訊的加密
- 查詢和批次抓取

Azure 應用程式組態會保留七天對機碼值設定所做的變更。 時間點快照集功能可讓您重建設定的歷程記錄，甚至是復原失敗的部署。

應用程式設定會自動快取每個設定，以避免對設定存放區進行過多的呼叫。 重新整理作業會等到設定的快取值過期，才會更新該設定，即使其值在設定存放區中有所變更也一樣。 預設讀快取到期時間為 30 秒。 您可以覆寫到期時間。

應用程式設定會加密傳輸中和待用的所有設定值。 索引鍵名稱和標籤是用來作為抓取設定資料的索引，且不會加密。

雖然應用程式設定提供強化的安全性，但 Azure Key Vault 仍是儲存應用程式秘密的最佳位置。 Key Vault 提供硬體層級的加密、細微的存取原則，以及像是憑證輪替的管理作業。 您可以建立參考儲存在 Key Vault 中之秘密的應用程式設定值。

## <a name="azure-key-vault"></a>Azure 金鑰保存庫

Key Vault 是可安全儲存及存取秘密的受控服務。 祕密是指任何需受到嚴密存取控制的項目，例如 API 金鑰、密碼或憑證。 保存庫是秘密的邏輯群組。

Key Vault 可大幅降低不小心洩露祕密的風險。 使用 Key Vault 時，應用程式開發人員不再需要在其應用程式中儲存安全性資訊。 這種做法不需要將此資訊儲存在您的程式碼內。 例如，應用程式可能需要連線到資料庫。 您可以在 Key Vault 中妥善儲存連接字串，而不用在應用程式程式碼中儲存連接字串。

您的應用程式可以使用 URI 安全地存取其所需的資訊。 這些 URI 可讓應用程式擷取特定版本的祕密。 不需要撰寫自訂程式碼來保護 Key Vault 中儲存的任何秘密資訊。

存取 Key Vault 需要適當的呼叫端驗證和授權。 一般來說，每個雲端原生微服務都會使用 ClientId/ClientSecret 組合。 請務必將這些認證保留在原始檔控制之外。 最佳做法是在應用程式的環境中設定這些專案。 您可以使用 [Key Vault FlexVolume](https://github.com/Azure/kubernetes-keyvault-flexvol)，直接存取 AKS 的 Key Vault。

## <a name="configuration-in-eshop"></a>EShop 中的設定

EShopOnContainers 應用程式包含每個微服務的本機應用程式佈建檔。 這些檔案會簽入原始檔控制中，但不包含實際執行的秘密，例如連接字串或 API 金鑰。 在生產環境中，每個服務環境變數可能會覆寫個別設定。 在環境變數中插入秘密是託管應用程式的常見作法，但不提供中央設定存放區。 為了支援集中管理設定，每個微服務都包含一個設定，可在本機設定或 Azure Key Vault 設定之間切換。

## <a name="references"></a>參考資料

- [EShopOnContainers 架構](https://github.com/dotnet-architecture/eShopOnContainers/wiki/Architecture)
- [協調微服務和多容器應用程式的高延展性和可用性](../microservices/architect-microservice-container-applications/scalable-available-multi-container-microservice-applications.md)
- [Azure API 管理](/azure/api-management/api-management-key-concepts)
- [Azure SQL Database 總覽](/azure/sql-database/sql-database-technical-overview)
- [Azure Cache for Redis](https://azure.microsoft.com/services/cache/)
- [適用於 MongoDB 的 Azure Cosmos DB API](/azure/cosmos-db/mongodb-introduction)
- [Azure 服務匯流排](/azure/service-bus-messaging/service-bus-messaging-overview)
- [Azure 監視器概觀](/azure/azure-monitor/overview) \(部分機器翻譯\)
- [eShopOnContainers：在 AKS 中建立 Kubernetes 叢集](https://github.com/dotnet-architecture/eShopOnContainers/wiki/Deploy-to-Azure-Kubernetes-Service-(AKS)#create-kubernetes-cluster-in-aks)
- [eShopOnContainers： Azure Dev Spaces](https://github.com/dotnet-architecture/eShopOnContainers/wiki/Azure-Dev-Spaces)
- [Azure 開發人員空間](/azure/dev-spaces/about)

>[!div class="step-by-step"]
>[上一個](deploy-eshoponcontainers-azure.md) 
>[下一步](scale-applications.md)
