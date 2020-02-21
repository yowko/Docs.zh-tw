---
title: WCF 開發人員的 gRPC-gRPC 總覽
description: 瞭解指導開發 gRPC 的原則集合。
ms.date: 09/02/2019
ms.openlocfilehash: a0811adadc617097d86edc5f845c42a7e90f560f
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2020
ms.locfileid: "77542919"
---
# <a name="grpc-overview"></a>gRPC 總覽

在查看上一章中 Windows Communication Foundation （WCF）和 gRPC 的創世之後，本章會考慮 gRPC 的一些主要功能，以及它們與 WCF 的比較。

ASP.NET Core 3.0 是 ASP.NET 的第一版，以原生方式支援 gRPC 作為第一級公民，而 Microsoft 團隊則參與 gRPC 的官方 .NET 實施。 建議使用 .NET 建立分散式應用程式，以便與其他主要的程式設計語言和架構相交互操作。

## <a name="key-principles"></a>主要原則

如第1章所述，Google 想要使用 HTTP/2 的引進來取代 Stubby，其內部的一般用途 RPC 基礎結構。 gRPC 以 Stubby 為基礎，現在可以利用標準化，並擴充其對行動運算、雲端和物聯網的適用性。

為了達到此目的，[雲端原生運算基礎（由 cncf）](https://www.cncf.io/)建立了一組可管理 gRPC 的原則。 下列清單顯示最相關的內容，主要關心最大化協助工具和可用性：

- **免費和開放**-所有成品都應該是開放原始碼，且授權不會限制開發人員採用 gRPC。
- **涵蓋範圍和簡易性**– gRPC 應可在每個熱門平臺上使用，並可輕鬆地在任何平臺上建立。
- **互通性和**觸達–使用廣泛可用的網路標準，無論頻寬或延遲為何，都可以在任何網路上使用 gRPC。
- **一般用途和**高效能–架構應可由廣泛使用案例的可用範圍，而不會影響效能。
- **串流**–此通訊協定應該提供大型資料集或非同步訊息的資料流程處理語義。
- **中繼資料交換**–此通訊協定可讓非商務資料（例如驗證權杖）與實際的商務資料分開處理。
- **標準化的狀態碼**–應該減少錯誤碼的變異數，以更清楚地進行錯誤處理決策。 如果需要更豐富的錯誤處理，則必須提供機制來管理中繼資料交換內的此程式。

>[!div class="step-by-step"]
>[上一頁](introduction.md)
>[下一頁](approach.md)
