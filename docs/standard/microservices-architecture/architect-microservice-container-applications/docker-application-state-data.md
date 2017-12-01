---
title: "狀態和 Docker 應用程式中的資料"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |狀態和 Docker 應用程式中的資料"
keywords: "Docker Microservices、 ASP.NET、 容器、 SQL、 CosmosDB、 Docker"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 36d0fb9f27ef56b36c380e2fc972c79cff77003e
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="state-and-data-in-docker-applications"></a>狀態和 Docker 應用程式中的資料

在大部分情況下，您可以將做為處理序的執行個體的容器。 處理程序不會維護永續性狀態。 假設執行個體將會無限期周圍是容器可以寫入其本機儲存體，而就像假設記憶體中的單一位置將會永久性。 容器映像，例如處理程序，應該假設有多個執行個體，或它們就最終會終止。如果它們透過容器 orchestrator 管理，它應該假設，它們可能會取得一個節點或 VM 間移動。

Docker 提供功能，稱為*重疊檔案系統*。 這會實作寫入時複製工作存放區更新容器的根檔案系統的資訊。 該資訊是另外為原始的映像所依據的容器。 如果從系統刪除容器，則會失去這些變更。 因此，雖然也可以儲存在其本機儲存體容器的狀態，但是設計系統，以解決此衝突與容器的設計，其預設值是無狀態的內部部署。

下列解決方案可用於管理 Docker 應用程式中的永續性資料：

-   [資料磁碟區](https://docs.docker.com/engine/tutorials/dockervolumes/)，掛接至主機。

-   [資料磁碟區容器](https://docs.docker.com/engine/tutorials/dockervolumes/#creating-and-mounting-a-data-volume-container)可提供共用存放裝置使用的外部容器的容器。

-   [磁碟區外掛程式](https://docs.docker.com/engine/tutorials/dockervolumes/)的掛接磁碟區，以遠端服務，才能提供長期持續性。

-   [Azure 儲存體](https://docs.microsoft.com/azure/storage/)，這樣會提供可散布異地儲存體，容器提供很好的長期持續性解決方案。

-   遠端關聯式資料庫喜歡[Azure SQL Database](https://azure.microsoft.com/services/sql-database/)或是想要的 NoSQL 資料庫[Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction)，或是快取服務，例如[Redis](https://redis.io/)。

以下提供有關這些選項的更多詳細資料。

**資料磁碟區**主機 OS 從對應到容器中的目錄的目錄。 當容器中的程式碼可存取主機作業系統上的目錄實際上是存取的目錄。 此目錄未繫結至容器本身的存留期和從直接在主機作業系統上執行的程式碼可以存取目錄，或由另一個容器對應相同的主機目錄至本身。 因此，資料磁碟區被設計來保存資料與容器的生命週期無關。 如果您刪除容器或映像從 Docker 主機時，將資料保存在資料磁碟區不會刪除。 從主機作業系統，以及可以存取磁碟區中的資料。

**資料磁碟區容器**是演進而來的一般資料磁碟區。 資料磁碟區容器是簡單的容器具有中的一個或多個資料磁碟。 從中央的掛接點，資料磁碟區容器會提供存取至容器。 這個方法的資料存取是很方便，因為它擷取原始資料的位置。 除此之外，其行為未類似於一般資料磁碟區，讓資料保存於獨立應用程式的容器的生命週期此專用的容器。

如所示圖 4-5，就可以儲存規則的 Docker 磁碟區容器本身之外，但實體界限內的主機伺服器或 VM。 不過，Docker 容器無法存取磁碟區從一部主機伺服器或 VM 之間。 換句話說，使用這些磁碟區，就不能夠管理不同的 Docker 主機執行的容器之間共用的資料

![](./media/image5.png)

**圖 4-5**。 資料磁碟區與容器基礎的應用程式的外部資料來源

此外，Docker 容器管理時由 orchestrator，容器可能"「 主機之間移動，根據叢集所執行的最佳化。 因此，不建議您將資料磁碟區使用商務資料。 但它們是良好的機制，來使用追蹤檔案，暫存檔案，或類似，並不會影響商務資料的一致性。

**磁碟區外掛程式**像[Flocker](https://clusterhq.com/flocker/)不同叢集中所有主機之間提供資料存取。 並非所有的磁碟區外掛程式所建立時同樣地，磁碟區外掛程式通常提供外部化持續的可靠存放從不可變的容器。

**遠端資料來源和快取**工具，例如 Azure SQL Database、 Azure Cosmos DB 或遠端快取像 Redis 可在容器化應用程式開發沒有容器時，它們會使用相同的方式。 這是經過證實的方式來儲存商業應用程式資料。

**Azure 儲存體。** 商務資料通常會需要放在外部的資源或資料庫，例如 Azure 儲存體。 Azure 儲存體，在實體，提供在雲端中的下列服務：

-   Blob 儲存體儲存非結構化的物件資料。 Blob 可以是任何類型的文字或二進位資料，例如文件或媒體檔案 （影像、 音訊及視訊檔案）。 Blob 儲存體也稱為物件儲存體。

-   檔案存放裝置提供使用標準 SMB 通訊協定的舊版應用程式的共用存放裝置。 Azure 虛擬機器和雲端服務可以透過掛接共用應用程式元件在共用檔案資料。 在內部部署應用程式可以存取檔案共用，以透過檔案服務 REST API 中的資料。

-   資料表儲存體會儲存結構化資料集。 資料表儲存體是 NoSQL 索引鍵屬性的資料存放區，可快速開發和迅速存取大量資料。

**關聯式資料庫和 NoSQL 資料庫。** 有許多的選擇，可從關聯式資料庫，例如 SQL Server、 PostgreSQL、 Oracle 或 NoSQL 資料庫，例如 Azure Cosmos DB、 MongoDB 等外部資料庫。這些資料庫不會說明本指南的一部分，因為它是以完全不同的主體中。


>[!div class="step-by-step"]
[上一個](化-整合-applications.md) [下一步] (服務-導向-architecture.md)
