---
title: "控制 WCF 服務主機的自動啟動功能"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: dc89ed3ae41471af49fc92f31834f0ae268309dd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a>控制 WCF 服務主機的自動啟動功能
在針對包含多個專案之相同 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 方案中的另一個專案進行偵錯時，您可以控制 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務程式庫專案中 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 服務主機 (WcfSvcHost.exe) 的自動啟動功能。  
  
 若要這樣做，請以滑鼠右鍵按一下[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]服務專案中**方案總管 中**，選擇**屬性**，然後按一下**WCF 選項** 索引標籤。**啟動 WCF 服務主機相同方案中的另一個專案進行偵錯時**核取方塊預設為啟用。 您可以清除這個方塊，這樣一來這個特定專案的 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務主機就不會在相同方案中的另一個專案進行偵錯時啟動。  
  
 這個行為不會影響這個專案的 F5 偵錯或是 [加入服務參考] 等功能。  
  
 這個選項可供下列專案使用：  
  
-   [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務程式庫專案。  
  
-   循序工作流程服務程式庫專案。  
  
-   狀態機器工作流程服務程式庫專案。  
  
-   新聞訂閱服務程式庫專案。  
  
## <a name="see-also"></a>另請參閱  
 [WCF 服務主機 (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
