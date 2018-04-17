---
title: Docker 應用程式中的狀態和資料
description: Microsoft 平台和工具的容器化 Docker 應用程式生命週期
ms.prod: .net
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 83094cd9a13d77f489df639096bb42b23ce152e7
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="state-and-data-in-docker-applications"></a>Docker 應用程式中的狀態和資料

基本的容器項目是不變性。 相較於 VM，容器就不會經常為消失。 VM 可能會以不同的形式從終止程序、 多載的 CPU 或完整或失敗的磁碟失敗。 棒的是，我們預期可用 VM 和 RAID 磁碟機以確保磁碟機失敗維護資料相差不多。

不過，容器凡是系統認為是處理程序的執行個體。 處理程序不會維護持久狀態。 即使容器可以寫入其本機儲存體，假設該執行個體將會無限期周圍就會相當於假設單一複本記憶體將會永久性。 您應該假設重複容器，例如處理程序，刪除，或當容器 orchestrator 的管理，可能會移動。

Docker 使用功能，又稱為*重疊檔案系統*若要實作儲存任何寫入時複製程序更新容器，相較於原始的映像所依據的根檔案系統資訊。 如果從系統，接下來刪除容器，這些變更會遺失。 一種容器，因此，沒有永續性儲存體預設。 雖然可以儲存容器的狀態，在設計系統，以解決這個問題會是與容器架構的原則衝突。

若要管理 Docker 應用程式中的永續性資料，有常見的解決方案：

-   [**資料磁碟區**](https://docs.docker.com/engine/tutorials/dockervolumes/) 這些掛接至主機，如剛才所述。

-   [**資料磁碟區容器**](https://docs.docker.com/engine/tutorials/dockervolumes/#/creating-and-mounting-a-data-volume-container) 這些容器，使用可以循環的外部容器提供共用存放裝置。

-   [**磁碟區外掛程式**](https://docs.docker.com/engine/tutorials/dockervolumes/#/mount-a-shared-storage-volume-as-a-data-volume) 這些掛接至遠端位置，提供長期持續性的磁碟區。

-   **遠端資料來源** 範例包括 SQL 和 NO SQL 資料庫或服務，例如 Redis 快取。

-   [**Azure 儲存體**](https://docs.microsoft.com/azure/storage/) 這會提供地理可散布平台做為服務 (PaaS) 儲存，以長期持續性提供最佳的容器。

資料磁碟區會特別指定略過的一或多個容器內的目錄[聯集的檔案系統](https://docs.docker.com/v1.8/reference/glossary#union-file-system)。 資料磁碟區被設計來維護容器的生命週期的獨立資料。 Docker 因此永遠不會自動刪除磁碟區時您移除容器，也無法將它不再參考由容器的 「 記憶體回收收集 「 磁碟區。 主機作業系統可以瀏覽和編輯任何磁碟區中的資料自由，即盡量不要使用資料磁碟區只是另一個原因。

A[資料磁碟區容器](https://docs.docker.com/v1.8/userguide/dockervolumes/)是一般資料磁碟區。 其本質上是休眠容器具有一個或多個資料磁碟區，在其中建立 （如先前所述）。 資料磁碟區容器可讓您從中央掛接點存取容器。 這種存取方法的優點是它擷取原始的資料，讓資料容器的邏輯的掛接點的位置。 它也允許存取資料容器的磁碟區建立和終結同時資料持續性專用的容器中的 「 應用程式 」 容器。

圖 4-5 顯示規則的 Docker 磁碟區可以置於容器本身之外，但主應用程式伺服器 VM/實體界限內的儲存體。 *Docker 磁碟區沒有使用從一部主機伺服器/VM 到另一個磁碟區的能力*。

![](./media/image5.png)

圖 4-5： 資料磁碟區和容器應用程式/容器的外部資料來源

因為無法管理個別的實體主機執行的容器之間共用的資料，建議您不要使用磁碟區的商務資料除非 Docker 主機已固定的主機/VM，因為在 orchestrator 中，使用 Docker 容器時容器應該要移動一到另一部主機，根據在叢集中所要執行的最佳化。

因此，一般資料磁碟區會使用追蹤檔案、 暫存檔案或任何類似的概念，或如果您的容器移動遍及多部主機時不會影響商務資料一致性的良好機制。

磁碟區外掛程式喜歡[Flocker](https://clusterhq.com/flocker/)不同叢集中所有主機之間提供資料。 雖然並非所有的磁碟區外掛程式建立同樣地，磁碟區外掛程式通常提供外部化持續的可靠存放在不可變的容器。

遠端資料來源，例如 SQL Database、 DocumentDB 或遠端像 Redis 快取的快取會做為開發容器不相同。 這是一種慣用及經過驗證，來儲存商業應用程式資料。


>[!div class="step-by-step"]
[上一個] (龐大-applications.md) [下一步] (soa applications.md)
