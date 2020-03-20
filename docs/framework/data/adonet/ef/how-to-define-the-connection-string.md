---
title: 如何：定義連接字串
ms.date: 03/30/2017
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
ms.openlocfilehash: e5b675a50f883825cce97275048447b79b64cc97
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150567"
---
# <a name="how-to-define-the-connection-string"></a>如何：定義連接字串

本主題將示範如何定義連接至概念模型時所使用的連接字串 (Connection String)。 本主題基於[AdventureWorks 銷售](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100))概念模型。 AdventureWorks 銷售模型用於實體框架文檔中與任務相關的主題。 本主題假定您已配置實體框架並定義了 AdventureWorks 銷售模型。 有關詳細資訊，請參閱[如何：手動定義模型和映射檔](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100))。 本主題中的過程也包含在["如何：手動設定實體框架專案](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))"中。

> [!NOTE]
> 如果在 Visual Studio 專案中使用實體資料模型嚮導，它會自動生成 .edmx 檔並將專案配置為使用實體框架。 有關詳細資訊，請參閱[：使用實體資料模型嚮導](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))。

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

如果專案沒有應用程式佈建檔，則可以通過從 **"專案**"功能表中選擇 **"添加新專案**"、選擇 **"常規**類別"、"選擇**應用程式佈建檔**"以及按一下"**添加**"來添加一個設定檔。

## <a name="see-also"></a>另請參閱

- [快速入門](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))
- [HOW TO：建立新 .edmx 檔案](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))
- [ADO.NET 實體資料模型工具](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
