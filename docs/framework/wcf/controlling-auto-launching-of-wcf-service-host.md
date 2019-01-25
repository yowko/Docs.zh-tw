---
title: 控制 WCF 服務主機的自動啟動功能
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: f7f58a684449819fe945ad1ba5bff12f425c8294
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54712388"
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a>控制 WCF 服務主機的自動啟動功能
相同的 Visual Studio 方案包含多個專案中的另一個專案進行偵錯時，您可以控制 WCF 服務程式庫專案中，Windows Communication Foundation (WCF) 服務主機 (WcfSvcHost.exe) 的自動啟動功能。  
  
 若要這樣做，請以滑鼠右鍵按一下 WCF 服務專案中**方案總管**，選擇**屬性**，然後按一下**WCF 選項** 索引標籤。**啟動 WCF 服務主機時相同的方案中的另一個專案進行偵錯**預設會啟用 核取方塊。 如此一來這個特定專案的 WCF 服務主機就不會啟動另一個專案進行偵錯相同的方案時，您可以清除方塊。  
  
 這個行為不會影響這個專案的 F5 偵錯或是 [加入服務參考] 等功能。  
  
 這個選項可供下列專案使用：  
  
-   WCF 服務程式庫專案。  
  
-   循序工作流程服務程式庫專案。  
  
-   狀態機器工作流程服務程式庫專案。  
  
-   新聞訂閱服務程式庫專案。  
  
## <a name="see-also"></a>另請參閱
- [WCF 服務主機 (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
