---
title: "使用 .NET Framework 開發用戶端應用程式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- client application services
- applications [Windows Forms]
- Windows Presentation Foundation, in Visual Studio
- WPF, in Visual Studio
- Windows applications
- rich client applications
- .NET applications, Windows applications
- Visual Basic code, creating applications
- Visual C#, creating applications
- client/server applications, Windows applications
ms.assetid: 2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: daf09f94b4c0854365274773f8c426cc07e8c6dd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="developing-client-applications-with-the-net-framework"></a><span data-ttu-id="e681f-102">使用 .NET Framework 開發用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="e681f-102">Developing Client Applications with the .NET Framework</span></span>
<span data-ttu-id="e681f-103">您可以透過許多方式，使用 .NET Framework 開發在使用者電腦或裝置上本機執行的 Windows 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e681f-103">There are multiple ways to develop Windows-based applications with the .NET framework that run locally on users' computers or devices.</span></span> <span data-ttu-id="e681f-104">本節中的主題說明如何使用 Windows Presentation Foundation (WPF) 或 Windows Form 建立 Windows 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e681f-104">This section contains topics that describe how to create Windows-based applications by using Windows Presentation Foundation (WPF) or by using Windows Forms.</span></span> <span data-ttu-id="e681f-105">不過，您也可以使用 .NET Framework 來建立 Web 應用程式，以及適用於您透過「Windows 市集」或「Windows Phone 市集」提供之電腦或裝置上的用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="e681f-105">However, you can also create web applications using the .NET Framework, and client applications for computers or devices that you make available through the Windows Store or Windows Phone Store.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e681f-106">本章節內容</span><span class="sxs-lookup"><span data-stu-id="e681f-106">In This Section</span></span>  
 [<span data-ttu-id="e681f-107">Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="e681f-107">Windows Presentation Foundation</span></span>](../../docs/framework/wpf/index.md)  
 <span data-ttu-id="e681f-108">提供使用 WPF 開發應用程式的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e681f-108">Provides information about developing applications by using WPF.</span></span>  
  
 [<span data-ttu-id="e681f-109">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e681f-109">Windows Forms</span></span>](../../docs/framework/winforms/index.md)  
 <span data-ttu-id="e681f-110">提供使用 Windows Form 開發應用程式的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e681f-110">Provides information about developing applications by using Windows Forms.</span></span>  
  
 [<span data-ttu-id="e681f-111">常見的用戶端技術</span><span class="sxs-lookup"><span data-stu-id="e681f-111">Common Client Technologies</span></span>](../../docs/framework/common-client-technologies/index.md)  
 <span data-ttu-id="e681f-112">提供可在開發用戶端應用程式時使用之其他技術的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e681f-112">Provides information about additional technologies that can be used when developing client applications.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e681f-113">相關章節</span><span class="sxs-lookup"><span data-stu-id="e681f-113">Related Sections</span></span>  
 [<span data-ttu-id="e681f-114">Windows 市集應用程式</span><span class="sxs-lookup"><span data-stu-id="e681f-114">Windows Store apps</span></span>](http://msdn.microsoft.com/windows/apps/)  
 <span data-ttu-id="e681f-115">描述如何建立可透過 Windows 市集提供給使用者的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e681f-115">Describes how to create apps that you can make available to users through the Windows Store</span></span>  
  
 [<span data-ttu-id="e681f-116">適用於市集應用程式的 .NET</span><span class="sxs-lookup"><span data-stu-id="e681f-116">.NET for Store apps</span></span>](http://msdn.microsoft.com/library/windows/apps/br230302.aspx)  
 <span data-ttu-id="e681f-117">描述可部署至 Windows 電腦和裝置之市集應用程式的 .NET Framework 支援。</span><span class="sxs-lookup"><span data-stu-id="e681f-117">Describes the .NET Framework support for Store apps, which can be deployed to Windows computers and devices.</span></span>  
  
 <span data-ttu-id="e681f-118">[適用於 Windows Phone Silverlight 的 .NET API](http://msdn.microsoft.com/library/windows/apps/xaml/jj207211\(v=vs.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="e681f-118">[.NET API for Windows Phone Silverlight](http://msdn.microsoft.com/library/windows/apps/xaml/jj207211\(v=vs.105\).aspx)</span></span>  
 <span data-ttu-id="e681f-119">列出可用於建置 Windows Phone Silverlight 應用程式的 .NET Framework API。</span><span class="sxs-lookup"><span data-stu-id="e681f-119">List the .NET Framework APIs you can use for building apps with Windows Phone Silverlight</span></span>  
  
 [<span data-ttu-id="e681f-120">進行多平台開發</span><span class="sxs-lookup"><span data-stu-id="e681f-120">Developing for Multiple Platforms</span></span>](../../docs/standard/cross-platform/index.md)  
 <span data-ttu-id="e681f-121">描述您可以針對多種用戶端應用程式類型使用 .NET Framework 的不同方法。</span><span class="sxs-lookup"><span data-stu-id="e681f-121">Describes the different methods you can use the .NET Framework to target multiple client app types.</span></span>  
  
 [<span data-ttu-id="e681f-122">開始使用 ASP.NET 網站</span><span class="sxs-lookup"><span data-stu-id="e681f-122">Get Started with ASP.NET Web Sites</span></span>](http://www.asp.net/get-started/websites)  
 <span data-ttu-id="e681f-123">描述您可以使用 ASP.NET 開發 Web 應用程式的方式。</span><span class="sxs-lookup"><span data-stu-id="e681f-123">Describes the ways you can develop web apps using ASP.NET.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e681f-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e681f-124">See Also</span></span>  
 [<span data-ttu-id="e681f-125">可攜式類別庫</span><span class="sxs-lookup"><span data-stu-id="e681f-125">Portable Class Library</span></span>](../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)  
 [<span data-ttu-id="e681f-126">概觀</span><span class="sxs-lookup"><span data-stu-id="e681f-126">Overview</span></span>](../../docs/framework/get-started/overview.md)  
 [<span data-ttu-id="e681f-127">開發指南</span><span class="sxs-lookup"><span data-stu-id="e681f-127">Development Guide</span></span>](../../docs/framework/development-guide.md)  
 [<span data-ttu-id="e681f-128">如何： 建立 Windows 傳統型應用程式</span><span class="sxs-lookup"><span data-stu-id="e681f-128">How to: Create a Windows Desktop Application</span></span>](http://msdn.microsoft.com/library/47021403-eaca-4c34-946a-a26c42a64148)  
 [<span data-ttu-id="e681f-129">Windows 服務應用程式</span><span class="sxs-lookup"><span data-stu-id="e681f-129">Windows Service Applications</span></span>](../../docs/framework/windows-services/index.md)
