---
title: 利用無伺服器函式
description: 利用雲端原生應用程式中的無伺服器和 Azure Functions
ms.date: 05/13/2020
ms.openlocfilehash: 53a0fdd29630b2a4368f3aa37ddfc5f93df10a24
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83613859"
---
# <a name="leveraging-serverless-functions"></a>利用無伺服器函式

在管理實體機器以利用雲端功能的範圍中，無伺服器存在於極致端。 您的程式碼是唯一的責任，而您只需支付程式碼的執行時間。 Azure Functions 提供在雲端原生應用程式中建立無伺服器功能的方式。

## <a name="what-is-serverless"></a>什麼是無伺服器？

無伺服器是雲端運算的相對新服務模型。 這並不表示伺服器是選擇性的，您的程式碼仍會在某個伺服器上執行。 差別在於應用程式小組不再關心管理伺服器基礎結構的問題。 取而代之的是，雲端廠商擁有此責任。 開發小組供應商務解決方案給客戶，而不是配管，以提高生產力。

無伺服器運算會使用事件觸發的無狀態容器來裝載您的服務。 他們可以視需要相應放大和縮小以符合需求。 無伺服器平臺（如 Azure Functions）與其他 Azure 服務（例如佇列、事件和儲存體）緊密整合。

## <a name="what-challenges-are-solved-by-serverless"></a>無伺服器可解決哪些挑戰？

無伺服器平臺會解決許多耗時且昂貴的問題：

- 購買機器和軟體授權
- 存放、保護、設定和維護電腦及其網路功能、電源和 A/C 需求
- 修補和升級作業系統與軟體
- 設定網頁伺服器或機器服務來裝載應用程式軟體
- 在其平臺中設定應用程式軟體

許多公司會配置大型預算來支援硬體基礎結構的考慮。 移至雲端有助於降低這些成本;將應用程式轉移到無伺服器有助於排除它們。

## <a name="what-is-the-difference-between-a-microservice-and-a-serverless-function"></a>微服務與無伺服器函式之間的差異為何？

一般來說，微服務會封裝商務功能，例如線上電子商務網站的購物車。 它會公開多個可讓使用者管理其購物體驗的作業。 不過，函式是一個小型、輕量的程式碼區塊，會執行單一用途的作業來回應事件。
微服務通常是用來回應要求，通常是來自介面。 要求可以是 HTTP Rest，或以 gRPC 為基礎。 無伺服器服務會回應事件。 其事件驅動架構適合用來處理簡短執行的背景工作。

## <a name="what-scenarios-are-appropriate-for-serverless"></a>什麼是適用于無伺服器的案例？

無伺服器會公開針對回應觸發程式而叫用的個別短期執行函數。 這讓它們適合用來處理背景工作。

應用程式可能需要傳送電子郵件，做為工作流程中的步驟。 將訊息詳細資料放在佇列上，而不是在微服務要求中傳送通知。 Azure 函數可以清除佇列訊息，並以非同步方式傳送電子郵件。 這麼做可以改善微服務的效能和擴充性。 以[佇列為基礎的負載調節](https://docs.microsoft.com/azure/architecture/patterns/queue-based-load-leveling)可以執行，以避免與傳送電子郵件相關的瓶頸。 此外，您可以在許多不同的應用程式中重複使用此獨立服務作為公用程式。

佇列和主題的非同步訊息是觸發無伺服器函式的常見模式。 不過，Azure Functions 可以由其他事件觸發，例如 Azure Blob 儲存體的變更。 支援影像上傳的服務可能會有負責優化影像大小的 Azure 函數。 函式可以透過插入 Azure Blob 儲存體直接觸發，讓微服務作業的複雜性變得更複雜。

許多服務在其工作流程中都有長時間執行的進程。 這些工作通常會在使用者與應用程式互動的過程中完成。 這些工作可以強制使用者等待，對他們的體驗造成負面影響。 無伺服器運算提供絕佳的方式，在使用者互動迴圈之外移動較慢的工作。 這些工作可以隨需求調整，而不需要調整整個應用程式。

## <a name="when-should-you-avoid-serverless"></a>何時應該避免無伺服器？

無伺服器解決方案會依需求布建和調整。 叫用新的實例時，冷啟動是常見的問題。 冷啟動是布建這個實例所花費的時間。 一般來說，此延遲可能是幾秒鐘，但可能會因為各種因素而較長。 一旦布建之後，只要單一實例收到定期要求，就會保持運作狀態。 但是，如果服務的呼叫頻率較低，Azure 可能會將它從記憶體中移除，並在 reinvoked 時要求冷啟動。 當函數向外延展至新的實例時，也需要冷啟動。

圖3-10 顯示冷啟動模式。 請注意，應用程式冷時所需的額外步驟。

![冷與暖開機 ](./media/cold-start-warm-start.png)
 **圖 3-10**。 冷啟動和暖開機。

若要避免冷啟動，您可以從取用[方案切換至專用方案](https://azure.microsoft.com/blog/understanding-serverless-cold-start/)。 您也可以使用 premium 方案升級來設定一個或多個[預先準備就緒的實例](https://docs.microsoft.com/azure/azure-functions/functions-premium-plan#pre-warmed-instances)。 在這些情況下，當您需要加入另一個實例時，它已經啟動並準備好了。 這些選項可協助降低與無伺服器運算相關聯的冷啟動問題。

雲端提供者會根據計算執行時間和耗用的記憶體，為無伺服器計費。 長時間執行的作業或高記憶體耗用量工作負載不一定是無伺服器的最佳候選項目。 無伺服器函式偏好可快速完成的小型工作區塊。 大部分的無伺服器平臺都需要在幾分鐘內完成個別的函式。 Azure Functions 預設為5分鐘的超時期間，最多可設定10分鐘。 Azure Functions premium 方案也可以緩和此問題，並將超時時間設定為30分鐘，而此限制可加以設定。 計算時間不是行事歷時間。 使用[Azure Durable Functions 架構](https://docs.microsoft.com/azure/azure-functions/durable/durable-functions-overview?tabs=csharp)的更多先進函式可能會在數天的期間暫停執行。 計費是以實際執行時間為基礎-當函式喚醒並繼續處理時。

最後，利用 Azure Functions 的應用程式工作會增加複雜度。 最好先使用模組化、鬆散結合的設計來架構您的應用程式。 然後，找出無伺服器可提供的優點，以證明額外的複雜性。

>[!div class="step-by-step"]
>[上一個](leverage-containers-orchestrators.md) 
>[下一步](combine-containers-serverless-approaches.md)
