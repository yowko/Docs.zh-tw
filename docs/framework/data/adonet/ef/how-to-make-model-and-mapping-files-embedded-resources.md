---
title: HOW TO：讓模型和對應檔成為內嵌資源
ms.date: 03/30/2017
ms.assetid: 20dfae4d-e95a-4264-9540-f5ad23b462d3
ms.openlocfilehash: 371f8f0317295ee39d543b5637afb93102036b62
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854585"
---
# <a name="how-to-make-model-and-mapping-files-embedded-resources"></a>作法：讓模型和對應檔成為內嵌資源
此 Entity Framework 可讓您將模型和對應檔部署為應用程式的內嵌資源。 具有內嵌模型和對應檔的組件必須載入與實體連接相同的應用程式定義域中。 如需詳細資訊，請參閱[連接字串](connection-strings.md)。 根據預設，實體資料模型工具會內嵌模型和對應檔。 當您手動定義模型和對應檔時，請使用此程式，以確保檔案會部署為內嵌資源，以及 Entity Framework 應用程式。  
  
> [!NOTE]
> 若要維護內嵌資源，您必須在每次修改模型和對應檔時重複這個程序。  
  
### <a name="to-embed-model-and-mapping-files"></a>內嵌模型和對應檔  
  
1. 在 **方案總管**中，選取概念（csdl）檔案。  
  
2. 在 [**屬性**] 窗格中，將 [**組建動作**] 設定為 [**內嵌資源**]。  
  
3. 針對儲存 (.ssdl) 檔和對應檔 (.msl) 重複步驟 1 和 2。  
  
4. 在**方案總管**中，按兩下 app.config 檔案，然後根據下列其中一種格式`Metadata` ，修改`connectionString`屬性中的參數：  
  
    - `Metadata=` `res://<assemblyFullName>/<resourceName>;`  
  
    - `Metadata=` `res://*/<resourceName>;`  
  
    - `Metadata=res://*;`  
  
     如需詳細資訊，請參閱[連接字串](connection-strings.md)。  
  
## <a name="example"></a>範例  
 下列連接字串會參考[AdventureWorks Sales model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)的內嵌模型和對應檔。 此連接字串儲存在專案的 App.config 檔案中。  

## <a name="see-also"></a>另請參閱

- [建立模型和對應](modeling-and-mapping.md)
- [如何：定義連接字串](how-to-define-the-connection-string.md)
- [如何：建立 EntityConnection 連接字串](how-to-build-an-entityconnection-connection-string.md)
- [ADO.NET 實體資料模型工具](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
