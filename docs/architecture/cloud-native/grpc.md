---
title: gRPC
description: 瞭解 gRPC 及其在雲原生應用程式中的角色,以及它與 HTTP RESTful 通信有何不同。
author: robvet
ms.date: 03/31/2020
ms.openlocfilehash: 28a07ad5ec105d3fc5b65e4cf0ac0cd85eb16627
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2020
ms.locfileid: "80524170"
---
# <a name="grpc"></a>gRPC

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

到目前為止,在這本書中,我們專注於[基於REST](https://docs.microsoft.com/azure/architecture/best-practices/api-design)的溝通。 我們已經看到 REST 是一種靈活的體系結構風格,它根據實體資源定義基於 CRUD 的操作。 用戶端使用請求/回應通信模型跨 HTTP 與資源進行交互。 雖然 REST 得到了廣泛實施,但一種較新的通信技術 gRPC 在整個雲原生社區中獲得了巨大的發展勢頭。

## <a name="what-is-grpc"></a>什麼是 gRPC?

gRPC 是一個現代的高性能框架,它發展古老的[遠端過程調用 (RPC)](https://en.wikipedia.org/wiki/Remote_procedure_call)協定。 在應用程式級別,gRPC 簡化了用戶端和後端服務之間的消息傳遞。 gRPC 源自 Google,是雲[原生產品雲原生計算基礎 (CNCF)](https://www.cncf.io/)生態系統的一部分。 CNCF認為gRPC是一個[孵化專案](https://github.com/cncf/toc/blob/master/process/graduation_criteria.adoc)。 孵化意味著最終使用者在生產應用程式中使用該技術,並且專案具有大量貢獻者。

典型的 gRPC 用戶端應用將公開實現業務操作的本地進程內函數。 在封面下,該本地函數調用遠程電腦上的另一個函數。 看似本地呼叫的內容實質上變成了對遠端服務的透明進程外調用。 RPC 管道抽象了計算機之間的點對點網路通信、序列化和執行。

在雲原生應用程式中,開發人員通常跨程式設計語言、框架和技術工作。 這種*互操作性*使消息協定和跨平臺通信所需的管道複雜化。  gRPC 提供了一個"統一的水準層",用於抽象這些關注點。 開發人員在其本機平臺中的代碼側重於業務功能,而 gRPC 處理通信管道。

gRPC 在最流行的開發堆疊中提供全面支援,包括 JAVA、JAvaScript、C#、Go、Swift 和 NodeJS。

## <a name="grpc-benefits"></a>gRPC 優勢

gRPC 使用 HTTP/2 進行傳輸協定。 雖然 HTTP/2 與 HTTP 1.1 相容,但具有許多高級功能:

- 用於資料傳輸的二進位協定 - 與 HTTP 1.1 不同,HTTP 1.1 以明文形式發送數據。
- 跨行支援通過同一連接發送多個並行請求 - HTTP 1.1 將處理限制為一次一個請求/回應消息。
- 雙向全雙工通信,用於同時發送用戶端請求和伺服器回應。
- 內置流式處理,支援對非同步串流大型資料集的請求和回應。

gRPC 重量輕,性能高。 與 JSON 序列化相比,其速度可能高達 8 倍,消息小 60-80%。 用微軟[視窗通訊基金會(WCF)](https://docs.microsoft.com/dotnet/framework/wcf/whats-wcf)的話說,gRPC性能超過了高度優化的[NetTCP 綁定](https://docs.microsoft.com/dotnet/api/system.servicemodel.nettcpbinding?view=netframework-4.8)的速度和效率。 與支援微軟堆疊的 NetTCP 不同,gRPC 是跨平臺的。

## <a name="protocol-buffers"></a>通訊協定緩衝區

gRPC 採用一種稱為[協定緩衝區的](https://developers.google.com/protocol-buffers/docs/overview)開源技術。 它們為序列化服務相互發送的結構化消息提供了高效且平臺中立的序列化格式。 使用跨平臺介面定義語言 (IDL),開發人員為每個微服務定義服務協定。 協定作為基於`.proto`文本的文件實現,描述每個服務的方法、輸入和輸出。 相同的合同檔可用於在不同開發平臺上構建的 gRPC 客戶端和服務。

使用 proto 檔案 Protobuf`protoc`編譯器 ,為您的目標平臺生成用戶端和服務代碼。 該代碼包括以下元件:

- 由用戶端和服務共用的強類型物件,表示消息的服務操作和數據元素。
- 具有遠端 gRPC 服務可以繼承和擴展所需的網路管道的強類型基類。
- 包含調用遠端 gRPC 服務所需的管道的用戶端存根。

在運行時,每條消息都序列化為標準 Protobuf 表示形式,並在用戶端和遠端服務之間交換。 與 JSON 或 XML 不同,Protobuf 消息被序列化為編譯的二進位元組。

該書名為[gRPC,適用於 WCF 開發人員](https://docs.microsoft.com/dotnet/architecture/grpc-for-wcf-developers/),可從 Microsoft 體系結構網站獲得,提供 gRPC 和協定緩衝區的深入覆蓋。

## <a name="grpc-support-in-net"></a>gRPC 支援 .NET

gRPC 整合到 .NET 核心 3.0 SDK 或更高版本中。 以下工具支援它:

- Visual Studio 2019,版本 16.3 或更高版本,安裝了 Web 開發工作負載。
- Visual Studio Code
- 點網 CLI

SDK 包括用於端點路由、內建 IoC 和日誌記錄的工具。 開源 Kestrel Web 伺服器支援 HTTP/2 連接。 圖 4-20 顯示了 Visual Studio 2019 範本,該範本為 gRPC 服務的腳架式骨架專案提供了支架。 請注意 .NET Core 如何完全支援 Windows、Linux 和 macOS。

![gRPC 支援視覺工作室 2019](./media/visual-studio-2019-grpc-template.png)

**圖 4-20**： gRPC 支援視覺工作室 2019
  
圖 4-21 顯示了從 Visual Studio 2019 中包含的內建基架生成的骨架 gRPC 服務。  

![gRPC 專案在視覺工作室 2019](./media/grpc-project.png  )

**圖 4-21**： gRPC 專案在視覺工作室 2019

在上圖中,請注意原型描述檔和服務代碼。 正如您稍後看到的,Visual Studio 會在啟動類和基礎專案檔中生成其他配置。

## <a name="grpc-usage"></a>gRPC 使用方式

以下方案有利於 gRPC:

- 同步後端微服務到微服務通信,需要立即回應才能繼續處理。
- 需要支援混合程式設計平臺的多面體環境。
- 低延遲和高吞吐量通信,其中性能至關重要。
- 點對點即時通信 - gRPC 無需輪詢即可即時推送消息,並且對雙向流流具有出色的支援。
- 網路受限環境 – 二進位 gRPC 消息始終小於等效的基於文本的 JSON 消息。

在撰寫本文時,gRPC 主要用於後端服務。 大多數現代瀏覽器無法提供支援前端 gRPC 用戶端所需的 HTTP/2 控制級別。 也就是說,有一[個早期計劃](https://devblogs.microsoft.com/aspnet/grpc-web-experiment/),支援 gRPC 通信從基於瀏覽器的應用程式構建與 JavaScript 或 Blazor WebAssembly 技術。 [gRPC-Web 表示 .NET,](https://github.com/grpc/grpc/blob/master/doc/PROTOCOL-WEB.md)支援ASP.NET核心 gRPC 應用,以支援瀏覽器應用中的 gRPC 功能:

- 強類型代碼產生的用戶端
- 緊湊型 Protobuf 訊息
- 伺服器流程處理

## <a name="grpc-implementation"></a>gRPC 實現

微軟的微服務參考體系結構[,即容器上的eShop,](https://github.com/dotnet-architecture/eShopOnContainers)展示了如何在 .NET Core 應用程式中實現 gRPC 服務。 圖 4-22 顯示了後端體系結構。

![容器上 eShop 的後端結構](./media/eshop-with-aggregators.png)

**圖 4-22**。 容器上 eShop 的後端結構

在上圖中,請注意 eShop 如何通過公開多個 API 閘道來擁抱[前端模式](https://docs.microsoft.com/azure/architecture/patterns/backends-for-frontends)(BFF) 的後端。 本章前面討論了 BFF 模式。 密切關注位於 Web 購物 API 閘道和後端購物微服務之間的聚合器微服務(灰色)。 聚合器接收來自用戶端的單個請求,將其調度到各種微服務,聚合結果,並將它們發送回請求用戶端。 此類操作通常需要同步通信才能立即產生回應。 在 eShop 中,聚合器的後端調用使用 gRPC 執行,如圖 4-23 所示。

![gRPC 在容器上的 eShop 中](./media/grpc-implementation.png)

**圖 4-23**： gRPC 在容器上的 eShop 中

gRPC 通訊需要用戶端和伺服器元件。 在上圖中,請注意購物聚合器如何實現 gRPC 用戶端。 用戶端對後端微服務進行同步 gRPC 調用(紅色),每個微服務都實現 gRPC 伺服器。 用戶端和伺服器都利用了 .NET Core 3.0 SDK 的內建 gRPC 管道。 用戶端*存根*提供調用遠端 gRPC 調用的管道。 伺服器端元件提供自定義服務類可以繼承和使用 gRPC 管道。

公開 RESTful API 和 gRPC 通訊的微服務需要多個終結點來管理流量。 您將打開一個終結點,用於偵聽呼叫的 HTTP 流量,為 gRPC 呼叫打開另一個終結點。 gRPC 終結點必須配置為 gRPC 通訊所需的 HTTP/2 協定。

儘管我們努力使微服務與非同步通信模式分離,但某些操作需要直接調用。 gRPC 應該是微服務之間直接同步通信的主要選擇。 基於 HTTP/2 和協定緩衝區的高性能通訊協定使其成為一個完美的選擇。

## <a name="looking-ahead"></a>展望未來

展望未來,gRPC將繼續為雲本機系統贏得牽引力。 性能優勢和易於開發是引人注目的。 但是,REST 可能會出現很長時間。 它擅長公開公開的 API 和向後相容性原因。

>[!div class="step-by-step"]
>[前一個](service-to-service-communication.md)
>[下一個](service-mesh-communication-infrastructure.md)
