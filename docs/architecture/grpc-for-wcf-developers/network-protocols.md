---
title: 網路通訊協定-WCF 開發人員的 gRPC
description: GRPC 網路通訊協定的總覽。
ms.date: 09/02/2019
ms.openlocfilehash: 1ceb140f7b7ac7e796a87612ebb9d21e28d33968
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628484"
---
# <a name="network-protocols"></a>網路通訊協定

不同于 Windows Communication Foundation （WCF），gRPC 會使用 HTTP/2 做為其網路功能的基礎。 這在 WCF 和 SOAP 上提供顯著的優點，這只會在 HTTP/1.1 上運作。 對於想要使用 gRPC 的開發人員而言，假設沒有 HTTP/2 的替代方案，那麼最好的時機是探索 HTTP/2，並找出使用 gRPC 的其他優點。

2015中由網際網路工程任務推動小組發行的 HTTP/2 衍生自已由 Google 使用的實驗性 SPDY 通訊協定。 其設計目的是要比 HTTP/1.1 更有效率、更快速且更安全。

## <a name="key-features-of-http2"></a>HTTP/2 的主要功能

這份清單會顯示 HTTP/2 的一些主要功能和優點：

### <a name="binary-protocol"></a>二進位通訊協定

要求/回應週期不再需要文字命令。 這可簡化和加速命令的執行。 具體而言，剖析資料的速度較快，且使用的記憶體較少，網路延遲會隨著速度的明顯相關改良而降低，而且會有更好的網路資源使用。

### <a name="streams"></a>資料流

資料流程可讓您在傳送者與接收者之間建立長期的連線，以便以非同步方式傳送多個訊息或框架。 多個資料流程可以在單一 HTTP/2 連接上獨立運作。

### <a name="request-multiplexing-over-a-single-tcp-connection"></a>透過單一 TCP 連線要求多工處理

這項功能是 HTTP/2 其中一項最重要的創新。 因為它允許對資料進行多個平行要求，所以現在可以從單一伺服器同時下載 web 檔案。 網站的載入速度更快，而優化的需求也會減少。 標頭（逾越）封鎖，其中已準備好的回應必須等到先前的要求完成後才會被降低（雖然在 TCP 傳輸層級仍然會發生阻礙封鎖）。

### <a name="nettcp-like-performance-cross-platform"></a>Net.tcp like 效能，跨平臺

基本上，gRPC 和 HTTP/2 的組合可為開發人員提供與 WCF 的 Net.tcp 系結至少相等的速度和效率，而在某些情況下，甚至更快的速度和效率。 但不同于 Net.tcp，gRPC over HTTP/2 並不限於 .NET 應用程式。

>[!div class="step-by-step"]
>[上一頁](interface-definition-language.md)
>[下一頁](why-grpc.md)
