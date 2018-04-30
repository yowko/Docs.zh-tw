---
title: 直接用戶端與微服務通訊與 API 閘道模式
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 直接用戶端與微服務通訊與 API 閘道模式
keywords: Docker, 微服務, ASP.NET, 容器, API 閘道
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: fa3f4bb97cf942ee7698b1efa1dcd09b3f2ca571
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="direct-client-to-microservice-communication-versus-the-api-gateway-pattern"></a>直接用戶端與微服務通訊與 API 閘道模式

在微服務架構中，每個微服務都會公開一組 (通常) 微調端點。 這項事實可能會影響用戶端與微服務通訊，如本節所述。

## <a name="direct-client-to-microservice-communication"></a>直接用戶端對微服務通訊

可能的方法是使用直接用戶端對微服務通訊架構。 使用這種方法，用戶端應用程式可以直接對某些微服務提出要求，如圖 4-12 所示。

![](./media/image12.png)

**圖 4-12**. 使用直接用戶端對微服務通訊架構

使用這種方法， 每個微服務都會有公用端點，有時每個微服務會有不同的 TCP 連接埠。 在 Azure 中，特定服務的 URL 範例可以是下列 URL：

<http://eshoponcontainers.westus.cloudapp.azure.com:88/>

在根據叢集的生產環境中，該 URL 會對應至叢集中所使用的負載平衡器，而負載平衡器接著會將要求分散到微服務。 在生產環境中，您在微服務與網際網路之間可能會有 [Azure 應用程式閘道](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction)這類應用程式傳遞控制站 (ADC)。 這會作為透明層，不僅可執行負載平衡，也會透過提供 SSL 終止來保護您的服務。 這會改善主機的負載，方法是將 CPU 密集 SSL 終止和其他路由責任卸載給 Azure 應用程式閘道。 從邏輯應用程式架構觀點，在任何情況下，負載平衡器和 ADC 都是透明的。

直接用戶端對微服務通訊架構可能適用於小型微服務應用程式，特別是用戶端應用程式為 ASP.NET MVC 應用程式這類伺服器端 Web 應用程式時。 不過，如果您建置大型且複雜的微服務應用程式 (例如，處理數十個微服務型別時)，特別是用戶端應用程式為遠端行動應用程式或 SPA Web 應用程式時，該方法會面臨的一些問題。

開發根據微服務的大型應用程式時，請考慮下列問題：

-   *用戶端應用程式如何最小化後端要求數目以及減少與多個微服務的過於頻繁通訊？*

與多個微服務互動來建置單一 UI 畫面，會增加跨網際網路往返的次數。 這會增加 UI 端的延遲和複雜性。 在理想情況下，應該會在伺服器端有效率地彙總回應，而這樣做可減少延遲，因為會平行取得多個資料片段，而且只要準備就緒，某些 UI 就會顯示資料。

-   *如何處理授權、資料轉換和動態要求分派這類跨領域考量？*

實作安全性和跨領域考量 (例如每個微服務上的安全性和授權) 可能需要大量開發工作。 可能的方法是 Docker 主機或內部叢集內有這些服務，以限制從外部直接存取它們，並在集中位置 (例如 API 閘道) 實作這些跨領域考量。

-   *用戶端應用程式如何與使用非友善網際網路通訊協定的服務通訊？*

用戶端應用程式通常不支援伺服器端上使用的通訊協定 (例如 AMQP 或二進位通訊協定)。 因此，必須透過 HTTP/HTTPS 這類通訊協定執行要求，而且之後會轉譯成其他通訊協定。 在此情況下，「攔截式」方法可能有幫助。

-   *如何形成特別針對行動應用程式所產生的外觀？*

多個微服務 API 的設計可能不是最適合不同用戶端應用程式的需求。 例如，行動應用程式需求可能會與 Web 應用程式需求不同。 針對行動應用程式，您甚至可能需要更進一步最佳化，讓資料回應更具效率。 作法是彙總多個微服務中的資料並傳回一組資料，有時會排除行動應用程式不需要之回應中的任何資料。 而且，您當然可以壓縮該資料。 同樣地，在此案例中，行動應用程式與微服務之間的外觀或 API 可能十分方便使用。

## <a name="using-an-api-gateway"></a>使用 API 閘道

當您使用多個用戶端應用程式來設計和建置大型或複雜微服務應用程式時，可以考慮使用的不錯方法是 [API 閘道](https://microservices.io/patterns/apigateway.html)。 這個服務提供特定一組微服務的單一進入點。 它與物件導向設計中的[外觀模式](https://en.wikipedia.org/wiki/Facade_pattern)類似但在此情況下，它是分散式系統的一部分。 API 閘道模式有時也稱為「前端的後端 [(BFF)](https://samnewman.io/patterns/architectural/bff/)」，因為您是在考量用戶端應用程式需求時建置它。

圖 4-13 顯示自訂 API 閘道如何納入微服務架構。
請務必在該圖表中將它反白顯示，您會使用面向多個和不同用戶端應用程式的單一自訂 API 閘道服務。 這項事實的風險可能十分重大，因為 API 閘道服務將會根據用戶端應用程式的許多不同需求而成長和演變。 最後，它會因為這些不同需求而十分繁雜，而且可能十分類似整合型應用程式或整合型服務。 這是極為建議將 API 閘道分割為多個服務或多個較小 API 閘道 (例如一個板型規格一個) 的原因。

![](./media/image13.png)

**圖 4-13**. 使用實作為自訂 Web API 服務的 API 閘道

在此範例中，API 閘道會實作為以容器形式執行的自訂 Web API 服務。

如前所述，您應該實作數個 API 閘道，以擁有每個用戶端應用程式需求的不同樣貌。 每個 API 閘道都可以提供針對每個用戶端應用程式量身訂做的不同 API，甚至可能會根據用戶端板型規格，方法是實作其下呼叫多個內部微服務的特定介面卡程式碼。

因為自訂 API 閘道通常是資料彙總工具，所以您必須謹慎使用它。 通常不適合讓單一 API 閘道彙總您應用程式的所有內部微服務。 若是如此，它會作為整合型彙總工具或協調器，並且因結合所有微服務而違反微服務自主性。 因此，應該根據商務界限來隔離 API 閘道，而不是作為整個應用程式的彙總工具。

細微 API 閘道有時也可以是微服務本身，甚至具有領域或公司名稱和相關資料。 擁有商務或領域所指出的 API 閘道界限可幫助您獲得更好的設計。

API 閘道層中的細微性可能特別適用於根據微服務的更進階複合 UI 應用程式，因為微調 API 閘道概念類似於 UI 組合服務。 我們稍後會在[建立根據微服務的複合 UI](#creating-composite-ui-based-on-microservices-including-visual-ui-shape-and-layout-generated-by-multiple-microservices) 中討論這點。

因此，針對許多中型和大型應用程式，使用自訂建置的 API 閘道通常是不錯的方法，但不能作為單一整合型彙總工具或唯一中央自訂 API 閘道。

另一種方法是使用 [Azure API 管理](https://azure.microsoft.com/services/api-management/)這類產品，如圖 4-14 所示。 這種方法不僅可以解決 API 閘道需求，也可以提供收集 API 深入資訊這類功能。 如果您使用 API 管理解決方案，則 API 閘道只是該完整 API 管理解決方案內的元件。

![](./media/image14.png)

**圖 4-14**. 將 Azure API 管理用於 API 閘道

在此情況下，使用 Azure API 管理這類產品時，您可能會有單一 API 閘道的這個事實的風險不大，因為這類 API 閘道較「輕量」，表示您未實作可能朝向整合型元件發展的自訂 C# 程式碼。 

這類型的產品更像是輸入通訊的反向 Proxy，在其中，您也可以從內部微服務篩選 API，以及將授權套用至這個單一階層的已發行 API。

可從 API 管理系統取得的深入資訊可幫助您了解 API 使用方式和其執行方式。 作法是讓您檢視接近即時的分析報表，以及識別可能會影響您商務的趨勢。 此外，您可能會有要求和回應活動的記錄，以進行進一步線上及離線分析。

使用 Azure API 管理，您可以使用金鑰、權杖和 IP 篩選來保護 API。 這些功能可讓您強制執行彈性且微調的配額和速率限制、使用原則修改您 API 的形狀和行為，並改善快取回應的效能。

在本指南和參考範例應用程式 (eShopOnContainers) 中，我們會限制更簡單且自訂容器化架構的架構，以專注於一般容器，而不需要使用 Azure API 管理這類 PaaS 產品。 但對於部署至 Microsoft Azure 的大型微服務應用程式，建議您檢閱並採用作為 API 閘道基底的 Azure API 管理。

## <a name="drawbacks-of-the-api-gateway-pattern"></a>API 閘道模式的缺點

-   最大的缺點在於當您實作 API 閘道時，會結合該階層與內部微服務。 這類結合可能會造成您應用程式的嚴重問題。 Clemens Vaster 是 Azure 服務匯流排小組的架構設計人員，在他於 GOTO 2016 的 [Messaging and Microservices](https://www.youtube.com/watch?v=rXi5CLjIQ9k) (訊息和微服務) 講習會中將這項潛在困難稱為「新的 ESB」。

-   使用微服務 API 閘道會建立其他可能單一失敗點。

-   API 閘道可能會導致因額外網路呼叫而增加回應時間。 不過，這個額外呼叫的影響通常會小於擁有過於頻繁直接呼叫內部微服務的用戶端介面。

-   如果未正確地相應放大，則 API 閘道可能會成為瓶頸。

-   如果 API 閘道包含自訂邏輯和資料彙總，則需要額外開發成本和未來維護。 開發人員必須更新 API 閘道，才能公開每個微服務的端點。 此外，內部微服務中的實作變更可能會導致 API 閘道層級的程式碼變更。 不過，如果 API 閘道只會套用安全性、記錄和版本控制 (就像使用 Azure API 管理時一樣)，可能不會套用這個額外的開發成本。

-   如果 API 閘道是由單一小組所開發，則可能會有開發瓶頸。 這是較佳方法是具有數個回應不同用戶端需求之微調 API 閘道的另一個原因。 您也可以在內部將 API 閘道區分為處理內部微服務之不同小組所擁有的多個區域或層級。

## <a name="additional-resources"></a>其他資源

-   **Charles Richardson：模式：API 閘道/前端的後端**
    [*https://microservices.io/patterns/apigateway.html*](https://microservices.io/patterns/apigateway.html)

-   **Azure API 管理**
    [*https://azure.microsoft.com/services/api-management/*](https://azure.microsoft.com/services/api-management/)

-   **Udi Dahan.Service Oriented Composition (服務導向組合)**\
    [*http://udidahan.com/2014/07/30/service-oriented-composition-with-video/*](http://udidahan.com/2014/07/30/service-oriented-composition-with-video/)

-   **Clemens Vasters：GOTO 2016 的傳訊和微服務** (影片) [*https://www.youtube.com/watch?v=rXi5CLjIQ9k*](https://www.youtube.com/watch?v=rXi5CLjIQ9k)


>[!div class="step-by-step"]
[上一個] (identify-microservice-domain-model-boundaries.md) [下一個] (communication-in-microservice-architecture.md)
