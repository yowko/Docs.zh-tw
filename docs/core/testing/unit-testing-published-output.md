---
title: "測試已發佈的輸出結果與 dotnet vstest"
description: "了解如何在已發行的輸出結果與 dotnet vstest 命令上執行測試。"
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 3965e4ca-75b8-4969-b3af-ca993c397a15
ms.openlocfilehash: 217787d41a9da6000941ded6caaa4f44d124644b
ms.sourcegitcommit: 8a4f8e6a7f1341764abcd188a332cc28d1e2d8ec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="test-published-output-with-dotnet-vstest"></a>測試已發佈的輸出結果與 dotnet vstest

您也可以使用已發行的輸出上執行測試`dotnet vstest`命令。 這將會處理 xUnit，MSTest 和 NUnit 測試。 只要尋找已發行的輸出的一部分的 DLL 檔案，並執行：
```
dotnet vstest <MyPublishedTests>.dll
```
其中`<MyPublishedTests>`是已發行的測試專案的名稱。

### <a name="example-of-running-tests-on-a-published-dll"></a>已發行的 DLL 上執行測試的範例

```
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE] 注意： 如果您的應用程式的目標 framework 以外`netcoreapp`您仍然可以執行`dotnet vstest`命令藉由傳遞目標 framework 架構的旗標。 例如，`dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`。 在 Visual Studio 2017 更新 5 中所需的架構會自動偵測。

### <a name="related-topics"></a>相關主題
- [Dotnet 測試與 xUnit 單元測試](unit-testing-with-dotnet-test.md)
- [Dotnet 測試與 MSTest 的單元測試](unit-testing-with-mstest.md)
