---
title: "如何：定義連接字串"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 355d313fd607ccf85ba55b09b9ece4d9c88e298f
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-define-the-connection-string"></a>如何：定義連接字串
本主題將示範如何定義連接至概念模型時所使用的連接字串 (Connection String)。 本主題根據[AdventureWorks Sales](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832)概念模型。 AdventureWorks Sales Model 會在 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 文件的所有工作相關的主題內使用。 本主題假設您已經設定[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]和定義 AdventureWorks Sales Model。 如需詳細資訊，請參閱[How to： 手動定義模型和對應檔](http://msdn.microsoft.com/library/d4fd6864-f2a1-48f0-aa32-1e318775a99a)。 本主題中的程序也會包含在[How to： 手動設定 Entity Framework 專案](http://msdn.microsoft.com/library/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)。  
  
> [!NOTE]
>  如果在 [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] 專案中使用 [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] 精靈，精靈會自動產生 .edmx 檔案，並設定專案使用 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]。 如需詳細資訊，請參閱[How to： 使用實體資料模型精靈](http://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d)  
  
### <a name="to-define-the-entity-framework-connection-string"></a>定義 Entity Framework 連接字串  
  
-   開啟專案的應用程式組態檔 (app.config) 並加入下列連接字串：  
  
  
  
     如果您的專案沒有應用程式組態檔，您可以加入一個選取**加入新項目**從**專案**功能表上，選取**一般**類別目錄選取**應用程式組態檔**，然後按一下**新增**。  
  
## <a name="see-also"></a>請參閱  
 [快速入門](http://msdn.microsoft.com/library/0bc534be-789f-4819-b9f6-76e51d961675)  
 [如何： 建立新的.edmx 檔案](http://msdn.microsoft.com/library/beb8189e-e51c-4051-839c-9902c224abf2)  
 [ADO.NET 實體資料模型工具](http://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)
