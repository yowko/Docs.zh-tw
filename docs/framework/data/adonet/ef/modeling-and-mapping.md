---
title: "建立模型和對應"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ec8a9515-3708-4cde-a688-4d8e6975f150
caps.latest.revision: "7"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2004b950f1096f574734259ba02944577dd9adc9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="modeling-and-mapping"></a>建立模型和對應
在 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 中，您可以使用應用程式最適合的方式來定義概念模型、儲存體模型，以及兩者間的對應。 中的實體資料模型工具[!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)]可讓您建立。[edmx 檔案](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4)從資料庫或圖形化模型，然後更新該檔案在資料庫或模型變更時。  
  
 從 Entity Framework 4.1 開始，您也可以使用 Code First 開發透過程式設計方式建立模型。 Code First 開發有兩種不同的方案。 在這兩種情況下，開發人員透過編碼 .NET Framework 類別定義建立模型，然後選擇性地使用資料註解或 Fluent 應用程式開發介面指定其他對應或組態。  
  
 如需詳細資訊，請參閱[建立與對應概念模型](http://go.microsoft.com/fwlink/?LinkId=235016)。  
  
 您也可以使用 EDM 產生器隨附於[!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]。 EdmGen.exe 可從現有的資料來源產生 .csdl、.ssdl 和 .msl 檔。 您也可以手動建立模型和對應內容。 如需詳細資訊，請參閱[EDM 產生器 (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md)。
