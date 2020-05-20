---
title: 雲端原生復原
description: 架構適用于 Azure 的雲端原生 .NET 應用程式 |雲端原生復原
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: f3aa89e3ae21b13a31f65013b59636b3f931553c
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83613768"
---
# <a name="cloud-native-resiliency"></a>雲端原生復原

復原是指您的系統對失敗做出反應的能力，而且仍然可以繼續運作。 這不是為了避免失敗，而是要接受失敗並建立雲端原生服務來回應。 您想要儘快回到完全正常運作的狀態。

與傳統的整合型應用程式不同的是，在單一進程中，所有專案都在一起執行，雲端原生系統採用分散式架構，如圖6-1 所示：

![分散式雲端-原生環境](./media/distributed-cloud-native-environment.png)

**圖6-1。** 分散式雲端-原生環境

在上圖中，每個微服務和雲端式[支援服務](https://12factor.net/backing-services)都會在不同的進程中執行，跨伺服器基礎結構，透過網路呼叫進行通訊。

在此環境中操作時，服務必須區分許多不同的挑戰：

- 非預期的網路延遲-服務要求傳送至接收者並返回的時間。

- [暫時性錯誤](https://docs.microsoft.com/azure/architecture/best-practices/transient-faults)-短期網路連線錯誤。

- 由長時間執行的同步作業所封鎖。

- 已損毀且正在重新開機或移動的主機進程。

- 無法回應短時間的多載微服務。

- 進行中的協調器作業，例如輪流升級或將服務從一個節點移至另一個節點。

- 硬體故障。

雲端平臺可以偵測並減輕其中許多基礎結構問題。 它可能會重新開機、相應放大，甚至將您的服務轉散發至不同的節點。  不過，若要充分利用這項內建保護功能，您必須設計您的服務，以在此動態環境中對 it 和發展做出反應。

在下列各節中，我們將探索您的服務和受控雲端資源可以利用的防禦技術，將停機時間和停機時間降到最低。

>[!div class="step-by-step"]
>[上一個](elastic-search-in-azure.md) 
>[下一步](application-resiliency-patterns.md)
