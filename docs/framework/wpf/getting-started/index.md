---
title: "使用者入門 (WPF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- getting started [WPF]
- introduction [WPF]
- WPF [WPF], getting started
ms.assetid: 04f91da8-708c-46c7-8172-f1695ec847cd
caps.latest.revision: "60"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b74eafb1189335a642df7cb267727ef7e8ee59b7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="getting-started-wpf"></a><span data-ttu-id="26bfb-102">使用者入門 (WPF)</span><span class="sxs-lookup"><span data-stu-id="26bfb-102">Getting Started (WPF)</span></span>
<span data-ttu-id="26bfb-103">Windows Presentation Foundation (WPF) 是建立桌面用戶端應用程式的 UI 架構。</span><span class="sxs-lookup"><span data-stu-id="26bfb-103">Windows Presentation Foundation (WPF) is a UI framework that creates desktop client applications.</span></span> <span data-ttu-id="26bfb-104">WPF 開發平台支援一組廣泛的應用程式開發功能，包含應用程式模型、資源、控制項、圖形、版面配置、資料繫結、文件和安全性。</span><span class="sxs-lookup"><span data-stu-id="26bfb-104">The WPF development platform supports a broad set of application development features, including an application model, resources, controls, graphics, layout, data binding, documents, and security.</span></span> <span data-ttu-id="26bfb-105">它是 .NET Framework 的子集，所以若您先前已使用 ASP.NET 或 Windows Form 以 .NET Framework 建置過應用程式，應該會對此程式設計體驗感到熟悉。</span><span class="sxs-lookup"><span data-stu-id="26bfb-105">It is a subset of the .NET Framework, so if you have previously built applications with the .NET Framework using ASP.NET or Windows Forms, the programming experience should be familiar.</span></span> <span data-ttu-id="26bfb-106">WPF 使用可延伸應用程式標記語言 (XAML) 來提供應用程式設計的宣告式模型。</span><span class="sxs-lookup"><span data-stu-id="26bfb-106">WPF uses the Extensible Application Markup Language (XAML) to provide a declarative model for application programming.</span></span> <span data-ttu-id="26bfb-107">本章節的主題將介紹及幫助您開始使用 WPF。</span><span class="sxs-lookup"><span data-stu-id="26bfb-107">This section has topics that introduce and help you get started with WPF.</span></span>  
  
## <a name="where-should-i-start"></a><span data-ttu-id="26bfb-108">我該從哪裡開始？</span><span class="sxs-lookup"><span data-stu-id="26bfb-108">Where Should I Start?</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="26bfb-109">我想直接開始</span><span class="sxs-lookup"><span data-stu-id="26bfb-109">I want to jump right in…</span></span>|[<span data-ttu-id="26bfb-110">逐步解說：我的第一個 WPF 傳統型應用程式</span><span class="sxs-lookup"><span data-stu-id="26bfb-110">Walkthrough: My first WPF desktop application</span></span>](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)|  
|<span data-ttu-id="26bfb-111">我該如何設計應用程式 UI？</span><span class="sxs-lookup"><span data-stu-id="26bfb-111">How do I design the application UI?</span></span>|[<span data-ttu-id="26bfb-112">在 Visual Studio 中設計 XAML</span><span class="sxs-lookup"><span data-stu-id="26bfb-112">Designing XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)|  
|<span data-ttu-id="26bfb-113">剛開始使用 .NET 嗎？</span><span class="sxs-lookup"><span data-stu-id="26bfb-113">New to .NET?</span></span>|<span data-ttu-id="26bfb-114">[.NET Framework 概觀](https://msdn.microsoft.com/en-us/library/zw4w595w\(v=vs.140\).aspx)</span><span class="sxs-lookup"><span data-stu-id="26bfb-114">[Overview of the .NET Framework](https://msdn.microsoft.com/en-us/library/zw4w595w\(v=vs.140\).aspx)</span></span><br /><br /> [<span data-ttu-id="26bfb-115">.NET Framework 應用程式基本概念</span><span class="sxs-lookup"><span data-stu-id="26bfb-115">.NET Framework Application Essentials</span></span>](../../../../docs/standard/application-essentials.md)<br /><br /> <span data-ttu-id="26bfb-116">[Visual C# 和 Visual Basic 使用者入門](https://msdn.microsoft.com/en-us/library/dd492171\(v=vs.140\).aspx)</span><span class="sxs-lookup"><span data-stu-id="26bfb-116">[Getting Started with Visual C# and Visual Basic](https://msdn.microsoft.com/en-us/library/dd492171\(v=vs.140\).aspx)</span></span>|  
|<span data-ttu-id="26bfb-117">WPF 的相關詳細資訊...</span><span class="sxs-lookup"><span data-stu-id="26bfb-117">Tell me more about WPF…</span></span>|[<span data-ttu-id="26bfb-118">Visual Studio 2015 中的 WPF 簡介</span><span class="sxs-lookup"><span data-stu-id="26bfb-118">Introduction to WPF in Visual Studio 2015</span></span>](../../../../docs/framework/wpf/getting-started/introduction-to-wpf-in-vs.md)<br /><br /> [<span data-ttu-id="26bfb-119">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="26bfb-119">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)<br /><br /> [<span data-ttu-id="26bfb-120">控制項</span><span class="sxs-lookup"><span data-stu-id="26bfb-120">Controls</span></span>](../../../../docs/framework/wpf/controls/index.md)<br /><br /> [<span data-ttu-id="26bfb-121">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="26bfb-121">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)|  
|<span data-ttu-id="26bfb-122">您是 Windows Form 開發人員嗎？</span><span class="sxs-lookup"><span data-stu-id="26bfb-122">Are you a Windows Forms developer?</span></span>|[<span data-ttu-id="26bfb-123">Windows Form 控制項和對等 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="26bfb-123">Windows Forms Controls and Equivalent WPF Controls</span></span>](../../../../docs/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls.md)<br /><br /> [<span data-ttu-id="26bfb-124">WPF 和 Windows Forms 互通</span><span class="sxs-lookup"><span data-stu-id="26bfb-124">WPF and Windows Forms Interoperation</span></span>](../../../../docs/framework/wpf/advanced/wpf-and-windows-forms-interoperation.md)|  
  
## <a name="see-also"></a><span data-ttu-id="26bfb-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="26bfb-125">See Also</span></span>  
 [<span data-ttu-id="26bfb-126">類別庫</span><span class="sxs-lookup"><span data-stu-id="26bfb-126">Class Library</span></span>](../../../../docs/framework/wpf/class-library-wpf.md)  
 [<span data-ttu-id="26bfb-127">應用程式開發</span><span class="sxs-lookup"><span data-stu-id="26bfb-127">Application Development</span></span>](../../../../docs/framework/wpf/app-development/index.md)  
 [<span data-ttu-id="26bfb-128">.NET Framework 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="26bfb-128">.NET Framework Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=187437)
