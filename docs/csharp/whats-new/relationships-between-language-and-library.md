---
title: "語言功能和程式庫類型之間的關聯性 |Microsoft 文件"
description: "語言功能經常會依賴程式庫類型實作。 了解該關聯性。"
keywords: "C# 語言設計中，標準程式庫"
author: billwagner
ms.author: wiwagn
ms.date: 07/20/2017
ms.topic: article
ms.prod: .net
ms.devlang: devlang-csharp
ms.openlocfilehash: 93fd26a72743fcf45df3904cb8d0c787d8a228a8
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2017
---
# <a name="relationships-between-language-features-and-library-types"></a><span data-ttu-id="350ec-105">語言功能和程式庫類型之間的關聯性</span><span class="sxs-lookup"><span data-stu-id="350ec-105">Relationships between language features and library types</span></span>

<span data-ttu-id="350ec-106">C# 語言定義需要具有特定型別和特定可存取的成員在這些類型的標準程式庫。</span><span class="sxs-lookup"><span data-stu-id="350ec-106">The C# language definition requires a standard library to have certain types and certain accessible members on those types.</span></span> <span data-ttu-id="350ec-107">編譯器會產生許多不同的語言功能會使用這些必要的型別和成員的程式碼。</span><span class="sxs-lookup"><span data-stu-id="350ec-107">The compiler generates code that uses these required types and members for many different language features.</span></span> <span data-ttu-id="350ec-108">必要時，有包含的類型撰寫程式碼，其中這些型別或成員具有尚未部署的環境時，所需的語言的較新版本的 NuGet 封裝。</span><span class="sxs-lookup"><span data-stu-id="350ec-108">When necessary, there are NuGet packages that contain types needed for newer versions of the language when writing code for environments where those types or members have not been deployed yet.</span></span>

<span data-ttu-id="350ec-109">這種相依性的標準程式庫功能已自其第一個版本的 C# 語言的一部分。</span><span class="sxs-lookup"><span data-stu-id="350ec-109">This dependency on standard library functionality has been part of the C# language since its first version.</span></span> <span data-ttu-id="350ec-110">在該版本中，包含的範例：</span><span class="sxs-lookup"><span data-stu-id="350ec-110">In that version, examples included:</span></span>

* <span data-ttu-id="350ec-111"><xref:System.Exception>-用於編譯器產生的所有例外狀況。</span><span class="sxs-lookup"><span data-stu-id="350ec-111"><xref:System.Exception> - used for all compiler generated exceptions.</span></span>
* <span data-ttu-id="350ec-112"><xref:System.String>-C#`string`類型是同義字<xref:System.String>。</span><span class="sxs-lookup"><span data-stu-id="350ec-112"><xref:System.String> - the C# `string` type is a synonym for <xref:System.String>.</span></span>
* <span data-ttu-id="350ec-113"><xref:System.Int32>-的同義字`int`。</span><span class="sxs-lookup"><span data-stu-id="350ec-113"><xref:System.Int32> - synonym of `int`.</span></span>

<span data-ttu-id="350ec-114">第一個版本很簡單： 編譯器和標準程式庫隨附在一起，而且每個版本，只有一個。</span><span class="sxs-lookup"><span data-stu-id="350ec-114">That first version was simple: the compiler and the standard library shipped together, and there was only one version of each.</span></span>

<span data-ttu-id="350ec-115">後續版本的 C# 偶爾會有新增新的型別或成員的相依性。</span><span class="sxs-lookup"><span data-stu-id="350ec-115">Subsequent versions of C# have occasionally added new types or members to the dependencies.</span></span> <span data-ttu-id="350ec-116">範例包括： <xref:System.Runtime.CompilerServices.INotifyCompletion>，<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>和<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>。</span><span class="sxs-lookup"><span data-stu-id="350ec-116">Examples include: <xref:System.Runtime.CompilerServices.INotifyCompletion>, <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> and <xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>.</span></span> <span data-ttu-id="350ec-117">C# 7.0 會繼續這上新增相依性<xref:System.ValueTuple>實作[tuple](../tuples.md)語言功能。</span><span class="sxs-lookup"><span data-stu-id="350ec-117">C# 7.0 continues this by adding a dependency on <xref:System.ValueTuple> to implement the [tuples](../tuples.md) language feature.</span></span>

<span data-ttu-id="350ec-118">語言設計團隊的運作方式的類型和相容的標準程式庫中所需成員的介面區最小化。</span><span class="sxs-lookup"><span data-stu-id="350ec-118">The language design team works to minimize the surface area of the types and members required in a compliant standard library.</span></span> <span data-ttu-id="350ec-119">針對全新設計，其中新程式庫功能會併入到語言的順暢地平衡該目標。</span><span class="sxs-lookup"><span data-stu-id="350ec-119">That goal is balanced against a clean design where new library features are incorporated seamlessly into the language.</span></span> <span data-ttu-id="350ec-120">會在 C# 需要新類型的未來版本中的新功能和標準程式庫中的成員。</span><span class="sxs-lookup"><span data-stu-id="350ec-120">There will be new features in future versions of C# that require new types and members in a standard library.</span></span> <span data-ttu-id="350ec-121">請務必了解如何管理您的工作中的這些相依性。</span><span class="sxs-lookup"><span data-stu-id="350ec-121">It's important to understand how to manage those dependencies in your work.</span></span>

## <a name="managing-your-dependencies"></a><span data-ttu-id="350ec-122">管理相依性</span><span class="sxs-lookup"><span data-stu-id="350ec-122">Managing your dependencies</span></span>

<span data-ttu-id="350ec-123">C# 編譯器工具現在會分開.NET 程式庫支援的平台上的發行週期。</span><span class="sxs-lookup"><span data-stu-id="350ec-123">C# compiler tools are now decoupled from the release cycle of the .NET libraries on supported platforms.</span></span> <span data-ttu-id="350ec-124">事實上，不同的.NET 程式庫有不同的發行週期： 在 Windows 上的.NET Framework 與 Windows Update relesed，.NET Core 隨附於個別的排程，並利用 Xamarin 工具，為每個目標平台程式庫更新出貨的 Xamarin 版本。</span><span class="sxs-lookup"><span data-stu-id="350ec-124">In fact, different .NET libraries have different release cycles: the .NET Framework on Windows is relesed as a Windows Update, .NET Core ships on a separate schedule, and the Xamarin versions of library updates ship with the Xamarin tools for each target platform.</span></span>

<span data-ttu-id="350ec-125">大部分的時間，您可能會發現這些變更。</span><span class="sxs-lookup"><span data-stu-id="350ec-125">The majority of time, you won't notice these changes.</span></span> <span data-ttu-id="350ec-126">不過，當您正在該平台上不需要功能的語言，但是.NET 程式庫中的較新版本，將參考的 NuGet 套件，以提供這些新的類型。</span><span class="sxs-lookup"><span data-stu-id="350ec-126">However, when you are working with a newer version of the language that requires features not yet in the .NET libraries on that platform, you'll reference the NuGet packages to provide those new types.</span></span>
<span data-ttu-id="350ec-127">為新的 framework 安裝會更新您的應用程式支援的平台，您可以移除額外的參考。</span><span class="sxs-lookup"><span data-stu-id="350ec-127">As the platforms your app supports are updated with new framework installations, you can remove the extra reference.</span></span>

<span data-ttu-id="350ec-128">這項分隔表示即使您的目標機器可能無法正確對應的架構，您可以使用新語言功能。</span><span class="sxs-lookup"><span data-stu-id="350ec-128">This separation means you can use new language features even when you are targeting machines that may not have the corresponding framework.</span></span>
