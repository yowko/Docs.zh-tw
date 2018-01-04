---
title: "執行個體編碼選項"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 89e4b029-4f68-438c-8117-9b21fe094ef4
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a7664eecb68ff9aec0f5e3e31aa08058700f0e92
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="instance-encoding-option"></a>執行個體編碼選項
**執行個體編碼選項**SQL 工作流程執行個體存放區的屬性可讓您指定 SQL 持續性提供者是否應該壓縮使用 GZip 演算法，之後再儲存工作流程執行個體狀態資訊將持續性資料庫的資訊。 此屬性允許的值為：GZip 和 None。 預設值為 None。 下列清單描述這些選項。  
  
1.  **GZip**。 將狀態資訊保存在持續性資料庫中之前，持續性提供者會利用 GZip 演算法編碼狀態資訊。  
  
2.  **無**。 將狀態資訊保存在持續性資料庫中之前，持續性提供者不會將狀態資訊編碼。  
  
 利用 GZip 編碼工作流程執行個體狀態資訊可以減少耗用 SQL 資料庫中的記憶體，同時也能減少耗用網路流量 (如果資料庫所在的電腦與執行工作流程服務主機的電腦位於不同的網路)。 通用準則是設定**執行個體編碼選項**屬性**無**如果工作流程執行個體狀態不大。
