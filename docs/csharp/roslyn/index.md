---
title: "使用 .NET 編譯器 SDK - C# 指南"
description: "探索 Roslyn API 以建立自動診斷和程式碼修正"
keywords: .NET, .NET Core, C#, Roslyn,
ms.date: 06/25/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: abed9e00-2ddc-468e-9cca-d033bd6a7e36
redirect_url: /dotnet/csharp/index
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: b227d67fd5431da328e1686fd9afc6a3b9db035e
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---

# <a name="-using-the-net-compiler-sdk"></a><span data-ttu-id="27154-104">🔧 使用 .NET 編譯器 SDK</span><span class="sxs-lookup"><span data-stu-id="27154-104">🔧 Using the .NET Compiler SDK</span></span>

> <span data-ttu-id="27154-105">**注意**</span><span class="sxs-lookup"><span data-stu-id="27154-105">**Note**</span></span>
> 
> <span data-ttu-id="27154-106">本主題尚未開稿！</span><span class="sxs-lookup"><span data-stu-id="27154-106">This topic hasn’t been written yet!</span></span> 
>
> <span data-ttu-id="27154-107">歡迎您提供意見，協助擬定範圍和方向。</span><span class="sxs-lookup"><span data-stu-id="27154-107">We welcome your input to help shape the scope and approach.</span></span> <span data-ttu-id="27154-108">您可以追蹤狀態，並在 GitHub 提供關於此[問題](https://github.com/dotnet/docs/issues/972)的輸入。</span><span class="sxs-lookup"><span data-stu-id="27154-108">You can track the status and provide input on this [issue](https://github.com/dotnet/docs/issues/972) at GitHub.</span></span>
> 
> <span data-ttu-id="27154-109">如果您想要檢閱早期草稿和本主題的大綱，請在問題中留言並附上您的連絡資訊。</span><span class="sxs-lookup"><span data-stu-id="27154-109">If you would like to review early drafts and outlines of this topic, please leave a note with your contact information in the issue.</span></span>
>
> <span data-ttu-id="27154-110">深入了解如何參與 [GitHub](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md)。</span><span class="sxs-lookup"><span data-stu-id="27154-110">Learn more about how you can contribute on [GitHub](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).</span></span>
>

<span data-ttu-id="27154-111">這是整節的中繼主題。</span><span class="sxs-lookup"><span data-stu-id="27154-111">This is a meta-topic for an entire section.</span></span> <span data-ttu-id="27154-112">本文需要的涵蓋範圍領域包括：</span><span class="sxs-lookup"><span data-stu-id="27154-112">Areas that need to be covered here include:</span></span> 
* <span data-ttu-id="27154-113">快速入門</span><span class="sxs-lookup"><span data-stu-id="27154-113">Getting Started</span></span>
* <span data-ttu-id="27154-114">範例和教學課程</span><span class="sxs-lookup"><span data-stu-id="27154-114">Samples and tutorials</span></span>
* <span data-ttu-id="27154-115">概念性內容</span><span class="sxs-lookup"><span data-stu-id="27154-115">conceptual content</span></span>
* <span data-ttu-id="27154-116">API 的整體模型</span><span class="sxs-lookup"><span data-stu-id="27154-116">overall model of the APIs</span></span>
* <span data-ttu-id="27154-117">[roslyn-analyzers (英文)](http://github.com/dotnet/roslyn-analyzers) 儲存機制上範例的連結</span><span class="sxs-lookup"><span data-stu-id="27154-117">links to samples on the [roslyn-analyzers](http://github.com/dotnet/roslyn-analyzers) repository</span></span>
* <span data-ttu-id="27154-118">其他參考內容的連結</span><span class="sxs-lookup"><span data-stu-id="27154-118">links to other reference content</span></span>

