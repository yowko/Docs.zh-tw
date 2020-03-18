---
title: Microsoft XML 序列化程式產生器
description: Microsoft XML 序列化程式產生器的概觀。 您可以使用 XML 序列化程式產生器，為專案中包含的類型產生 XML 序列化組件。
author: mlacouture
ms.date: 01/19/2017
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 094dd1227033e167050ad73121b3005a592a0ae4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714517"
---
# <a name="using-microsoft-xml-serializer-generator-on-net-core"></a>在 .NET Core 上使用 Microsoft XML 序列化程式產生器

本教學課程教導您如何在 C#.NET Core 應用程式中使用 Microsoft XML 序列化程式產生器。 您會在本教學課程中了解︰

> [!div class="checklist"]
>
> - 如何建立 .NET Core 應用程式
> - 如何新增 Microsoft.XmlSerializer.Generator 套件的參考
> - 如何編輯 MyApp.csproj 以新增相依性
> - 如何新增類別和 XmlSerializer
> - 如何建置和執行應用程式

[Microsoft.XmlSerializer.Generator NuGet 套件](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator)類似於 [XML 序列化程式產生器 (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md)，是 .NET Core 和 .NET Standard 專案的對等項目。 此套件能夠為組件中包含的類型建立 XML 序列化組件，可在將這些類型的物件序列化或還原序列化時，使用 <xref:System.Xml.Serialization.XmlSerializer> 來提升 XML 序列化的啟動效能。

## <a name="prerequisites"></a>必要條件

若要完成本教學課程：

- [.NET 核心 2.1 SDK](https://dotnet.microsoft.com/download)或更高版本。
- 您慣用的程式碼編輯器。

> [!TIP]
> 需要安裝程式碼編輯器嗎？ 試用 [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)！

## <a name="use-microsoft-xml-serializer-generator-in-a-net-core-console-application"></a>在 .NET Core 主控台應用程式中使用 Microsoft XML 序列化程式產生器

下列指示示範如何在 .NET Core 主控台應用程式中使用 XML 序列化程式產生器。

### <a name="create-a-net-core-console-application"></a>建立 .NET Core 主控台應用程式

開啟命令提示字元，並建立名為 *MyApp* 的資料夾。 巡覽至您已建立的資料夾，並鍵入下列命令：

```dotnetcli
dotnet new console
```

### <a name="add-a-reference-to-the-microsoftxmlserializergenerator-package-in-the-myapp-project"></a>在 MyApp 專案中新增 Microsoft.XmlSerializer.Generator 套件的參考

使用[`dotnet add package`](../tools//dotnet-add-package.md)命令在專案中增加參考。

輸入：

```dotnetcli
dotnet add package Microsoft.XmlSerializer.Generator -v 1.0.0
```

### <a name="verify-changes-to-myappcsproj-after-adding-the-package"></a>在新增套件之後驗證 MyApp.csproj 變更

開啟程式碼編輯器，並讓我們開始吧！ 我們仍然從在其中建置應用程式的 *MyApp* 目錄中工作。

在文字編輯器中，開啟 *MyApp.csproj*。

運行該[`dotnet add package`](../tools//dotnet-add-package.md)命令後，以下行將添加到*MyApp.csproj*專案檔案中：

 ```xml
 <ItemGroup>
    <PackageReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```

### <a name="add-another-itemgroup-section-for-net-core-cli-tool-support"></a>新增 .NET Core CLI 工具支援的另一個 ItemGroup 區段

在檢查的 `ItemGroup` 區段後面新增下列數行：

 ```xml
 <ItemGroup>
    <DotNetCliToolReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```

### <a name="add-a-class-in-the-application"></a>在應用程式中新增類別

在文字編輯器中，開啟 *Program.cs*。 在 *Program.cs* 中，新增名為 *MyClass* 的類別。

```csharp
public class MyClass
{
   public int Value;
}
```

### <a name="create-an-xmlserializer-for-myclass"></a>建立 MyClass 的 `XmlSerializer`

在 *Main* 內新增下列數行，以建立 MyClass 的 `XmlSerializer`：

```csharp
var serializer = new System.Xml.Serialization.XmlSerializer(typeof(MyClass));
```

### <a name="build-and-run-the-application"></a>建置並執行應用程式

在 *MyApp* 資料夾內，仍然透過 [`dotnet run`](../tools/dotnet-run.md) 執行應用程式，並在執行階段自動載入和使用預先產生的序列化程式。

在主控台視窗中，鍵入下列命令：

```dotnetcli
dotnet run
```

> [!NOTE]
> [`dotnet run`](../tools/dotnet-run.md)調用[`dotnet build`](../tools/dotnet-build.md)以確保生成目標已生成，然後調用`dotnet <assembly.dll>`以運行目標應用程式。

> [!IMPORTANT]
> 本教學課程中所示用於執行應用程式的命令和步驟，僅供開發階段使用。 準備好部署應用程式之後，請查看不同的 .NET Core 應用程式[部署策略](../deploying/index.md)和 [`dotnet publish`](../tools/dotnet-publish.md) 命令。

如果所有項目都成功，則會在輸出資料夾中產生名為 *MyApp.XmlSerializers.dll* 的組件。

恭喜！ 您已：
> [!div class="checklist"]
>
> - 建立 .NET Core 應用程式。
> - 新增 Microsoft.XmlSerializer.Generator 套件的參考。
> - 編輯 MyApp.csproj 以新增相依性。
> - 新增類別和 XmlSerializer。
> - 建置和執行應用程式。

## <a name="related-resources"></a>相關資源

- [XML 序列化簡介](../../standard/serialization/introducing-xml-serialization.md)
- [如何使用 Xml 序列化器 （C#） 序列化](../../csharp/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)
- [如何：使用 XmlSerializer 進行序列化 (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)
