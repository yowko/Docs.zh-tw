---
title: REST 和 gRPC
description: 瞭解 gRPC、其在雲端原生應用程式中的角色，以及它與 HTTP REST 的差異
author: robvet
ms.date: 09/08/2019
ms.openlocfilehash: d888069168aee1fcfb13354f4b6f9ae2c8d1f233
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71214542"
---
# <a name="rest-and-grpc"></a>REST 和 gRPC

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

到目前為止，我們都著重于以[REST 為基礎的](https://docs.microsoft.com/azure/architecture/best-practices/api-design)通訊。 REST 是一種架構樣式，可提升分散式運算機系統之間的互通性。 它會使用要求/回應模型，其中來自伺服器的每個回應都是來自用戶端的要求。 雖然很普遍，但 REST 並不適合每個問題。 較新的通訊技術（有權 gRPC）會快速獲得普及，並使其進入雲端原生世界。

## <a name="grpc"></a>gRPC

gRPC 是源自 Google 的開放原始碼通訊。 它是以[遠端程序呼叫（RPC）](https://en.wikipedia.org/wiki/Remote_procedure_call)模型為基礎，在分散式運算中很熱門。 在此模型之後，本機用戶端程式會公開同進程方法來執行作業。 在幕後，會在跨分散式網路的跨進程微服務上叫用該呼叫。 開發人員將作業編碼為本機程序呼叫。 基礎平臺會將點對點網路通訊、序列化和執行抽象化。

gRPC 是現代化的 RPC 架構，它既輕量又高效能。 它會使用 HTTP/2 作為其傳輸通訊協定。 與 HTTP 1.1 相容，HTTP/2 具備許多先進的功能：

- HTTP 1.1 以純文字傳送資料時，HTTP/2 是二進位通訊協定。 它會使用較少的記憶體，更快地剖析資料、降低網路延遲與速度的相關改善，以及更有效率地管理網路資源。
- 雖然 HTTP 1.1 限制為一次處理一個往返的要求/回應，但 HTTP/2 支援多工傳送，或透過相同連線的多個平行要求。
- HTTP/2 支援全雙工或雙向通訊，其中用戶端和伺服器都可以同時進行通訊。 用戶端可以在伺服器送迴響應資料時，同時上傳要求資料。
- 串流內建于 HTTP/2，這表示要求和回應都可以非同步地串流處理大型資料集。
- 結合 gRPC 和 HTTP/2，效能會大幅增加。 在[Windows Communication Foundation （WCF）](https://docs.microsoft.com/dotnet/framework/wcf/whats-wcf)用語中中，gPRC 效能符合並超過[NetTCP](https://docs.microsoft.com/dotnet/api/system.servicemodel.nettcpbinding?view=netframework-4.8)系結的速度和效率。 不過，不同于 NetTCP，gRPC 不受限於 Microsoft 語言， C#例如或 VB.NET。

跨最受歡迎的平臺（包括 JAVA、 C#、Golang 和 NodeJS）都支援 gRPC。 

## <a name="protocol-buffers"></a>通訊協定緩衝區

gRPC 採用另一種稱為[通訊協定緩衝區](https://developers.google.com/protocol-buffers/docs/overview)或 Protobuf 訊息的開放原始碼技術，來傳送和接收資料。 類似于[WCF 資料合約](https://docs.microsoft.com/dotnet/framework/wcf/feature-details/using-data-contracts)，Protobuf 會將系統的結構化資料序列化，以便進行讀取和寫入。 它可降低人類看得懂的格式（例如 XML 或 JSON）所產生的額外負荷。

許多物件序列化技術在執行時間會反映在資料物件的結構上。 Protobuf 需要您預先定義具有平臺中立語言（通訊協定緩衝區語言）的結構。 每個定義都會儲存在「. proto」檔案中。 然後使用 Protobuf 編譯器「Proton」，為任何支援的平臺產生用戶端和伺服器程式碼。 產生的程式碼已針對資料的快速序列化/還原序列化進行優化。 在執行時間，每個訊息都會包裝在強型別服務合約中，並以標準的 Protobuf 標記法進行序列化。

## <a name="grpc-support-in-net"></a>.NET 中的 gRPC 支援

Microsoft .NET Core framework 3.0 包含 gRPC 的工具和原生支援。 圖4-20 顯示的 Visual Studio 2019 範本會 scaffold gRPC 服務的 gRPC 基本架構專案。 請注意 .NET Core 如何支援 Windows、Linux、macOS 平臺。

![Visual Studio 2019 中的 gRPC 支援](./media/visual-studio-2019-grpc-template.png)

**圖 4-20**： Visual Studio 2019 中的 gRPC 支援

.NET Core 3.0 順暢地將 gRPC 整合到其架構中，包括端點路由、內建 IoC 支援和記錄。 開放原始碼 Kestrel web 伺服器完全支援 HTTP/2 連接。 

圖4-21 顯示 Visual Studio 2019 中的 gRPC 服務結構。 請注意資料夾結構如何包含適用于 proto 檔案和服務程式代碼的資料夾。

![Visual Studio 2019 中的 gRPC 專案](./media/grpc-project.png  )

**圖 4-21**： Visual Studio 2019 中的 gRPC 專案

## <a name="gprc-usage"></a>gPRC 使用方式

gRPC 適用于下列案例：

- 低延遲和高輸送量的通訊。 gRPC 非常適合用於效率非常重要的輕量微服務。
- 點對點即時通訊。 gRPC 有絕佳的雙向串流支援。 gRPC 服務可以即時推播訊息，而不需要輪詢。
- 多語言環境– gRPC 工具支援最熱門的開發語言，使其成為多語言環境的理想選擇。
- 網路限制環境– gRPC 訊息會使用 Protobuf （輕量訊息格式）進行序列化。 GRPC 訊息一律會小於對等的 JSON 訊息。

在撰寫本書時，大部分的瀏覽器對於 gRPC 的支援有限。 gRPC 大量使用 HTTP/2 功能，而且沒有瀏覽器提供 web 要求所需的控制層級來支援 gRPC 用戶端。 gRPC 通常用於內部微服務以微服務通訊。 圖4-22 顯示簡單但常見的使用模式。

![gRPC 使用模式](./media/grpc-usage.png)

**圖 4-22**。 gRPC 使用模式

請注意，上圖中的前端流量會以 HTTP 叫用，而後端微服務至微服務會使用 gRPC。

期待 gRPC，在 dethroning 雲端原生系統的 REST 支配方面，可能扮演著重要的角色。 效能優勢和開發的便利性也太好了。 不過，請不要犯任何錯誤，其餘部分仍會持續一段時間。 它仍然是針對公開公開的 Api 擅長，基於回溯相容性的理由。 

>[!div class="step-by-step"]
>[上一頁](service-to-service-communication.md)
>[下一頁](service-mesh-communication-infrastructure.md)
