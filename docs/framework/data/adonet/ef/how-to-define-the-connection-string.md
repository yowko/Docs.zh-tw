---
title: HOW TO：定義連接字串
ms.date: 03/30/2017
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
ms.openlocfilehash: 9ce0b427cac17fc338877c5f85d3648d15d5ee14
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833957"
---
# <a name="how-to-define-the-connection-string"></a>HOW TO：定義連接字串

本主題將示範如何定義連接至概念模型時所使用的連接字串 (Connection String)。 本主題是以[AdventureWorks Sales](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100))概念模型為基礎。 AdventureWorks Sales Model 是在 Entity Framework 檔的整個工作相關主題中使用。 本主題假設您已經設定 Entity Framework 並定義 AdventureWorks Sales Model。 如需詳細資訊，請參閱[如何：手動定義模型和對應](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100))檔。 本主題中的程式也包含在[如何：手動設定 Entity Framework 專案](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))。

> [!NOTE]
> 如果您在 Visual Studio 專案中使用實體資料模型 Wizard，它會自動產生 .edmx 檔，並將專案設定為使用 Entity Framework。 如需詳細資訊，請參閱[如何：使用實體資料模型 Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))。

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

如果您的專案沒有應用程式佈建檔，您可以從 [**專案**] 功能表選取 [**新增專案**]、選取 [**一般**] 分類、選取 [**應用程式佈建檔**]，然後按一下 []，以加入一個檔案。**新增**。

## <a name="see-also"></a>另請參閱

- [快速入門](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))
- [如何：建立新的 .edmx 檔案](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))
- [ADO.NET 實體資料模型工具](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
