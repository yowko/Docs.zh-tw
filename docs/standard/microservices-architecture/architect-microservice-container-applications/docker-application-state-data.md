---
title: Docker 應用程式中的狀態和資料
description: Docker 應用程式中的狀態和資料管理。 微服務執行個體可消耗，但資料無法消耗；如何使用微服務處理它。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/20/2018
ms.openlocfilehash: 70c3cee8c5fd1e63f2ff869f49b1fb02ab8f59dd
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152652"
---
# <a name="state-and-data-in-docker-applications"></a>Docker 應用程式中的狀態和資料

在大多數情況下，您可以將容器視為處理序執行個體。 處理序不會保留持續性狀態。 雖然容器可以寫入至其本機存放區，但假設執行個體會無限期存在，就像是假設記憶體中的某個位置會持久一樣。 建議您假設容器映像與處理序相似，擁有多個執行個體，或是最後會遭到終止。 若它們是使用容器協調器進行管理，建議您假設它們可能會從一個節點或 VM 移動到另一個。

下列解決方案可用來管理 Docker 應用程式中的持續性資料：

從 Docker 主機，透過 [Docker Volumes](https://docs.docker.com/engine/admin/volumes/) (Docker 磁碟區)：

- **磁碟區**會儲存在主機檔案系統中由 Docker 管理的一個區域內。

- 由於**繫結裝載**可對應到主機檔案系統內的任何資料夾，因此無法從 Docker 處理序管理存取，且可能會因為容器能存取敏感性 OS 資料夾，而帶來安全性風險。

- **tmpfs 裝載**則與虛擬資料夾相似，只存在於主機的記憶體中，永遠不會寫入檔案系統。

從遠端存放：

- [Azure 儲存體](https://azure.microsoft.com/documentation/services/storage/)，備有異地分散式儲存體，以提供容器的長期持續性解決方案。

- 遠端關聯式資料庫 (例如 [Azure SQL Database](https://azure.microsoft.com/services/sql-database/))、NoSQL 資料庫 (例如 [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction)) 或快取服務 (例如 [Redis](https://redis.io/))。

從 Docker 容器：

> Docker 提供一項功能，稱為「重疊檔案系統」。 這會實作寫入時複製工作，將已更新的資訊儲存至容器的根檔案系統。 該資訊是容器所依據之原始映像以外的資訊。 如果從系統中刪除容器，這些變更將會遺失。 因此，雖然有可能將容器的狀態儲存在其本機存放區，但以此為中心來設計系統會與容器設計的前提 (預設為無狀態) 衝突。
>
> 但是，先前引進的 Docker 磁碟區現在是處理本機資料 Docker 的慣用方式。 若您需要容器內儲存體的詳細資訊，請查看 [Docker storage drivers ](https://docs.docker.com/storage/storagedriver/select-storage-driver/) (Docker 儲存體驅動程式) 與 [About storage drivers](https://docs.docker.com/storage/storagedriver/) (關於儲存體驅動程式)。

下列提供這些選項的更多詳細資料：

**磁碟區**是從主機 OS 對應至容器內目錄的目錄。 當容器中的程式碼具有目錄的存取權時，該存取權實際上就是主機 OS 上的目錄存取權。 此目錄不會和容器本身的存留期繫結，且目錄會由 Docker 管理，且和主機電腦的核心功能隔離。 因此，資料磁碟區設計成可無視於容器的存留期來保存資料。 如果您從 Docker 主機中刪除容器或映像，則不會刪除保存在資料磁碟區中的資料。

磁碟區可以具名，也可以是匿名 (預設)。 具名磁碟區是**資料磁碟區容器**的演進，可輕鬆的在容器間共用資料。 磁碟區也支援磁碟區驅動程式，除了其他選項之外，也可讓您將資料儲存在遠端主機上。

**繫結裝載**則是從很久以前開始便持續存在的可用選項，允許將任何資料夾對應到容器中的掛接點。 繫結裝載的限制比磁碟區更多，且具有某些重要的安全性問題，因此磁碟區是建議的選項。

**tmpfs 裝載**基本上就是虛擬資料夾，只存在於主機的記憶體中，永遠不會寫入檔案系統。 它們既快速又安全，但會使用記憶體，且僅適用於非持續性資料。

如圖 4-5 所示，一般 Docker 磁碟區可儲存在容器本身之外，但必須在主機伺服器或 VM 的實體界限內。 不過，Docker 容器無法從一部主機伺服器或 VM 存取另一部主機伺服器或 VM 的磁碟區。 換句話說，使用這些磁碟區，將無法管理在不同 Docker 主機上執行容器間所共用的資料，雖然仍可透過支援遠端主機的磁碟區驅動程式來達到此目的。

![磁碟區可以在容器間共用，但僅限位於相同的主機，除非您使用支援遠端主機的遠端驅動程式。 ](./media/image5.png)

**圖 4-5**： 容器式應用程式的磁碟區和外部資料來源

此外，當 Docker 容器是由協調器所管理時，容器可能會根據叢集所執行的最佳化，在主機之間「移動」。 因此，不建議您使用資料磁碟區來儲存商務資料。 但針對追蹤檔案、時態性檔案或不影響商務資料一致性的類似檔案而言，這會是不錯的機制。

**遠端資料來源和快取**工具 (例如 Azure SQL Database、Azure Cosmos DB) 或遠端快取 (例如 Redis) 可用於容器化應用程式，就像是在沒有容器時用於開發一樣。 此方法經過實證，可儲存商務應用程式資料。

**Azure 儲存體。** 商務資料通常需要放在外部資源或資料庫中，例如 Azure 儲存體。 具體來說，Azure 儲存體會提供下列雲端服務：

- Blob 儲存體可儲存非結構化的物件資料。 Blob 可以是任何類型的文字或二進位資料，例如文件或媒體檔案 (影像、音訊和視訊檔案)。 Blob 儲存體也稱為物件儲存體。

- 檔案儲存體為使用標準 SMB 通訊協定的舊版應用程式提供共用存放裝置。 Azure 虛擬機器和雲端服務可透過掛接共用，在應用程式元件之間共用檔案資料。 內部部署應用程式可透過檔案服務 REST API，來存取共用中的檔案資料。

- 表格儲存體可儲存結構化的資料集。 表格儲存體是 NoSQL 索引鍵屬性資料存放區，可快速開發及存取大量資料。

**關聯式資料庫和 NoSQL 資料庫。** 外部資料庫的選擇有許多，從關聯式資料庫 (例如 SQL Server、PostgreSQL、Oracle) 到 NoSQL 資料庫 (例如 Azure Cosmos DB、MongoDB) 等等。這些資料庫由於是完全不同的主題，因此不會在本指南中說明。

>[!div class="step-by-step"]
>[上一頁](containerize-monolithic-applications.md)
>[下一頁](service-oriented-architecture.md)