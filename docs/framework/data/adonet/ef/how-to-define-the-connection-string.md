---
title: 作法：定義連接字串
ms.date: 03/30/2017
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
ms.openlocfilehash: 9b029644e0d4e4c7467fbe1e1144579e6edb3478
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90536206"
---
# <a name="how-to-define-the-connection-string"></a>作法：定義連接字串

本主題將示範如何定義連接至概念模型時所使用的連接字串 (Connection String)。 本主題是以 [AdventureWorks Sales](/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) 概念模型為基礎。 AdventureWorks Sales Model 是在 Entity Framework 檔的工作相關主題中使用。 本主題假設您已經設定 Entity Framework 並定義 AdventureWorks Sales Model。 如需詳細資訊，請參閱 [如何：手動定義模型和對應](/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100))檔。 本主題中的程式也包含在 how [to：手動設定 Entity Framework 專案](/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))中。

> [!NOTE]
> 如果您在 Visual Studio 專案中使用實體資料模型 Wizard，它會自動產生 .edmx 檔，並將專案設定為使用 Entity Framework。 如需詳細資訊，請參閱 [如何：使用實體資料模型 Wizard](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))。

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

如果您的專案沒有應用程式佈建檔，您可以從 [**專案**] 功能表中選取 [**加入新專案**]，選取 [**一般**] 類別，選取 [**應用程式佈建檔**]，然後按一下 [**新增**]，以新增一個應用程式佈建檔。

## <a name="see-also"></a>另請參閱

- [快速入門](/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))
- [HOW TO：建立新 .edmx 檔案](/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))
- [ADO.NET 實體資料模型工具](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
