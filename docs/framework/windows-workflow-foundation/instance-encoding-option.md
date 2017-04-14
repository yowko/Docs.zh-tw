---
title: "執行個體編碼選項 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 89e4b029-4f68-438c-8117-9b21fe094ef4
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# 執行個體編碼選項
SQL 工作流程執行個體存放區的**執行個體編碼選項**屬性可讓您指定 SQL 持續性提供者是否應先利用 GZip 演算法壓縮工作流程執行個體狀態資訊，再將此資訊儲存至持續性資料庫。此屬性允許的值為：GZip 和 None。預設值是 None。下列清單描述這些選項。  
  
1.  **GZip**：將狀態資訊保存在持續性資料庫中之前，持續性提供者會利用 GZip 演算法編碼狀態資訊。  
  
2.  **None**。將狀態資訊保存在持續性資料庫中之前，持續性提供者不會將狀態資訊編碼。  
  
 利用 GZip 編碼工作流程執行個體狀態資訊可以減少耗用 SQL 資料庫中的記憶體，同時也能減少耗用網路流量 \(如果資料庫所在的電腦與執行工作流程服務主機的電腦位於不同的網路\)。通用準則是將**執行個體編碼選項**屬性設為 **None** \(如果工作流程執行個體狀態不大\)。