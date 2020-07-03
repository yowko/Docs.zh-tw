---
title: 開始使用
description: 使用 Windows Presentation Foundation （WPF）的 UI 架構（.NET Framework 的子集）來建立桌面用戶端應用程式。
ms.date: 01/26/2018
helpviewer_keywords:
- getting started [WPF]
- introduction [WPF]
- WPF [WPF], getting started
ms.assetid: 04f91da8-708c-46c7-8172-f1695ec847cd
ms.openlocfilehash: 2977831bf17ac11a67f71037d26e4f4665131721
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853856"
---
# <a name="get-started-wpf"></a><span data-ttu-id="1056c-103">開始使用 (WPF)</span><span class="sxs-lookup"><span data-stu-id="1056c-103">Get started (WPF)</span></span>

<span data-ttu-id="1056c-104">Windows Presentation Foundation (WPF) 是建立桌面用戶端應用程式的 UI 架構。</span><span class="sxs-lookup"><span data-stu-id="1056c-104">Windows Presentation Foundation (WPF) is a UI framework that creates desktop client applications.</span></span> <span data-ttu-id="1056c-105">WPF 開發平台支援一組廣泛的應用程式開發功能，包含應用程式模型、資源、控制項、圖形、版面配置、資料繫結、文件和安全性。</span><span class="sxs-lookup"><span data-stu-id="1056c-105">The WPF development platform supports a broad set of application development features, including an application model, resources, controls, graphics, layout, data binding, documents, and security.</span></span> <span data-ttu-id="1056c-106">它是 .NET Framework 的子集，所以若您先前已使用 ASP.NET 或 Windows Form 以 .NET Framework 建置過應用程式，應該會對此程式設計體驗感到熟悉。</span><span class="sxs-lookup"><span data-stu-id="1056c-106">It is a subset of the .NET Framework, so if you have previously built applications with the .NET Framework using ASP.NET or Windows Forms, the programming experience should be familiar.</span></span> <span data-ttu-id="1056c-107">WPF 使用可延伸應用程式標記語言 (XAML) 來提供應用程式設計的宣告式模型。</span><span class="sxs-lookup"><span data-stu-id="1056c-107">WPF uses the Extensible Application Markup Language (XAML) to provide a declarative model for application programming.</span></span> <span data-ttu-id="1056c-108">本章節的主題將介紹及幫助您開始使用 WPF。</span><span class="sxs-lookup"><span data-stu-id="1056c-108">This section has topics that introduce and help you get started with WPF.</span></span>  
  
## <a name="where-should-i-start"></a><span data-ttu-id="1056c-109">我該從哪裡開始？</span><span class="sxs-lookup"><span data-stu-id="1056c-109">Where should I start?</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1056c-110">我想直接開始</span><span class="sxs-lookup"><span data-stu-id="1056c-110">I want to jump right in…</span></span>|[<span data-ttu-id="1056c-111">逐步解說：我的第一個 WPF 桌面應用程式</span><span class="sxs-lookup"><span data-stu-id="1056c-111">Walkthrough: My first WPF desktop application</span></span>](walkthrough-my-first-wpf-desktop-application.md)|  
|<span data-ttu-id="1056c-112">我該如何設計應用程式 UI？</span><span class="sxs-lookup"><span data-stu-id="1056c-112">How do I design the application UI?</span></span>|[<span data-ttu-id="1056c-113">在 Visual Studio 中設計 XAML</span><span class="sxs-lookup"><span data-stu-id="1056c-113">Designing XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)|  
|<span data-ttu-id="1056c-114">剛開始使用 .NET 嗎？</span><span class="sxs-lookup"><span data-stu-id="1056c-114">New to .NET?</span></span>|[<span data-ttu-id="1056c-115">.NET Framework 的概觀</span><span class="sxs-lookup"><span data-stu-id="1056c-115">Overview of the .NET Framework</span></span>](../../get-started/overview.md)<br /><br /> [<span data-ttu-id="1056c-116">Visual C# 和 Visual Basic 使用者入門</span><span class="sxs-lookup"><span data-stu-id="1056c-116">Getting Started with Visual C# and Visual Basic</span></span>](/visualstudio/ide/quickstart-visual-basic-console)|  
|<span data-ttu-id="1056c-117">WPF 的相關詳細資訊...</span><span class="sxs-lookup"><span data-stu-id="1056c-117">Tell me more about WPF…</span></span>|[<span data-ttu-id="1056c-118">Visual Studio 中的 WPF 簡介</span><span class="sxs-lookup"><span data-stu-id="1056c-118">Introduction to WPF in Visual Studio</span></span>](introduction-to-wpf-in-vs.md)<br /><br /> [<span data-ttu-id="1056c-119">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="1056c-119">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)<br /><br /> [<span data-ttu-id="1056c-120">控制項</span><span class="sxs-lookup"><span data-stu-id="1056c-120">Controls</span></span>](../controls/index.md)<br /><br /> [<span data-ttu-id="1056c-121">資料系結總覽</span><span class="sxs-lookup"><span data-stu-id="1056c-121">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)|  
|<span data-ttu-id="1056c-122">您是 Windows Form 開發人員嗎？</span><span class="sxs-lookup"><span data-stu-id="1056c-122">Are you a Windows Forms developer?</span></span>|[<span data-ttu-id="1056c-123">Windows Form 控制項和對等 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="1056c-123">Windows Forms Controls and Equivalent WPF Controls</span></span>](../advanced/windows-forms-controls-and-equivalent-wpf-controls.md)<br /><br /> [<span data-ttu-id="1056c-124">WPF 和 Windows Form 互通</span><span class="sxs-lookup"><span data-stu-id="1056c-124">WPF and Windows Forms Interoperation</span></span>](../advanced/wpf-and-windows-forms-interoperation.md)|  
  
## <a name="see-also"></a><span data-ttu-id="1056c-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1056c-125">See also</span></span>

- [<span data-ttu-id="1056c-126">類別庫</span><span class="sxs-lookup"><span data-stu-id="1056c-126">Class Library</span></span>](../class-library-wpf.md)
- [<span data-ttu-id="1056c-127">應用程式開發</span><span class="sxs-lookup"><span data-stu-id="1056c-127">Application Development</span></span>](../app-development/index.md)
- [<span data-ttu-id="1056c-128">.NET Framework 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="1056c-128">.NET Framework Developer Center</span></span>](https://dotnet.microsoft.com)
