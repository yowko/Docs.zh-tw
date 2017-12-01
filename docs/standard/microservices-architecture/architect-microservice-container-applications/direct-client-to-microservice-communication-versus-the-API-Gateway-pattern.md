---
title: "與 API 閘道模式的直接用戶端的微服務通訊"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |與 API 閘道模式的直接用戶端的微服務通訊"
keywords: "Docker Microservices、 ASP.NET、 容器、 API 閘道"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: c8227ec47888c7cf361f34c4c85a09c0666f886e
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="direct-client-to-microservice-communication-versus-the-api-gateway-pattern"></a>與 API 閘道模式的直接用戶端的微服務通訊

在 microservices 架構中，每個微服務會公開一組一般 fine‑grained 端點。 這項事實可能會影響 client‑to‑microservice 通訊，如本節所述。

## <a name="direct-client-to-microservice-communication"></a>若要微服務的用戶端會直接通訊

可能的方法是使用直接通訊，用戶端的微服務架構。 這種方法，用戶端應用程式可以對要求直接某些 microservices，如圖 4-12 版中所示。

![](./media/image12.png)

**圖 4-12**。 使用直接通訊，用戶端的微服務架構

在這種方法。 每個微服務有公用端點，有時會有不同的 TCP 連接埠的每個微服務。 針對特定服務的 URL 的範例可能是在 Azure 中的下列 URL:

<http://eshoponcontainers.westus.cloudapp.azure.com:88 />

在生產環境中的叢集，URL 會對應至叢集中使用的負載平衡器為基礎的接著將要求分散到 microservices。 在實際執行環境中，您可能會有類似的應用程式傳遞控制站 (ADC) [Azure 應用程式閘道](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction)您 microservices 與網際網路之間。 這可以做為透明的層，不會執行負載平衡，只保護您的服務供應項目 SSL 終止。 這可以改善您的主機負載卸載 CPU 運算密集 SSL 終止和其他路由的責任給 Azure 應用程式閘道。 在任何情況下，負載平衡器和 ADC 皆為透明從邏輯應用程式架構的觀點。

直接通訊，用戶端的微服務架構可能是適用於小型微服務應用程式中，特別是當用戶端應用程式是伺服器端 web 應用程式，例如 ASP.NET MVC 應用程式。 不過，當您建置大型且複雜微服務為基礎的應用程式 （例如，處理數十個微服務型別時），而且特別是當用戶端應用程式遠端行動裝置應用程式或 SPA web 應用程式，該方法會面臨的一些問題。

開發 microservices 為基礎的大型應用程式時，請考慮下列問題：

-   *用戶端應用程式如何最小化後端要求的數目和減少至多個 microservices 多對話通訊？*

在網際網路上會互動來建置單一 UI 畫面的多個 microservices 增加往返的次數。 這會增加延遲和 UI 端上的複雜性。 在理想情況下，回應應該有效率地彙總伺服器端 — 這會減少延遲，因為多個資料片段回來以平行方式，而且只要準備就緒時，某些 UI 可以顯示的資料。

-   *您要如何處理跨領域的考量，如授權、 資料轉換和動態要求分派？*

實作的安全性與跨領域考量，像是安全性和授權上每個微服務可能需要大量的開發工作。 可能的方法是讓這些服務內的 Docker 主機或內部的叢集，以限制他們從外部，直接存取，並在集中位置，例如應用程式開發介面 Gateway 實作這些跨領域的考量。

-   *可以用戶端應用程式與通訊的方式使用非易記網際網路通訊協定的服務？*

通常在用戶端應用程式中不支援通訊協定 （例如 AMQP 或二進位通訊協定） 的伺服器端上使用。 因此，要求必須透過如 HTTP/HTTPS 通訊協定來執行，而且之後轉譯成其他通訊協定。 A*攔截*方法可以在此情況下幫助。

-   *您要如何形成外觀，尤其是對行動裝置應用程式？*

針對不同的用戶端應用程式的需求可能不會也設計多個 microservices API。 比方說，行動裝置應用程式的需求可能會與 web 應用程式的需求不同。 行動裝置應用程式，您可能需要更進一步最佳化，讓資料回應可能會更有效率。 您可能會從多個 microservices 彙總資料並傳回單一集合的資料，有時排除不需要行動裝置應用程式的回應中的任何資料，藉以執行這項操作。 而且，您可能會壓縮該資料。 同樣地，外觀或行動裝置應用程式和 microservices 之間的應用程式開發介面可以是此案例中很方便。

## <a name="using-an-api-gateway"></a>使用 API 閘道

當您設計及建置大型或複雜微服務為基礎的應用程式使用多個用戶端應用程式時，可以是一個好的方法，考慮[API 閘道](http://microservices.io/patterns/apigateway.html)。 這是 microservices 的特定群組提供單一進入點的服務。 類似於[外觀模式](https://en.wikipedia.org/wiki/Facade_pattern)從 object‑oriented 設計，但在此情況下，它是分散式系統的一部分。 API 閘道模式有時也稱為 「 後端的 「 前端 」 [(BFF)](http://samnewman.io/patterns/architectural/bff/)因為您建置時思考用戶端應用程式的需求。

圖 4-13 顯示自訂 API 閘道器如何納入微服務為基礎的架構。
請務必中反白顯示，該圖表，您會使用單一自訂 API 閘道服務對向多個與不同的用戶端應用程式。 事實可以是重要的風險，因為將會成長及演變，您的應用程式開發介面的閘道服務會根據許多不同的需求，從用戶端應用程式。 最後，將予以繁雜因為這些不同的需求並有效地可能很類似於整合型應用程式或整合服務。 這是非常建議使用分割應用程式開發介面中的閘道多個服務或多個較小 API 閘道，其中每個表單係數類型執行個體的原因。

![](./media/image13.png)

**圖 4-13**。 使用 API 閘道實作為自訂的 Web API 服務

在此範例中，API 閘道會實作為自訂的 Web API 服務執行的容器。

如前所述，您應該實作數個應用程式開發介面閘道，以便您可以有不同的外觀，針對每個用戶端應用程式的需求。 每個 API 閘道可提供不同的應用程式開發介面量身訂做的每個用戶端應用程式中，可能甚至會根據用戶端衩怮藉由實作特定介面卡的下方呼叫多個內部 microservices 的程式碼。

由於自訂 API 閘道通常是資料彙總工具，您必須謹慎使用它。 通常最好是有單一彙總您的應用程式的所有內部 microservices API 閘道沒有資源。 若是如此，它會做為整合型彙總工具或 orchestrator，並藉由所有 microservices 違反自主微服務。 因此，應用程式開發介面閘道應該被隔離根據商務界限，並不針對做為整個應用程式彙總工具。

有時候細微的 API 閘道可以也是微服務本身，而甚至可將網域或公司名稱及相關的資料。 擁有商務或網域所指定的 API 閘道的界限會幫助您獲得更好的設計。

閘道應用程式開發介面層中的資料粒度可能特別適用於更進階的複合 UI 應用程式根據 microservices，因為更細緻的 API 閘道概念就類似於 UI 組合服務。 我們會討論這稍後在[根據建立複合 UI microservices](#creating-composite-ui-based-on-microservices-including-visual-ui-shape-and-layout-generated-by-multiple-microservices)。

因此，許多和大型-中型應用程式中使用自訂 API 閘道通常是較好的方法，但不是能作為單一龐大的彙總工具或唯一中央的自訂 API 閘道。

另一個方法是使用像是產品[Azure API 管理](https://azure.microsoft.com/services/api-management/)如圖 4-14 版中所示。 這個方法不僅可以解決您的應用程式開發介面閘道需求，提供功能，例如收集 insights 從您的應用程式開發介面。 如果您使用 API 管理解決方案，API 閘道會是該完整的 API 管理方案中的元件。

![](./media/image14.png)

**圖 4-14**。 您的應用程式開發介面閘道使用 Azure API 管理

在此情況下，當使用 Azure API 管理，您可能會有單一的應用程式開發介面閘道的事實等產品並不那麼風險因為這類的應用程式開發介面閘道 」 細"，這表示您不會實作自訂 C# 程式碼可能發展朝向整合元件。 

這種類型的產品更像是輸入通訊，其中也篩選從內部 microservices Api 以及將授權套用至已發行應用程式開發介面，此單一階層中的反向 proxy。

可從 API 管理系統說明的深入資訊了解您的應用程式開發介面的使用方式，而且正在執行的方式。 他們這麼做會讓您以接近即時的分析報告檢視及識別可能會影響您公司的趨勢。 此外，您可以要求和回應的活動，供進一步線上及離線分析的相關記錄檔。

使用 Azure API 管理，您可以保護您應用程式開發介面使用的索引鍵、 語彙基元，和 IP 篩選。 這些功能可讓您強制執行彈性且更細緻的配額和速率限制、 修改圖形和使用原則，您 Api 的行為，並改善快取回應的效能。

在本指南和參考範例應用程式 (eShopOnContainers) 中，我們會限制更簡單且自訂的容器化架構的架構，以便專注於一般的容器，而不需使用 Azure API 管理等的 PaaS 產品。 但對於大型微服務為基礎應用程式部署到 Microsoft Azure，建議您檢閱，並採用做為基底的 Azure API 管理的應用程式開發介面閘道。

## <a name="drawbacks-of-the-api-gateway-pattern"></a>API 閘道模式的缺點

-   最重要的缺點是，當您實作應用程式開發介面閘道，您會結合該層內部 microservices 與。 像這樣的結合程度可能會造成嚴重的問題，您的應用程式。 Clemens Vaster，架構設計人員的 Azure 服務匯流排小組，是指在他此潛在難度"新 ESB 」 與 「[訊息和 Microservices](https://www.youtube.com/watch?v=rXi5CLjIQ9k)」 工作階段在 GOTO 2016。

-   使用 API 閘道 microservices 建立其他可能單一失敗點。

-   API 閘道可能導致回應時間增加由於額外的網路呼叫。 不過，這個額外的呼叫通常有較少的影響，而不需要用戶端介面，是太多話直接呼叫內部 microservices。

-   如果未向外延展正確，API 閘道成為瓶頸。

-   如果它包含自訂邏輯和資料彙總，API 閘道需要額外的開發成本和未來的維護。 開發人員必須更新 API 閘道，才能公開每個微服務端點。 此外，在內部 microservices 實作變更可能會導致 API 閘道層級的程式碼變更。 不過，如果應用程式開發介面閘道只將套用的安全性、 記錄和版本控制 （如同使用 Azure API 管理時），可能不會套用此額外的開發成本。

-   單一小組所開發的應用程式開發介面閘道，可以是開發瓶頸。 這是較佳的方法為何有數個不同的用戶端需要回應的處以精細 API 閘道的另一個原因。 您也可以在內部隔離 API 閘道為多個區域或不同處理內部 microservices 的小組所擁有的圖層。

## <a name="additional-resources"></a>其他資源

-   **Charles Richardson。模式： API 閘道 / 後的端前端**
    [*http://microservices.io/patterns/apigateway.html*](http://microservices.io/patterns/apigateway.html)

-   **Azure API 管理**
    [*https://azure.microsoft.com/services/api-management/*](https://azure.microsoft.com/services/api-management/)

-   **Udi Dahan。服務導向組合**\
    [*http://udidahan.com/2014/07/30/service-oriented-composition-with-video/*](http://udidahan.com/2014/07/30/service-oriented-composition-with-video/)

-   **Clemens Vasters。訊息和在 GOTO 2016 Microservices** （影片） [ *https://www.youtube.com/watch?v=rXi5CLjIQ9k*](https://www.youtube.com/watch?v=rXi5CLjIQ9k)


>[!div class="step-by-step"]
[上一個](識別的微服務-網域-模型-boundaries.md) [下一步] (通訊層中的微服務-architecture.md)
