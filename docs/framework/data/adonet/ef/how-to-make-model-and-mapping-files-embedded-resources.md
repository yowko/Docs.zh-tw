---
title: 作法：讓模型和對應檔成為內嵌資源
ms.date: 03/30/2017
ms.assetid: 20dfae4d-e95a-4264-9540-f5ad23b462d3
ms.openlocfilehash: 3abb0ead210903a4ac2d16e4a977aaefbcde8ceb
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/21/2019
ms.locfileid: "67307351"
---
# <a name="how-to-make-model-and-mapping-files-embedded-resources"></a>作法：讓模型和對應檔成為內嵌資源
[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]可讓您部署模型和對應檔做為內嵌資源的應用程式。 具有內嵌模型和對應檔的組件必須載入與實體連接相同的應用程式定義域中。 如需詳細資訊，請參閱[連接字串](../../../../../docs/framework/data/adonet/ef/connection-strings.md)。 根據預設，Entity Data Model 工具會內嵌模型和對應檔。 當您手動定義模型和對應檔時，請使用這個程序，確保檔案與 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 應用程式已一起部署為內嵌資源。  
  
> [!NOTE]
>  若要維護內嵌資源，您必須在每次修改模型和對應檔時重複這個程序。  
  
### <a name="to-embed-model-and-mapping-files"></a>內嵌模型和對應檔  
  
1. 在 [**方案總管] 中**，選取概念 (.csdl) 檔案。  
  
2. 在 **屬性**窗格中，將**建置動作**來**內嵌資源**。  
  
3. 針對儲存 (.ssdl) 檔和對應檔 (.msl) 重複步驟 1 和 2。  
  
4. 在**方案總管**中，按兩下 App.config 檔案，然後修改`Metadata`中的參數`connectionString`屬性根據下列格式之一：  
  
    - `Metadata=` `res://<assemblyFullName>/<resourceName>;`  
  
    - `Metadata=` `res://*/<resourceName>;`  
  
    - `Metadata=res://*;`  
  
     如需詳細資訊，請參閱[連接字串](../../../../../docs/framework/data/adonet/ef/connection-strings.md)。  
  
## <a name="example"></a>範例  
 下列連接字串參考內嵌的模型和對應檔[AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)。 此連接字串儲存在專案的 App.config 檔案中。  

## <a name="see-also"></a>另請參閱

- [建立模型和對應](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)
- [如何：定義連接字串](../../../../../docs/framework/data/adonet/ef/how-to-define-the-connection-string.md)
- [如何：建置 Entitycollection 連接字串](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)
- [ADO.NET 實體資料模型工具](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
