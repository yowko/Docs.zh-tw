---
title: "在開發期間，安全地儲存應用程式密碼"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |在開發期間，安全地儲存應用程式密碼"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: f1b8b257a3e677c7e665e1d394a8adf7e651bec2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="storing-application-secrets-safely-during-development"></a>在開發期間，安全地儲存應用程式密碼

若要連接與受保護的資源和其他服務，ASP.NET Core 應用程式通常需要使用連接字串、 密碼或其他包含機密資訊的認證。 這些機密的資訊片段稱為*密碼*。 最佳作法是在原始程式碼中包含機密資料，當然不將密碼儲存在原始檔控制它。 相反地，您應該從更安全的位置讀取密碼使用 ASP.NET Core 組態模型。

您應該將用於存取開發和暫存資源，因為不同的個人將需要存取這些不同的密碼，以存取實際執行資源使用的密碼。 若要儲存在開發期間使用的密碼，常見的方法是請將密碼儲存在環境變數，或使用 ASP.NET Core 密碼管理員工具。 在生產環境中更安全的儲存體，microservices 可以將密碼儲存在 Azure 金鑰保存庫。

## <a name="storing-secrets-in-environment-variables"></a>環境變數中儲存機密資料

保留原始程式碼出的機密資料的其中一個方法是讓開發人員設定字串為基礎的密碼，做為[環境變數](https://docs.microsoft.com/aspnet/core/security/app-secrets#environment-variables)其開發電腦上。 當您使用環境變數以儲存機密資料，有名為階層式 （其組態區段中的巢狀），建立包含密碼的名稱的完整階層架構的環境變數名稱時，會以冒號 （:） 分隔。

例如，要進行偵錯設定環境變數記錄： LogLevel:Default 會等於下列 JSON 檔案中設定值：

```json
{
    "Logging": {
        "LogLevel": {
            "Default": "Debug"
        }
    }
}
```

若要存取這些值從環境變數，應用程式只需要建構 IConfigurationRoot 物件時，呼叫其 ConfigurationBuilder AddEnvironmentVariables。

請注意，環境變數通常會儲存為純文字，因此如果遭到入侵的電腦或使用環境變數的程序，會顯示環境變數值。

## <a name="storing-secrets-using-the-aspnet-core-secret-manager"></a>儲存機密資料，使用 ASP.NET Core 密碼管理員

ASP.NET Core[密碼管理員](https://docs.microsoft.com/aspnet/core/security/app-secrets#secret-manager)工具提供的原始碼超出保密的另一種方法。 若要使用密碼管理員工具，包含的工具參考 (DotNetCliToolReference) Microsoft.Extensions.SecretManager.Tools 封裝專案檔中。 一旦該相依性存在，並且已還原，dotnet 使用者密碼命令可用來從命令列設定密碼的值。 這些密碼將儲存在使用者的設定檔目錄中 （詳細資料會因作業系統），遠離原始碼在 JSON 檔案中。

密碼管理員工具來設定的密碼被依專案是使用密碼 UserSecretsId 屬性。 因此，您必須確定在專案檔 （如以下程式碼片段所示） 中設定 UserSecretsId 屬性。 用做為識別碼的實際字串並不重要，只要它是唯一的專案中。

```xml
<PropertyGroup>
    <UserSecretsId>UniqueIdentifyingString</UserSecretsId>
</PropertyGroup>
```

使用儲存在應用程式中使用密碼管理員密碼都會伴隨著呼叫 AddUserSecrets&lt;T&gt; ConfigurationBuilder 執行個體，要在其組態中包含機密資料的應用程式上。 泛型參數 T 應該是來自 UserSecretId 已套用至組件的類型。 通常使用 AddUserSecrets&lt;啟動&gt;是正常的。


>[!div class="step-by-step"]
[上一個](授權-網路-microservices-web-applications.md) [下一步] (azure-金鑰-保存庫-保護-secrets.md)
