---
title: "使用 dotnet vstest 測試已發行的輸出"
description: "了解如何使用 dotnet vstest 命令在已發行的輸出上執行測試。"
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.topic: article
ms.prod: .net-core
ms.openlocfilehash: 6651d41d4d60194aec035107e3a65df6a5f70a51
ms.sourcegitcommit: 4a96a0fe9f87de70291245d71b76c7d1b15127ae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2017
---
# <a name="test-published-output-with-dotnet-vstest"></a><span data-ttu-id="be776-103">使用 dotnet vstest 測試已發行的輸出</span><span class="sxs-lookup"><span data-stu-id="be776-103">Test published output with dotnet vstest</span></span>

<span data-ttu-id="be776-104">您可以使用 `dotnet vstest` 命令在已經發行的輸出上執行測試。</span><span class="sxs-lookup"><span data-stu-id="be776-104">You can run tests on already published output by using the `dotnet vstest` command.</span></span> <span data-ttu-id="be776-105">此作法適用於 xUnit、MSTest 和 NUnit 測試。</span><span class="sxs-lookup"><span data-stu-id="be776-105">This will work on xUnit, MSTest, and NUnit tests.</span></span> <span data-ttu-id="be776-106">只需找到已發行輸出之一部分的 DLL 檔，並執行：</span><span class="sxs-lookup"><span data-stu-id="be776-106">Simply locate the DLL file that was part of your published output and run:</span></span>

```
dotnet vstest <MyPublishedTests>.dll
```

<span data-ttu-id="be776-107">其中 `<MyPublishedTests>` 是已發行測試專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="be776-107">where `<MyPublishedTests>` is the name of your published test project.</span></span>

## <a name="example-of-running-tests-on-a-published-dll"></a><span data-ttu-id="be776-108">在已發行的 DLL 上執行測試的範例</span><span class="sxs-lookup"><span data-stu-id="be776-108">Example of running tests on a published DLL</span></span>

```
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE]
> <span data-ttu-id="be776-109">注意：如果您的應用程式是以 `netcoreapp` 以外的架構為目標，您仍然能以架構旗標傳入目標架構，來執行 `dotnet vstest` 命令。</span><span class="sxs-lookup"><span data-stu-id="be776-109">Note: If your app is targeting a framework other than `netcoreapp` you can still run the `dotnet vstest` command by passing in the targeted framework with a framework flag.</span></span> <span data-ttu-id="be776-110">例如，`dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`。</span><span class="sxs-lookup"><span data-stu-id="be776-110">For example, `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`.</span></span> <span data-ttu-id="be776-111">在 Visual Studio 2017 Update 5 中，系統會自動偵測所需架構。</span><span class="sxs-lookup"><span data-stu-id="be776-111">In Visual Studio 2017 Update 5 the desired framework is automatically detected.</span></span>

## <a name="see-also"></a><span data-ttu-id="be776-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="be776-112">See also</span></span>
 [<span data-ttu-id="be776-113">使用 dotnet test 及 xUnit 執行單元測試</span><span class="sxs-lookup"><span data-stu-id="be776-113">Unit Testing with dotnet test and xUnit</span></span>](unit-testing-with-dotnet-test.md)  
 [<span data-ttu-id="be776-114">使用 dotnet test 及 MSTest 執行單元測試</span><span class="sxs-lookup"><span data-stu-id="be776-114">Unit Testing with dotnet test and MSTest</span></span>](unit-testing-with-mstest.md)  
