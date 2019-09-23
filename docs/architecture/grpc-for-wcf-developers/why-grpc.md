---
title: 為什麼為 WCF 開發人員建議使用 gRPC-針對 WCF 開發人員 gRPC
description: 討論為什麼 gRPC 是適合想要遷移至現代化架構和平臺的 WCF 開發人員。
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 7e80936eb36bbba92958c349b5f1c0cb389d6b8d
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184033"
---
# <a name="why-grpc-is-recommended-for-wcf-developers"></a>為什麼為 WCF 開發人員建議使用 gRPC

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

在深入探討 gRPC 的語言和技術之前，值得一提的是，對於想要遷移至 .NET Core 的 WCF 開發人員而言，gRPC 是正確的解決方案，但有提供替代方案。

## <a name="similarity-to-wcf"></a>WCF 的相似性

雖然它的執行與方法不同，但使用 gRPC 來開發和使用服務的實際經驗，對於 WCF 開發人員而言應該非常直覺。 讓您能夠以用戶端和伺服器為基礎的程式碼，就像是在相同的平臺上，而不需要擔心網路的情況一樣。 這兩種平臺都共用宣告和執行介面的原則，即使宣告該介面的程式不同也是一樣。 您會在第5章中看到，gRPC 對應所支援的不同類型 RPC 呼叫，非常適合 WCF 服務可用的不同系結。

## <a name="benefits-of-grpc"></a>GRPC 的優點

GRPC 代表其他解決方案的其他原因如下：

### <a name="performance"></a>效能

如先前所討論，使用 HTTP/2 而不是 HTTP/1.1，會移除人們可讀取訊息的需求，而改為使用較快速的二進位通訊協定。 這對於要剖析的電腦更有效率。 HTTP/2 也支援透過單一連線的多工處理要求，讓回應在準備就緒時立即傳送，而不需要在佇列中等候（HTTP/1.1 中的問題稱為「行首（逾越）封鎖」）。 使用 gRPC 時需要較少的資源，這讓它成為適用于行動裝置和較慢網路的絕佳解決方案。

### <a name="interoperability"></a>互通性

有適用于所有主要程式設計語言和平臺的 gRPC 工具和程式庫，包括 .NET、JAVA、Python C++、Go、Node.js、Swift、Dart、RUBY 和 PHP。 由於通訊協定會緩衝二進位電傳格式，並為每個平臺產生有效率的程式碼，因此開發人員可以建立高效能的應用程式，同時仍然享有完整的跨平臺支援。

### <a name="usability-and-productivity"></a>可用性和生產力

gRPC 是一套完整的 RPC 解決方案。 它在多個語言和平臺上一致運作，並提供絕佳的工具，其中包含自動產生的許多必要的程式碼，因此更多的開發人員時間也會更專注于商務邏輯。

### <a name="streaming"></a>資料流

gRPC 具有完整的雙向串流，其可為 WCF 的全雙工服務提供非常類似的功能。 gRPC 串流可以透過一般的網際網路連線、負載平衡器和服務網格運作。

### <a name="deadlinetimeouts-and-cancellation"></a>期限/超時和取消

gRPC 可讓用戶端指定 RPC 完成的最長時間。 如果超過指定的期限，伺服器就可以取消用戶端的獨立作業。 您可以透過進一步的 gRPC 呼叫來傳播期限和取消，以協助強制執行資源使用限制。 用戶端也可能會在超過期限時中止作業，或在必要時（例如，因使用者互動而發生）。

### <a name="security"></a>安全性

透過 TLS 端對端加密連線使用 HTTP/2 時，gRPC 會隱含地受到保護。 支援用戶端憑證驗證（請參閱第6章）進一步增加用戶端與伺服器之間的安全性和信任。

>[!div class="step-by-step"]
>[上一頁](network-protocols.md)
>[下一頁](protocol-buffers.md)
