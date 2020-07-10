---
title: gRPC
description: 瞭解 gRPC、其在雲端原生應用程式中的角色，以及它與 HTTP RESTful 通訊有何不同。
author: robvet
no-loc:
- Blazor
- Blazor WebAssembly
ms.date: 05/13/2020
ms.openlocfilehash: 6b41363008405032f4233448f134a8a602dbd26a
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173155"
---
# <a name="grpc"></a>gRPC

到目前為止，我們都著重于以[REST 為基礎的](https://docs.microsoft.com/azure/architecture/best-practices/api-design)通訊。 我們已瞭解 REST 是彈性的架構樣式，其定義以 CRUD 為基礎的實體資源作業。 用戶端會使用要求/回應通訊模型，透過 HTTP 與資源互動。 雖然 REST 已廣泛實行，但較新的通訊技術 gRPC 在雲端原生的社區獲得了巨大的動力。

## <a name="what-is-grpc"></a>什麼是 gRPC？

gRPC 是一種現代化、高效能的架構，會 (RPC) 通訊協定來演變過時的[遠端程序呼叫](https://en.wikipedia.org/wiki/Remote_procedure_call)。 在應用層級，gRPC 會簡化用戶端和後端服務之間的訊息處理。 源自 Google、gRPC 是開放原始碼，而[雲端原生運算基礎](https://www.cncf.io/)的一部分， (由 cncf 雲端原生供應專案的) 生態系統。 由 CNCF 會將 gRPC 視為[發展專案](https://github.com/cncf/toc/blob/master/process/graduation_criteria.adoc)。 發展表示終端使用者在生產應用程式中使用此技術，而專案的參與者數目良好。

一般的 gRPC 用戶端應用程式會公開可執行商務作業的本機、同進程函式。 實際上，該區域函式會在遠端電腦上叫用另一個函式。 所謂的本機呼叫基本上會成為對遠端服務的透明跨進程呼叫。 RPC 配會將點對點網路通訊、序列化和電腦之間的執行抽象化。

在雲端原生應用程式中，開發人員通常可以跨程式設計語言、架構和技術來工作。 此*互通性*會使訊息合約和跨平臺通訊所需的管道變得複雜。  gRPC 提供「統一水準層」，可將這些考慮抽象化。 開發人員在其原生平臺中撰寫著重于商務功能的程式碼，而 gRPC 則會處理通訊。

gRPC 在最熱門的開發堆疊中提供全方位的支援，包括 JAVA、JavaScript、c #、Go、Swift 和 NodeJS。

## <a name="grpc-benefits"></a>gRPC 權益

gRPC 會使用 HTTP/2 作為其傳輸通訊協定。 與 HTTP 1.1 相容，HTTP/2 具備許多先進的功能：

- 用於資料傳輸的二進位通訊協定-與 HTTP 1.1 不同，後者會以純文字傳送資料。
- 多工支援透過相同的連接傳送多個平行要求-HTTP 1.1 限制一次處理一個要求/回應訊息。
- 雙向的全雙工通訊，可同時傳送用戶端要求和伺服器回應。
- 內建串流功能，可讓要求和回應以非同步方式串流處理大型資料集。

gRPC 是輕量且高效能。 其最高可比 JSON 序列化更快，且訊息60-80% 較小。 在 Microsoft [Windows Communication Foundation 中 (WCF) ](https://docs.microsoft.com/dotnet/framework/wcf/whats-wcf)用語中，gRPC 效能超過高度優化[NetTCP](https://docs.microsoft.com/dotnet/api/system.servicemodel.nettcpbinding?view=netframework-4.8)系結的速度和效率。 不同于 NetTCP，這是 Microsoft stack 的優先，gRPC 是跨平臺。

## <a name="protocol-buffers"></a>通訊協定緩衝區

gRPC 採用稱為[通訊協定緩衝區](https://developers.google.com/protocol-buffers/docs/overview)的開放原始碼技術。 它們提供高度有效率和平臺中立的序列化格式，以便將服務傳送至彼此的結構化訊息進行序列化。 使用跨平臺介面定義語言 (IDL) ，開發人員會針對每個微服務定義服務合約。 合約（實作為以文字為基礎的檔案 `.proto` ）會說明每個服務的方法、輸入和輸出。 相同的合約檔案可以用於 gRPC 在不同開發平臺上建立的用戶端和服務。

使用 proto 檔案（Protobuf 編譯器），會 `protoc` 為您的目標平臺產生用戶端和服務程式代碼。 程式碼包含下列元件：

- 由用戶端和服務共用的強型別物件，代表訊息的服務作業和資料元素。
- 具有遠端 gRPC 服務可繼承和擴充之必要網路配管的強型別基類。
- 用戶端存根，其中包含叫用遠端 gRPC 服務所需的管道。

在執行時間，每個訊息會序列化為標準的 Protobuf 標記法，並在用戶端與遠端服務之間交換。 不同于 JSON 或 XML，Protobuf 訊息會序列化為已編譯的二進位位元組。

[GRPC FOR WCF 開發人員](https://docs.microsoft.com/dotnet/architecture/grpc-for-wcf-developers/)（可從 Microsoft 架構網站取得）提供 GRPC 和通訊協定緩衝區的深入涵蓋範圍。

## <a name="grpc-support-in-net"></a>.NET 中的 gRPC 支援

gRPC 已整合到 .NET Core 3.0 SDK 和更新版本中。 下列工具支援它：

- Visual Studio 2019、16.3 版或更新版本，並已安裝 網頁程式開發工作負載。
- Visual Studio Code
- dotnet CLI

SDK 包含端點路由、內建 IoC 和記錄的工具。 開放原始碼 Kestrel web 伺服器支援 HTTP/2 連接。 圖4-20 顯示的 Visual Studio 2019 範本會 scaffold gRPC 服務的基本架構專案。 請注意 .NET Core 如何完全支援 Windows、Linux 和 macOS。

![Visual Studio 2019 中的 gRPC 支援](./media/visual-studio-2019-grpc-template.png)

**圖 4-20**： Visual Studio 2019 中的 gRPC 支援
  
圖4-21 顯示從 Visual Studio 2019 所包含的內建樣板產生的基本架構 gRPC 服務。  

![Visual Studio 2019 中的 gRPC 專案](./media/grpc-project.png  )

**圖 4-21**： Visual Studio 2019 中的 gRPC 專案

在上圖中，請注意 proto 描述檔案和服務程式代碼。 您很快就會看到，Visual Studio 會在啟動類別和基礎專案檔案中產生額外的設定。

## <a name="grpc-usage"></a>gRPC 使用方式

在下列案例中偏好 gRPC：

- 同步後端微服務對微服務通訊，其中需要立即回應才能繼續處理。
- 多語言需要支援混合程式設計平臺的環境。
- 效能非常重要的低延遲和高輸送量通訊。
- 點對點即時通訊-gRPC 可以即時推播訊息，而不需輪詢，而且具有雙向串流的絕佳支援。
- 網路限制環境–二進位 gRPC 訊息一律會小於對等的以文字為基礎的 JSON 訊息。

在撰寫本文時，gRPC 主要是與後端服務搭配使用。 大部分的新式瀏覽器無法提供支援前端 gRPC 用戶端所需的 HTTP/2 控制層級。 話雖如此，還有一個[早期的計畫](https://devblogs.microsoft.com/aspnet/grpc-web-experiment/)，可以讓以 JavaScript 或技術建立的瀏覽器型應用程式進行 gRPC 通訊 Blazor WebAssembly 。 [適用于 .net 的 GRPC Web](https://github.com/grpc/grpc/blob/master/doc/PROTOCOL-WEB.md)可讓 ASP.NET Core gRPC 應用程式支援瀏覽器應用程式中的 gRPC 功能：

- 強型別、程式碼產生的用戶端
- Compact Protobuf 訊息
- 伺服器串流

## <a name="grpc-implementation"></a>gRPC 執行

微服務參考架構（由 Microsoft[在容器上 eShop](https://github.com/dotnet-architecture/eShopOnContainers)）示範如何在 .net Core 應用程式中執行 gRPC 服務。 圖4-22 顯示後端架構。

![容器上的 eShop 後端架構](./media/eshop-with-aggregators.png)

**圖 4-22**。 容器上的 eShop 後端架構

在上圖中，請注意 eShop 如何藉由公開多個 API 閘道，[來為前端模式提供後端](https://docs.microsoft.com/azure/architecture/patterns/backends-for-frontends) (BFF) 。 我們在本章稍早討論過 BFF 模式。 請密切注意位於 Web 購物 API 閘道與後端購物微服務之間的灰色) 的匯總工具微服務 (。 匯總工具會接收來自用戶端的單一要求、將其分派至各種微服務、匯總結果，並將其傳回給要求的用戶端。 這類作業通常需要同步通訊，才能產生立即回應。 在 eShop 中，會使用 gRPC 來執行來自匯總工具的後端呼叫，如圖4-23 所示。

![容器上 eShop 中的 gRPC](./media/grpc-implementation.png)

**圖 4-23**： 容器上 eShop 中的 gRPC

gRPC 通訊需要用戶端和伺服器元件。 在上圖中，請注意購物匯總工具如何實行 gRPC 用戶端。 用戶端會進行同步 gRPC 呼叫， (以 red) 對後端微服務，每個都會執行 gRPC 伺服器。 用戶端和伺服器都利用來自 .NET Core SDK 的內建 gRPC 配管。 用戶端*stub*提供了用來叫用遠端 gRPC 呼叫的管道。 伺服器端元件提供自訂服務類別可以繼承和使用的 gRPC 配管。

公開 RESTful API 和 gRPC 通訊的微服務需要多個端點來管理流量。 您會開啟一個端點，以接聽 RESTful 呼叫的 HTTP 流量，另一個用於 gRPC 呼叫。 GRPC 端點必須針對 gRPC 通訊所需的 HTTP/2 通訊協定進行設定。

雖然我們致力於將微服務與非同步通訊模式分離，但某些作業需要直接呼叫。 gRPC 應該是微服務之間直接同步通訊的主要選擇。 其高效能通訊協定（根據 HTTP/2 和通訊協定緩衝區）讓它成為最佳選擇。

## <a name="looking-ahead"></a>展望未來

在未來，gRPC 會繼續為雲端原生系統取得吸引力。 效能優勢和開發的便利性很吸引人。 不過，REST 可能會有很長一段時間。 它會針對公開公開的 Api 和回溯相容性的理由而擅長。

>[!div class="step-by-step"]
>[上一個](service-to-service-communication.md) 
>[下一步](service-mesh-communication-infrastructure.md)
