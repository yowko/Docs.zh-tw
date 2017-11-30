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
# <a name="test-published-output-with-dotnet-vstest"></a><span data-ttu-id="df4ac-103">測試已發佈的輸出結果與 dotnet vstest</span><span class="sxs-lookup"><span data-stu-id="df4ac-103">Test published output with dotnet vstest</span></span>

<span data-ttu-id="df4ac-104">您也可以使用已發行的輸出上執行測試`dotnet vstest`命令。</span><span class="sxs-lookup"><span data-stu-id="df4ac-104">You can run tests on already published output by using the `dotnet vstest` command.</span></span> <span data-ttu-id="df4ac-105">這將會處理 xUnit，MSTest 和 NUnit 測試。</span><span class="sxs-lookup"><span data-stu-id="df4ac-105">This will work on xUnit, MSTest, and NUnit tests.</span></span> <span data-ttu-id="df4ac-106">只要尋找已發行的輸出的一部分的 DLL 檔案，並執行：</span><span class="sxs-lookup"><span data-stu-id="df4ac-106">Simply locate the DLL file that was part of your published output and run:</span></span>
```
dotnet vstest <MyPublishedTests>.dll
```
<span data-ttu-id="df4ac-107">其中`<MyPublishedTests>`是已發行的測試專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="df4ac-107">where `<MyPublishedTests>` is the name of your published test project.</span></span>

### <a name="example-of-running-tests-on-a-published-dll"></a><span data-ttu-id="df4ac-108">已發行的 DLL 上執行測試的範例</span><span class="sxs-lookup"><span data-stu-id="df4ac-108">Example of running tests on a published DLL</span></span>

```
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE] <span data-ttu-id="df4ac-109">注意： 如果您的應用程式的目標 framework 以外`netcoreapp`您仍然可以執行`dotnet vstest`命令藉由傳遞目標 framework 架構的旗標。</span><span class="sxs-lookup"><span data-stu-id="df4ac-109">Note: If your app is targeting a framework other than `netcoreapp` you can still run the `dotnet vstest` command by passing in the targeted framework with a framework flag.</span></span> <span data-ttu-id="df4ac-110">例如，`dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`。</span><span class="sxs-lookup"><span data-stu-id="df4ac-110">For example, `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`.</span></span> <span data-ttu-id="df4ac-111">在 Visual Studio 2017 更新 5 中所需的架構會自動偵測。</span><span class="sxs-lookup"><span data-stu-id="df4ac-111">In Visual Studio 2017 Update 5 the desired framework is automatically detected.</span></span>

### <a name="related-topics"></a><span data-ttu-id="df4ac-112">相關主題</span><span class="sxs-lookup"><span data-stu-id="df4ac-112">Related topics</span></span>
- [<span data-ttu-id="df4ac-113">Dotnet 測試與 xUnit 單元測試</span><span class="sxs-lookup"><span data-stu-id="df4ac-113">Unit Testing with dotnet test and xUnit</span></span>](unit-testing-with-dotnet-test.md)
- [<span data-ttu-id="df4ac-114">Dotnet 測試與 MSTest 的單元測試</span><span class="sxs-lookup"><span data-stu-id="df4ac-114">Unit Testing with dotnet test and MSTest</span></span>](unit-testing-with-mstest.md)
