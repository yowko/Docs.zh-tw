---
title: 控制 WCF 服務主機的自動啟動功能
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: 2fa060e567fba9bb5e6344b2c8fc67fb639ad0f7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61608446"
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
