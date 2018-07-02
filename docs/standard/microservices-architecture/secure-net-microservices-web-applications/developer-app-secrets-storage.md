---
title: 在開發期間安全地儲存應用程式祕密
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 在開發期間安全地儲存應用程式祕密
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 560120db35ae190bdef1f95d72ac1e5de697124e
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2018
ms.locfileid: "37105942"
---
# <a name="storing-application-secrets-safely-during-development"></a>在開發期間安全地儲存應用程式祕密

為了連接到受保護的資源和其他服務，ASP.NET Core 應用程式通常需要使用包含機密資訊的連接字串、密碼或其他認證。 這些機密資訊稱為「祕密」。 最佳做法是不要在原始程式碼中包含祕密，而且絕不要在原始檔控制中儲存秘密。 相反地，您應該使用 ASP.NET Core 組態模型，從更安全的位置讀取秘密。

您應該將用於存取開發和暫存資源的秘密，與用於存取生產資源的秘密分開，因為不同的人需要存取不同組的秘密。 若要儲存在開發期間使用的秘密，常見的方法是將秘密儲存在環境變數中，或藉由使用 ASP.NET Core Secret Manager 工具來儲存。 為了在生產環境中更安全的儲存，微服務可以將秘密儲存在 Azure Key Vault 中。

## <a name="storing-secrets-in-environment-variables"></a>將秘密儲存在環境變數中

將秘密與原始程式碼分開保存的一個方法，是由開發人員在其開發電腦上將字串型秘密設定為[環境變數](https://docs.microsoft.com/aspnet/core/security/app-secrets#environment-variables)。 當您使用環境變數來儲存具有階層式名稱 (巢狀於組態區段中) 的秘密時，請建立環境變數的名稱，其中包含秘密名稱的完整階層，並以冒號 (:) 分隔。

例如，將環境變數 Logging:LogLevel:Default 設定為 Debug 相當於下列 JSON 檔案中的組態值：

```json
{
    "Logging": {
        "LogLevel": {
            "Default": "Debug"
        }
    }
}
```

若要從環境變數存取這些值，應用程式只需要在建構 IConfigurationRoot 物件時在其 ConfigurationBuilder 上呼叫 AddEnvironmentVariables 即可。

請注意，環境變數通常會儲存為純文字，因此如果具有環境變數的電腦或處理序遭到入侵，就會顯示環境變數值。

## <a name="storing-secrets-using-the-aspnet-core-secret-manager"></a>使用 ASP.NET Core Secret Manager 儲存秘密

ASP.NET Core [Secret Manager](https://docs.microsoft.com/aspnet/core/security/app-secrets#secret-manager) 工具提供另一種方法來將秘密與原始程式碼分開保存。 若要使用 Secret Manager 工具，請在您的專案檔中包含 Microsoft.Extensions.SecretManager.Tools 封裝的工具參考 (DotNetCliToolReference)。 一旦該相依性存在並已還原，即可使用 dotnet user-secrets 命令從命令列設定秘密的值。 這些秘密會儲存在使用者設定檔目錄中的 JSON 檔案中 (細目會因 OS 而異)，並遠離原始程式碼。

Secret Manager 工具所設定的秘密會依使用秘密之專案的 UserSecretsId 屬性來組織。 因此，您必須確定在專案檔中設定 UserSecretsId 屬性 (如下列程式碼片段所示)。 識別碼只要在專案中是唯一的，所使用的實際字串並不重要。

```xml
<PropertyGroup>
    <UserSecretsId>UniqueIdentifyingString</UserSecretsId>
</PropertyGroup>
```

若要使用 Secret Manager 儲存在應用程式中的秘密，請在 ConfigurationBuilder 執行個體上呼叫 AddUserSecrets&lt;T&gt; 以在其組態中包含應用程式的秘密。 泛型參數 T 應該是已套用 UserSecretId 之組件的類型。 通常使用 AddUserSecrets&lt;Startup&gt; 就可以。


>[!div class="step-by-step"]
[上一頁](authorization-net-microservices-web-applications.md)
[下一頁](azure-key-vault-protects-secrets.md)
