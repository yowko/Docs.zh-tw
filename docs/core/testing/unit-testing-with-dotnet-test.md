---
title: 使用 dotnet test 與 xUnit 為 .NET Core 中的 C# 程式碼進行單元測試
description: 透過逐步使用 dotnet test 和 xUnit 建置範例方案的互動式體驗，了解 C# 與 .NET Core 中的單元測試概念。
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: c9e3d63a2cf4f560591459833340b729ffec1b95
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240892"
---
# <a name="unit-testing-c-in-net-core-using-dotnet-test-and-xunit"></a>使用 dotnet test 與 xUnit 為 .NET Core 中的 C# 進行單元測試

本教程演示如何構建包含單元測試專案和原始程式碼專案的解決方案。 要使用預構建的解決方案按照本教程進行操作，[請查看或下載示例代碼](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/)。 如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。

## <a name="create-the-solution"></a>建立方案

在本節中，將創建包含源和測試專案的解決方案。 已完成的解決方案具有以下目錄結構：

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        PrimeService.cs
        PrimeService.csproj
    /PrimeService.Tests
        PrimeService_IsPrimeShould.cs
        PrimeServiceTests.csproj
```

以下說明提供了創建測試解決方案的步驟。 請參閱[命令以創建測試解決方案](#create-test-cmd)，以便一步創建測試解決方案。

* 開啟 Shell 視窗。
* 執行以下命令：

  ```dotnetcli
  dotnet new sln -o unit-testing-using-dotnet-test
  ```

  該[`dotnet new sln`](../tools/dotnet-new.md)命令在*單元測試-使用點-測試*目錄中創建新的解決方案。
* 將目錄更改為*單元測試使用點網路測試*資料夾。
* 執行以下命令：

  ```dotnetcli
  dotnet new classlib -o PrimeService
  ```

   該[`dotnet new classlib`](../tools/dotnet-new.md)命令在*PrimeService*資料夾中創建新的類庫專案。 新的類庫將包含要測試的代碼。
* 將 *Class1.cs* 重新命名為 *PrimeService.cs*。
* 將*PrimeService.cs*中的代碼替換為以下代碼：
  
  ```csharp
    using System;

    namespace Prime.Services
    {
        public class PrimeService
        {
            public bool IsPrime(int candidate)
            {
                throw new NotImplementedException("Not implemented.");
            }
        }
    }
  ```

* 上述程式碼：
  * 引發帶有<xref:System.NotImplementedException>消息的 ，指示其未實現。
  * 在本教程的後面部分更新。

<!-- preceding code shows an english bias. Message makes no sense outside english -->

* 在*單元測試使用點-測試*目錄中，運行以下命令將類庫專案添加到解決方案：

  ```dotnetcli
  dotnet sln add ./PrimeService/PrimeService.csproj
  ```

* 通過運行以下命令創建*PrimeService.測試*專案：

  ```dotnetcli
  dotnet new xunit -o PrimeService.Tests
  ```

* 上述命令會：
  * 在*PrimeService.測試*目錄中創建*PrimeService.* 測試專案。 測試專案使用[xUnit](https://xunit.github.io/)作為測試庫。
  * 通過將以下`<PackageReference />`元素添加到專案檔案來配置測試流道：
    * "微軟.NET.Test.Sdk"
    * "xunit"
    * "xunit.runner.Visualstudio"

* 通過運行以下命令將測試專案添加到解決方案檔：

  ```dotnetcli
  dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
  ```

* 將`PrimeService`類庫作為依賴項添加到*PrimeService.測試*專案：

  ```dotnetcli
  dotnet add ./PrimeService.Tests/PrimeService.Tests.csproj reference ./PrimeService/PrimeService.csproj  
  ```

<a name="create-test-cmd"></a>

### <a name="commands-to-create-the-solution"></a>創建解決方案的命令

本節匯總上一節中的所有命令。 如果您已完成上一節中的步驟，請跳過此部分。

以下命令在視窗電腦上創建測試解決方案。 對於 macOS 和 Unix，將`ren`命令更新到`ren`的作業系統版本以重命名檔：

```dotnetcli
dotnet new sln -o unit-testing-using-dotnet-test
cd unit-testing-using-dotnet-test
dotnet new classlib -o PrimeService
ren .\PrimeService\Class1.cs PrimeService.cs
dotnet sln add ./PrimeService/PrimeService.csproj
dotnet new xunit -o PrimeService.Tests
dotnet add ./PrimeService.Tests/PrimeService.Tests.csproj reference ./PrimeService/PrimeService.csproj
dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
```

按照上一節中有關"用以下代碼替換*PrimeService.cs*代碼"的說明進行操作。

## <a name="create-a-test"></a>創建測試

測試驅動開發 （TDD） 中的一種常用方法是在實現目標代碼之前編寫測試。 本教程使用 TDD 方法。 該方法`IsPrime`是可調用的，但不可實現。 測試調用`IsPrime`失敗。 使用 TDD 時，將編寫已知失敗測試。 更新目標代碼以使測試通過。 您繼續重複此方法，編寫失敗的測試，然後更新目標代碼以通過。

更新*PrimeService.測試*專案：

* 刪除*主要服務.測試/單元測試1.cs*。
* 創建*PrimeService.測試/PrimeService_IsPrimeShould.cs*檔。
* 將*PrimeService_IsPrimeShould.cs*中的代碼替換為以下代碼：

```csharp
using Xunit;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    public class PrimeService_IsPrimeShould
    {
        private readonly PrimeService _primeService;

        public PrimeService_IsPrimeShould()
        {
            _primeService = new PrimeService();
        }

        [Fact]
        public void IsPrime_InputIs1_ReturnFalse()
        {
            var result = _primeService.IsPrime(1);

            Assert.False(result, "1 should not be prime");
        }
    }
}
```

該`[Fact]`屬性聲明由測試回合程式運行的測試方法。 從*PrimeService.測試*資料夾，運行`dotnet test`。 [dotnet 測試](../tools/dotnet-test.md)命令同時生成兩個專案並運行測試。 xUnit 測試回合套裝程式含運行測試的程式進入點。 `dotnet test`使用單元測試專案啟動測試回合程式。

測試失敗，因為`IsPrime`尚未實現。 使用 TDD 方法，只編寫足夠的代碼，以便通過此測試。 使用`IsPrime`以下代碼進行更新：

```csharp
public bool IsPrime(int candidate)
{
    if (candidate == 1)
    {
        return false;
    }
    throw new NotImplementedException("Not fully implemented.");
}
```

執行 `dotnet test`。 測試會成功。

### <a name="add-more-tests"></a>添加更多測試

添加 0 和 -1 的質數測試。 您可以複製前面的測試並將以下代碼更改為使用 0 和 -1：

```csharp
var result = _primeService.IsPrime(1);

Assert.False(result, "1 should not be prime");
```

當只有參數更改時複製測試代碼會導致代碼重複和測試膨脹。 以下 xUnit 屬性允許編寫一組類似的測試：

- `[Theory]` 代表執行相同程式碼但具有不同輸入引數的測試套件。

- `[InlineData]` 屬性會指定這些輸入的值。

與其創建新測試，不如應用前面的 xUnit 屬性來創建單個理論。 將下列程式碼：

```csharp
[Fact]
public void IsPrime_InputIs1_ReturnFalse()
{
    var result = _primeService.IsPrime(1);

    Assert.False(result, "1 should not be prime");
}
```

取代為下列程式碼：

[!code-csharp[Sample_TestCode](../../../samples/snippets/core/testing/unit-testing-using-dotnet-test/csharp/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

在前面的代碼中，`[Theory]`並`[InlineData]`啟用測試多個值小於兩個。 二是最小的質數。

運行`dotnet test`，兩個測試失敗。 要使所有測試都通過，`IsPrime`請使用以下代碼更新該方法：

```csharp
public bool IsPrime(int candidate)
{
    if (candidate < 2)
    {
        return false;
    }
    throw new NotImplementedException("Not fully implemented.");
}
```

按照 TDD 方法，添加更多失敗的測試，然後更新目標代碼。 請參閱[測試的已完成版本](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs)和[庫的完整實現](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs)。

完整的`IsPrime`方法不是測試原始性的有效演算法。

### <a name="additional-resources"></a>其他資源

- [xUnit.net 官方網站](https://xunit.github.io)
- [測試 ASP.NET Core 中的控制器邏輯](/aspnet/core/mvc/controllers/testing)
- [`dotnet add reference`](../tools/dotnet-add-reference.md)
