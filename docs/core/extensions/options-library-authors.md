---
title: .NET 程式庫作者的選項模式指引
author: IEvangelist
description: 瞭解如何在 .NET 中以程式庫作者的形式公開選項模式。
ms.author: dapine
ms.date: 01/28/2021
ms.openlocfilehash: d0da94a8f25c9e5aba6093fab07ccca6a0a7c345
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2021
ms.locfileid: "99217210"
---
# <a name="options-pattern-guidance-for-net-library-authors"></a>.NET 程式庫作者的選項模式指引

在相依性插入的協助下，註冊您的服務及其對應的設定，就可以利用 *選項模式*。 選項模式可讓您程式庫 (的取用者和您的服務) 要求 [選項介面](options.md#options-interfaces) 的實例，其中 `TOptions` 是您的 options 類別。 透過強型別物件取用設定選項有助於確保一致的值表示，並移除手動剖析字串值的負擔。 您的程式庫取用者有許多設定 [提供者](configuration-providers.md) 可供使用。 透過這些提供者，取用者可以透過許多方式來設定您的程式庫。

作為 .NET 程式庫作者，您將瞭解如何正確地將選項模式公開給媒體櫃取用者的一般指引。 有各種不同的方式可以達成相同的內容，以及進行幾項考慮。

## <a name="naming-conventions"></a>命名規範

依照慣例，負責註冊服務的擴充方法會命名為 `Add{Service}` ，其中 `{Service}` 是有意義且描述性的名稱。 根據套件的不同，服務的註冊可能會伴隨 `Use{Service}` 擴充方法。 `Use{Service}`擴充方法在[ASP.NET Core](/aspnet)中很常見。

✔️考慮可讓您的服務與其他供應專案區分的名稱。

❌ 請勿使用已是官方 Microsoft 套件的 .NET 生態系統一部分的名稱。

✔️考慮將公開擴充方法的靜態類別命名為 `{Type}Extensions` ，其中 `{Type}` 是您要延伸的型別。

### <a name="namespace-guidance"></a>命名空間指引

Microsoft 套件會利用 `Microsoft.Extensions.DependencyInjection` 命名空間來統一註冊各種服務供應專案。

✔️考慮清楚識別套件供應專案的命名空間。

❌ 請勿將 `Microsoft.Extensions.DependencyInjection` 命名空間用於非官方 Microsoft 套件。

## <a name="parameterless"></a>依據

如果您的服務可以使用最少量或沒有明確的設定，請考慮使用無參數的擴充方法。

:::code language="csharp" source="snippets/configuration/options-noparams/ServiceCollectionExtensions.cs" highlight="10-14":::

在上述程式碼中， `AddMyLibraryService` ：

- 擴充的實例 <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>
- <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%60%601(Microsoft.Extensions.DependencyInjection.IServiceCollection)?displayProperty=nameWithType>使用型別參數的呼叫`LibraryOptions`
- 將呼叫連結至 <xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A> ，以指定預設選項值

## <a name="iconfiguration-parameter"></a>`IConfiguration` 參數

當您撰寫可向取用者公開許多選項的程式庫時，您可能會想要考慮要求 `IConfiguration` 參數擴充方法。 預期的 `IConfiguration` 實例應該使用函數，將範圍設定為設定的命名區段 <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A?displayProperty=nameWithType> 。

:::code language="csharp" source="snippets/configuration/options-configparam/ServiceCollectionExtensions.cs" highlight="10,12-16":::

在上述程式碼中， `AddMyLibraryService` ：

- 擴充的實例 <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>
- 定義 <xref:Microsoft.Extensions.Configuration.IConfiguration> 參數 `namedConfigurationSection`
- 傳遞設定所系結之 <xref:Microsoft.Extensions.Configuration.ConfigurationBinder.Bind(Microsoft.Extensions.Configuration.IConfiguration,System.Object)> 選項實例的呼叫

這種模式的取用者會提供 `IConfiguration` 已命名之區段的範圍實例：

:::code language="csharp" source="snippets/configuration/options-configparam/Program.cs" highlight="22-23":::

呼叫 `.AddMyLibraryService` 會在方法中進行 <xref:Microsoft.Extensions.Hosting.IHostBuilder.ConfigureServices%2A> 。 使用類別時也是如此 `Startup` ，註冊的服務也會在中進行 `ConfigureServices` 。

以程式庫作者來說，指定預設值是由您負責。

> [!NOTE]
> 您可以將設定系結至選項實例。 不過，有名稱衝突的風險，這會導致錯誤。 此外，當以這種方式手動系結時，您可以將選項模式的耗用量限制為唯讀。 設定的變更不會重新系結，因為這類取用者將無法使用 [IOptionsMonitor](options.md#ioptionsmonitor) 介面。
>
> ```csharp
> services.AddOptions<LibraryOptions>()
>     .Configure<IConfiguration>(
>         (options, configuration) =>
>             configuration.GetSection("LibraryOptions").Bind(options));
> ```

## <a name="actiontoptions-parameter"></a>`Action<TOptions>` 參數

您程式庫的取用者可能會想要提供 lambda 運算式來產生 options 類別的實例。 在此案例中，您會 `Action<LibraryOptions>` 在擴充方法中定義參數。

:::code language="csharp" source="snippets/configuration/options-action/ServiceCollectionExtensions.cs" highlight="10,12":::

在上述程式碼中， `AddMyLibraryService` ：

- 擴充的實例 <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>
- 定義 <xref:System.Action%601> where `T` 是 `LibraryOptions` 參數 `configureOptions`
- <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.Configure%2A>指定動作的 `configureOptions` 呼叫

這種模式的取用者會提供 lambda 運算式 (或符合 `Action<LibraryOptions>` 參數) 的委派：

:::code language="csharp" source="snippets/configuration/options-action/Program.cs" highlight="22-26":::

## <a name="options-instance-parameter"></a>選項實例參數

您程式庫的取用者可能會想要提供內嵌的選項實例。 在此案例中，您會公開擴充方法，以接受選項物件的實例 `LibraryOptions` 。

:::code language="csharp" source="snippets/configuration/options-object/ServiceCollectionExtensions.cs" highlight="9,11-17":::

在上述程式碼中， `AddMyLibraryService` ：

- 擴充的實例 <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>
- <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%60%601(Microsoft.Extensions.DependencyInjection.IServiceCollection)?displayProperty=nameWithType>使用型別參數的呼叫`LibraryOptions`
- 將呼叫連結到 <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.Configure%2A> ，指定可以從指定的實例覆寫的預設選項值 `userOptions`

這種模式的取用者會提供類別的實例，並以 `LibraryOptions` 內嵌方式定義所需的屬性值：

:::code language="csharp" source="snippets/configuration/options-object/Program.cs" highlight="22-26":::

## <a name="post-configuration"></a>設定前

系結或指定所有設定選項值之後，便可使用 post 設定功能。 如先前所述公開相同的[ `Action<TOptions>` 參數](#actiontoptions-parameter)，您可以選擇呼叫 <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigure%2A> 。 Post 設定會在所有 `.Configure` 呼叫之後執行。

:::code language="csharp" source="snippets/configuration/options-postconfig/ServiceCollectionExtensions.cs" highlight="10,12":::

在上述程式碼中， `AddMyLibraryService` ：

- 擴充的實例 <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>
- 定義 <xref:System.Action%601> where `T` 是 `LibraryOptions` 參數 `configureOptions`
- <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigure%2A>指定動作的 `configureOptions` 呼叫

這種模式的取用者會提供 lambda 運算式 (或符合 `Action<LibraryOptions>` 參數) 的委派，就像 `Action<TOptions>` 在非 post 設定案例中使用 [參數] 一樣：

:::code language="csharp" source="snippets/configuration/options-postconfig/Program.cs" highlight="22-26":::

## <a name="see-also"></a>另請參閱

- [.NET 中的選項模式](options.md)
- [.NET 中的相依性插入](dependency-injection.md)
- [相依性插入指導方針](dependency-injection-guidelines.md)
