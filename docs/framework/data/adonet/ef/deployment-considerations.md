---
title: 部署考量 (Entity Framework)
ms.date: 03/30/2017
ms.assetid: 3a847a22-4eb8-4565-b18b-453bbca070db
ms.openlocfilehash: 7ab3827a9f2072f6f4b0c34f3801ee5dff2821d3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59199592"
---
# <a name="deployment-considerations-entity-framework"></a>部署考量 (Entity Framework)
本主題提供的資訊是有關部署使用 ADO.NET Entity Framework 進行資料存取的應用程式。 如需有關 Entity Framework 的詳細資訊，請參閱[開始使用](../../../../../docs/framework/data/adonet/ef/getting-started.md)。  
  
 Entity Framework 提供一組整合的工具，可讓您更輕鬆在 Visual Studio 中進行開發。 如需詳細資訊，請參閱 < [ADO.NET 實體資料模型工具](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))。 本主題未描述如何使用特定技術來部署 Entity Framework 架構應用程式。  
  
 Visual Studio 提供了散發及部署應用程式的機能，例如 ClickOnce 部署。 如需詳細資訊，請參閱 <<c0> [ 部署應用程式和元件](/visualstudio/deployment/deploying-applications-services-and-components)Visual Studio 文件中。  
  
 以下考量適用於當您部署使用 Entity Framework 的應用程式時：  
  
-   從 .NET Framework 3.5 Service Pack 1 (SP1) 開始，Entity Framework 就是 .NET Framework 的元件。 當您部署 Entity Framework 架構應用程式時，您必須確定 .NET Framework 3.5 SP1 或更新的版本已安裝。  
  
-   實體資料模型精靈產生概念模型之後，就會在應用程式組態檔中建立連接字串。 模型和對應檔可內嵌為應用程式資源，或是複製到輸出目錄。 根據預設，模型和對應檔會部署為內嵌應用程式資源。 使用 Entity Designer 檔案的 `Metadata Artifact Processing` 屬性，選取其中一個選項。 如需詳細資訊，請參閱[如何：複製模型，並將檔案對應到輸出目錄](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716709(v=vs.100))。  
  
-   請確認模型和對應檔資訊 (於概念結構定義語言 (CSDL)、存放結構定義語言 (SSDL) 和對應規格語言 (MSL) 中表示) 已與應用程式一起部署在連接字串所指定的位置 如需詳細資訊，請參閱[連接字串](../../../../../docs/framework/data/adonet/ef/connection-strings.md)。  
  
-   如果將內嵌模型和對應資訊內嵌為應用程式資源，每當概念模型更新時，就必須重新編譯和重新部署應用程式。  
  
-   因為 Entity Framework 是 .NET Framework 的元件，所以可以將它與應用程式一起轉散發，這是 .NET Framework 授權合約所允許的。  
  
## <a name="see-also"></a>另請參閱

- [ADO.NET Entity Framework](../../../../../docs/framework/data/adonet/ef/index.md)
- [開發和部署考量](../../../../../docs/framework/data/adonet/ef/development-and-deployment-considerations.md)
