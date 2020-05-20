---
title: 使用 .NET Core 3.1 在 Windows 10 上現代化桌面應用程式
description: 瞭解如何使用 .NET Core 3.1 現代化現有的桌面應用程式
ms.date: 05/12/2020
ms.openlocfilehash: 5861f806a9158ef761c47bc23e51327d4e2d0480
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2020
ms.locfileid: "83423233"
---
# <a name="modernizing-desktop-apps-on-windows-10-with-net-core-31"></a><span data-ttu-id="e6b93-103">使用 .NET Core 3.1 在 Windows 10 上現代化桌面應用程式</span><span class="sxs-lookup"><span data-stu-id="e6b93-103">Modernizing Desktop Apps on Windows 10 with .NET Core 3.1</span></span>

![顯示現代化桌面應用程式電子書的螢幕擷取畫面。](./media/modernizing-existing-desktop-apps-ebook-cover.png)

<span data-ttu-id="e6b93-105">發行者</span><span class="sxs-lookup"><span data-stu-id="e6b93-105">PUBLISHED BY</span></span>

<span data-ttu-id="e6b93-106">Microsoft 開發人員部門 .NET 和 Visual Studio 產品小組</span><span class="sxs-lookup"><span data-stu-id="e6b93-106">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="e6b93-107">Microsoft Corporation 部門</span><span class="sxs-lookup"><span data-stu-id="e6b93-107">A division of Microsoft Corporation</span></span>

<span data-ttu-id="e6b93-108">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="e6b93-108">One Microsoft Way</span></span>

<span data-ttu-id="e6b93-109">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="e6b93-109">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="e6b93-110">Microsoft Corporation 的著作權©2020</span><span class="sxs-lookup"><span data-stu-id="e6b93-110">Copyright © 2020 by Microsoft Corporation</span></span>

<span data-ttu-id="e6b93-111">著作權所有，並保留一切權利。</span><span class="sxs-lookup"><span data-stu-id="e6b93-111">All rights reserved.</span></span> <span data-ttu-id="e6b93-112">本書內容的任何部分在未經過發行者書面許可下，不得以任何形式或透過任何方式進行重製或傳送。</span><span class="sxs-lookup"><span data-stu-id="e6b93-112">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="e6b93-113">本書依照「現況」提供，代表作者的觀點和意見。</span><span class="sxs-lookup"><span data-stu-id="e6b93-113">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="e6b93-114">本書中所述之觀點、意見與資訊 (包括 URL 及其他網際網路網站參考) 可能會隨時變更，恕不另行通知。</span><span class="sxs-lookup"><span data-stu-id="e6b93-114">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="e6b93-115">此處描述的一些範例僅供說明之用，純屬虛構。</span><span class="sxs-lookup"><span data-stu-id="e6b93-115">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="e6b93-116">並未影射或關聯任何真實的人、事、物。</span><span class="sxs-lookup"><span data-stu-id="e6b93-116">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="e6b93-117">Microsoft 與列於 <https://www.microsoft.com>「商標」網頁的商標是 Microsoft 集團的商標。</span><span class="sxs-lookup"><span data-stu-id="e6b93-117">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="e6b93-118">Mac 與 macOS 是 Apple Inc. 的商標。</span><span class="sxs-lookup"><span data-stu-id="e6b93-118">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="e6b93-119">所有其他商標和標誌屬於其各自擁有者的財產。</span><span class="sxs-lookup"><span data-stu-id="e6b93-119">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="e6b93-120">共同作者：</span><span class="sxs-lookup"><span data-stu-id="e6b93-120">Co-Authors:</span></span>

> <span data-ttu-id="e6b93-121">**Olia Gavrysh**，Microsoft 的計畫經理，.net 團隊</span><span class="sxs-lookup"><span data-stu-id="e6b93-121">**Olia Gavrysh**, Program Manager, .NET team, Microsoft</span></span>

> <span data-ttu-id="e6b93-122">**Miguel 天使 Castejón Dominguez**，創新架構師，Kabel</span><span class="sxs-lookup"><span data-stu-id="e6b93-122">**Miguel Angel Castejón Dominguez**, Innovation Architect, Kabel</span></span>

<span data-ttu-id="e6b93-123">參與者和檢閱者：</span><span class="sxs-lookup"><span data-stu-id="e6b93-123">Participants and reviewers:</span></span>

> <span data-ttu-id="e6b93-124">**Maira Wenzel**，Microsoft 的資深計畫經理，.net 團隊</span><span class="sxs-lookup"><span data-stu-id="e6b93-124">**Maira Wenzel**, Senior Program Manager, .NET team, Microsoft</span></span>

> <span data-ttu-id="e6b93-125">**Gorge**，Microsoft 的資深內容開發人員，.net 檔團隊</span><span class="sxs-lookup"><span data-stu-id="e6b93-125">**Andy De Gorge**, Senior Content Developer, .NET docs team, Microsoft</span></span>

> <span data-ttu-id="e6b93-126">**Miguel Ramos**，Microsoft 資深計畫經理，Windows 開發人員平臺小組</span><span class="sxs-lookup"><span data-stu-id="e6b93-126">**Miguel Ramos**, Senior Program Manager, Windows Developer Platform team, Microsoft</span></span>

> <span data-ttu-id="e6b93-127">**Adam Braden**，首席程式經理，Windows 開發人員平臺小組，Microsoft</span><span class="sxs-lookup"><span data-stu-id="e6b93-127">**Adam Braden**, Principal Program Manager, Windows Developer Platform team, Microsoft</span></span>

> <span data-ttu-id="e6b93-128">**Ricardo Minguez Pablos**，Microsoft 資深計畫經理，Azure IoT 團隊</span><span class="sxs-lookup"><span data-stu-id="e6b93-128">**Ricardo Minguez Pablos**, Senior Program Manager, Azure IoT team, Microsoft</span></span>

> <span data-ttu-id="e6b93-129">**Nish Anil**，Microsoft 的資深計畫經理，.net 團隊</span><span class="sxs-lookup"><span data-stu-id="e6b93-129">**Nish Anil**, Senior Program Manager, .NET team, Microsoft</span></span>

> <span data-ttu-id="e6b93-130">Microsoft 資深產品行銷經理**Beth Massi**</span><span class="sxs-lookup"><span data-stu-id="e6b93-130">**Beth Massi**, Senior Product Marketing Manager, Microsoft</span></span>

> <span data-ttu-id="e6b93-131">**Scott Hunter**，合作夥伴總監計畫經理，.net 小組，Microsoft</span><span class="sxs-lookup"><span data-stu-id="e6b93-131">**Scott Hunter**, Partner Director Program Manager, .NET team, Microsoft</span></span>

> <span data-ttu-id="e6b93-132">**Marta Fuentes Lara**、Kabel</span><span class="sxs-lookup"><span data-stu-id="e6b93-132">**Marta Fuentes Lara**, Kabel</span></span>

> <span data-ttu-id="e6b93-133">**Raúl Fernández De Córdoba**，Kabel</span><span class="sxs-lookup"><span data-stu-id="e6b93-133">**Raúl Fernández de Córdoba**, Kabel</span></span>

> <span data-ttu-id="e6b93-134">**Antonio Manuel Fernández Cantos**，Kabel</span><span class="sxs-lookup"><span data-stu-id="e6b93-134">**Antonio Manuel Fernández Cantos**, Kabel</span></span>

## <a name="introduction"></a><span data-ttu-id="e6b93-135">簡介</span><span class="sxs-lookup"><span data-stu-id="e6b93-135">Introduction</span></span>

<span data-ttu-id="e6b93-136">本書是關於透過現代化的途徑來移動現有的桌面應用程式，以及納入最新的執行時間、語言和平臺功能時，您可以採用的策略。</span><span class="sxs-lookup"><span data-stu-id="e6b93-136">This book is about strategies you can adopt to move your existing desktop applications through the path of modernization and incorporate the latest runtime, language, and platform features.</span></span> <span data-ttu-id="e6b93-137">您會發現，因為每個應用程式都不同，所以沒有任何獨特的配方，因此您的需求和喜好設定。</span><span class="sxs-lookup"><span data-stu-id="e6b93-137">You'll discover that there's no unique recipe as each application is different, and so are your requirements and preferences.</span></span> <span data-ttu-id="e6b93-138">好消息是，您可以套用一些常用的方法，在應用程式中加入新的功能和功能。</span><span class="sxs-lookup"><span data-stu-id="e6b93-138">The good news is that there are common approaches you can apply to add new features and capabilities to your applications.</span></span> <span data-ttu-id="e6b93-139">其中一些甚至不需要對程式碼進行重大修改。</span><span class="sxs-lookup"><span data-stu-id="e6b93-139">Some of them won't even require major modifications of your code.</span></span> <span data-ttu-id="e6b93-140">在本書中，我們將展示這些功能在幕後的運作方式，並說明其實現的機制。</span><span class="sxs-lookup"><span data-stu-id="e6b93-140">In this book, we'll reveal how all those features work behind the scenes and explain the mechanics of their implementations.</span></span> <span data-ttu-id="e6b93-141">此外，您還可以找到現代化詳細顯示的現有桌面應用程式的一些常見案例，讓您可以找出演變專案的靈感。</span><span class="sxs-lookup"><span data-stu-id="e6b93-141">Moreover, you'll find some common scenarios for modernizing existing desktop applications shown in detail so you can find inspiration for evolving your projects.</span></span>

<span data-ttu-id="e6b93-142">Microsoft 現代化現有應用程式的方法，是讓您彈性地建立自己的自訂路徑。</span><span class="sxs-lookup"><span data-stu-id="e6b93-142">Microsoft's approach to modernizing existing applications is to give you the flexibility to create your own customized path.</span></span> <span data-ttu-id="e6b93-143">本書中所述的所有現代化策略大多都是獨立的。</span><span class="sxs-lookup"><span data-stu-id="e6b93-143">All the modernization strategies described in this book are mostly independent.</span></span> <span data-ttu-id="e6b93-144">您可以選擇與您的應用程式相關的專案，並略過其他對您不重要的部分。</span><span class="sxs-lookup"><span data-stu-id="e6b93-144">You can choose ones that are relevant for your application and skip others that aren't important for you.</span></span> <span data-ttu-id="e6b93-145">換句話說，您可以混搭並符合您的應用程式需求的最佳處理策略。</span><span class="sxs-lookup"><span data-stu-id="e6b93-145">In other words, you can mix and match the strategies to best address your application needs.</span></span>

## <a name="who-should-use-the-book"></a><span data-ttu-id="e6b93-146">誰應該使用本書</span><span class="sxs-lookup"><span data-stu-id="e6b93-146">Who should use the book</span></span>

<span data-ttu-id="e6b93-147">我們為想要現代化現有 Windows Forms 和 WPF 桌面應用程式的開發人員和解決方案架構師寫本書，以利用 .NET Core 和 Windows 10 的優勢。</span><span class="sxs-lookup"><span data-stu-id="e6b93-147">We wrote this book for developers and solution architects who want to modernize existing Windows Forms and WPF desktop applications to leverage the benefits of .NET Core and Windows 10.</span></span>

<span data-ttu-id="e6b93-148">如果您是技術決策者，例如企業架構師或開發組長或主管，想要瞭解更新現有桌面應用程式的優點，您也可能會發現這本書很有用。</span><span class="sxs-lookup"><span data-stu-id="e6b93-148">You might also find this book useful if you're a technical decision maker, such as an enterprise architect or a development lead or director who wants an overview of the benefits of updating existing desktop applications.</span></span>

## <a name="how-to-use-the-book"></a><span data-ttu-id="e6b93-149">如何使用本書</span><span class="sxs-lookup"><span data-stu-id="e6b93-149">How to use the book</span></span>

<span data-ttu-id="e6b93-150">本書解決了「原因」-您可能想要將現有的應用程式現代化，以及使用 NET Core 3.1 和 MSIX 將桌面應用程式現代化所得到的特定權益。</span><span class="sxs-lookup"><span data-stu-id="e6b93-150">This book addresses the "why"—why you might want to modernize your existing applications, and the specific benefits you get from using NET Core 3.1 and MSIX to modernize your desktop apps.</span></span> <span data-ttu-id="e6b93-151">本書的內容是專為想要總覽，但不需要專注于執行和技術、逐步詳細資料的架構師和技術決策者所設計。</span><span class="sxs-lookup"><span data-stu-id="e6b93-151">The content of the book is designed for architects and technical decision makers who want an overview, but who don't need to focus on implementation and technical, step-by-step details.</span></span>

<span data-ttu-id="e6b93-152">在不同的章節中，會提供範例執行程式碼片段和螢幕擷取畫面，其中第5章專門用來展示範例應用程式的完整遷移流程。</span><span class="sxs-lookup"><span data-stu-id="e6b93-152">Along the different chapters, sample implementation code snippets and screenshots are provided, with chapter 5 devoted to showcase a complete migration process for sample applications.</span></span>

## <a name="what-this-book-doesnt-cover"></a><span data-ttu-id="e6b93-153">本書未涵蓋的內容</span><span class="sxs-lookup"><span data-stu-id="e6b93-153">What this book doesn't cover</span></span>

<span data-ttu-id="e6b93-154">本書涵蓋了一組特定的案例，著重于隨即轉移案例，並概述在不需要重寫程式碼的情況下，取得現代化優勢的方式。</span><span class="sxs-lookup"><span data-stu-id="e6b93-154">This book covers a specific subset of scenarios that are focused on lift-and-shift scenarios, outlining the way to gain the benefits of modernizing without the effort of rewriting code.</span></span>

<span data-ttu-id="e6b93-155">本書不是關於從頭開始使用 .NET Core 來開發現代化應用程式，或 Windows Forms 和 WPF 入門。</span><span class="sxs-lookup"><span data-stu-id="e6b93-155">This book isn't about developing modern applications with .NET Core from scratch or about getting started with Windows Forms and WPF.</span></span> <span data-ttu-id="e6b93-156">它著重于如何使用最新的桌面開發技術來更新現有的桌面應用程式。</span><span class="sxs-lookup"><span data-stu-id="e6b93-156">It focuses on how you can update existing desktop applications with the latest technologies for desktop development.</span></span>

## <a name="samples-used-in-this-book"></a><span data-ttu-id="e6b93-157">本書中使用的範例</span><span class="sxs-lookup"><span data-stu-id="e6b93-157">Samples used in this book</span></span>

<span data-ttu-id="e6b93-158">為了強調執行現代化的必要步驟，我們將使用名為的範例應用程式 `eShopModernizing` 。</span><span class="sxs-lookup"><span data-stu-id="e6b93-158">To highlight the necessary steps to perform a modernization, we'll be using a sample application called `eShopModernizing`.</span></span> <span data-ttu-id="e6b93-159">此應用程式有兩種類別，Windows Forms 和 WPF，我們將示範如何對 .NET Core 執行其現代化的逐步程式。</span><span class="sxs-lookup"><span data-stu-id="e6b93-159">This application has two flavors, Windows Forms and WPF, and we'll show a step-by-step process on how to perform the modernization on both of them to .NET Core.</span></span>

<span data-ttu-id="e6b93-160">此外，在本書的 GitHub 存放庫中，您會發現程式的結果，如果您決定遵循逐步教學課程，就可以向您詢問。</span><span class="sxs-lookup"><span data-stu-id="e6b93-160">Also, on the GitHub repository for this book, you'll find the results of the process, which you can consult with if you decide to follow the step-by-step tutorial.</span></span>

## <a name="send-your-feedback"></a><span data-ttu-id="e6b93-161">傳送您的意見反應</span><span class="sxs-lookup"><span data-stu-id="e6b93-161">Send your feedback</span></span>

<span data-ttu-id="e6b93-162">這本書與相關範例不斷演進，所以您的意見反應歡迎！</span><span class="sxs-lookup"><span data-stu-id="e6b93-162">This book and related samples are constantly evolving, so your feedback is welcomed!</span></span> <span data-ttu-id="e6b93-163">如果您有關于如何改進這本書的意見，請使用[GitHub 問題](https://github.com/dotnet/docs/issues)上任何網頁底部的 [意見反應] 區段。</span><span class="sxs-lookup"><span data-stu-id="e6b93-163">If you have comments about how this book can be improved, use the feedback section at the bottom of any page built on [GitHub issues](https://github.com/dotnet/docs/issues).</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="e6b93-164">下一步</span><span class="sxs-lookup"><span data-stu-id="e6b93-164">Next</span></span>](why-modern-applications.md)
