---
title: 控制 WCF 服務主機的自動啟動功能
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: 63c3ca00c0cdc0b28de0fe245b616acd04ca50fe
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a>控制 WCF 服務主機的自動啟動功能
當您偵錯包含多個專案的相同 Visual Studio 方案中另一個專案時，您可以控制 WCF 服務程式庫專案中，Windows Communication Foundation (WCF) 服務主機 (WcfSvcHost.exe) 的自動啟動功能。  
  
 若要這樣做，請以滑鼠右鍵按一下 WCF 服務專案中**方案總管 中**，選擇**屬性**，然後按一下**WCF 選項** 索引標籤。**啟動 WCF 服務主機相同方案中的另一個專案進行偵錯時**核取方塊預設為啟用。 您可以清除方塊，以便在相同方案中的另一個專案進行偵錯時，將無法啟動這個特定專案的 WCF 服務主機。  
  
 這個行為不會影響這個專案的 F5 偵錯或是 [加入服務參考] 等功能。  
  
 這個選項可供下列專案使用：  
  
-   WCF 服務程式庫專案。  
  
-   循序工作流程服務程式庫專案。  
  
-   狀態機器工作流程服務程式庫專案。  
  
-   新聞訂閱服務程式庫專案。  
  
## <a name="see-also"></a>另請參閱  
 [WCF 服務主機 (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
