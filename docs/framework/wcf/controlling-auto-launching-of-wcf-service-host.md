---
title: 控制 WCF 服務主機的自動啟動功能
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: 7f21cd7ea600277461146387b962a89ea0a8472b
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320632"
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a>控制 WCF 服務主機的自動啟動功能
您可以控制 WCF 服務程式庫專案的 Windows Communication Foundation （WCF）服務主機（WcfSvcHost）的自動啟動功能，當您在同一個包含多個專案的 Visual Studio 方案中，對另一個專案進行偵錯工具。  
  
 若要這樣做，請在**方案總管**的 WCF 服務專案上按一下滑鼠右鍵，選擇 [**屬性**]，然後按一下 [ **WCF 選項**] 索引標籤。預設會啟用 [在**同一個方案中偵測到另一個專案時啟動 WCF 服務主機**] 核取方塊。 您可以清除此方塊，如此一來，在相同的方案中調試另一個專案時，就不會啟動此特定專案的 WCF 服務主機。  
  
 這個行為不會影響這個專案的 F5 偵錯或是 [加入服務參考] 等功能。  
  
 這個選項可供下列專案使用：  
  
- WCF 服務程式庫專案。  
  
- 循序工作流程服務程式庫專案。  
  
- 狀態機器工作流程服務程式庫專案。  
  
- 新聞訂閱服務程式庫專案。  
  
## <a name="see-also"></a>請參閱

- [WCF 服務主機 (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)
