---
title: WCF 開發人員的 gRPC-gRPC 總覽
description: 瞭解指導開發 gRPC 的原則集合。
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: b372cc9dcdb2efd605b3d9b688513e4ff8530b01
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184439"
---
# <a name="grpc-overview"></a>gRPC 總覽

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

在查看上一章中 WCF 和 gRPC 的創世之後，本章將會考慮 gRPC 的一些重要功能，以及它們與 WCF 之間的比較。

ASP.NET Core 3.0 是 ASP.NET 的第一版，以原生方式支援 gRPC 作為第一級公民，而 Microsoft 團隊則參與 gRPC 的官方 .NET 實施。 建議您使用 .NET 建立分散式應用程式的最佳方法，以便與所有其他主要的程式設計語言和架構相交互操作。

## <a name="key-principles"></a>主要原則

如第1章所述，Google 想要使用 HTTP/2 的引進來修改 Stubby，其內部的一般用途 RPC 基礎結構。 Stubby，重新命名的 gRPC 現在可以利用標準化，並擴充其對行動運算、雲端和物聯網的適用性。

為了達到此目的，[雲端原生運算基礎（由 cncf）](https://www.cncf.io/)建立了一組可管理 gRPC 的原則。 下列清單顯示最相關的內容，主要關心最大化協助工具和可用性：

- **免費和開放**-所有成品都應該是具有授權的開放原始碼，而不會限制開發人員採用 gRPC。
- **涵蓋範圍和簡易性**– gRPC 應可跨各種熱門平臺使用，且簡單到足以在任何平臺上建立。
- **互通性和**觸達–使用廣泛可用的網路標準，無論頻寬或延遲為何，都可以在任何網路上使用 gRPC。
- **一般用途和**效能–架構應可由廣泛使用案例的可用範圍，而不會影響到效能。
- **串流**–此通訊協定應該提供大型資料集或非同步訊息的資料流程處理語義。
- **中繼資料交換**–通訊協定允許非商務資料，例如驗證權杖，與實際的商務資料分開處理。
- **標準化的狀態碼**–應該減少錯誤碼的變異數，讓錯誤處理決策更清楚，而且需要更豐富的錯誤處理，就應該提供機制來管理中繼資料交換內的此項。

>[!div class="step-by-step"]
>[上一頁](introduction.md)
>[下一頁](approach.md)
