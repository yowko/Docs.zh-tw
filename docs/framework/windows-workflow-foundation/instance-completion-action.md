---
title: 執行個體完成動作
ms.date: 03/30/2017
ms.assetid: 90cc99d2-9fef-42fd-bcbf-a56917993721
ms.openlocfilehash: d68f41a586e44f96c9ca26cf8a142a2782adaa36
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662969"
---
# <a name="instance-completion-action"></a>執行個體完成動作
**執行個體完成動作**SQL 工作流程執行個體存放區的屬性可讓您指定是否的資料和工作流程執行個體的中繼資料從持續性資料庫完成後，刪除執行個體。 允許的值，這個屬性為**DeleteAll**並**DeleteNothing**。 下列清單描述這些選項：  
  
- **DeleteAll （預設值）。** 如果將屬性的值設定為 DeleteAll，則在執行個體完成後，就會自持續性資料庫刪除工作流程執行個體的資料和中繼資料。  
  
- **DeleteNothing。** 如果將屬性的值設定為 DeleteNothing，則即使執行個體已完成，仍會將工作流程執行個體的資料和中繼資料保存在持續性資料庫中。  
  
    > [!CAUTION]
    >  在執行個體完成後仍保留執行個體狀態資訊，會使持續性資料庫變大。 隨著資料庫的擴充，持續性子系統執行資料庫作業的時間就會變長，因此您需要定期清除持續性資料庫中的執行個體狀態資訊，服務的執行層級才能符合您的效能需求。
