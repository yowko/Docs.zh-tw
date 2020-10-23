---
title: 使用 dotnet test 與 xUnit 為 .NET Core 中的 C# 程式碼進行單元測試
description: 透過逐步使用 dotnet test 和 xUnit 建置範例方案的互動式體驗，了解 C# 與 .NET Core 中的單元測試概念。
author: ardalis
ms.author: wiwagn
ms.date: 10/21/2020
ms.openlocfilehash: e1972858be00e8a884efbd66b618ddb9ab77e9ba
ms.sourcegitcommit: 870bc4b4087510f6fba3c7b1c0d391f02bcc1f3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2020
ms.locfileid: "92471533"
---
# <a name="unit-testing-c-in-net-core-using-dotnet-test-and-xunit"></a>使用 dotnet test 與 xUnit 為 .NET Core 中的 C# 進行單元測試

本教學課程說明如何建立包含單元測試專案和原始程式碼專案的方案。 若要遵循使用預先建立之解決方案的教學課程，請 [參閱或下載範例程式碼](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/)。 如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#view-and-download-samples)。

## <a name="create-the-solution"></a>建立方案

在本節中，會建立包含來源和測試專案的方案。 完成的解決方案具有下列目錄結構：

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

下列指示提供建立測試解決方案的步驟。 請參閱 [建立測試解決方案的命令](#create-test-cmd) ，以取得在一個步驟中建立測試解決方案的指示。

* 開啟 Shell 視窗。
* 執行下列命令：

  ```dotnetcli
  dotnet new sln -o unit-testing-using-dotnet-test
  ```

  此 [`dotnet new sln`](../tools/dotnet-new.md) 命令會 *使用-dotnet-test* 目錄，在單元測試中建立新的解決方案。
* 將目錄變更為 *單元測試-使用-dotnet-測試* 資料夾。
* 執行下列命令：

  ```dotnetcli
  dotnet new classlib -o PrimeService
  ```

   此 [`dotnet new classlib`](../tools/dotnet-new.md) 命令會在 *>primeservice* 資料夾中建立新的類別庫專案。 新的類別庫將包含要測試的程式碼。
* 將 *Class1.cs* 重新命名為 *PrimeService.cs*。
* 將 *PrimeService.cs* 中的程式碼取代為下列程式碼：
  
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
  * 擲回， <xref:System.NotImplementedException> 並顯示訊息，指出未執行此訊息。
  * 稍後會在本教學課程中更新。

<!-- preceding code shows an english bias. Message makes no sense outside english -->

* 在 [ *單元測試-使用-dotnet-測試* ] 目錄中，執行下列命令以將類別庫專案新增至方案：

  ```dotnetcli
  dotnet sln add ./PrimeService/PrimeService.csproj
  ```

* 藉由執行下列命令來建立 *>primeservice 測試* 專案：

  ```dotnetcli
  dotnet new xunit -o PrimeService.Tests
  ```

* 上述命令︰
  * 在 *>primeservice. 測試*目錄中建立 *>primeservice*專案。 測試專案會使用 [xUnit](https://xunit.net/) 做為測試程式庫。
  * 將下列元素新增至專案檔， `<PackageReference />` 以設定測試執行器：
    * "Microsoft. Test. Sdk"
    * xunit
    * "xunit. visualstudio"

* 藉由執行下列命令，將測試專案新增至方案檔：

  ```dotnetcli
  dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
  ```

* 將 `PrimeService` 類別庫新增為 >primeservice 的相依性 *。測試* 專案：

  ```dotnetcli
  dotnet add ./PrimeService.Tests/PrimeService.Tests.csproj reference ./PrimeService/PrimeService.csproj  
  ```

<a name="create-test-cmd"></a>

### <a name="commands-to-create-the-solution"></a>用來建立解決方案的命令

本節摘要說明上一節中的所有命令。 如果您已完成上一節中的步驟，請略過本節。

下列命令會在 windows 電腦上建立測試解決方案。 針對 macOS 和 Unix，將 `ren` 命令更新為的作業系統版本， `ren` 以重新命名檔案：

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

請依照上一節中的「以下列程式碼取代 *PrimeService.cs* 中的程式碼」的指示進行。

## <a name="create-a-test"></a>建立測試

測試導向開發 (TDD) 的常用方法是在執行目的程式代碼之前撰寫測試。 本教學課程使用 TDD 方法。 `IsPrime`方法是可呼叫的，但不會執行。 測試呼叫 `IsPrime` 失敗。 使用 TDD 時，會寫入已知失敗的測試。 目的程式代碼會更新以進行測試。 您可以重複此方法，撰寫失敗的測試，然後更新要通過的目的程式代碼。

更新 *>primeservice。測試* 專案：

* 刪除 *>primeservice. 測試/UnitTest1 .cs*。
* 建立 *>primeservice 測試/PrimeService_IsPrimeShould .cs*  檔案。
* 以下列程式碼取代 *PrimeService_IsPrimeShould* 中的程式碼：

```csharp
using Xunit;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    public class PrimeService_IsPrimeShould
    {
        [Fact]
        public void IsPrime_InputIs1_ReturnFalse()
        {
            var primeService = new PrimeService();
            bool result = primeService.IsPrime(1);

            Assert.False(result, "1 should not be prime");
        }
    }
}
```

`[Fact]`屬性宣告由測試執行器執行的測試方法。 在 [ *>primeservice* ] 資料夾中，執行 `dotnet test` 。 [Dotnet test](../tools/dotnet-test.md)命令會建立兩個專案，並執行測試。 XUnit 測試執行器包含執行測試的程式進入點。 `dotnet test` 使用單元測試專案啟動測試執行器。

測試失敗，因為 `IsPrime` 尚未執行。 使用 TDD 方法，只寫入足夠的程式碼，使此測試通過。 `IsPrime`以下列程式碼更新：

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

### <a name="add-more-tests"></a>新增更多測試

為0和-1 新增質數測試。 您可以複製先前的測試，並變更下列程式碼以使用0和-1：

```csharp
var primeService = new PrimeService();
bool result = primeService.IsPrime(1);

Assert.False(result, "1 should not be prime");
```

只有在參數變更時複製測試程式碼會導致程式碼重複和測試膨脹。 下列 xUnit 屬性可讓您撰寫類似測試的套件：

- `[Theory]` 代表執行相同程式碼但具有不同輸入引數的測試套件。
- `[InlineData]` 屬性會指定這些輸入的值。

不是建立新的測試，而是套用先前的 xUnit 屬性來建立單一的理論。 將下列程式碼：

```csharp
[Fact]
public void IsPrime_InputIs1_ReturnFalse()
{
    var primeService = new PrimeService();
    bool result = primeService.IsPrime(1);

    Assert.False(result, "1 should not be prime");
}
```

取代為下列程式碼：

[!code-csharp[Sample_TestCode](../../../samples/snippets/core/testing/unit-testing-using-dotnet-test/csharp/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

在上述程式碼中，您 `[Theory]` `[InlineData]` 可以測試數個小於二的值。 兩個是最小的質數。

執行時 `dotnet test` ，兩個測試會失敗。 若要讓所有測試都通過，請 `IsPrime` 使用下列程式碼來更新方法：

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

遵循 TDD 方法，新增更多失敗的測試，然後更新目的程式代碼。 查看 [已完成的測試版本](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) 和連結 [庫的完整執行](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs)。

完成的 `IsPrime` 方法不是測試 primality 的有效演算法。

### <a name="additional-resources"></a>其他資源

- [xUnit.net 官方網站](https://xunit.net)
- [測試 ASP.NET Core 中的控制器邏輯](/aspnet/core/mvc/controllers/testing)
- [`dotnet add reference`](../tools/dotnet-add-reference.md)
