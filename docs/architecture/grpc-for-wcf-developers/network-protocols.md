---
title: 網路通訊協定-適用于 WCF 開發人員的 gRPC
description: GRPC 網路通訊協定的總覽。
ms.date: 09/02/2019
ms.openlocfilehash: 801d57c95aec748e5dcf667ca480775ff945b55c
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938555"
---
# <a name="network-protocols"></a>網路通訊協定

不同于 WCF) 的 Windows Communication Foundation (，gRPC 會使用 HTTP/2 做為其網路功能的基礎。 此通訊協定可提供比 WCF 和 SOAP 更顯著的優點，而這只會在 HTTP/1.1 上運作。 對於想要使用 gRPC 的開發人員，假設沒有 HTTP/2 的替代方案，則看起來應該是更詳細探索 HTTP/2 的理想時機，並找出使用 gRPC 的其他好處。

由2015中的網際網路工程任務推動小組所發行的 HTTP/2，衍生自已由 Google 使用的實驗性 SPDY 通訊協定。 其設計目的是要比 HTTP/1.1 更有效率、更快速且更安全。

## <a name="key-features-of-http2"></a>HTTP/2 的主要功能

此清單顯示 HTTP/2 的一些主要功能和優點：

### <a name="binary-protocol"></a>二進位通訊協定

要求/回應迴圈不再需要文字命令。 此活動可簡化並加速命令的執行。 具體來說，剖析資料的速度較快，且使用的記憶體較少，網路延遲會因為速度明顯的相關改良而降低，而網路資源的整體使用也會更好。

### <a name="streams"></a>串流

資料流程可讓您建立傳送者與收件者之間的長期連接，以非同步方式傳送多個訊息或框架。 多個資料流程可以在單一 HTTP/2 連接上獨立運作。

### <a name="request-multiplexing-over-a-single-tcp-connection"></a>透過單一 TCP 連接要求多工

這項功能是 HTTP/2 最重要的創新之一。 因為它允許對資料進行多個平行要求，所以現在可以從單一伺服器同時下載 web 檔案。 網站的載入速度更快，而優化的需求也會降低。 標頭 (住) 封鎖的情況下，已就緒的回應必須等待傳送，直到先前的要求完成為止 (，但仍封鎖仍可在) 的 TCP 傳輸層級進行。

### <a name="nettcp-like-performance-cross-platform"></a>Net.tcp （類似 TCP）效能，跨平臺

基本上，gRPC 和 HTTP/2 的組合可為開發人員提供 WCF 的 Net.tcp 系結的同等速度和效率，而且在某些情況下，速度和效率更高。 但是，與 Net.tcp 不同的是，透過 HTTP/2 的 gRPC 不受限於 .NET 應用程式。

>[!div class="step-by-step"]
>[上一個](interface-definition-language.md) 
>[下一步](why-grpc.md)
