---
title: 開始使用 - C# 指南
description: 搜尋片長短、內容簡單扼要的教學課程，介紹 C# 概念及如何撰寫.NET Core 應用程式，協助您快速進入狀況。
helpviewer_keywords:
- Visual C#, getting started
- getting started, Visual C#
author: rpetrusha
ms.author: ronpet
ms.date: 08/23/2017
ms.openlocfilehash: aa34c181073d089d137ac0ef64c85c8fe2772093
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44195263"
---
# <a name="get-started-with-c"></a><span data-ttu-id="92194-103">開始使用 C\#</span><span class="sxs-lookup"><span data-stu-id="92194-103">Get started with C\#</span></span>

<span data-ttu-id="92194-104">本節提供簡短且簡單的教學課程，可讓您使用 C# 和 .NET Core 快速建置應用程式。</span><span class="sxs-lookup"><span data-stu-id="92194-104">This section provides short, simple tutorials that let you quickly build an application using C# and .NET Core.</span></span> <span data-ttu-id="92194-105">本節內容涵蓋適用於 Visual Studio 2017 和 Visual Studio Code 的使用者入門主題。</span><span class="sxs-lookup"><span data-stu-id="92194-105">There are getting started topics for Visual Studio 2017 and Visual Studio Code.</span></span> <span data-ttu-id="92194-106">您可以建置一個簡單的 Hello World 應用程式，或者，如果您擁有 Visual Studio 2017，則能建置可供其他應用程式使用的簡單類別庫。</span><span class="sxs-lookup"><span data-stu-id="92194-106">You can build either a simple Hello World application or, if you have Visual Studio 2017, a simple class library that can be used by other applications.</span></span>

<span data-ttu-id="92194-107">我們將提供下列主題：</span><span class="sxs-lookup"><span data-stu-id="92194-107">The following topics are available:</span></span>

* [<span data-ttu-id="92194-108">C# 語言和 .NET Framework 簡介</span><span class="sxs-lookup"><span data-stu-id="92194-108">Introduction to the C# Language and the .NET Framework</span></span>](introduction-to-the-csharp-language-and-the-net-framework.md)

     <span data-ttu-id="92194-109">提供 C# 語言和 .NET 的概觀。</span><span class="sxs-lookup"><span data-stu-id="92194-109">Provides an overview of the C# language and .NET.</span></span>

* [<span data-ttu-id="92194-110">在 Visual Studio 2017 中使用 .NET Core 建置 C# Hello World 應用程式</span><span class="sxs-lookup"><span data-stu-id="92194-110">Building a C# Hello World application with .NET Core in Visual Studio 2017</span></span>](../../core/tutorials/with-visual-studio.md)

   <span data-ttu-id="92194-111">Visual Studio 2017 (最新版的 Visual Studio) 可讓您從適用於 Windows 的整合式開發環境中，針對應用程式撰寫程式碼，並進行編譯、執行、偵錯、程式碼剖析及發行。</span><span class="sxs-lookup"><span data-stu-id="92194-111">Visual Studio 2017, the latest release of Visual Studio, lets you code, compile, run, debug, profile, and publish your applications from a integrated development environment for Windows.</span></span>

   <span data-ttu-id="92194-112">此主題可讓您建立並執行簡單的 Hello World 應用程式，然後修改它以執行稍微更具互動性的 Hello World 應用程式。</span><span class="sxs-lookup"><span data-stu-id="92194-112">The topic lets you create and run a simple Hello World application and then modify it to run a slightly more interactive Hello World application.</span></span> <span data-ttu-id="92194-113">當您完成建置並執行應用程式之後，您也可以學習如何[為應用程式偵錯](../../core/tutorials/debugging-with-visual-studio.md)，以及如何[發行應用程式](../../core/tutorials/publishing-with-visual-studio.md)，讓它可在任何 .NET Core 支援的平台上執行。</span><span class="sxs-lookup"><span data-stu-id="92194-113">Once you've finished building and running your application, you can also learn how to [debug it](../../core/tutorials/debugging-with-visual-studio.md) and how to [publish it](../../core/tutorials/publishing-with-visual-studio.md) so that it can be run on any platform supported by .NET Core.</span></span>

* [<span data-ttu-id="92194-114">在 Visual Studio 2017 中使用 C# 和 .NET Core 建置類別庫</span><span class="sxs-lookup"><span data-stu-id="92194-114">Building a class library with C# and .NET Core in Visual Studio 2017</span></span>](../../core/tutorials/library-with-visual-studio.md)

   <span data-ttu-id="92194-115">類別庫讓您能夠定義可從另一個應用程式呼叫的型別和型別成員。</span><span class="sxs-lookup"><span data-stu-id="92194-115">A class library lets you define types and type members that can be called from another application.</span></span> <span data-ttu-id="92194-116">此主題可讓您建立具有單一方法的類別庫，來決定字串是否要以大寫字元為開頭。</span><span class="sxs-lookup"><span data-stu-id="92194-116">This topic lets you create a class library with a single method that determines whether a string begins with an uppercase character.</span></span> <span data-ttu-id="92194-117">當您完成建置類別庫之後，可以開發[單元測試](../../core/tutorials/testing-library-with-visual-studio.md)以確保該類別庫可如預期般運作，然後您可以讓[想要取用它的應用程式](../../core/tutorials/consuming-library-with-visual-studio.md)能夠使用該類別庫。</span><span class="sxs-lookup"><span data-stu-id="92194-117">Once you've finished building the library, you can develop a [unit test](../../core/tutorials/testing-library-with-visual-studio.md) to ensure that it works as expected, and then you can make it available to [applications that want to consume it](../../core/tutorials/consuming-library-with-visual-studio.md).</span></span>

* [<span data-ttu-id="92194-118">C# 與 Visual Studio Code 使用者入門</span><span class="sxs-lookup"><span data-stu-id="92194-118">Get started with C# and Visual Studio Code</span></span>](../../core/tutorials/with-visual-studio-code.md)

   <span data-ttu-id="92194-119">Visual Studio Code 這個免費的程式碼編輯器已經過最佳化，可用於建置新式 Web 和雲端應用程式並為其偵錯。</span><span class="sxs-lookup"><span data-stu-id="92194-119">Visual Studio Code is a free code editor optimized for building and debugging modern web and cloud applications.</span></span> <span data-ttu-id="92194-120">支援 IntelliSense 並適用於 Linux、macOS 和 Windows。</span><span class="sxs-lookup"><span data-stu-id="92194-120">It supports IntelliSense and is available for Linux, macOS, and Windows.</span></span>

   <span data-ttu-id="92194-121">此主題說明如何使用 Visual Studio Code 和 .NET Core，來建立並執行簡單的 Hello World 應用程式。</span><span class="sxs-lookup"><span data-stu-id="92194-121">This topic shows you how to create and run a simple Hello World application with Visual Studio Code and .NET Core.</span></span>

## <a name="related-sections"></a><span data-ttu-id="92194-122">相關章節</span><span class="sxs-lookup"><span data-stu-id="92194-122">Related Sections</span></span>

* [<span data-ttu-id="92194-123">使用 C# 的 Visual Studio 開發環境</span><span class="sxs-lookup"><span data-stu-id="92194-123">Using the Visual Studio Development Environment for C#</span></span>](/visualstudio/csharp-ide/using-the-visual-studio-development-environment-for-csharp)  

    <span data-ttu-id="92194-124">提供使用 Visual C# 整合式開發環境的指南。</span><span class="sxs-lookup"><span data-stu-id="92194-124">Provides a guide to using the Visual C# integrated development environment.</span></span>

* [<span data-ttu-id="92194-125">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="92194-125">C# Programming Guide</span></span>](../../csharp/programming-guide/index.md)

    <span data-ttu-id="92194-126">提供 C# 程式設計概念的資訊，並說明如何在 C# 中執行各種工作。</span><span class="sxs-lookup"><span data-stu-id="92194-126">Provides information about C# programming concepts, and describes how to perform various tasks in C#.</span></span>

* [<span data-ttu-id="92194-127">C# 參考</span><span class="sxs-lookup"><span data-stu-id="92194-127">C# Reference</span></span>](../../csharp/language-reference/index.md)

    <span data-ttu-id="92194-128">提供 C# 關鍵字、運算子、前置處理器指示詞、編譯器選項以及編譯器錯誤和警告的詳細參考資訊。</span><span class="sxs-lookup"><span data-stu-id="92194-128">Provides detailed reference information about C# keywords, operators, preprocessor directives, compiler options, and compiler errors and warnings.</span></span>

* [<span data-ttu-id="92194-129">Visual Studio 範例</span><span class="sxs-lookup"><span data-stu-id="92194-129">Visual Studio Samples</span></span>](/visualstudio/ide/visual-studio-samples)

    <span data-ttu-id="92194-130">提供有關如何存取線上範例的資訊。</span><span class="sxs-lookup"><span data-stu-id="92194-130">Provides information about how you can access online samples.</span></span>

* [<span data-ttu-id="92194-131">逐步解說</span><span class="sxs-lookup"><span data-stu-id="92194-131">Walkthroughs</span></span>](../../csharp/walkthroughs.md)

    <span data-ttu-id="92194-132">提供使用 C# 之程式設計逐步解說及個別逐步解說之簡短描述的連結。</span><span class="sxs-lookup"><span data-stu-id="92194-132">Provides links to programming walkthroughs that use C# and a brief description of each walkthrough.</span></span>

## <a name="see-also"></a><span data-ttu-id="92194-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92194-133">See also</span></span>

* [<span data-ttu-id="92194-134">使用 Visual Studio 的 Visual C# 和 Visual Basic 使用者入門</span><span class="sxs-lookup"><span data-stu-id="92194-134">Getting Started with Visual C# and Visual Basic using Visual Studio</span></span>](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)
