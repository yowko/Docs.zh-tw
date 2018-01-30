---
title: "使用 .NET Framework 開發以 Windows 為基礎的用戶端應用程式"
ms.date: 01/09/2018
ms.prod: .net-framework
ms.technology:
- dotnet-clr
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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4cfc8a0f176e3732e7fe6f088c9973bfbcdaf89a
ms.sourcegitcommit: f28752eab00d2bd97e971542c0f49ce63cfbc239
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2018
---
# <a name="developing-client-applications-with-the-net-framework"></a><span data-ttu-id="79928-102">使用 .NET Framework 開發用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="79928-102">Developing client applications with the .NET Framework</span></span>

<span data-ttu-id="79928-103">有數種方式能夠使用 .NET Framework 開發以 Windows 為基礎的應用程式。</span><span class="sxs-lookup"><span data-stu-id="79928-103">There are several ways to develop Windows-based applications with the .NET Framework.</span></span> <span data-ttu-id="79928-104">您可以使用下列任一工具及架構：</span><span class="sxs-lookup"><span data-stu-id="79928-104">You can use any of these tools and frameworks:</span></span> 

* [<span data-ttu-id="79928-105">通用 Windows 平台 (UWP)</span><span class="sxs-lookup"><span data-stu-id="79928-105">Universal Windows Platform (UWP)</span></span>](https://developer.microsoft.com/windows/apps)
* [<span data-ttu-id="79928-106">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="79928-106">Windows Presentation Foundation (WPF)</span></span>](../../docs/framework/wpf/index.md)
* [<span data-ttu-id="79928-107">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="79928-107">Windows Forms</span></span>](../../docs/framework/winforms/index.md)

<span data-ttu-id="79928-108">本節中的主題說明如何使用 Windows Presentation Foundation 或 Windows Forms 建立以 Windows 為基礎的應用程式。</span><span class="sxs-lookup"><span data-stu-id="79928-108">This section contains topics that describe how to create Windows-based applications by using Windows Presentation Foundation or by using Windows Forms.</span></span> <span data-ttu-id="79928-109">不過，您也可以使用 .NET Framework 來建立 Web 應用程式，以及可在您透過 Microsoft Store 取得的電腦或裝置上執行的用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="79928-109">However, you can also create web applications using the .NET Framework, and client applications for computers or devices that you make available through the Microsoft Store.</span></span>
 
## <a name="in-this-section"></a><span data-ttu-id="79928-110">本節內容</span><span class="sxs-lookup"><span data-stu-id="79928-110">In this section</span></span>

[<span data-ttu-id="79928-111">Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="79928-111">Windows Presentation Foundation</span></span>](../../docs/framework/wpf/index.md)  
<span data-ttu-id="79928-112">提供使用 WPF 開發應用程式的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="79928-112">Provides information about developing applications by using WPF.</span></span>

[<span data-ttu-id="79928-113">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="79928-113">Windows Forms</span></span>](../../docs/framework/winforms/index.md)  
<span data-ttu-id="79928-114">提供使用 Windows Form 開發應用程式的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="79928-114">Provides information about developing applications by using Windows Forms.</span></span>

[<span data-ttu-id="79928-115">常見的用戶端技術</span><span class="sxs-lookup"><span data-stu-id="79928-115">Common Client Technologies</span></span>](../../docs/framework/common-client-technologies/index.md)  
<span data-ttu-id="79928-116">提供可在開發用戶端應用程式時使用之其他技術的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="79928-116">Provides information about additional technologies that can be used when developing client applications.</span></span>

## <a name="related-sections"></a><span data-ttu-id="79928-117">相關章節</span><span class="sxs-lookup"><span data-stu-id="79928-117">Related sections</span></span>

[<span data-ttu-id="79928-118">通用 Windows 平台</span><span class="sxs-lookup"><span data-stu-id="79928-118">Universal Windows Platform</span></span>](https://developer.microsoft.com/windows/apps)  
<span data-ttu-id="79928-119">描述如何建立可透過 Microsoft Store 提供給使用者的 Windows 10 適用應用程式。</span><span class="sxs-lookup"><span data-stu-id="79928-119">Describes how to create applications for Windows 10 that you can make available to users through the Windows Store.</span></span>

[<span data-ttu-id="79928-120">適用於 UWP app 的 .NET</span><span class="sxs-lookup"><span data-stu-id="79928-120">.NET for UWP apps</span></span>](https://msdn.microsoft.com/library/windows/apps/mt185501.aspx)  
<span data-ttu-id="79928-121">描述可部署至 Windows 電腦和裝置之市集應用程式的 .NET Framework 支援。</span><span class="sxs-lookup"><span data-stu-id="79928-121">Describes the .NET Framework support for Store apps, which can be deployed to Windows computers and devices.</span></span>

<span data-ttu-id="79928-122">[適用於 Windows Phone Silverlight 的 .NET API](https://docs.microsoft.com/en-us/previous-versions/windows/apps/jj207211\(v=vs.105\))</span><span class="sxs-lookup"><span data-stu-id="79928-122">[.NET API for Windows Phone Silverlight](https://docs.microsoft.com/en-us/previous-versions/windows/apps/jj207211\(v=vs.105\))</span></span>  
<span data-ttu-id="79928-123">列出可用於建置 Windows Phone Silverlight 應用程式的 .NET Framework API。</span><span class="sxs-lookup"><span data-stu-id="79928-123">Lists the .NET Framework APIs you can use for building apps with Windows Phone Silverlight.</span></span>
  
[<span data-ttu-id="79928-124">進行多平台開發</span><span class="sxs-lookup"><span data-stu-id="79928-124">Developing for Multiple Platforms</span></span>](../../docs/standard/cross-platform/index.md)  
<span data-ttu-id="79928-125">描述您可以針對多種用戶端應用程式類型使用 .NET Framework 的不同方法。</span><span class="sxs-lookup"><span data-stu-id="79928-125">Describes the different methods you can use the .NET Framework to target multiple client app types.</span></span>

[<span data-ttu-id="79928-126">開始使用 ASP.NET 網站</span><span class="sxs-lookup"><span data-stu-id="79928-126">Get Started with ASP.NET Web Sites</span></span>](http://www.asp.net/get-started/websites)  
<span data-ttu-id="79928-127">描述您可以使用 ASP.NET 開發 Web 應用程式的方式。</span><span class="sxs-lookup"><span data-stu-id="79928-127">Describes the ways you can develop web apps using ASP.NET.</span></span>

## <a name="see-also"></a><span data-ttu-id="79928-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79928-128">See also</span></span>

[<span data-ttu-id="79928-129">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="79928-129">.NET Standard</span></span>](../../docs/standard/net-standard.md)  
[<span data-ttu-id="79928-130">概觀</span><span class="sxs-lookup"><span data-stu-id="79928-130">Overview</span></span>](../../docs/framework/get-started/overview.md)  
[<span data-ttu-id="79928-131">開發指南</span><span class="sxs-lookup"><span data-stu-id="79928-131">Development Guide</span></span>](../../docs/framework/development-guide.md)  
[<span data-ttu-id="79928-132">Windows 服務應用程式</span><span class="sxs-lookup"><span data-stu-id="79928-132">Windows Service Applications</span></span>](../../docs/framework/windows-services/index.md)  
