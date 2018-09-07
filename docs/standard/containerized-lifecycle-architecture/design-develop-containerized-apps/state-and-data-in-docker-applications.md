---
title: Docker 應用程式中的狀態和資料
description: Microsoft 平台和工具的容器化 Docker 應用程式生命週期
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 78db191bdec4c25c11728d819d89eaaaff4bd7da
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44070260"
---
# <a name="state-and-data-in-docker-applications"></a>Docker 應用程式中的狀態和資料

基本類型的容器是不變性。 相較於 VM，容器不會經常為會消失。 VM 可能會以不同的形式從終止程序、 多載的 CPU 或完整或失敗的磁碟失敗。 但是，我們預期可用的 VM，並 RAID 磁碟機是以確保磁碟機失敗維護資料的老生常談。

不過，容器會認為的處理序的執行個體。 處理程序不會維護持久狀態。 即使容器可以寫入其本機存放區，假設該執行個體將會解決無限期會等於假設單一複本的記憶體會持久。 您應該假設容器，例如處理序會重複，刪除，或管理由容器協調器，可能會移動。

Docker 使用的功能，稱為*重疊檔案系統*實作寫入時複製程序，會儲存任何容器，相較於原始的映像所依據的根檔案系統以更新的資訊。 如果之後從系統刪除容器時，會遺失這些變更。 容器，因此，不會預設不具有永續性儲存體。 雖然可以儲存容器的狀態，但設計系統，以解決這個問題是與容器架構的原則衝突。

若要管理 Docker 應用程式中的永續性資料，有常見的解決方案：

-   [**資料磁碟區**](https://docs.docker.com/engine/tutorials/dockervolumes/) 這些掛接至主機，如剛才所述。

-   [**資料磁碟區容器**](https://docs.docker.com/engine/tutorials/dockervolumes/#/creating-and-mounting-a-data-volume-container) 這些容器，使用可以循環的外部容器提供共用存放裝置。

-   [**磁碟區外掛程式**](https://docs.docker.com/engine/tutorials/dockervolumes/#/mount-a-shared-storage-volume-as-a-data-volume) 這些掛接至遠端位置，並提供長期持續性磁碟區。

-   **遠端資料來源** 範例包含 SQL 和 NO SQL 資料庫或快取服務，例如 Redis。

-   [**Azure 儲存體**](https://docs.microsoft.com/azure/storage/) 這做為服務 (PaaS) 的儲存體，提供最佳的容器，長期持續性提供異地散發平台。

資料磁碟區特別會指定略過的一或多個容器內的目錄[等位的檔案系統](https://docs.docker.com/glossary/?term=Union%20file%20system)。 資料磁碟區被設計來維護資料，容器的生命週期無關。 Docker 因此永遠不會自動刪除磁碟區時您移除容器，也無法將它容器所不再參考的 「 記憶體回收收集 「 磁碟區。 主機作業系統可以瀏覽並編輯任何磁碟區中的資料，這是要盡量不要使用資料磁碟區的只是另一個原因。

A[的資料磁碟區容器](https://docs.docker.com/glossary/?term=volume)一般資料磁碟區是一大改進。 它本質上是休眠容器具有一個或多個資料磁碟區，在其中建立 （如先前所述）。 資料磁碟區容器可讓您從中央掛接點存取容器。 這種存取方法的優點是，它會擷取原始的資料，讓資料容器的邏輯的掛接點的位置。 它也允許存取資料容器的而建立和終結同時專用容器中的永續性資料磁碟區的 [應用程式] 容器。

[圖 4-5] 顯示一般 Docker 磁碟區可置於容器本身錯亂但在主應用程式伺服器 VM/實體界限內的儲存體。 *Docker 磁碟區沒有使用到另一個 從一部主機伺服器/VM 的磁碟區的能力*。

![](./media/image5.png)

圖 4-5： 資料磁碟區和容器應用程式/容器的外部資料來源

因為無法管理在不同的實體主機執行的容器之間共用的資料，建議，除非您不使用磁碟區的商務資料的 Docker 主機已固定的主機/VM，因為當協調器時，在使用 Docker 容器容器應要移動一到另一部主機，根據叢集所執行的最佳化。

因此，一般資料磁碟區會使用追蹤檔案、 時態性檔案或任何類似的概念，或如果您的容器移動遍及多部主機時不會影響商務資料一致性的良好機制。

[磁碟區外掛程式](https://docs.docker.com/engine/extend/plugins_volume/)跨叢集中的所有主機提供的資料。 雖然並非所有的磁碟區外掛程式會建立方式都相同，但磁碟區外掛程式通常會提供已外部化永續性可靠的儲存體從不可變的容器。

遠端資料來源，例如 SQL Database、 DocumentDB 或遠端的快取，例如 Redis 快取會是不含容器開發相同。 這是其中一種慣用，且經過實證，來儲存商務應用程式資料。


>[!div class="step-by-step"]
[上一頁](monolithic-applications.md)
[下一頁](soa-applications.md)
