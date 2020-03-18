---
title: 使用 dotnet vstest 測試已發行的輸出
description: 了解如何使用 dotnet vstest 命令在已發行的程式庫 (而不是原始程式碼) 上執行測試。
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.openlocfilehash: 7618d37782de3a16f1963380bbb56945fb73e8eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714260"
---
# <a name="test-published-output-with-dotnet-vstest"></a>使用 dotnet vstest 測試已發行的輸出

您可以使用 `dotnet vstest` 命令在已經發行的輸出上執行測試。 此作法適用於 xUnit、MSTest 和 NUnit 測試。 只需找到已發行輸出之一部分的 DLL 檔，並執行：

```dotnetcli
dotnet vstest <MyPublishedTests>.dll
```

其中 `<MyPublishedTests>` 是已發行測試專案的名稱。

## <a name="example"></a>範例

下列命令示範如何在已發行的 DLL 上執行測試。

```dotnetcli
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE]
> 注意：如果應用針對的框架以外的`netcoreapp`框架，您仍可以通過使用框架標誌傳入`dotnet vstest`目標框架來運行該命令。 例如： `dotnet vstest <MyPublishedTests>.dll --Framework:".NETFramework,Version=v4.6"` 。 在 Visual Studio 2017 更新 5 及更高版本中，將自動檢測到所需的框架。

## <a name="see-also"></a>另請參閱

- [使用點網測試和 xUnit 進行單元測試](unit-testing-with-dotnet-test.md)
- [使用 dotnet test 與 NUnit 執行單元測試](unit-testing-with-nunit.md)
- [使用 dotnet test 與 MSTest 執行單元測試](unit-testing-with-mstest.md)
