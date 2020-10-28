---
title: 使用 .NET 中的相依性插入
description: 瞭解如何在您的 .NET 應用程式中使用相依性插入。
author: IEvangelist
ms.author: dapine
ms.date: 09/23/2020
ms.topic: tutorial
no-loc:
- Transient
- Scoped
- Singleton
- Example
ms.openlocfilehash: 589e15736c07b465fda308b04c91384a2502755c
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2020
ms.locfileid: "92888582"
---
# <a name="tutorial-use-dependency-injection-in-net"></a>教學課程：在 .NET 中使用相依性插入

本教學課程說明如何 [在 .net 中使用相依性插入 (DI) ](dependency-injection.md)。 使用 *Microsoft 擴充* 功能時，DI 是在中新增和設定服務的第一類公民 <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection> 。 <xref:Microsoft.Extensions.Hosting.IHost>介面會公開 <xref:System.IServiceProvider> 實例，作為所有已註冊服務的容器。

在本教學課程中，您會了解如何：

> [!div class="checklist"]
>
> - 建立使用相依性插入的 .NET 主控台應用程式
> - 建立並設定 [泛型主機](generic-host.md)
> - 撰寫數個介面和對應的實作為
> - 針對 DI 使用服務存留期和範圍

## <a name="prerequisites"></a>先決條件

- [.Net Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core) 或更新版本。
- 熟悉如何建立新的 .NET 應用程式及安裝 NuGet 套件。

## <a name="create-a-new-console-application"></a>建立新的主控台應用程式

使用 [dotnet new](../tools/dotnet-new.md)命令或 IDE [新增專案] 嚮導，建立名為 **Example ConsoleDI** 的新 .net 主控台應用程式。 將 [裝載](https://www.nuget.org/packages/Microsoft.Extensions.Hosting) NuGet 套件的專案新增至專案。

## <a name="add-interfaces"></a>新增介面

將下列介面新增至專案根目錄：

*IOperation.cs*

:::code language="csharp" source="snippets/configuration/console-di/IOperation.cs":::

`IOperation`介面會定義單一 `OperationId` 屬性。

*我 Transient Operation.cs*

：：： code language = "csharp" source = "程式碼片段/設定/主控台-di/I Transient Operation.cs"：：：

*我 Scoped Operation.cs*

：：： code language = "csharp" source = "程式碼片段/設定/主控台-di/I Scoped Operation.cs"：：：

*我 Singleton Operation.cs*

：：： code language = "csharp" source = "程式碼片段/設定/主控台-di/I Singleton Operation.cs"：：：

`IOperation`其預期服務存留期的所有名稱子介面。 例如，" Transient " 或 " Singleton "。

## <a name="add-default-implementation"></a>新增預設實作為

針對各種作業新增下列預設實作為：

*DefaultOperation.cs*

:::code language="csharp" source="snippets/configuration/console-di/DefaultOperation.cs":::

會實作為 `DefaultOperation` 所有命名標記介面，並將 `OperationId` 屬性初始化為新全域唯一識別碼 (GUID) 的最後四個字元。

## <a name="add-service-that-requires-di"></a>新增需要 DI 的服務

新增下列作業記錄器物件，作為主控台應用程式的服務：

*OperationLogger.cs*

:::code language="csharp" source="snippets/configuration/console-di/OperationLogger.cs":::

`OperationLogger`會定義需要上述每一個標記介面的函式，也就是 `ITransientOperation` 、 `IScopedOperation` 和 `ISingletonOperation` 。 此物件會公開單一方法，讓取用者使用指定的參數來記錄作業 `scope` 。 叫用時， `LogOperations` 方法會使用範圍字串和訊息來記錄每個作業的唯一識別碼。

## <a name="register-services-for-di"></a>註冊適用于 DI 的服務

使用下列程式碼更新 *Program.cs* ：

:::code language="csharp" source="snippets/configuration/console-di/Program.cs" range="1-18,35-60" highlight="22-26":::

應用程式：

- <xref:Microsoft.Extensions.Hosting.IHostBuilder>使用預設系結器[設定](generic-host.md#default-builder-settings)建立實例。
- 設定服務，並將其新增至其對應的服務存留期。
- 呼叫 <xref:Microsoft.Extensions.Hosting.IHostBuilder.Build> 並指派的實例 <xref:Microsoft.Extensions.Hosting.IHost> 。
- 呼叫 `ExemplifyScoping` ，傳入 <xref:Microsoft.Extensions.Hosting.IHost.Services?displayProperty=nameWithType> 。

## <a name="conclusion"></a>結論

應用程式會顯示類似下列範例的輸出：

```console
Scope 1-Call 1 .GetRequiredService<OperationLogger>(): ITransientOperation [ 80f4...Always different        ]
Scope 1-Call 1 .GetRequiredService<OperationLogger>(): IScopedOperation    [ c878...Changes only with scope ]
Scope 1-Call 1 .GetRequiredService<OperationLogger>(): ISingletonOperation [ 1586...Always the same         ]
...
Scope 1-Call 2 .GetRequiredService<OperationLogger>(): ITransientOperation [ f3c0...Always different        ]
Scope 1-Call 2 .GetRequiredService<OperationLogger>(): IScopedOperation    [ c878...Changes only with scope ]
Scope 1-Call 2 .GetRequiredService<OperationLogger>(): ISingletonOperation [ 1586...Always the same         ]

Scope 2-Call 1 .GetRequiredService<OperationLogger>(): ITransientOperation [ f9af...Always different        ]
Scope 2-Call 1 .GetRequiredService<OperationLogger>(): IScopedOperation    [ 2bd0...Changes only with scope ]
Scope 2-Call 1 .GetRequiredService<OperationLogger>(): ISingletonOperation [ 1586...Always the same         ]
...
Scope 2-Call 2 .GetRequiredService<OperationLogger>(): ITransientOperation [ fa65...Always different        ]
Scope 2-Call 2 .GetRequiredService<OperationLogger>(): IScopedOperation    [ 2bd0...Changes only with scope ]
Scope 2-Call 2 .GetRequiredService<OperationLogger>(): ISingletonOperation [ 1586...Always the same         ]
```

從應用程式輸出中，您可以看到：

- Transient 作業永遠不同，會在每次抓取服務時建立新的實例。
- Scoped 作業只會與新的範圍變更，但在範圍內是相同的實例。
- Singleton 作業一律相同，只會建立一次新的實例。

## <a name="see-also"></a>請參閱

* [相依性插入指導方針](dependency-injection-guidelines.md)
* [ASP.NET Core 中的相依性插入](/aspnet/core/fundamentals/dependency-injection)
