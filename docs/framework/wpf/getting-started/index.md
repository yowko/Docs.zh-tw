---
title: "使用者入門 (WPF) | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- getting started [WPF]
- introduction [WPF]
- WPF, getting started
ms.assetid: 04f91da8-708c-46c7-8172-f1695ec847cd
caps.latest.revision: 60
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 83c9c6fc754bcee3bb3a893ca21be21d169226cf
ms.contentlocale: zh-tw
ms.lasthandoff: 05/02/2017

---
# <a name="getting-started-wpf"></a><span data-ttu-id="a74a2-102">使用者入門 (WPF)</span><span class="sxs-lookup"><span data-stu-id="a74a2-102">Getting Started (WPF)</span></span>
<span data-ttu-id="a74a2-103">Windows Presentation Foundation (WPF) 是建立桌面用戶端應用程式的 UI 架構。</span><span class="sxs-lookup"><span data-stu-id="a74a2-103">Windows Presentation Foundation (WPF) is a UI framework that creates desktop client applications.</span></span> <span data-ttu-id="a74a2-104">WPF 開發平台支援一組廣泛的應用程式開發功能，包含應用程式模型、資源、控制項、圖形、版面配置、資料繫結、文件和安全性。</span><span class="sxs-lookup"><span data-stu-id="a74a2-104">The WPF development platform supports a broad set of application development features, including an application model, resources, controls, graphics, layout, data binding, documents, and security.</span></span> <span data-ttu-id="a74a2-105">它是 .NET Framework 的子集，所以若您先前已使用 ASP.NET 或 Windows Form 以 .NET Framework 建置過應用程式，應該會對此程式設計體驗感到熟悉。</span><span class="sxs-lookup"><span data-stu-id="a74a2-105">It is a subset of the .NET Framework, so if you have previously built applications with the .NET Framework using ASP.NET or Windows Forms, the programming experience should be familiar.</span></span> <span data-ttu-id="a74a2-106">WPF 使用可延伸應用程式標記語言 (XAML) 來提供應用程式設計的宣告式模型。</span><span class="sxs-lookup"><span data-stu-id="a74a2-106">WPF uses the Extensible Application Markup Language (XAML) to provide a declarative model for application programming.</span></span> <span data-ttu-id="a74a2-107">本章節的主題將介紹及幫助您開始使用 WPF。</span><span class="sxs-lookup"><span data-stu-id="a74a2-107">This section has topics that introduce and help you get started with WPF.</span></span>  
  
## <a name="where-should-i-start"></a><span data-ttu-id="a74a2-108">我該從哪裡開始？</span><span class="sxs-lookup"><span data-stu-id="a74a2-108">Where Should I Start?</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a74a2-109">我想直接開始</span><span class="sxs-lookup"><span data-stu-id="a74a2-109">I want to jump right in…</span></span>|[<span data-ttu-id="a74a2-110">逐步解說：我的第一個 WPF 傳統型應用程式</span><span class="sxs-lookup"><span data-stu-id="a74a2-110">Walkthrough: My First WPF Desktop Application</span></span>](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)|  
|<span data-ttu-id="a74a2-111">我該如何設計應用程式 UI？</span><span class="sxs-lookup"><span data-stu-id="a74a2-111">How do I design the application UI?</span></span>|[<span data-ttu-id="a74a2-112">在 Visual Studio 中設計 XAML</span><span class="sxs-lookup"><span data-stu-id="a74a2-112">Designing XAML in Visual Studio</span></span>](http://msdn.microsoft.com/library/288e2415-9fcf-408e-bc35-9848315e14fd)|  
|<span data-ttu-id="a74a2-113">剛開始使用 .NET 嗎？</span><span class="sxs-lookup"><span data-stu-id="a74a2-113">New to .NET?</span></span>|<span data-ttu-id="a74a2-114">[.NET Framework 概觀](https://msdn.microsoft.com/en-us/library/zw4w595w\(v=vs.140\).aspx)</span><span class="sxs-lookup"><span data-stu-id="a74a2-114">[Overview of the .NET Framework](https://msdn.microsoft.com/en-us/library/zw4w595w\(v=vs.140\).aspx)</span></span><br /><br /> [<span data-ttu-id="a74a2-115">.NET Framework 應用程式基本概念</span><span class="sxs-lookup"><span data-stu-id="a74a2-115">.NET Framework Application Essentials</span></span>](../../../../docs/standard/application-essentials.md)<br /><br /> <span data-ttu-id="a74a2-116">[Visual C# 和 Visual Basic 使用者入門](https://msdn.microsoft.com/en-us/library/dd492171\(v=vs.140\).aspx)</span><span class="sxs-lookup"><span data-stu-id="a74a2-116">[Getting Started with Visual C# and Visual Basic](https://msdn.microsoft.com/en-us/library/dd492171\(v=vs.140\).aspx)</span></span>|  
|<span data-ttu-id="a74a2-117">WPF 的相關詳細資訊...</span><span class="sxs-lookup"><span data-stu-id="a74a2-117">Tell me more about WPF…</span></span>|[<span data-ttu-id="a74a2-118">Visual Studio 2015 中的 WPF 簡介</span><span class="sxs-lookup"><span data-stu-id="a74a2-118">Introduction to WPF in Visual Studio 2015</span></span>](../../../../docs/framework/wpf/getting-started/introduction-to-wpf-in-vs.md)<br /><br /> [<span data-ttu-id="a74a2-119">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="a74a2-119">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)<br /><br /> [<span data-ttu-id="a74a2-120">控制項</span><span class="sxs-lookup"><span data-stu-id="a74a2-120">Controls</span></span>](../../../../docs/framework/wpf/controls/index.md)<br /><br /> [<span data-ttu-id="a74a2-121">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="a74a2-121">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)|  
|<span data-ttu-id="a74a2-122">您是 Windows Form 開發人員嗎？</span><span class="sxs-lookup"><span data-stu-id="a74a2-122">Are you a Windows Forms developer?</span></span>|[<span data-ttu-id="a74a2-123">Windows Forms 控制項和對等 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="a74a2-123">Windows Forms Controls and Equivalent WPF Controls</span></span>](../../../../docs/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls.md)<br /><br /> [<span data-ttu-id="a74a2-124">WPF 和 Windows Forms 互通</span><span class="sxs-lookup"><span data-stu-id="a74a2-124">WPF and Windows Forms Interoperation</span></span>](../../../../docs/framework/wpf/advanced/wpf-and-windows-forms-interoperation.md)|  
  
## <a name="see-also"></a><span data-ttu-id="a74a2-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a74a2-125">See Also</span></span>  
 <span data-ttu-id="a74a2-126">[類別庫](../../../../docs/framework/wpf/class-library-wpf.md) </span><span class="sxs-lookup"><span data-stu-id="a74a2-126">[Class Library](../../../../docs/framework/wpf/class-library-wpf.md) </span></span>  
<span data-ttu-id="a74a2-127"> [應用程式開發](../../../../docs/framework/wpf/app-development/index.md) </span><span class="sxs-lookup"><span data-stu-id="a74a2-127"> [Application Development](../../../../docs/framework/wpf/app-development/index.md) </span></span>  
<span data-ttu-id="a74a2-128"> [.NET Framework 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=187437)</span><span class="sxs-lookup"><span data-stu-id="a74a2-128"> [.NET Framework Developer Center](http://go.microsoft.com/fwlink/?LinkId=187437)</span></span>
