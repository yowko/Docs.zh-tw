---
title: 利用無伺服器函式
description: 利用雲端原生應用程式中的無伺服器和 Azure Functions
ms.date: 06/30/2019
ms.openlocfilehash: 61bf4db6d61160c7ec11ffa3f178cc3917ae6cf9
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182822"
---
# <a name="leveraging-serverless-functions"></a>利用無伺服器函式

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

在管理完整機器和作業系統以利用雲端功能的範圍中，無伺服器的最大目的在於您的程式碼，而您只需要為程式碼執行時才需要付費。 Azure Functions 提供一種方式，可在您的應用程式中建立無伺服器功能。 

## <a name="what-is-serverless"></a>什麼是無伺服器？

無伺服器運算並不表示執行您的應用程式時，不會有一台伺服器，那就是程式碼仍會在某個伺服器上執行。 差別在於應用程式開發小組不再需要自行顧慮管理伺服器基礎結構。 無伺服器運算解決方案（例如 Azure Functions 協助小組提高生產力，並可讓組織將其資源優化，並將焦點放在提供解決方案。

無伺服器運算會使用事件觸發的無狀態容器來裝載您的應用程式或部分應用程式。 無伺服器平臺可以視需要相應增加和減少，以符合需求。 像 Azure Functions 的平臺可以輕鬆直接存取其他 Azure 服務，例如佇列、事件和儲存體。

## <a name="what-challenges-are-solved-by-serverless"></a>無伺服器可解決哪些挑戰？

無伺服器是從執行您自己的硬體開始的最終抽象概念。 開發人員可以專門專注于撰寫程式碼來解決商務問題，而不需要考慮下列任何可能在裝載您自己的伺服器時所需的工作：

- 購買機器和軟體授權
- 存放、保護、設定和維護電腦及其網路功能、電源和 A/C 需求
- 修補和升級作業系統與軟體
- 設定網頁伺服器或機器服務來裝載應用程式軟體
- 在其平臺中設定應用程式軟體

許多公司都採用數十個員工成員，並配置大型預算來支援這些硬體基礎結構的考慮。 直接移至雲端可以排除其中一些問題;將應用程式一直轉移到無伺服器，可以排除其餘部分。

## <a name="what-scenarios-are-appropriate-for-serverless"></a>什麼是適用于無伺服器的案例？

無伺服器會使用個別的簡短執行函式，以回應某個觸發程式來進行呼叫。 這讓它們適合用來處理背景工作。

例如，應用程式可能需要在處理要求的過程中傳送電子郵件。 您不需要在處理 web 要求時傳送電子郵件，而是將電子郵件的詳細資料放在佇列上，並使用 Azure 函式來挑選訊息並傳送電子郵件。 應用程式的許多不同元件（或甚至許多應用程式）都可以利用這個相同的 Azure 函式，為應用程式提供改善的效能和擴充性，並使用[佇列型負載調節](https://docs.microsoft.com/azure/architecture/patterns/queue-based-load-leveling)來避免與下列相關的瓶頸：傳送電子郵件。

雖然應用程式和 Azure Functions 之間的[發行者/訂閱者模式](https://docs.microsoft.com/azure/architecture/patterns/publisher-subscriber)是最常見的模式，但其他模式也是可行的。 Azure Functions 可以由其他事件觸發，例如 Azure Blob 儲存體的變更。 支援的影像上傳的應用程式可能有負責建立縮圖影像的 Azure 函式，或將上傳影像的大小調整為一致的維度，或優化影像大小。 所有這項功能都可以透過插入 Azure Blob 儲存體直接觸發，讓應用程式本身的複雜性和工作負載保持不變。

許多應用程式都有長時間執行的進程，做為其工作流程的一部分。 這些工作通常會在使用者與應用程式互動的過程中完成，強制使用者等待並對其體驗造成負面影響。 無伺服器運算提供了在使用者互動迴圈外執行較慢工作的絕佳方式，而這些工作可以輕鬆地隨需求調整，而不需要調整整個應用程式。

## <a name="when-should-you-avoid-serverless"></a>何時應該避免無伺服器？

無伺服器運算最適合用於不會封鎖使用者介面的工作。 這表示它們不是直接裝載 web 應用程式或 web Api 的理想選擇。 其主要原因是無伺服器解決方案會依需求布建和調整。 當需要新的函式實例時（稱為*冷啟動*），需要一些時間來布建。 這次通常是幾秒鐘的時間，但可能會因為各種不同的因素而變長。 單一實例通常可以無限期地維護（例如，定期向其提出要求），但如果實例數目需要相應增加，則會保留冷啟動問題。

![冷與暖開機](./media/cold-start-warm-start.png)
**圖 3-10**。 冷啟動和暖開機。

如果您需要避免冷啟動，您可以選擇從取用[方案切換到專用的方案](https://azure.microsoft.com/blog/understanding-serverless-cold-start/)。 您也可以使用 premium 方案[設定一或多個預先準備就緒的實例](https://docs.microsoft.com/azure/azure-functions/functions-premium-plan#pre-warmed-instances)，因此當您需要新增另一個實例時，它已經啟動並準備就緒。 這些選項可以減輕與無伺服器運算相關的其中一個重要考慮。

您通常也應該避免長時間執行之工作的無伺服器。 它們最適用于可快速完成的一小段工作。 大部分的無伺服器平臺都需要在幾分鐘內完成個別的函式。 Azure Functions 預設為5分鐘的超時期間（最多可設定10分鐘）。 Azure Functions premium 方案也可以緩和此問題，並將時間輸出預設為30分鐘，並允許設定未限制的更高限制。

最後，針對應用程式內的特定工作運用無伺服器，會增加複雜度。 通常最好先以模組化、鬆散耦合的方式來設計您的應用程式，然後找出無伺服器可提供的優點，使額外的複雜性更有價值。 許多較小的應用程式在單一整合式部署中都可以順利執行，而不需要無伺服器運算所需的分散式應用程式架構。

## <a name="references"></a>reference

- [瞭解無伺服器冷啟動](https://azure.microsoft.com/blog/understanding-serverless-cold-start/)
- [預先準備就緒 Azure Functions 實例](https://docs.microsoft.com/azure/azure-functions/functions-premium-plan#pre-warmed-instances)
- [使用自訂映射在 Linux 上建立函式](https://docs.microsoft.com/azure/azure-functions/functions-create-function-linux-custom-image)

>[!div class="step-by-step"]
>[上一頁](leverage-containers-orchestrators.md)
>[下一頁](combine-containers-serverless-approaches.md)
