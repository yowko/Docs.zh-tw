---
title: 適用于 WCF 開發人員的 gRPC-gRPC 總覽
description: 瞭解指導 gRPC 開發的一組原則。
ms.date: 12/15/2020
ms.openlocfilehash: 99e1bdb1f49469f444044027c3ac5d927f9cab13
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938399"
---
# <a name="grpc-overview"></a>gRPC 總覽

在查看 Windows Communication Foundation 的 (WCF) 和 gRPC 的創世之後，這一章會考慮 gRPC 的一些主要功能，以及它們與 WCF 的比較。

ASP.NET Core 3.0 是原生支援 gRPC 的第一版 ASP.NET，其中的 Microsoft 團隊會參與 gRPC 的官方 .NET 實施。 建議您使用 .NET 來建立分散式應用程式，以便與其他主要的程式設計語言和架構交互操作。

## <a name="key-principles"></a>主要原則

如第1章所述，Google 希望使用 HTTP/2 的引進來取代 Stubby，也就是其內部的一般用途 RPC 基礎結構。 以 Stubby 為基礎的 gRPC 現在可以利用標準化，並將其適用性延伸至行動運算、雲端及物聯網。

為了達成這項標準化， [雲端原生運算基礎 (CNCF) ](https://www.cncf.io/) 建立了一組管理 gRPC 的原則。 下列清單顯示最相關的專案，其主要考慮最大化的存取範圍和可用性：

- **免費且開放** ：所有成品都應該是開放原始碼，並具有授權，而不會限制開發人員採用 gRPC。
- **涵蓋範圍和簡單性** – gRPC 應該可在每個受歡迎的平臺上使用，且相當簡單，可以在任何平臺上建立。
- **互通性和觸及** –無論頻寬或延遲為何，都應該使用廣泛可用的網路標準，在任何網路上使用 gRPC。
- **一般用途和** 效能–架構應該盡可能廣泛使用案例，而不會影響效能。
- **串流** –通訊協定應提供大型資料集或非同步訊息的資料流程處理。
- **中繼資料交換** -通訊協定可讓非商務資料（例如驗證權杖）與實際商務資料分開處理。
- **標準化狀態碼** –應減少錯誤碼的變化性，讓錯誤處理決策更清楚。 如果需要更豐富的錯誤處理，則應該提供機制來管理中繼資料交換內的行為。

>[!div class="step-by-step"]
>[上一個](introduction.md) 
>[下一步](approach.md)
