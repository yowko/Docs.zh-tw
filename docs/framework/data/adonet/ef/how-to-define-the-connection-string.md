---
title: 如何：定義連接字串
ms.date: 03/30/2017
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
ms.openlocfilehash: f40b8bc68eda1cb4b64b34d12b2922da69929203
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44210158"
---
# <a name="how-to-define-the-connection-string"></a>如何：定義連接字串
本主題將示範如何定義連接至概念模型時所使用的連接字串 (Connection String)。 本主題根據[AdventureWorks Sales](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832)概念模型。 AdventureWorks Sales Model 會在 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 文件的所有工作相關的主題內使用。 本主題假設您已經設定[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]並且定義 AdventureWorks Sales Model。 如需詳細資訊，請參閱 <<c0> [ 如何： 手動定義模型和對應檔](https://msdn.microsoft.com/library/d4fd6864-f2a1-48f0-aa32-1e318775a99a)。 本主題中的程序也會包含在[如何： 手動設定 Entity Framework 專案](https://msdn.microsoft.com/library/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)。  
  
> [!NOTE]
>  如果您使用[!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)]精靈在 Visual Studio 專案中，會自動產生.edmx 檔案並設定專案使用[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]。 如需詳細資訊，請參閱[How to： 使用實體資料模型精靈](https://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d)  
  
### <a name="to-define-the-entity-framework-connection-string"></a>定義 Entity Framework 連接字串  
  
-   開啟專案的應用程式組態檔 (app.config) 並加入下列連接字串：  
  
  
  
     如果您的專案沒有應用程式組態檔，您可以加入一個方法是選取**加入新項目**從**專案**功能表上，選取**一般**類別選取**應用程式組態檔**，然後按一下**新增**。  
  
## <a name="see-also"></a>另請參閱  
 [快速入門](https://msdn.microsoft.com/library/0bc534be-789f-4819-b9f6-76e51d961675)  
 [如何： 建立新.edmx 檔案](https://msdn.microsoft.com/library/beb8189e-e51c-4051-839c-9902c224abf2)  
 [ADO.NET 實體資料模型工具](https://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)
