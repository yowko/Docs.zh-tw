---
title: 使用 dotnet vstest 測試已發行的輸出
description: 了解如何使用 dotnet vstest 命令在已發行的程式庫 (而不是原始程式碼) 上執行測試。
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.openlocfilehash: 7618d37782de3a16f1963380bbb56945fb73e8eb
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714260"
---
# <a name="test-published-output-with-dotnet-vstest"></a><span data-ttu-id="56e73-103">使用 dotnet vstest 測試已發行的輸出</span><span class="sxs-lookup"><span data-stu-id="56e73-103">Test published output with dotnet vstest</span></span>

<span data-ttu-id="56e73-104">您可以使用 `dotnet vstest` 命令在已經發行的輸出上執行測試。</span><span class="sxs-lookup"><span data-stu-id="56e73-104">You can run tests on already published output by using the `dotnet vstest` command.</span></span> <span data-ttu-id="56e73-105">此作法適用於 xUnit、MSTest 和 NUnit 測試。</span><span class="sxs-lookup"><span data-stu-id="56e73-105">This will work on xUnit, MSTest, and NUnit tests.</span></span> <span data-ttu-id="56e73-106">只需找到已發行輸出之一部分的 DLL 檔，並執行：</span><span class="sxs-lookup"><span data-stu-id="56e73-106">Simply locate the DLL file that was part of your published output and run:</span></span>

```dotnetcli
dotnet vstest <MyPublishedTests>.dll
```

<span data-ttu-id="56e73-107">其中 `<MyPublishedTests>` 是已發行測試專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="56e73-107">Where `<MyPublishedTests>` is the name of your published test project.</span></span>

## <a name="example"></a><span data-ttu-id="56e73-108">範例</span><span class="sxs-lookup"><span data-stu-id="56e73-108">Example</span></span>

<span data-ttu-id="56e73-109">下列命令示範如何在已發行的 DLL 上執行測試。</span><span class="sxs-lookup"><span data-stu-id="56e73-109">The commands below demonstrate running tests on a published DLL.</span></span>

```dotnetcli
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE]
> <span data-ttu-id="56e73-110">注意：如果您的應用程式以 `netcoreapp`以外的架構為目標，您仍然可以藉由使用架構旗標傳入目標架構，來執行 `dotnet vstest` 命令。</span><span class="sxs-lookup"><span data-stu-id="56e73-110">Note: If your app targets a framework other than `netcoreapp`, you can still run the `dotnet vstest` command by passing in the targeted framework with a framework flag.</span></span> <span data-ttu-id="56e73-111">例如，`dotnet vstest <MyPublishedTests>.dll --Framework:".NETFramework,Version=v4.6"`。</span><span class="sxs-lookup"><span data-stu-id="56e73-111">For example, `dotnet vstest <MyPublishedTests>.dll --Framework:".NETFramework,Version=v4.6"`.</span></span> <span data-ttu-id="56e73-112">在 Visual Studio 2017 Update 5 和更新版本中，會自動偵測所需的架構。</span><span class="sxs-lookup"><span data-stu-id="56e73-112">In Visual Studio 2017 Update 5 and later, the desired framework is automatically detected.</span></span>

## <a name="see-also"></a><span data-ttu-id="56e73-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="56e73-113">See also</span></span>

- [<span data-ttu-id="56e73-114">使用 dotnet test 及 xUnit 執行單元測試</span><span class="sxs-lookup"><span data-stu-id="56e73-114">Unit Testing with dotnet test and xUnit</span></span>](unit-testing-with-dotnet-test.md)
- [<span data-ttu-id="56e73-115">使用 dotnet test 和 NUnit 執行單元測試</span><span class="sxs-lookup"><span data-stu-id="56e73-115">Unit Testing with dotnet test and NUnit</span></span>](unit-testing-with-nunit.md)
- [<span data-ttu-id="56e73-116">使用 dotnet test 及 MSTest 執行單元測試</span><span class="sxs-lookup"><span data-stu-id="56e73-116">Unit Testing with dotnet test and MSTest</span></span>](unit-testing-with-mstest.md)
