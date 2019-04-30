---
title: 建立模型和對應
ms.date: 03/30/2017
ms.assetid: ec8a9515-3708-4cde-a688-4d8e6975f150
ms.openlocfilehash: 847d518710b21df714343b541401ff7fc8443fb3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62034017"
---
# <a name="modeling-and-mapping"></a>建立模型和對應
在 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 中，您可以使用應用程式最適合的方式來定義概念模型、儲存體模型，以及兩者間的對應。 在 Visual Studio 中的實體資料模型工具可讓您建立。[edmx 檔案](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))從資料庫或圖形模型，然後更新該檔案在資料庫或模型變更時。  
  
 從 Entity Framework 4.1 開始，您也可以使用 Code First 開發透過程式設計方式建立模型。 Code First 開發有兩種不同的方案。 在這兩種情況下，開發人員透過編碼 .NET Framework 類別定義建立模型，然後選擇性地使用資料註解或 Fluent 應用程式開發介面指定其他對應或組態。  
  
 如需詳細資訊，請參閱 <<c0> [ 建立與對應概念模型](https://go.microsoft.com/fwlink/?LinkId=235016)。  
  
 您也可以使用 EDM 產生器隨附[!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]。 EdmGen.exe 可從現有的資料來源產生 .csdl、.ssdl 和 .msl 檔。 您也可以手動建立模型和對應內容。 如需詳細資訊，請參閱 < [EDM 產生器 (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md)。
