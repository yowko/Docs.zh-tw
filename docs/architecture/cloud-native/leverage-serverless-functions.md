---
title: 利用無伺服器函式
description: 在雲端原生應用程式中運用無伺服器和 Azure Functions
ms.date: 05/13/2020
ms.openlocfilehash: 8e5c60d29cd8d635f79f42c232b33f060949e2b5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155363"
---
# <a name="leveraging-serverless-functions"></a>利用無伺服器函式

在管理實體機器以利用雲端功能的範圍中，無伺服器存在於極端的端。 您唯一的責任是您的程式碼，而您只需支付程式碼執行的時間。 Azure Functions 可讓您在雲端原生應用程式中建立無伺服器功能。

## <a name="what-is-serverless"></a>什麼是無伺服器？

無伺服器是雲端運算的一個相對新服務模型。 這並不表示伺服器是選擇性的，您的程式碼仍會在某處的伺服器上執行。 差別在於應用程式小組不再關注管理伺服器基礎結構。 相反地，雲端廠商擁有這種責任。 開發團隊將商務解決方案傳遞給客戶，而不是進行管線，藉此提升其生產力。

無伺服器運算會使用事件觸發的無狀態容器來裝載您的服務。 他們可以視需要相應放大和縮小以符合需求。 無伺服器平臺（例如 Azure Functions）與其他 Azure 服務（例如佇列、事件和儲存體）緊密整合。

## <a name="what-challenges-are-solved-by-serverless"></a>無伺服器可解決哪些挑戰？

無伺服器平臺解決了許多耗時且昂貴的考慮：

- 購買電腦和軟體授權
- 存放、保護、設定和維護機器及其網路功能、電源及 A/C 需求
- 修補及升級作業系統和軟體
- 設定 web 伺服器或電腦服務以裝載應用程式軟體
- 在其平臺中設定應用程式軟體

許多公司都會配置大型預算來支援硬體基礎結構的考慮。 移至雲端有助於降低這些成本;將應用程式轉移到無伺服器有助於排除它們。

## <a name="what-is-the-difference-between-a-microservice-and-a-serverless-function"></a>微服務與無伺服器函式有何不同？

一般而言，微服務會封裝商務功能，例如線上電子商務網站的購物車。 它會公開多個作業，讓使用者能夠管理其購物體驗。 不過，函式是一種小型的輕量程式碼區塊，會執行單一用途作業來回應事件。
微服務通常是為了回應要求而建立的，通常是來自介面。 要求可以是 HTTP Rest 或以 gRPC 為基礎。 無伺服器服務會回應事件。 它的事件驅動架構很適合用來處理短期執行的背景工作。

## <a name="what-scenarios-are-appropriate-for-serverless"></a>無伺服器適用哪些案例？

無伺服器會公開個別的短期執行函式，以回應觸發程式。 這讓它們適合用來處理背景工作。

應用程式可能需要以工作流程中的步驟來傳送電子郵件。 將訊息詳細資料放在佇列上，而不是在微服務要求中傳送通知。 Azure 函式可將訊息清除佇列，並以非同步方式傳送電子郵件。 這麼做可以改善微服務的效能和擴充性。 可以執行以[佇列為基礎的負載調節](/azure/architecture/patterns/queue-based-load-leveling)，以避免與傳送電子郵件相關的瓶頸。 此外，您可以在許多不同的應用程式中重複使用此獨立服務作為公用程式。

佇列和主題的非同步通訊是觸發無伺服器功能的常見模式。 不過，Azure Functions 可由其他事件觸發，例如 Azure Blob 儲存體的變更。 支援影像上傳的服務可能會有負責將映射大小優化的 Azure 函數。 您可以藉由插入 Azure Blob 儲存體來直接觸發函式，以避免微服務作業的複雜度。

許多服務都有長時間執行的程式做為工作流程的一部分。 這些工作通常是在使用者與應用程式互動的過程中完成。 這些工作可以強制使用者等待、對其體驗產生負面影響。 無伺服器運算提供在使用者互動迴圈之外移動較慢工作的絕佳方法。 這些工作可以隨需調整，而不需要整個應用程式進行調整。

## <a name="when-should-you-avoid-serverless"></a>何時應避免無伺服器？

無伺服器解決方案會依需求布建及調整。 叫用新的實例時，冷啟動是常見的問題。 冷啟動是布建此實例所需的時間長度。 一般來說，這種延遲可能是幾秒鐘的時間，但視各種因素而定，可能會更長。 一旦布建之後，只要單一實例收到定期要求，就會保持運作狀態。 但是，如果服務的呼叫頻率較低，Azure 可能會將它從記憶體中移除，並在 reinvoked 時要求冷啟動。 當函數相應放大至新的實例時，也需要冷啟動。

圖3-10 顯示冷啟動模式。 請注意應用程式很冷時所需的額外步驟。

![冷與暖啟動 ](./media/cold-start-warm-start.png)
 **圖 3-10**。 冷啟動和暖開機。

為了避免冷啟動，您可以從取用方案切換 [為專用方案](https://azure.microsoft.com/blog/understanding-serverless-cold-start/)。 您也可以使用高階方案升級設定一或多個 [預先準備就緒的實例](/azure/azure-functions/functions-premium-plan#pre-warmed-instances) 。 在這些情況下，當您需要加入另一個實例時，該實例已啟動且已準備好開始進行。 這些選項有助於減輕與無伺服器運算相關聯的冷啟動問題。

雲端提供者會根據計算執行時間和已耗用的記憶體，針對無伺服器收費。 長時間執行的作業或高記憶體耗用量工作負載不一定是最適合無伺服器的候選項目。 無伺服器函式偏好可快速完成的小型工作區塊。 大部分的無伺服器平臺都需要在幾分鐘內完成個別的功能。 Azure Functions 預設為5分鐘的超時時間，最多可設定10分鐘。 Azure Functions premium 方案也可減輕此問題，並將超時時間設定為30分鐘，而且可設定未系結的限制較高。 計算時間不是行事歷時間。 使用 [Azure Durable Functions framework](/azure/azure-functions/durable/durable-functions-overview?tabs=csharp) 的更先進函式可能會在數天的期間暫停執行。 計費是以實際執行時間為基礎-函式喚醒並繼續處理時。

最後，利用應用程式工作的 Azure Functions 會增加複雜度。 最好先使用模組化、鬆散結合的設計來設計您的應用程式。 然後，找出無伺服器可提供的優點，以證明額外的複雜性。

>[!div class="step-by-step"]
>[上一個](leverage-containers-orchestrators.md) 
>[下一步](combine-containers-serverless-approaches.md)
