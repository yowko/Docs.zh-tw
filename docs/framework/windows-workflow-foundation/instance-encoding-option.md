---
title: 執行個體編碼選項
ms.date: 03/30/2017
ms.assetid: 89e4b029-4f68-438c-8117-9b21fe094ef4
ms.openlocfilehash: 416394eb346a7c82385da32a89bd54179b255cd4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96279892"
---
# <a name="instance-encoding-option"></a>執行個體編碼選項

SQL 工作流程實例存放區的 **實例編碼選項** 屬性，可讓您指定 sql 持續性提供者是否應使用 GZip 演算法壓縮工作流程實例狀態資訊，再將資訊儲存至持續性資料庫中。 此屬性允許的值為：GZip 和 None。 預設值為 None。 下列清單描述這些選項。  
  
1. **GZip**。 將狀態資訊保存在持續性資料庫中之前，持續性提供者會利用 GZip 演算法編碼狀態資訊。  
  
2. **None**： 將狀態資訊保存在持續性資料庫中之前，持續性提供者不會將狀態資訊編碼。  
  
 利用 GZip 編碼工作流程執行個體狀態資訊可以減少耗用 SQL 資料庫中的記憶體，同時也能減少耗用網路流量 (如果資料庫所在的電腦與執行工作流程服務主機的電腦位於不同的網路)。 一般的指導方針是，如果工作流程實例的狀態很小，則將 [ **實例編碼選項** ] 屬性設定為 [ **無** ]。
