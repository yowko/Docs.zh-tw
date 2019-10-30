---
title: 分散式資料
description: 架構適用于 Azure 的雲端原生 .NET 應用程式 |雲端原生應用程式的分散式資料
ms.date: 06/30/2019
ms.openlocfilehash: b715ae5203264a023bc9f911aa74ee222afe3d68
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73087450"
---
# <a name="distributed-data-for-cloud-native-apps"></a>雲端原生應用程式的分散式資料

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

當您在建立由許多獨立微服務所組成的雲端原生系統時，您認為資料儲存體的變更方式。

傳統的整合型應用程式偏好如圖5-1 所示的集中式資料存放區。

![單一整合型資料庫](./media/single-monolithic-database.png)

**圖 5-1**. 單一整合型資料庫

請注意，在上圖中，所有應用程式元件都會使用單一關係資料庫。

這種方法有許多優點。 查詢分散在多個資料表中的資料很簡單，而且可以直接執行[ACID 交易](https://docs.microsoft.com/windows/desktop/cossdk/acid-properties)以確保資料的一致性。 最後，您會得到*立即的一致性*：您所有的資料更新，或不會執行任何動作。

雲端原生系統偏好 [圖 5-2] 中所示的資料結構，每個微服務都擁有並封裝自己的資料。

![跨微服務的多個資料庫](./media/data-across-microservices.png)

**圖 5-2**。 跨微服務的多個資料庫

請注意，在上圖中，每個微服務會擁有並封裝它的資料存放區，而且只會從其公用 API 向外界公開資料。

此模型可讓每個微服務獨立發展，而不需要協調其他微服務的資料架構變更。 每個微服務都可以自由地執行最符合其需求的資料存放區（關係資料庫、檔資料庫、索引鍵/值存放區）類型。 在執行時間，每個微服務都可以據以調整其資料。 如圖5-3 所示：

![多語言資料持續性](./media/polyglot-data-persistence.png)

**圖 5-3**。 多語言資料持續性

請注意，在上圖中，產品目錄和清查微服務會採用關係資料庫、訂購微服務、NoSql 檔資料庫和購物車微服務，這是外部索引鍵/值存放區。 雖然關係資料庫與複雜資料的微服務保持相關，但 NoSQL 資料庫已獲得相當大的普及，並提供適應性、快速查閱和高可用性。 其無架構的本質可讓開發人員從具類型的資料類別和 Orm 的架構中移出，這會使變更成本高昂且耗時。

>[!div class="step-by-step"]
>[上一頁](service-mesh-communication-infrastructure.md)
>[下一頁](data-patterns.md)
