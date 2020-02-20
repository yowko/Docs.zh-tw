---
title: 為什麼我們建議 WCF 開發人員的 gRPC-針對 WCF 開發人員的 gRPC
description: 討論為什麼 gRPC 是適合想要遷移至現代化架構和平臺的 WCF 開發人員。
ms.date: 09/02/2019
ms.openlocfilehash: fc93ca4c8f2a28dc4d3a0b0466d19c86273b40b8
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503321"
---
# <a name="why-we-recommend-grpc-for-wcf-developers"></a>為什麼我們建議 WCF 開發人員 gRPC

在深入探討 gRPC 的語言和技術之前，值得討論為什麼 gRPC 是適合想要遷移至 .NET Core 之 Windows Communication Foundation （WCF）開發人員的正確解決方案。

## <a name="similarity-to-wcf"></a>WCF 的相似性

雖然 gRPC 的實和方法不同，但使用 gRPC 開發和使用服務的經驗，對於 WCF 開發人員而言應該是直覺的。 基礎目標是相同的：讓程式碼可以如同用戶端和伺服器位於相同的平臺上，而不需要擔心網路功能。 

這兩種平臺都共用宣告和執行介面的原則，即使宣告該介面的程式不同也是一樣。 如您在第5章所見，gRPC 支援的各種 RPC 呼叫類型，都能正確對應到 WCF 服務可用的系結。

## <a name="benefits-of-grpc"></a>GRPC 的優點

gRPC 會因下列原因而代表其他解決方案。

### <a name="performance"></a>效能

使用 HTTP/2 而不是 HTTP/1.1，會移除人們可讀取訊息的需求，而改為使用較小、更快的二進位通訊協定。 這對於要剖析的電腦更有效率。 HTTP/2 也支援透過單一連接進行多工處理要求。 這項支援可讓回應在準備好時立即傳送，而不需要在佇列中等候。 （在 HTTP/1.1 中，此問題稱為「行首（逾越）封鎖」）。使用 gRPC 時，您需要較少的資源，這讓它成為適用于行動裝置和較慢網路的絕佳解決方案。

### <a name="interoperability"></a>互通性

有適用于所有主要程式設計語言和平臺的 gRPC 工具和程式庫，包括 .NET、JAVA、Python C++、Go、Node.js、Swift、Dart、RUBY 和 PHP。 由於通訊協定會緩衝二進位電傳格式，並為每個平臺產生有效率的程式碼，因此開發人員可以建立高效能的應用程式，同時仍然享有完整的跨平臺支援。

### <a name="usability-and-productivity"></a>可用性和產能

gRPC 是一套完整的 RPC 解決方案。 它在多種語言和平臺上一致運作。 它也提供絕佳的工具，並自動產生許多必要的重複使用程式碼。 更多的開發人員時間會被釋出，以專注于商務邏輯。

### <a name="streaming"></a>串流

gRPC 具有完整的雙向串流，可提供 WCF 的全雙工服務的類似功能。 gRPC 串流可以透過一般的網際網路連線、負載平衡器和服務網格運作。

### <a name="deadlinetimeouts-and-cancellation"></a>期限/超時和取消

gRPC 可讓用戶端指定 RPC 完成的最長時間。 如果超過指定的期限，伺服器就可以取消用戶端獨立的作業。 您可以透過進一步的 gRPC 呼叫來傳播期限和取消，以協助強制執行資源使用限制。 用戶端也可以在超過期限時停止作業，或在必要時（例如，因為使用者互動）。

### <a name="security"></a>安全性

當 gRPC 透過 TLS 端對端加密連線使用 HTTP/2 時，會隱含地保護。 支援用戶端憑證驗證（請參閱[第6章](security.md)）進一步增加用戶端與伺服器之間的安全性和信任。

>[!div class="step-by-step"]
>[上一頁](network-protocols.md)
>[下一頁](protocol-buffers.md)
