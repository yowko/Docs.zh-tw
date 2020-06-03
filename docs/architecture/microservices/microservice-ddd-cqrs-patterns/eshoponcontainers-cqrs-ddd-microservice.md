---
title: 在 eShopOnContainers 的 DDD 微服務中套用 CQRS 和 CQS 方法
description: .NET 微服務：容器化 .NET 應用程式的架構 | 了解 CQRS 在 eShopOnContainers 訂購微服務中的實作。
ms.date: 03/03/2020
ms.openlocfilehash: 2916df596a6d0f887411f3ef0074aed395ef58ba
ms.sourcegitcommit: 5280b2aef60a1ed99002dba44e4b9e7f6c830604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/03/2020
ms.locfileid: "84306938"
---
# <a name="apply-cqrs-and-cqs-approaches-in-a-ddd-microservice-in-eshoponcontainers"></a>在 eShopOnContainers 的 DDD 微服務中套用 CQRS 和 CQS 方式

eShopOnContainers 參考應用程式中訂購微服務的設計是基於 CQRS 準則。 然而，它使用了最簡單的方法，即單純將查詢與命令分開，以及針對這兩個動作使用相同的資料庫。

那些模式的精髓和重點在於查詢是等冪的：無論您對系統進行多少次查詢，系統的狀態都不會變更。 換句話說，查詢沒有副作用。

因此，即使訂購微服務使用相同的資料庫，您還是可以使用與交易式邏輯「寫入」網域模型不同的「讀取」資料模型。 因此，這是簡化過後的 CQRS 方法。

另一方面，觸發交易及資料更新的命令會變更系統的狀態。 使用命令時，您必須在處理複雜性及不斷變更的商務規則時多加小心。 這正是您希望套用 DDD 技術以獲得更良好模型化系統的場合。

本指南中呈現的 DDD 模式不應適用於所有情況。 他們可能會為您的設計帶來條件約束。 這些條件約束會隨著時間帶來像是更高品質等的優點，尤其是在修改系統狀態的命令及其他程式碼。 然而，這些條件約束也會為讀取及查詢資料新增複雜度，卻只能帶來較小的優點。

其中一個模式便是彙總模式，我們會在稍後的章節中檢查。 簡而言之，在彙總模式中，您會將許多領域物件視為其在領域內關聯性結果的單一單位。 您不一定會想要在查詢中利用這種模式，因為它可能會增加查詢邏輯的複雜度。 針對唯讀查詢，您無法藉由將多個物件視為單一彙總而取得好處。 您只會增加複雜度。

如前一節的圖7-2 所示，本指南建議您只在微服務的交易/更新區域中使用 DDD 模式（也就是透過命令觸發）。 查詢可遵循更簡單的方法，並且與命令分離，遵循 CQRS 方法。

若要執行「查詢端」，您可以在許多方法之間做選擇，包括 EF Core、AutoMapper 投影、預存程式、視圖、具體化視圖或微 ORM 等完整的 ORM。

本指南及 eShopOnContainers 中 (特別是訂購微服務)，我們選擇使用像是 [Dapper](https://github.com/StackExchange/dapper-dot-net) 的微型 ORM 來實作直接查詢。 這可讓您根據 SQL 語句來執行任何查詢，以取得最佳效能，因為輕量的架構不會有額外負荷。

當您使用這種方法時，對您的模型進行的任何更新，都會影響實體保存至 SQL 資料庫的方式，也需要 Dapper 所使用之 SQL 查詢的個別更新，或其他任何不同的（非 EF）方法來進行查詢。

## <a name="cqrs-and-ddd-patterns-are-not-top-level-architectures"></a>CQRS 及 DDD 模式並非頂層架構

了解 CQRS 和大多數的 DDD 模式 (例如 DDD 層或使用彙總的領域模型) 都不是架構樣式，而只是架構模式是非常重要的。 微服務、SOA，以及事件驅動架構 (EDA) 才是架構樣式的範例。 他們描述了由許多元件組成的系統，例如許多微服務。 CQRS 和 DDD 模式描述了單一系統或元件中的某些事物。在此範例中，即是微服務中的某些事物。

不同的限定內容 (BC) 會採用不同的模式。 他們都有著不同的責任，並會導致不同的解決方案。 值得強調的是，強制在所有場合下使用相同的模式會導致失敗。 請不要在每個地方都使用 CQRS 和 DDD 模式。 許多子系統、 BC 或微服務都更為簡單，並且可使用簡單的 CRUD 服務或使用其他方法來輕鬆的實作。

只有一種應用程式架構：您正在設計之系統或端點對端點應用程式的架構 (例如微服務架構)。 然而，該應用程式中每個限定內容或微服務的設計都會反映其自身的取捨和架構模式層級中的內部設計決策。 請勿嘗試將相同的架構模式，例如 CQRS 或 DDD 套用到所有地方。

### <a name="additional-resources"></a>其他資源

- **聖馬丁 Fowler。CQRS** \
  <https://martinfowler.com/bliki/CQRS.html>

- **Greg 年輕CQRS 檔** \
  <https://cqrs.files.wordpress.com/2010/11/cqrs_documents.pdf>

- **Udi Dahan。澄清 CQRS** \
  <https://udidahan.com/2009/12/09/clarified-cqrs/>

>[!div class="step-by-step"]
>[上一個](apply-simplified-microservice-cqrs-ddd-patterns.md) 
>[下一步](cqrs-microservice-reads.md)
