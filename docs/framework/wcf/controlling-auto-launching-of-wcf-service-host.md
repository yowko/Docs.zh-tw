---
title: 控制 WCF 服務主機的自動啟動功能
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: 2033e693003d0b50bcdada428e4a5f451b3ad67e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96255074"
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a>控制 WCF 服務主機的自動啟動功能

當您在包含多個專案的相同) 方案中，針對 WCF 服務程式庫專案的 Windows Communication Foundation (WCF) 服務主機 ( # A0 Visual Studio 時，您可以控制該專案的自動啟動功能。  
  
 若要這樣做，請在 **方案總管** 中的 WCF 服務專案上按一下滑鼠右鍵，選擇 [ **屬性**]，然後按一下 [ **WCF 選項** ] 索引標籤。預設會啟用 [在 **相同方案中偵錯工具時啟動 WCF 服務主機** ] 核取方塊。 您可以清除此方塊，讓這個特定專案的 WCF 服務主機不會在相同方案中的另一個專案進行調試時啟動。  
  
 這個行為不會影響這個專案的 F5 偵錯或是 [加入服務參考] 等功能。  
  
 這個選項可供下列專案使用：  
  
- WCF 服務程式庫專案。  
  
- 循序工作流程服務程式庫專案。  
  
- 狀態機器工作流程服務程式庫專案。  
  
- 新聞訂閱服務程式庫專案。  
  
## <a name="see-also"></a>另請參閱

- [WCF 服務主機 (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)
