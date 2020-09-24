---
title: 雲端原生復原
description: 設計適用于 Azure 的雲端原生 .NET 應用程式 |雲端原生復原
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: 5c4fb261515c151fd666cc33cbb020447716c814
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91163553"
---
# <a name="cloud-native-resiliency"></a>雲端原生復原

復原是指系統對失敗做出反應的能力，而且仍維持正常運作。 這並不是為了避免失敗，而是接受失敗並建立雲端原生服務來回應。 您想要儘快恢復正常運作的狀態。

與傳統的整合型應用程式不同的是，所有專案都會在單一程式中一起執行，雲端原生系統採用分散式架構，如圖6-1 所示：

![分散式雲端原生環境](./media/distributed-cloud-native-environment.png)

**圖6-1。** 分散式雲端原生環境

在上圖中，每個微服務和以雲端為基礎的 [支援服務](https://12factor.net/backing-services) 都會在不同的進程中執行，而跨伺服器基礎結構，透過網路型呼叫進行通訊。

在此環境中操作時，服務必須區分許多不同的挑戰：

- 非預期的網路延遲-服務要求傳送到接收者的時間。

- [暫時性錯誤](/azure/architecture/best-practices/transient-faults) -短暫的網路連接錯誤。

- 由長時間執行的同步作業來封鎖。

- 已損毀且正在重新開機或移動的主機進程。

- 無法回應短時間的多載微服務。

- 進行中的協調器作業，例如輪流升級或將服務從某個節點移至另一個節點。

- 硬體故障。

雲端平臺可以偵測和緩和許多這些基礎結構問題。 它可能會重新開機、向外延展，甚至將您的服務轉散發至不同的節點。  不過，若要充分利用此內建保護功能，您必須設計您的服務來對其做出反應，並在這個動態環境中發展。

在下列各節中，我們將探索您的服務和受控雲端資源可利用的防禦技術，以將停機時間和停機時間降至最低。

>[!div class="step-by-step"]
>[上一個](elastic-search-in-azure.md) 
>[下一步](application-resiliency-patterns.md)
