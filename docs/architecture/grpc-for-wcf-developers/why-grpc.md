---
title: 為什麼我們建議 WCF 開發人員的 gRPC-適用于 WCF 開發人員的 gRPC
description: 討論為何 gRPC 適合想要遷移至新式架構和平臺的 WCF 開發人員。
ms.date: 12/15/2020
ms.openlocfilehash: 058f85297610116e96c8580fcefb10ee6dfcf935
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/06/2021
ms.locfileid: "97937970"
---
# <a name="why-we-recommend-grpc-for-wcf-developers"></a>為何我們為 WCF 開發人員建議 gRPC

在我們深入探討 gRPC 的語言和技巧之前，值得先討論為什麼 gRPC 是適合想要遷移至 .NET 的 Windows Communication Foundation (WCF) 開發人員的解決方案。

## <a name="similarity-to-wcf"></a>與 WCF 的相似性

雖然 gRPC 的實和方法不同，但使用 gRPC 開發和取用服務的經驗對於 WCF 開發人員來說應該是直覺的。 基礎目標相同：讓用戶端和伺服器在相同平臺上進行編碼，而不需要擔心網路功能。

這兩個平臺都會共用宣告的原則，然後再執行介面，即使宣告該介面的程式不同也是一樣。 您將會在第5章中看到，gRPC 支援對應到 WCF 服務可用系結的不同 RPC 呼叫類型。

## <a name="benefits-of-grpc"></a>GRPC 的優點

gRPC 會因下列原因而出現在其他解決方案的上方。

### <a name="performance"></a>效能

使用 HTTP/2 而不是 HTTP/1.1 時，不需要人們可讀取的訊息，而是改用較小、更快的二進位通訊協定。 這對電腦進行剖析更有效率。 HTTP/2 也支援透過單一連接的多工要求。 這項支援可讓您立即傳送回應，而不需要在佇列中等候。  (在 HTTP/1.1 中，此問題稱為「前端 (阻) 封鎖」。) 您在使用 gRPC 時需要較少的資源，這讓它成為適用于行動裝置和較慢網路的絕佳解決方案。

### <a name="interoperability"></a>互通性

所有主要的程式設計語言和平臺都有 gRPC 的工具和程式庫，包括 .NET、JAVA、Python、Go、c + +、Node.js、Swift、Dart、Ruby 和 PHP。 多虧了通訊協定緩衝區的二進位電傳格式和有效率的程式碼產生，開發人員可以建立高效能的應用程式，同時還能享受完整的跨平臺支援。

### <a name="usability-and-productivity"></a>可用性和產能

gRPC 是全方位的 RPC 解決方案。 它在多種語言和平臺上都能一致地運作。 它也提供絕佳的工具，並自動產生許多必要的重複使用程式碼。 因此，更多的開發人員時間會釋出以專注于商務邏輯。

### <a name="streaming"></a>串流

gRPC 具有完整的雙向串流，可提供 WCF 雙工服務的類似功能。 gRPC 串流可以透過一般的網際網路連線、負載平衡器和服務網格來運作。

### <a name="deadlinetimeouts-and-cancellation"></a>期限/超時和取消

gRPC 可讓用戶端指定 RPC 完成的最長時間。 如果超過指定的期限，伺服器可以在用戶端之外取消作業。 期限和取消可透過進一步的 gRPC 呼叫傳播，以協助強制執行資源使用量限制。 用戶端也可以在超過期限時或稍早（如 (有需要）的情況下停止作業（例如，因為使用者互動) ）。

### <a name="security"></a>安全性

gRPC 在透過 TLS 端對端加密連線使用 HTTP/2 時，會隱含地受到保護。 支援用戶端憑證驗證 (請參閱 [第6章](security.md)) 進一步提高用戶端與伺服器之間的安全性與信任。

>[!div class="step-by-step"]
>[上一個](network-protocols.md) 
>[下一步](protocol-buffers.md)
