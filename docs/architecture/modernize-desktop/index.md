---
title: 使用 .NET 5 在 Windows 10 上現代化桌面應用程式
description: 瞭解如何使用 .NET 5 將現有的桌面應用程式現代化
ms.date: 01/06/2021
ms.openlocfilehash: de8a451b0598b5eabd99028d377c161dace61623
ms.sourcegitcommit: 632818f4b527e5bf3c48fc04e0c7f3b4bdb8a248
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98615696"
---
# <a name="modernizing-desktop-apps-on-windows-10-with-net-5"></a><span data-ttu-id="6a841-103">使用 .NET 5 在 Windows 10 上現代化桌面應用程式</span><span class="sxs-lookup"><span data-stu-id="6a841-103">Modernizing Desktop Apps on Windows 10 with .NET 5</span></span>

![顯示「現代化桌面應用程式」電子書封面的螢幕擷取畫面。](./media/modernizing-existing-desktop-apps-ebook-cover.png)

<span data-ttu-id="6a841-105">**版本 1.0.1** -更新至 .net 5</span><span class="sxs-lookup"><span data-stu-id="6a841-105">**EDITION v1.0.1** - Updated to .NET 5</span></span>

<span data-ttu-id="6a841-106">請參閱 [變更記錄](https://aka.ms/desktop-ebook-changelog) ，以取得書籍更新和社區貢獻。</span><span class="sxs-lookup"><span data-stu-id="6a841-106">Refer [changelog](https://aka.ms/desktop-ebook-changelog) for the book updates and community contributions.</span></span>

<span data-ttu-id="6a841-107">發行者</span><span class="sxs-lookup"><span data-stu-id="6a841-107">PUBLISHED BY</span></span>

<span data-ttu-id="6a841-108">Microsoft 開發人員部門 .NET 和 Visual Studio 產品小組</span><span class="sxs-lookup"><span data-stu-id="6a841-108">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="6a841-109">Microsoft Corporation 部門</span><span class="sxs-lookup"><span data-stu-id="6a841-109">A division of Microsoft Corporation</span></span>

<span data-ttu-id="6a841-110">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="6a841-110">One Microsoft Way</span></span>

<span data-ttu-id="6a841-111">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="6a841-111">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="6a841-112">Microsoft Corporation 的著作權©2021</span><span class="sxs-lookup"><span data-stu-id="6a841-112">Copyright © 2021 by Microsoft Corporation</span></span>

<span data-ttu-id="6a841-113">著作權所有，並保留一切權利。</span><span class="sxs-lookup"><span data-stu-id="6a841-113">All rights reserved.</span></span> <span data-ttu-id="6a841-114">本書內容的任何部分在未經過發行者書面許可下，不得以任何形式或透過任何方式進行重製或傳送。</span><span class="sxs-lookup"><span data-stu-id="6a841-114">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="6a841-115">本書依照「現況」提供，代表作者的觀點和意見。</span><span class="sxs-lookup"><span data-stu-id="6a841-115">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="6a841-116">本書中所述之觀點、意見與資訊 (包括 URL 及其他網際網路的網站參考) 如有變更，恕不另行通知。</span><span class="sxs-lookup"><span data-stu-id="6a841-116">The views, opinions, and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="6a841-117">此處描述的一些範例僅供說明之用，純屬虛構。</span><span class="sxs-lookup"><span data-stu-id="6a841-117">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="6a841-118">並未影射或關聯任何真實的人、事、物。</span><span class="sxs-lookup"><span data-stu-id="6a841-118">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="6a841-119">Microsoft 與列於 <https://www.microsoft.com>「商標」網頁的商標是 Microsoft 集團的商標。</span><span class="sxs-lookup"><span data-stu-id="6a841-119">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="6a841-120">Mac 與 macOS 是 Apple Inc. 的商標。</span><span class="sxs-lookup"><span data-stu-id="6a841-120">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="6a841-121">所有其他商標和標誌屬於其各自擁有者的財產。</span><span class="sxs-lookup"><span data-stu-id="6a841-121">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="6a841-122">共同作者：</span><span class="sxs-lookup"><span data-stu-id="6a841-122">Co-Authors:</span></span>

> <span data-ttu-id="6a841-123">**Olia Gavrysh**，Microsoft 的專案經理，.net 團隊</span><span class="sxs-lookup"><span data-stu-id="6a841-123">**Olia Gavrysh**, Program Manager, .NET team, Microsoft</span></span>

> <span data-ttu-id="6a841-124">**Miguel 天使 Castejón Dominguez**，創新架構設計師，Kabel</span><span class="sxs-lookup"><span data-stu-id="6a841-124">**Miguel Angel Castejón Dominguez**, Innovation Architect, Kabel</span></span>

<span data-ttu-id="6a841-125">參與者和檢閱者：</span><span class="sxs-lookup"><span data-stu-id="6a841-125">Participants and reviewers:</span></span>

> <span data-ttu-id="6a841-126">**Maira Wenzel**，Microsoft 資深專案經理，.net 團隊</span><span class="sxs-lookup"><span data-stu-id="6a841-126">**Maira Wenzel**, Senior Program Manager, .NET team, Microsoft</span></span>

> <span data-ttu-id="6a841-127">**Gorge**，資深內容開發人員，.net 檔團隊，Microsoft</span><span class="sxs-lookup"><span data-stu-id="6a841-127">**Andy De Gorge**, Senior Content Developer, .NET docs team, Microsoft</span></span>

> <span data-ttu-id="6a841-128">**Miguel Ramos**，Windows Developer Platform 團隊，Microsoft 的資深專案經理</span><span class="sxs-lookup"><span data-stu-id="6a841-128">**Miguel Ramos**, Senior Program Manager, Windows Developer Platform team, Microsoft</span></span>

> <span data-ttu-id="6a841-129">**Adam Braden**，首席程式經理，Windows Developer Platform 小組，Microsoft</span><span class="sxs-lookup"><span data-stu-id="6a841-129">**Adam Braden**, Principal Program Manager, Windows Developer Platform team, Microsoft</span></span>

> <span data-ttu-id="6a841-130">**Ricardo Minguez Pablos**，Microsoft Azure IoT 團隊資深專案經理</span><span class="sxs-lookup"><span data-stu-id="6a841-130">**Ricardo Minguez Pablos**, Senior Program Manager, Azure IoT team, Microsoft</span></span>

> <span data-ttu-id="6a841-131">**Nish Anil**，Microsoft 資深專案經理，.net 團隊</span><span class="sxs-lookup"><span data-stu-id="6a841-131">**Nish Anil**, Senior Program Manager, .NET team, Microsoft</span></span>

> <span data-ttu-id="6a841-132">Microsoft 資深產品行銷經理 **Beth Massi**</span><span class="sxs-lookup"><span data-stu-id="6a841-132">**Beth Massi**, Senior Product Marketing Manager, Microsoft</span></span>

> <span data-ttu-id="6a841-133">**Scott Hunter**，合作夥伴總監計畫經理，.net 團隊，Microsoft</span><span class="sxs-lookup"><span data-stu-id="6a841-133">**Scott Hunter**, Partner Director Program Manager, .NET team, Microsoft</span></span>

> <span data-ttu-id="6a841-134">**Marta Fuentes Lara**、Kabel</span><span class="sxs-lookup"><span data-stu-id="6a841-134">**Marta Fuentes Lara**, Kabel</span></span>

> <span data-ttu-id="6a841-135">**Raúl Fernández De Córdoba**、Kabel</span><span class="sxs-lookup"><span data-stu-id="6a841-135">**Raúl Fernández de Córdoba**, Kabel</span></span>

> <span data-ttu-id="6a841-136">**Antonio Manuel Fernández Cantos**，Kabel</span><span class="sxs-lookup"><span data-stu-id="6a841-136">**Antonio Manuel Fernández Cantos**, Kabel</span></span>

## <a name="introduction"></a><span data-ttu-id="6a841-137">簡介</span><span class="sxs-lookup"><span data-stu-id="6a841-137">Introduction</span></span>

<span data-ttu-id="6a841-138">這本書是關於您可以採用的策略，以透過現代化的途徑來移動現有的桌面應用程式，並納入最新的執行時間、語言和平臺功能。</span><span class="sxs-lookup"><span data-stu-id="6a841-138">This book is about strategies you can adopt to move your existing desktop applications through the path of modernization and incorporate the latest runtime, language, and platform features.</span></span> <span data-ttu-id="6a841-139">您會發現每個應用程式都不會有獨特的配方，因此您的需求和喜好設定。</span><span class="sxs-lookup"><span data-stu-id="6a841-139">You'll discover that there's no unique recipe as each application is different, and so are your requirements and preferences.</span></span> <span data-ttu-id="6a841-140">好消息是，您可以套用一些常見的方法，將新的功能新增至您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="6a841-140">The good news is that there are common approaches you can apply to add new features and capabilities to your applications.</span></span> <span data-ttu-id="6a841-141">其中有些甚至不需要修改程式碼。</span><span class="sxs-lookup"><span data-stu-id="6a841-141">Some of them won't even require major modifications of your code.</span></span> <span data-ttu-id="6a841-142">在本書中，我們將說明這些功能在幕後的運作方式，並說明其執行的機制。</span><span class="sxs-lookup"><span data-stu-id="6a841-142">In this book, we'll reveal how all those features work behind the scenes and explain the mechanics of their implementations.</span></span> <span data-ttu-id="6a841-143">此外，您會發現一些常見的現代化桌面應用程式案例，讓您可以找到發展專案的靈感。</span><span class="sxs-lookup"><span data-stu-id="6a841-143">Moreover, you'll find some common scenarios for modernizing existing desktop applications shown in detail so you can find inspiration for evolving your projects.</span></span>

<span data-ttu-id="6a841-144">Microsoft 的現代化現有應用程式的方法，是讓您彈性地建立自己的自訂路徑。</span><span class="sxs-lookup"><span data-stu-id="6a841-144">Microsoft's approach to modernizing existing applications is to give you the flexibility to create your own customized path.</span></span> <span data-ttu-id="6a841-145">本書中所述的所有現代化策略大多都是獨立的。</span><span class="sxs-lookup"><span data-stu-id="6a841-145">All the modernization strategies described in this book are mostly independent.</span></span> <span data-ttu-id="6a841-146">您可以選擇與您的應用程式相關的應用程式，並略過不重要的其他專案。</span><span class="sxs-lookup"><span data-stu-id="6a841-146">You can choose ones that are relevant for your application and skip others that aren't important for you.</span></span> <span data-ttu-id="6a841-147">換句話說，您可以混搭策略，以最符合您應用程式需求的方式。</span><span class="sxs-lookup"><span data-stu-id="6a841-147">In other words, you can mix and match the strategies to best address your application needs.</span></span>

## <a name="who-should-use-the-book"></a><span data-ttu-id="6a841-148">誰應該使用書</span><span class="sxs-lookup"><span data-stu-id="6a841-148">Who should use the book</span></span>

<span data-ttu-id="6a841-149">這本書適用于想要將現有的 Windows Forms 和 WPF 桌面應用程式現代化，以充分利用 .NET 和 Windows 10 的開發人員和解決方案架構設計人員。</span><span class="sxs-lookup"><span data-stu-id="6a841-149">This book for developers and solution architects who want to modernize existing Windows Forms and WPF desktop applications to leverage the benefits of .NET and Windows 10.</span></span>

<span data-ttu-id="6a841-150">如果您是技術決策者，例如企業架構設計人員或想要概述更新現有傳統型應用程式之優點的開發組長或主管，您可能也會覺得這本書很有用。</span><span class="sxs-lookup"><span data-stu-id="6a841-150">You might also find this book useful if you're a technical decision maker, such as an enterprise architect or a development lead or director who wants an overview of the benefits of updating existing desktop applications.</span></span>

## <a name="how-to-use-the-book"></a><span data-ttu-id="6a841-151">如何使用書</span><span class="sxs-lookup"><span data-stu-id="6a841-151">How to use the book</span></span>

<span data-ttu-id="6a841-152">本書解決了「原因」，也就是您可能想要將現有應用程式現代化的原因，以及利用 NET 和 MSIX 讓桌面應用程式現代化的特定好處。</span><span class="sxs-lookup"><span data-stu-id="6a841-152">This book addresses the "why"—why you might want to modernize your existing applications, and the specific benefits you get from using NET and MSIX to modernize your desktop apps.</span></span> <span data-ttu-id="6a841-153">本書的內容是專為想要瞭解的架構設計人員和技術決策者所設計，但不需要專注于執行和技術的逐步詳細資料。</span><span class="sxs-lookup"><span data-stu-id="6a841-153">The content of the book is designed for architects and technical decision makers who want an overview, but who don't need to focus on implementation and technical, step-by-step details.</span></span>

<span data-ttu-id="6a841-154">在不同的章節中，會提供範例程式碼程式碼片段和螢幕擷取畫面，其中第5章專門用來展示範例應用程式的完整遷移程式。</span><span class="sxs-lookup"><span data-stu-id="6a841-154">Along the different chapters, sample implementation code snippets and screenshots are provided, with chapter 5 devoted to showcase a complete migration process for sample applications.</span></span>

## <a name="what-this-book-doesnt-cover"></a><span data-ttu-id="6a841-155">本書未涵蓋的內容</span><span class="sxs-lookup"><span data-stu-id="6a841-155">What this book doesn't cover</span></span>

<span data-ttu-id="6a841-156">本書涵蓋了一組特定的案例，這些案例著重于隨即轉移案例，並概述在不需要重寫程式碼的情況下，獲得現代化優勢的方法。</span><span class="sxs-lookup"><span data-stu-id="6a841-156">This book covers a specific subset of scenarios that are focused on lift-and-shift scenarios, outlining the way to gain the benefits of modernizing without the effort of rewriting code.</span></span>

<span data-ttu-id="6a841-157">這本書不是從頭開始使用 .NET 開發新式應用程式，或是開始使用 Windows Forms 和 WPF。</span><span class="sxs-lookup"><span data-stu-id="6a841-157">This book isn't about developing modern applications with .NET from scratch or about getting started with Windows Forms and WPF.</span></span> <span data-ttu-id="6a841-158">它著重于如何以最新的桌上型電腦開發技術來更新現有的桌面應用程式。</span><span class="sxs-lookup"><span data-stu-id="6a841-158">It focuses on how you can update existing desktop applications with the latest technologies for desktop development.</span></span>

## <a name="samples-used-in-this-book"></a><span data-ttu-id="6a841-159">本書中使用的範例</span><span class="sxs-lookup"><span data-stu-id="6a841-159">Samples used in this book</span></span>

<span data-ttu-id="6a841-160">為了強調執行現代化的必要步驟，我們將使用名為的範例應用程式 `eShopModernizing` 。</span><span class="sxs-lookup"><span data-stu-id="6a841-160">To highlight the necessary steps to perform a modernization, we'll be using a sample application called `eShopModernizing`.</span></span> <span data-ttu-id="6a841-161">此應用程式有兩種類別，Windows Forms 和 WPF，而我們將示範如何在這兩個 .NET 上執行現代化的逐步流程。</span><span class="sxs-lookup"><span data-stu-id="6a841-161">This application has two flavors, Windows Forms and WPF, and we'll show a step-by-step process on how to perform the modernization on both of them to .NET.</span></span>

<span data-ttu-id="6a841-162">此外，您也可以在本書的 GitHub 存放庫中找到此程式的結果，如果您決定要遵循逐步教學課程，就可以參考此程式。</span><span class="sxs-lookup"><span data-stu-id="6a841-162">Also, on the GitHub repository for this book, you'll find the results of the process, which you can consult with if you decide to follow the step-by-step tutorial.</span></span>

## <a name="send-your-feedback"></a><span data-ttu-id="6a841-163">傳送您的意見反應</span><span class="sxs-lookup"><span data-stu-id="6a841-163">Send your feedback</span></span>

<span data-ttu-id="6a841-164">本書和相關的範例不斷演進，所以您的意見反應歡迎！</span><span class="sxs-lookup"><span data-stu-id="6a841-164">This book and related samples are constantly evolving, so your feedback is welcomed!</span></span> <span data-ttu-id="6a841-165">如果您有關于如何改進本書的意見，請使用內建于 [GitHub 問題](https://github.com/dotnet/docs/issues)之任何頁面底部的意見反應區段。</span><span class="sxs-lookup"><span data-stu-id="6a841-165">If you have comments about how this book can be improved, use the feedback section at the bottom of any page built on [GitHub issues](https://github.com/dotnet/docs/issues).</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="6a841-166">下一步</span><span class="sxs-lookup"><span data-stu-id="6a841-166">Next</span></span>](why-modern-applications.md)
