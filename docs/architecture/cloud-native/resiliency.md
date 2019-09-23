---
title: 雲端原生復原
description: 架構適用于 Azure 的雲端原生 .NET 應用程式 |雲端原生復原
ms.date: 06/30/2019
ms.openlocfilehash: 680542abc5d8c43c577321d5ae834f0a13290da3
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184838"
---
# <a name="cloud-native-resiliency"></a>雲端原生復原

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

復原是指您的系統對失敗做出反應的能力，而且仍然可以繼續運作。 這不是為了避免失敗。 但它是關於在雲端式系統中接受這項失敗的問題，並建立您的應用程式來回應它。 復原的最終目標是要在失敗後將應用程式恢復為完全正常運作的狀態。

與傳統的整合型應用程式不同的是，在單一進程中，所有專案都在一起執行，雲端原生系統採用分散式架構，如圖6-1 所示：

![分散式雲端-原生環境](./media/distributed-cloud-native-environment.png)

**圖 6-1。** 分散式雲端-原生環境

在上圖中，請注意每個用戶端、微服務和以雲端為基礎的[支援服務](https://12factor.net/backing-services)如何以個別的進程執行，在不同的伺服器上執行，全都透過網路呼叫進行通訊。

那麼，發生什麼問題？

- 未預期的[網路延遲](https://www.techopedia.com/definition/8553/network-latency)。
- [暫時性錯誤](https://docs.microsoft.com/azure/architecture/best-practices/transient-faults)（暫時性的網路連接錯誤）。
- 由長時間執行的同步作業封鎖。
- 已損毀且正在重新開機或移動的主機進程。
- 無法回應短時間的多載微服務。
- 進行中的 DevOps 作業，例如更新或調整規模作業。
- 協調器作業，例如將服務從一個節點移至另一個節點。
- 商用硬體的硬體失敗。

將分散式服務部署到雲端式基礎結構時，先前清單中的因素會變得非常真實，而且您必須設計和開發依舊撰寫, 來處理它們。

在小規模的分散式系統中，失敗會較不頻繁，但隨著系統相應增加和相應放大，您可以預期在部分失敗變成正常作業的情況下，遇到更多問題。

因此，您的應用程式和基礎結構必須具備復原能力。 在下列各節中，我們將探索您可以加入應用程式的防禦技術，以及您可以利用的內建雲端功能，協助您的使用者體驗。

>[!div class="step-by-step"]
>[上一頁](azure-data-storage.md)
>[下一頁](application-resiliency-patterns.md)
