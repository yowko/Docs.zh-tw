---
title: gRPC
description: 瞭解 gRPC、其在雲端原生應用程式中的角色，以及它與 HTTP RESTful 通訊的不同之處。
author: robvet
no-loc:
- Blazor
- Blazor WebAssembly
ms.date: 05/13/2020
ms.openlocfilehash: 9ed6906bd388a1ddef7f97bbaac001b4274853f9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158080"
---
# <a name="grpc"></a>gRPC

到目前為止，我們將著重于以 [REST 為基礎](/azure/architecture/best-practices/api-design) 的通訊。 我們已瞭解 REST 是一種彈性的架構樣式，可針對實體資源定義 CRUD 作業。 用戶端會使用要求/回應通訊模型，在 HTTP 之間與資源互動。 雖然 REST 已廣泛實行，但較新的通訊技術 gRPC，在雲端原生的全球各地獲得了巨大的動力。

## <a name="what-is-grpc"></a>什麼是 gRPC？

gRPC 是現代化、高效能的架構， (RPC) 通訊協定來發展舊的 [遠端程序呼叫 ](https://en.wikipedia.org/wiki/Remote_procedure_call) 。 在應用層級，gRPC 可簡化用戶端與後端服務之間的訊息傳遞。 從 Google 開始，gRPC 是開放原始碼和  [雲端原生運算基礎 ](https://www.cncf.io/) 的一部分， (CNCF 雲端原生供應專案的) 生態系統。 CNCF 會考慮 gRPC [發展專案](https://github.com/cncf/toc/blob/master/process/graduation_criteria.adoc)。 發展表示終端使用者在生產應用程式中使用此技術，而專案的參與者數目狀況良好。

一般的 gRPC 用戶端應用程式會公開本機的同進程函數，以執行商務作業。 在幕後，該區域函數會叫用遠端電腦上的另一個函式。 所謂的本機呼叫基本上會成為遠端服務的透明跨進程呼叫。 RPC 檢測會將點對點網路通訊、序列化以及電腦之間的執行抽象化。

在雲端原生應用程式中，開發人員通常可以跨程式設計語言、架構和技術。 這種 *互通性* 會使訊息合約和跨平臺通訊所需的管道變得更複雜。  gRPC 會提供「統一水準圖層」，以摘要說明這些考慮。 開發人員在其原生平臺中撰寫的程式碼著重于商務功能，而 gRPC 會處理通訊管道。

gRPC 為最受歡迎的開發堆疊提供完整的支援，包括 JAVA、JavaScript、c #、Go、Swift 和 NodeJS。

## <a name="grpc-benefits"></a>gRPC 權益

gRPC 會針對其傳輸通訊協定使用 HTTP/2。 與 HTTP 1.1 相容時，HTTP/2 有許多先進的功能：

- 用於資料傳輸的二進位框架通訊協定，與以文字為基礎的 HTTP 1.1 不同。
- 透過相同連線傳送多個平行要求的多工支援-HTTP 1.1 一次會將處理限制為一個要求/回應訊息。
- 雙向全雙工通訊，可同時傳送用戶端要求和伺服器回應。
- 內建串流，可讓要求和回應以非同步方式串流處理大型資料集。
- 減少網路使用量的標頭壓縮。

gRPC 是輕量且高效能。 其最多可比 JSON 序列化更快，且訊息60-80% 較小。 在 Microsoft [Windows Communication Foundation (WCF) ](../../framework/wcf/whats-wcf.md) 說法中，gRPC 效能超過高度優化 [NetTCP](/dotnet/api/system.servicemodel.nettcpbinding?view=netframework-4.8)系結的速度和效率。 不同于 NetTCP （喜好 Microsoft stack），gRPC 是跨平臺。

## <a name="protocol-buffers"></a>通訊協定緩衝區

gRPC 採用稱為 [通訊協定緩衝區](https://developers.google.com/protocol-buffers/docs/overview)的開放原始碼技術。 它們提供高效率且與平臺無關的序列化格式，可將服務傳送給彼此的結構化訊息進行序列化。 使用跨平臺介面定義語言 (IDL) ，開發人員會定義每個微服務的服務合約。 合約（實作為以文字為基礎的檔案 `.proto` ）會描述每個服務的方法、輸入和輸出。 相同的合約檔案可以用來 gRPC 以不同開發平臺為基礎的用戶端和服務。

Protobuf 編譯器會使用 proto 檔案， `protoc` 為您的目標平臺產生用戶端和服務程式代碼。 此程式碼包含下列元件：

- 用戶端和服務所共用的強型別物件，代表訊息的服務作業和資料元素。
- 強型別基類，具有遠端 gRPC 服務可以繼承和擴充的必要網路配管。
- 用戶端存根，包含叫用遠端 gRPC 服務所需的管線。

在執行時間，每個訊息都會序列化為標準 Protobuf 標記法，並在用戶端與遠端服務之間交換。 不同于 JSON 或 XML，Protobuf 訊息會序列化為編譯的二進位位元組。

Microsoft 架構網站提供的 [WCF 開發人員 gRPC](../grpc-for-wcf-developers/index.md)書籍，提供 GRPC 和通訊協定緩衝區的深入探討。

## <a name="grpc-support-in-net"></a>.NET 中的 gRPC 支援

gRPC 已整合到 .NET Core 3.0 SDK 和更新版本中。 以下是支援的工具：

- 已安裝 網頁程式開發工作負載的 Visual Studio 2019 16.3 版或更新版本。
- Visual Studio Code
- dotnet CLI

SDK 包含用於端點路由、內建 IoC 和記錄的工具。 開放原始碼 Kestrel web 伺服器支援 HTTP/2 連接。 圖4-20 顯示的 Visual Studio 2019 範本會 scaffold gRPC 服務的基本架構專案。 請注意 .NET Core 如何完全支援 Windows、Linux 和 macOS。

![Visual Studio 2019 中的 gRPC 支援](./media/visual-studio-2019-grpc-template.png)

**圖 4-20**： Visual Studio 2019 中的 gRPC 支援
  
圖4-21 顯示的基本架構 gRPC 服務是由 Visual Studio 2019 中包含的內建架構所產生。  

![Visual Studio 2019 中的 gRPC 專案](./media/grpc-project.png  )

**圖 4-21**： Visual Studio 2019 中的 gRPC 專案

在上圖中，請注意 proto 描述檔案和服務程式代碼。 您很快就會看到，Visual Studio 會在啟動類別和基礎專案檔中產生額外的設定。

## <a name="grpc-usage"></a>gRPC 使用方式

適用于下列案例的 gRPC：

- 同步後端微服務對微服務通訊，需要立即回應才能繼續處理。
- 多語言需要支援混合式程式設計平臺的環境。
- 效能至關重要的低延遲和高輸送量通訊。
- 點對點即時通訊-gRPC 可以即時推播訊息，而不需要輪詢，並且對雙向串流有絕佳的支援。
- 網路受限的環境–二進位 gRPC 訊息一律小於相等的文字型 JSON 訊息。

在撰寫本文時，gRPC 主要是與後端服務搭配使用。 新式瀏覽器無法提供支援前端 gRPC 用戶端所需的 HTTP/2 控制層級。 話雖如此， [GRPC Web 與 .net](https://devblogs.microsoft.com/aspnet/grpc-web-for-net-now-available/) 的支援可讓您從以 JavaScript 或技術為基礎的瀏覽器型應用程式進行 gRPC 通訊 Blazor WebAssembly 。 [GRPC Web](https://github.com/grpc/grpc/blob/master/doc/PROTOCOL-WEB.md) 可讓 ASP.NET Core gRPC 應用程式支援瀏覽器應用程式中的 gRPC 功能：

- 強型別，程式碼產生的用戶端
- Compact Protobuf 訊息
- 伺服器串流

## <a name="grpc-implementation"></a>gRPC 執行

Microsoft 的 [容器上 eShop](https://github.com/dotnet-architecture/eShopOnContainers)的微服務參考架構會顯示如何在 .net Core 應用程式中執行 gRPC 服務。 圖4-22 提供後端架構。

![容器上 eShop 的後端架構](./media/eshop-with-aggregators.png)

**圖 4-22**。 容器上 eShop 的後端架構

在上圖中，請注意 eShop 如何藉由公開多個 API 閘道，來將 [前端模式的後端](/azure/architecture/patterns/backends-for-frontends) 帶 (BFF) 。 本章節稍早討論過 BFF 模式。 請密切注意位於 Web 購物 API 閘道與後端購物微服務之間的灰色)  (。 匯總工具會接收來自用戶端的單一要求、將其分派至各種微服務、匯總結果，並將其傳回給提出要求的用戶端。 這類作業通常需要同步通訊，以產生立即回應。 在 eShop 中，會使用 gRPC 來執行來自匯總者的後端呼叫，如圖4-23 所示。

![容器上 eShop 中的 gRPC](./media/grpc-implementation.png)

**圖 4-23**： 容器上 eShop 中的 gRPC

gRPC 通訊需要用戶端和伺服器元件。 在上圖中，請注意購物匯總工具如何實行 gRPC 用戶端。 用戶端會進行同步的 gRPC 呼叫， (以紅色) 至後端微服務，每個都會執行 gRPC 伺服器。 用戶端和伺服器都利用 .NET Core SDK 的內建 gRPC。 用戶端 *存根* 提供可叫用遠端 gRPC 呼叫的管道。 伺服器端元件提供自訂服務類別可以繼承和使用的 gRPC 配管。

公開 RESTful API 和 gRPC 通訊的微服務需要多個端點來管理流量。 您會開啟一個端點，接聽 RESTful 呼叫的 HTTP 流量，另一個用於 gRPC 呼叫。 必須針對 gRPC 通訊所需的 HTTP/2 通訊協定設定 gRPC 端點。

雖然我們致力於將微服務與非同步通訊模式分離，但有些作業需要直接呼叫。 gRPC 應該是微服務之間直接同步通訊的主要選擇。 它是以 HTTP/2 和通訊協定緩衝區為基礎的高效能通訊協定，讓它成為絕佳的選擇。

## <a name="looking-ahead"></a>展望

GRPC 會繼續為雲端原生系統提供吸引力。 效能優勢和開發的便利性很吸引人。 不過，REST 可能會很長一段時間。 它擅長公開的 Api，並基於回溯相容性的理由。

>[!div class="step-by-step"]
>[上一個](service-to-service-communication.md) 
>[下一步](service-mesh-communication-infrastructure.md)
