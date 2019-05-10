---
title: 控制 WCF 服務主機的自動啟動功能
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: 806d85df2a7fff63704db755400b81cc2dc5c37b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64652081"
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a>控制 WCF 服務主機的自動啟動功能
相同的 Visual Studio 方案包含多個專案中的另一個專案進行偵錯時，您可以控制 WCF 服務程式庫專案中，Windows Communication Foundation (WCF) 服務主機 (WcfSvcHost.exe) 的自動啟動功能。  
  
 若要這樣做，請以滑鼠右鍵按一下 WCF 服務專案中**方案總管**，選擇**屬性**，然後按一下**WCF 選項** 索引標籤。**啟動 WCF 服務主機時相同的方案中的另一個專案進行偵錯**預設會啟用 核取方塊。 如此一來這個特定專案的 WCF 服務主機就不會啟動另一個專案進行偵錯相同的方案時，您可以清除方塊。  
  
 這個行為不會影響這個專案的 F5 偵錯或是 [加入服務參考] 等功能。  
  
 這個選項可供下列專案使用：  
  
- WCF 服務程式庫專案。  
  
- 循序工作流程服務程式庫專案。  
  
- 狀態機器工作流程服務程式庫專案。  
  
- 新聞訂閱服務程式庫專案。  
  
## <a name="see-also"></a>另請參閱

- [WCF 服務主機 (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
