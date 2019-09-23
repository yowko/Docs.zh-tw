---
title: 集中式設定
description: 使用 Azure Key Vault 的集中式設定可以讓您更輕鬆地管理雲端原生應用程式。
ms.date: 06/30/2019
ms.openlocfilehash: f4f495591550abccf2c64ef24cbe7620b039d8ca
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183515"
---
# <a name="centralized-configuration"></a>集中式設定

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

雲端原生應用程式牽涉到比傳統單一實例整合型應用程式更多的執行中服務。 管理數十個相互依存服務的設定，可能是一項挑戰，這也是為什麼集中式設定存放區通常會針對分散式應用程式執行的原因。

如[第1章](introduction.md)所述，十二個要素的應用程式建議需要在程式碼與設定之間進行嚴格的分隔。 這表示在程式碼中將設定的常數或常值儲存為違規。 這項建議存在的原因是，相同的程式碼應該在多個環境中使用，包括開發、測試、預備和生產。 不過，這兩個環境之間的設定值可能會有所不同。 因此，設定值應該儲存在環境本身，或環境應該將認證儲存至集中式設定存放區。

EShopOnContainers 應用程式包含每個微服務的本機應用程式佈建檔案。 這些檔案會簽入原始檔控制，但不包含生產秘密，例如連接字串或 API 金鑰。 在生產環境中，個別的設定可能會以每個服務的環境變數來覆寫。 這是託管應用程式的常見作法，但不提供中央設定存放區。 為了支援集中式的設定管理，每個微服務都包含一個設定，可在使用本機設定或 Azure Key Vault 設定之間切換。

## <a name="azure-key-vault"></a>Azure Key Vault

Azure Key Vault 提供權杖、密碼、憑證、API 金鑰和其他機密秘密的安全儲存體。 存取 Key Vault 需要適當的呼叫端驗證和授權，在 eShopOnContainers 微服務中，這表示使用 ClientId/ClientSecret 組合。 請不要將這些認證簽入原始檔控制，而是在應用程式的環境中設定。 您可以使用[Key Vault FlexVolume](https://github.com/Azure/kubernetes-keyvault-flexvol)，直接存取 AKS 的 Key Vault。

藉由集中式設定，套用至整個應用程式的設定（例如集中式記錄端點），可以一次，並供分散式應用程式的每個部分使用。 雖然微服務應該彼此獨立，但通常還是會有一些共用的相依性，其設定詳細資料可以從集中式設定存放區受益。

>[!div class="step-by-step"]
>[上一頁](deploy-eshoponcontainers-azure.md)
>[下一頁](scale-applications.md) <!-- Next Chapter -->
