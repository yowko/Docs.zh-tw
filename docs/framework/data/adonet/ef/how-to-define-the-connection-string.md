---
title: HOW TO：定義連接字串
ms.date: 03/30/2017
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
ms.openlocfilehash: 7fb722acbb13b3502d004978581701cc70118ff8
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53129684"
---
# <a name="how-to-define-the-connection-string"></a>HOW TO：定義連接字串

本主題將示範如何定義連接至概念模型時所使用的連接字串 (Connection String)。 本主題根據[AdventureWorks Sales](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100))概念模型。 AdventureWorks Sales Model 會在 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 文件的所有工作相關的主題內使用。 本主題假設您已經設定[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]並且定義 AdventureWorks Sales Model。 如需詳細資訊，請參閱[＜How to：手動定義模型和對應檔](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100))。 本主題中的程序也會包含在[How to:手動設定 Entity Framework 專案](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))。

> [!NOTE]
> 如果您使用[!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)]精靈在 Visual Studio 專案中，會自動產生.edmx 檔案並設定專案使用[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]。 如需詳細資訊，請參閱[＜How to：使用實體資料模型精靈](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))

## <a name="to-define-the-entity-framework-connection-string"></a>定義 Entity Framework 連接字串

- 開啟專案的應用程式組態檔 (app.config) 並加入下列連接字串：

```xml
<connectionStrings>
    <add name="AdventureWorksEntities" 
         connectionString="metadata=.\AdventureWorks.csdl|.\AdventureWorks.ssdl|.\AdventureWorks.msl;
         provider=System.Data.SqlClient;provider connection string='Data Source=localhost;
         Initial Catalog=AdventureWorks;Integrated Security=True;Connection Timeout=60;
         multipleactiveresultsets=true'" providerName="System.Data.EntityClient" />
</connectionStrings>
```

如果您的專案沒有應用程式組態檔，您可以加入一個方法是選取**加入新項目**從**專案**功能表上，選取**一般**類別選取**應用程式組態檔**，然後按一下**新增**。

## <a name="see-also"></a>另請參閱

- [快速入門](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))
- [操作說明：建立新.edmx 檔案](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))
- [ADO.NET 實體資料模型工具](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
