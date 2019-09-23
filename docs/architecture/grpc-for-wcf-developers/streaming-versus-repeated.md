---
title: gRPC 串流服務與重複的欄位-WCF 開發人員的 gRPC
description: 比較重複的欄位與串流服務，做為使用 gRPC 傳遞資料集合的方式。
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 7dc3c8f5bf2efc304da7d50661ba47db500e67a0
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184068"
---
# <a name="grpc-streaming-services-versus-repeated-fields"></a>gRPC 串流服務與重複的欄位

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

gRPC services 提供兩種方法來傳回資料集或物件清單。 通訊協定緩衝區訊息規格會使用`repeated`關鍵字來宣告清單或另一則訊息中的陣列。 GRPC 服務規格會使用`stream`關鍵字來宣告長時間執行的持續性連線，透過此連接會傳送多個訊息，並可個別處理。 這`stream`項功能也可用於長時間執行的時態性資料（例如通知或記錄訊息），但本章會考慮使用它來傳回單一資料集。

您應該使用的取決於各種因素，例如資料集的整體大小、在用戶端或伺服器端建立資料集所花的時間，以及資料集的取用者是否可以在第一個專案可用時立即開始作用。，或需要完整的資料集來執行任何有用的工作。

## <a name="when-to-use-repeated-fields"></a>使用`repeated`欄位的時機

對於大小限制，而且可以在短時間內完整產生的任何資料集（例如，在一秒內），您應該使用一般 Protobuf 訊息`repeated`中的欄位。 例如，在電子商務系統中，若要建立訂單中的專案清單可能很快，而且清單不會很大。 傳回具有`repeated`欄位的單一訊息是比`stream`使用更快的順序，而且會產生較少的網路額外負荷。

如果用戶端在開始處理之前需要所有資料，而且資料集夠小，可以在記憶體中建立，則即使在伺服器`repeated`的記憶體中實際建立資料集的速度較慢，也請考慮使用欄位。

## <a name="when-to-use-stream-methods"></a>使用`stream`方法的時機

訊息物件可能非常大的資料集，最好使用串流要求或回應來傳輸。 在記憶體中建立大型物件、將它寫入網路，然後釋放資源，會更有效率。 這種方法可以改善服務的擴充性。

同樣地，不受限制大小的資料集應該透過資料流程傳送，以避免在建立記憶體時用盡記憶體。

針對每個個別專案可由取用者分別進行處理的資料集，您應該考慮使用資料流程，如果這表示進度可以向使用者表示。 這可能會改善應用程式的明顯回應性，但這應該平衡應用程式的整體效能。

資料流程可能很有用的另一種情況是在多個服務之間處理訊息的位置。 如果鏈中的每個服務傳回資料流程，則終端機服務（也就是鏈中的最後一個）可以開始傳回可處理的訊息，並將鏈傳回給原始要求者，這可能會傳回資料流程或匯總產生單一回應訊息。 這種方法非常適合對應/減少之類的模式。

>[!div class="step-by-step"]
>[上一頁](migrate-duplex-services.md)
>[下一頁](client-libraries.md)
