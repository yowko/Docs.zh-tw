---
title: "Docker 應用程式中的狀態和資料"
description: "容器化 .NET 應用程式的 .NET 微服務架構 | Docker 應用程式中的狀態和資料"
keywords: "Docker, 微服務, ASP.NET, 容器, SQL, CosmosDB, Docker"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ef11d89c39ee02d52dab29f949d1ac6be981d87f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="state-and-data-in-docker-applications"></a>Docker 應用程式中的狀態和資料

在大多數情況下，您可以將容器視為處理序執行個體。 處理序不會保留持續性狀態。 雖然容器可以寫入至其本機存放區，但假設執行個體會無限期存在，就像是假設記憶體中的某個位置會持久一樣。 您應該假設容器映像 (例如處理序) 具有多個執行個體或最後終究會終止；如果是由容器協調器所管理，則應該假設它們可能會從某個節點或 VM 移至另一個。

Docker 提供一項功能，稱為「重疊檔案系統」。 這會實作寫入時複製工作，將已更新的資訊儲存至容器的根檔案系統。 該資訊是容器所依據之原始映像以外的資訊。 如果從系統中刪除容器，這些變更將會遺失。 因此，雖然有可能將容器的狀態儲存在其本機存放區，但以此為中心來設計系統會與容器設計的前提 (預設為無狀態) 衝突。

下列解決方案可用來管理 Docker 應用程式中的持續性資料：

-   [資料磁碟區](https://docs.docker.com/engine/tutorials/dockervolumes/)，可掛接至主機。

-   [資料磁碟區容器](https://docs.docker.com/engine/tutorials/dockervolumes/#creating-and-mounting-a-data-volume-container)，使用外部容器提供跨容器的共用存放裝置。

-   [磁碟區外掛程式](https://docs.docker.com/engine/tutorials/dockervolumes/)，可將磁碟區掛接至遠端服務，以提供長期持續性。

-   [Azure 儲存體](https://docs.microsoft.com/azure/storage/)，備有異地分散式儲存體，以提供容器的長期持續性解決方案。

-   遠端關聯式資料庫 (例如 [Azure SQL Database](https://azure.microsoft.com/services/sql-database/))、NoSQL 資料庫 (例如 [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction)) 或快取服務 (例如 [Redis](https://redis.io/))。

以下提供有關這些選項的更多詳細資料。

**資料磁碟區**是從主機 OS 對應至容器中目錄的目錄。 當容器中的程式碼具有目錄的存取權時，該存取權實際上就是主機 OS 上的目錄存取權。 此目錄不會受限於容器本身的存留期，而且可從主機 OS 上直接執行的程式碼，或由將相同主機目錄對應至本身的另一個容器存取該目錄。 因此，資料磁碟區設計成可無視於容器的存留期來保存資料。 如果您從 Docker 主機中刪除容器或映像，則不會刪除保存在資料磁碟區中的資料。 您也可以從主機 OS 存取磁碟區中的資料。

**資料磁碟區容器**是從一般資料磁碟區演進而來。 資料磁碟區容器是簡單的容器，其中包含一或多個資料磁碟區。 資料磁碟區容器可讓您從中央掛接點存取容器。 這個資料存取方法很方便，因為它會擷取原始資料的位置。 除此之外，其行為會類似於一般資料磁碟區，因此資料會保存在此專用容器中，而與應用程式容器的生命週期無關。

如圖 4-5 所示，一般 Docker 磁碟區可儲存在容器本身之外，但必須在主機伺服器或 VM 的實體界限內。 不過，Docker 容器無法從一部主機伺服器或 VM 存取另一部主機伺服器或 VM 的磁碟區。 換句話說，您無法使用這些磁碟區來管理不同 Docker 主機上所執行的容器之間共用的資料

![](./media/image5.png)

**圖 4-5**： 容器應用程式的資料磁碟區和外部資料來源

此外，當 Docker 容器是由協調器所管理時，容器可能會根據叢集所執行的最佳化在主機之間「移動」。 因此，不建議您使用資料磁碟區來存放商務資料。 但對於追蹤檔案、時態性檔案或不影響商務資料一致性的類似檔案而言，這會是不錯的機制。

**磁碟區外掛程式** (例如 [Flocker](https://clusterhq.com/flocker/)) 提供叢集中跨所有主機的資料存取權。 雖然並非所有磁碟區外掛程式的建立方式都相同，但磁碟區外掛程式通常會從不可變的容器提供外部化、持續性且可靠的儲存體。

**遠端資料來源和快取**工具 (例如 Azure SQL Database、Azure Cosmos DB) 或遠端快取 (例如 Redis) 可用於容器化應用程式，就像是在沒有容器時用於開發一樣。 此方法經過實證，可儲存商務應用程式資料。

**Azure 儲存體。** 商務資料通常需要放在外部資源或資料庫中，例如 Azure 儲存體。 具體來說，Azure 儲存體會提供下列雲端服務：

-   Blob 儲存體可儲存非結構化的物件資料。 Blob 可以是任何類型的文字或二進位資料，例如文件或媒體檔案 (影像、音訊和視訊檔案)。 Blob 儲存體也稱為物件儲存體。

-   檔案儲存體為使用標準 SMB 通訊協定的舊版應用程式提供共用存放裝置。 Azure 虛擬機器和雲端服務可透過掛接共用，在應用程式元件之間共用檔案資料。 內部部署應用程式可透過檔案服務 REST API，來存取共用中的檔案資料。

-   表格儲存體可儲存結構化的資料集。 表格儲存體是 NoSQL 索引鍵屬性資料存放區，可快速開發及存取大量資料。

**關聯式資料庫和 NoSQL 資料庫。** 外部資料庫的選擇有許多，從關聯式資料庫 (例如 SQL Server、PostgreSQL、Oracle) 到 NoSQL 資料庫 (例如 Azure Cosmos DB、MongoDB) 等等。這些資料庫由於是完全不同的主題，因此不會在本指南中說明。


>[!div class="step-by-step"]
[上一個] (containerize-monolithic-applications.md) [下一個] (service-oriented-architecture.md)
