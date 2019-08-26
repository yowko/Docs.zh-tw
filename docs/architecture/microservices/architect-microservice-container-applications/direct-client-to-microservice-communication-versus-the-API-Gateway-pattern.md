---
title: API 閘道模式與直接用戶端對微服務通訊
description: 了解 API 閘道模式和直接用戶端對微服務通訊的差異與使用方式。
ms.date: 01/07/2019
ms.openlocfilehash: c54287ea3e99ff7fe9faf02898b8c322b756e26f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914666"
---
# <a name="the-api-gateway-pattern-versus-the-direct-client-to-microservice-communication"></a>API 閘道模式與直接用戶端對微服務通訊

在微服務架構中，每個微服務都會公開一組 (通常是) 微調端點。 這項事實可能會影響用戶端與微服務通訊，如本節所述。

## <a name="direct-client-to-microservice-communication"></a>直接用戶端對微服務通訊

可能的方法是使用直接用戶端對微服務通訊架構。 使用這種方法，用戶端應用程式可以直接對某些微服務提出要求，如圖 4-12 所示。

![圖表，顯示直接用戶端對微服務通訊架構，其中每個應用程式均直接和個別微服務通訊。](./media/image12.png)

**圖 4-12**. 使用直接用戶端對微服務通訊架構

在此方法中，每個微服務都會有公用端點，有時每個微服務會有不同的 TCP 連接埠。 在 Azure 中，特定服務的 URL 範例可以是下列 URL：

`http://eshoponcontainers.westus.cloudapp.azure.com:88/`

在根據叢集的生產環境中，該 URL 會對應至叢集中所使用的負載平衡器，而負載平衡器接著會將要求分散到微服務。 在生產環境中，您在微服務與網際網路之間可能會有 [Azure 應用程式閘道](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction)這類應用程式傳遞控制站 (ADC)。 這會作為透明層，不僅可執行負載平衡，也會透過提供 SSL 終止來保護您的服務。 這會改善主機的負載，方法是將 CPU 密集 SSL 終止和其他路由責任卸載給 Azure 應用程式閘道。 從邏輯應用程式架構觀點，在任何情況下，負載平衡器和 ADC 都是透明的。

直接用戶端對微服務通訊架構可能適用於小型微服務應用程式，特別是用戶端應用程式為 ASP.NET MVC 應用程式這類伺服器端 Web 應用程式時。 不過，如果您建置大型且複雜的微服務應用程式 (例如，處理數十個微服務型別時)，特別是用戶端應用程式為遠端行動應用程式或 SPA Web 應用程式時，該方法會面臨的一些問題。

開發根據微服務的大型應用程式時，請考慮下列問題：

- 用戶端應用程式如何將後端要求數目最小化，以及減少與多個微服務的過度頻繁通訊？ 

與多個微服務互動來建置單一 UI 畫面，會增加跨網際網路來回行程的次數。 這會增加 UI 端的延遲和複雜性。 在理想情況下，回應應該有效率地在伺服器端中彙總。 因為多個部分的資料會平行返回，所以可以減少延遲，而某些 UI 一準備好就可以顯示資料。

- *如何處理授權、資料轉換和動態要求分派這類跨領域考量？*

實作安全性和跨領域考量 (例如每個微服務上的安全性和授權) 可能需要大量開發工作。 可能的方法是 Docker 主機或內部叢集內有這些服務，以限制從外部直接存取它們，並在集中位置 (例如 API 閘道) 實作這些跨領域考量。

- *用戶端應用程式如何與使用非友善網際網路通訊協定的服務通訊？*

用戶端應用程式通常不支援伺服器端上使用的通訊協定 (例如 AMQP 或二進位通訊協定)。 因此，必須透過 HTTP/HTTPS 這類通訊協定執行要求，而且之後會轉譯成其他通訊協定。 在此情況下，「攔截式」  方法可能有幫助。

- 如何形成特別針對行動應用程式所產生的外觀？ 

多個微服務 API 的設計可能不是最適合不同用戶端應用程式的需求。 例如，行動應用程式需求可能會與 Web 應用程式需求不同。 針對行動應用程式，您甚至可能需要更進一步最佳化，讓資料回應更具效率。 作法是彙總多個微服務中的資料並傳回一組資料，有時會排除行動應用程式不需要之回應中的任何資料。 而且，您當然可以壓縮該資料。 同樣地，在此案例中，行動應用程式與微服務之間的外觀或 API 可能十分方便使用。

## <a name="why-consider-api-gateways-instead-of-direct-client-to-microservice-communication"></a>為何考慮 API 閘道而不考慮直接用戶端對微服務通訊

在微服務架構中，用戶端應用程式通常需要從超過一個的微服務取用功能。 如直接執行取用，用戶端需要處理多個對微服務端點的呼叫。 當應用程式演進且微服務推出新版時，或現有的微服務推出更新時，會發生什麼事？ 如果您的應用程式有許多微服務，從用戶端應用程式處理這麼多端點會是個夢魘。 因為用戶端應用程式可能會與那些內部端點結合，導致未來微服務演進時，對用戶端應用程式可能產生重大影響。

因此，具有中繼層級或間接階層 (閘道)，對於微服務型應用程式會非常方便。 如果您沒有 API 閘道，用戶端應用程式就必須直接傳送要求至微服務，而這樣會產生如以下的問題：

- **結合程度**：如果沒有 API 閘道模式，用戶端應用程式就會與內部微服務結合。 用戶端應用程式需要知道應用程式的多個部分在微服務中分解的方式。 當演進及重構內部微服務時，那些動作會嚴重影響維護工作，因為用戶端應用程式直接參考內部微服務，所以它們會對用戶端應用程式造成中斷性變更。 用戶端應用程式需要經常更新，使解決方案難以演進。

- **過多來回行程**：用戶端應用程式中的單一頁面/畫面可能必須對多個服務進行數個呼叫。 這會造成用戶端和伺服器之間的多個網路來回行程，導致顯著延遲。 在中繼層級中處理的彙總可改善用戶端應用程式的效能和使用者體驗。

- **安全性問題**：在沒有閘道的情況下，所有微服務都必須對「外部世界」公開，如此，攻擊面會比隱藏未直接由用戶端應用程式使用的內部微服務來得更大。 攻擊面越小，您的應用程式就越安全。

- **跨領域考量**：每個公開發行的微服務都必須處理授權、SSL 等考量。在許多情況下，那些考量可以在單一階層中處理，這樣就能簡化內部的微服務。

## <a name="what-is-the-api-gateway-pattern"></a>什麼是 API 閘道模式？

當您使用多個用戶端應用程式來設計和建置大型或複雜微服務應用程式時，可以考慮使用的不錯方法是 [API 閘道](https://microservices.io/patterns/apigateway.html)。 這個服務提供特定一組微服務的單一進入點。 它類似物件導向設計的[外觀模式](https://en.wikipedia.org/wiki/Facade_pattern)，不過在此案例中，它是分散式系統的一部分。 因為您是在考量用戶端應用程式需求時建置 API 閘道模式，所以它有時也稱為「前端的後端」([BFF](https://samnewman.io/patterns/architectural/bff/))。

因此，API 閘道位在用戶端應用程式和微服務之間， 它會做為反向 Proxy 使用，將用戶端的要求路由至服務。 它也可以提供額外的跨領域功能，例如驗證、SSL 終止和快取。

圖 4-13 顯示自訂的 API 閘道如何搭配只有幾個微服務的簡化微服務型架構。

![此圖顯示 API 閘道作為自訂服務實作，使應用程式能連線至單一端點，即設定為將要求轉送至個別微服務的 API 閘道。](./media/image13.png)

**圖 4-13**. 使用實作為自訂服務的 API 閘道

在此範例中，API 閘道會實作為以容器形式執行的自訂 ASP.NET Core WebHost 服務。

請務必在該圖表中將它反白顯示，您會使用面向多個和不同用戶端應用程式的單一自訂 API 閘道服務。 這項事實的風險可能十分重大，因為 API 閘道服務將會根據用戶端應用程式的許多不同需求而成長和演變。 最後，它會因為這些不同需求而十分繁雜，而且可能十分類似整合型應用程式或整合型服務。 這就是為什麼我們極為建議將 API 閘道分割為多個服務或多個較小的 API 閘道 (例如，每個用戶端應用程式外形規格類型都有一個)。

您需要謹慎地實作 API 閘道模式。 通常不適合讓單一 API 閘道彙總您應用程式的所有內部微服務。 若是如此，它會作為整合型彙總工具或協調器，並且因結合所有微服務而違反微服務自主性。

因此，應該根據商務界限和用戶端應用程式來隔離 API 閘道，而不是作為所有內部微服務的彙總工具。

當 API 閘道階層分成多個 API 閘道時，如果您的應用程式有多個用戶端應用程式，這樣可當作識別多個 API 閘道類型的樞紐，您就可以擁有適用於每個用戶端應用程式需求的不同外觀。 此案例是名為「前端的後端」([BFF](https://samnewman.io/patterns/architectural/bff/)) 的模式，藉由實作底層會呼叫多個內部微服務的特定配接器程式碼，其中每個 API 閘道都可以提供針對每個用戶端應用程式類型量身訂做的不同 API (甚至可能以用戶端外形規格為基礎)，如以下影像所示：

![此圖顯示多個自訂 API 閘道，其中根據用戶端類型區分 API 閘道，分別應用於行動用戶端和 Web 用戶端。 使用 Web API 閘道連線至 MVC 微服務的傳統 Web 應用程式。](./media/image13.1.png)

**圖 4-13.1**. 使用多個自訂 API 閘道

上圖顯示具有多個更細微 API 閘道的簡化架構。 在此案例中，針對每個 API 閘道識別的界限只以「前端的後端」([BFF](https://samnewman.io/patterns/architectural/bff/)) 模式為基礎，因此也只以每個用戶端應用程式所需的 API 為基礎。 但在更大型的應用程式中，您應該也進一步建立以商務界限為基礎的 API 閘道，作為第二設計樞紐。

## <a name="main-features-in-the-api-gateway-pattern"></a>API 閘道模式中的主要功能

API 閘道可以提供多個功能。 視產品而定，它可以提供更豐富或更簡單的功能，不過，對於任何 API 閘道最重要且最基本的功能是以下設計模式：

**反向 Proxy 或閘道路由。** API 閘道提供反向 Proxy，以重新導向或路由要求 (第 7 層路由，通常是 HTTP 要求) 至內部微服務的端點。 閘道針對用戶端應用程式提供單一端點或 URL，然後在內部將要求對應至內部微服務群組。 此路由功能有助於將用戶端應用程式從微服務分離，此外，它對於將整合型 API 改為新式 API 也非常方便，方法是將 API 閘道置於整合型 API 與用戶端應用程式之間，然後您可以新增 API 作為新的微服務，同時繼續使用舊的整合型 API，直到它於未來分割為許多微服務。 因為 API 閘道的關係，用戶端應用程式不會注意到使用的 API 是實作成內部微服務或整合型 API，而且更重要的是，當整合型 API 演進並重構成微服務時，因為有 API 閘道路由，用戶端應用程式不會受任何 URI 變更影響。

如需詳細資訊，請參閱[閘道路由模式](https://docs.microsoft.com/azure/architecture/patterns/gateway-routing)。

**要求彙總。** 在選擇閘道模式時，您可以將多個目標為多個內部微服務的用戶端要求 (通常是 HTTP 要求) 彙總成單一用戶端要求。 當用戶端頁面/畫面需要來自數個微服務的資訊時，此模式特別方便。 使用此方法時，用戶端應用程式會傳送單一要求至 API 閘道，此閘道會將數個要求分派到內部微服務，然後彙總結果並將所有資訊傳送回用戶端應用程式。 此設計模式主要的好處和目標是減少用戶端應用程式和後端 API 之間的交談，這對不在微服務所在的資料中心之遠端應用程式來說格外重要，如行動裝置應用程式，或來自用戶端遠端瀏覽器中 Javascript 的 SPA 應用程式發出的要求。 針對在伺服器環境中執行要求的一般 Web 應用程式 (如 ASP.NET Core MVC Web 應用程式) 來說，此模式就不是那麼重要，因為其延遲遠小於遠端用戶端應用程式。

視您使用的 API 閘道產品而定，它可能可以執行此彙總。 不過在許多情況下，於 API 閘道的範圍內建立彙總微服務會更有彈性，因此建議您在程式碼 (亦即 C# 程式碼) 中定義彙總：

如需詳細資訊，請參閱[閘道彙總模式](https://docs.microsoft.com/azure/architecture/patterns/gateway-aggregation)。

**跨領域考量或閘道卸載。** 視每個 API 閘道產品提供的功能而定，您可以將功能從個別微服務卸載，以藉由將跨領域考量合併至一個階層來簡化每個微服務的實作。 這對於要在每個內部微服務中正確實作會很複雜的特殊功能來說格外方便，例如以下功能：

- 驗證與授權
- 服務探索整合
- 回應快取
- 重試原則、斷路器和 QoS
- 速率限制和節流
- 負載平衡
- 記錄、追蹤、相互關聯
- 標頭、查詢字串和宣告轉換
- IP 允許清單

如需詳細資訊，請參閱[閘道卸載模式](https://docs.microsoft.com/azure/architecture/patterns/gateway-offloading)。

## <a name="using-products-with-api-gateway-features"></a>使用具備 API 閘道功能的產品

視每個實作而定，API 閘道產品可以提供更多跨領域考量。 我們會探討以下項目：

- [Azure API 管理](https://azure.microsoft.com/services/api-management/)
- [Ocelot](https://github.com/ThreeMammals/Ocelot)

### <a name="azure-api-management"></a>Azure API 管理

[Azure API 管理](https://azure.microsoft.com/services/api-management/) (如圖 4-14 所示) 不但可以解決您的 API 閘道需求，還能提供如從 API 收集見解等功能。 如果您使用 API 管理解決方案，則 API 閘道只是該完整 API 管理解決方案內的元件。

![Azure API 管理能夠解決您的 API 閘道和管理需求，例如記錄、安全性和計量等。](./media/api-gateway-azure-api-management.png)

**圖 4-14**. 將 Azure API 管理用於 API 閘道

在此情況下，使用 Azure API 管理這類產品時，您可能會有單一 API 閘道的這個事實的風險不大，因為這類 API 閘道較「輕量」，表示您未實作可能朝向整合型元件發展的自訂 C# 程式碼。 

API 閘道產品的作用通常像是連入通訊的反向 Proxy，您也可以篩選內部微服務的 API，以及在此單一階層中將授權套用至已發行的 API。

可從 API 管理系統取得的深入資訊可幫助您了解 API 使用方式和其執行方式。 作法是讓您檢視接近即時的分析報表，以及識別可能會影響您商務的趨勢。 此外，您可能會有要求和回應活動的記錄，以進行進一步線上及離線分析。

使用 Azure API 管理，您可以使用金鑰、權杖和 IP 篩選來保護 API。 這些功能可讓您強制執行彈性且微調的配額和速率限制、使用原則修改您 API 的形狀和行為，並改善快取回應的效能。

在本指南和參考範例應用程式 (eShopOnContainers) 中，架構會限制在較簡單且自訂容器化的架構，以專注於一般容器，而不需要使用 Azure API 管理這類 PaaS 產品。 但對於部署至 Microsoft Azure 的大型微服務型應用程式，建議您考慮以 API Azure API 管理作為生產環境中的 API 閘道基底。

### <a name="ocelot"></a>Ocelot

[Ocelot](https://github.com/ThreeMammals/Ocelot) 是輕量型 API 閘道，如需較簡單的方法建議加以採用。 Ocelot 是開放原始碼的 .NET Core 型 API 閘道，專門為需要系統統一進入點的微服務架構而設計。 它輕量、快速、可調整規模且提供路由和驗證等更多其他功能。

為 [eShopOnContainers 參考應用程式](https://github.com/dotnet-architecture/eShopOnContainers) \(英文\) 選擇 Ocelot 的原因是因為 Ocelot 為 .NET Core 輕量型 API 閘道，您可以將它部署到您所部署微服務/容器 (如 Docker 主機、Kubernetes 等) 的同一個應用程式部署環境。且因為它是以 .NET Core 為基礎，所以能跨平台，讓您可以部署在 Linux 或 Windows 上。

上面的圖表顯示在容器中執行的自訂 API 閘道，正如同您也可以在容器和微服務型應用程式中執行 Ocelot。

此外，市場上許多其他產品也都提供 API 閘道功能，例如 Apigee、Kong、MuleSoft、WSO2，以及提供服務網格連入控制器功能的 Linkerd 和 Istio 等產品。

在初始架構和模式探索的小節之後，以下各節說明如何搭配 [Ocelot](https://github.com/ThreeMammals/Ocelot) \(英文\) 實作 API 閘道。

## <a name="drawbacks-of-the-api-gateway-pattern"></a>API 閘道模式的缺點

- 最大的缺點在於當您實作 API 閘道時，會結合該階層與內部微服務。 這類結合可能會造成您應用程式的嚴重問題。 Clemens Vaster 是 Azure 服務匯流排小組的架構設計人員，在 GOTO 2016 的 [Messaging and Microservices](https://www.youtube.com/watch?v=rXi5CLjIQ9k) \(傳訊和微服務\) 研討會中將這個潛在困難稱為「新的 ESB」。

- 使用微服務 API 閘道會建立其他可能單一失敗點。

- API 閘道可能會導致因額外網路呼叫而增加回應時間。 不過，這個額外呼叫的影響通常會小於擁有過於頻繁直接呼叫內部微服務的用戶端介面。

- 如果未正確地相應放大，則 API 閘道可能會成為瓶頸。

- 如果 API 閘道包含自訂邏輯和資料彙總，則需要額外開發成本和未來維護。 開發人員必須更新 API 閘道，才能公開每個微服務的端點。 此外，內部微服務中的實作變更可能會導致 API 閘道層級的程式碼變更。 不過，如果 API 閘道只會套用安全性、記錄和版本控制 (就像使用 Azure API 管理時一樣)，可能不會套用這個額外的開發成本。

- 如果 API 閘道是由單一小組所開發，則可能會有開發瓶頸。 這是較佳方法是具有數個回應不同用戶端需求之微調 API 閘道的另一個原因。 您也可以在內部將 API 閘道區分為處理內部微服務之不同小組所擁有的多個區域或層級。

## <a name="additional-resources"></a>其他資源

- **Chris Richardson：模式：API 閘道/前端的後端** \
  <https://microservices.io/patterns/apigateway.html>

- **API 閘道模式** \
  <https://docs.microsoft.com/azure/architecture/microservices/gateway>

- **彙總和撰寫模式** \
  <https://microservices.io/patterns/data/api-composition.html>

- **Azure API 管理** \
  <https://azure.microsoft.com/services/api-management/>

- **Udi Dahan.Service Oriented Composition (服務導向組合)**  \
  <http://udidahan.com/2014/07/30/service-oriented-composition-with-video/>

- **Clemens Vasters：GOTO 2016 的傳訊和微服務 (影片)**  \
  <https://www.youtube.com/watch?v=rXi5CLjIQ9k>

- **API 閘道簡介** (ASP.net Core API 閘道教學課程系列)\
  <https://www.pogsdotnet.com/2018/08/api-gateway-in-nutshell.html>

>[!div class="step-by-step"]
>[上一頁](identify-microservice-domain-model-boundaries.md)
>[下一頁](communication-in-microservice-architecture.md)
