---
title: 為什麼我們為 WCF 開發人員推薦 gRPC - gRPC 面向 WCF 開發人員
description: 討論 gRPC 為什麼非常適合想要遷移到現代體系結構和平臺的 WCF 開發人員。
ms.date: 09/02/2019
ms.openlocfilehash: 664781e94c24c1796eafa6a70eb28d453b530d66
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147642"
---
# <a name="why-we-recommend-grpc-for-wcf-developers"></a>為何我們為 WCF 開發人員建議 gRPC

在我們深入探討 gRPC 的語言和技術之前，值得討論為什麼 gRPC 是 Windows 通信基礎 （WCF） 開發人員想要遷移到 .NET Core 的正確解決方案。

## <a name="similarity-to-wcf"></a>與 WCF 的相似性

儘管 gRPC 的實現和方法不同，但使用 gRPC 開發和使用服務的經驗對於 WCF 開發人員來說應該是直觀的。 基本目標是相同的：使用戶端和伺服器位於同一平臺上，無需擔心網路，可以編寫代碼。

兩個平臺共用聲明然後實現介面的原則，即使聲明該介面的過程是不同的。 正如您將在第 5 章中看到的，gRPC 支援的不同類型的 RPC 調用很好地映射到 WCF 服務可用的綁定。

## <a name="benefits-of-grpc"></a>gRPC 的好處

gRPC 高於其他解決方案，原因如下。

### <a name="performance"></a>效能

使用 HTTP/2 而不是 HTTP/1.1 可消除對人可讀消息的要求，而是使用更小、更快的二進位協定。 這對電腦進行分析的效率更高。 HTTP/2 還支援通過單個連接進行多工請求。 此支援允許在回應準備就緒後立即發送，而無需在佇列中等待。 （在 HTTP/1.1 中，此問題稱為"線頭 （HOL） 阻塞"。使用 gRPC 時需要的資源更少，這使得它成為用於行動裝置和速度較慢的網路的良好解決方案。

### <a name="interoperability"></a>互通性

所有主要程式設計語言和平臺都有 gRPC 工具和庫，包括 .NET、JAVA、Python、Go、C++、Node.js、Swift、Dart、Ruby 和 PHP。 得益于協定緩衝區二進位線格式和每個平臺的有效代碼生成，開發人員可以構建執行應用程式，同時仍然享受全面的跨平臺支援。

### <a name="usability-and-productivity"></a>可用性和產能

gRPC 是一個全面的 RPC 解決方案。 它在多種語言和平臺上一致工作。 它還提供了出色的工具，自動生成許多必要的樣板代碼。 因此，可以騰出更多開發人員時間來關注業務邏輯。

### <a name="streaming"></a>串流

gRPC 具有完全雙向流式處理，提供與 WCF 全雙工服務類似的功能。 gRPC 流可以通過常規互聯網連接、負載等化器和服務聯結運行。

### <a name="deadlinetimeouts-and-cancellation"></a>截止日期/超時和取消

gRPC 允許用戶端指定 RPC 完成的最大時間。 如果超過指定的截止時間，伺服器可以獨立于用戶端取消操作。 截止和取消可以通過進一步的 gRPC 調用傳播，以説明強制實施資源使用限制。 用戶端也可以在超過截止時間時停止操作，或者在必要時更早停止操作（例如，由於使用者交互）。

### <a name="security"></a>安全性

gRPC 在 TLS 端到端加密連接上使用 HTTP/2 時具有隱式安全。 對用戶端憑證身份驗證的支援（參見[第 6 章](security.md)）進一步增強了用戶端和伺服器之間的安全性和信任。

>[!div class="step-by-step"]
>[上一個](network-protocols.md)
>[下一個](protocol-buffers.md)
