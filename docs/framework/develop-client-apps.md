---
title: 使用 .NET Framework 開發以 Windows 為基礎的用戶端應用程式
ms.date: 01/09/2018
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
ms.openlocfilehash: b8c63aa074f699fa77c25441995a2ae74b78caf8
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106500"
---
# <a name="developing-client-applications-with-the-net-framework"></a><span data-ttu-id="8925f-102">使用 .NET Framework 開發用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="8925f-102">Developing client applications with the .NET Framework</span></span>

<span data-ttu-id="8925f-103">有數種方式能夠使用 .NET Framework 開發以 Windows 為基礎的應用程式。</span><span class="sxs-lookup"><span data-stu-id="8925f-103">There are several ways to develop Windows-based applications with the .NET Framework.</span></span> <span data-ttu-id="8925f-104">您可以使用下列任一工具及架構：</span><span class="sxs-lookup"><span data-stu-id="8925f-104">You can use any of these tools and frameworks:</span></span> 

- [<span data-ttu-id="8925f-105">通用 Windows 平台 (UWP)</span><span class="sxs-lookup"><span data-stu-id="8925f-105">Universal Windows Platform (UWP)</span></span>](https://developer.microsoft.com/windows/apps)
- [<span data-ttu-id="8925f-106">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="8925f-106">Windows Presentation Foundation (WPF)</span></span>](../../docs/framework/wpf/index.md)
- [<span data-ttu-id="8925f-107">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8925f-107">Windows Forms</span></span>](../../docs/framework/winforms/index.md)

<span data-ttu-id="8925f-108">本節中的主題說明如何使用 Windows Presentation Foundation 或 Windows Forms 建立以 Windows 為基礎的應用程式。</span><span class="sxs-lookup"><span data-stu-id="8925f-108">This section contains topics that describe how to create Windows-based applications by using Windows Presentation Foundation or by using Windows Forms.</span></span> <span data-ttu-id="8925f-109">不過，您也可以使用 .NET Framework 來建立 Web 應用程式，以及可在您透過 Microsoft Store 取得的電腦或裝置上執行的用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="8925f-109">However, you can also create web applications using the .NET Framework, and client applications for computers or devices that you make available through the Microsoft Store.</span></span>
 
## <a name="in-this-section"></a><span data-ttu-id="8925f-110">本節內容</span><span class="sxs-lookup"><span data-stu-id="8925f-110">In this section</span></span>

[<span data-ttu-id="8925f-111">Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="8925f-111">Windows Presentation Foundation</span></span>](../../docs/framework/wpf/index.md)  
<span data-ttu-id="8925f-112">提供使用 WPF 開發應用程式的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="8925f-112">Provides information about developing applications by using WPF.</span></span>

[<span data-ttu-id="8925f-113">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8925f-113">Windows Forms</span></span>](../../docs/framework/winforms/index.md)  
<span data-ttu-id="8925f-114">提供使用 Windows Form 開發應用程式的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="8925f-114">Provides information about developing applications by using Windows Forms.</span></span>

[<span data-ttu-id="8925f-115">常見的用戶端技術</span><span class="sxs-lookup"><span data-stu-id="8925f-115">Common Client Technologies</span></span>](../../docs/framework/common-client-technologies/index.md)  
<span data-ttu-id="8925f-116">提供可在開發用戶端應用程式時使用之其他技術的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="8925f-116">Provides information about additional technologies that can be used when developing client applications.</span></span>

## <a name="related-sections"></a><span data-ttu-id="8925f-117">相關章節</span><span class="sxs-lookup"><span data-stu-id="8925f-117">Related sections</span></span>

[<span data-ttu-id="8925f-118">通用 Windows 平台</span><span class="sxs-lookup"><span data-stu-id="8925f-118">Universal Windows Platform</span></span>](https://developer.microsoft.com/windows/apps)  
<span data-ttu-id="8925f-119">描述如何建立可透過 Microsoft Store 提供給使用者的 Windows 10 適用應用程式。</span><span class="sxs-lookup"><span data-stu-id="8925f-119">Describes how to create applications for Windows 10 that you can make available to users through the Windows Store.</span></span>

[<span data-ttu-id="8925f-120">適用於 UWP app 的 .NET</span><span class="sxs-lookup"><span data-stu-id="8925f-120">.NET for UWP apps</span></span>](https://msdn.microsoft.com/library/windows/apps/mt185501.aspx)  
<span data-ttu-id="8925f-121">描述可部署至 Windows 電腦和裝置之市集應用程式的 .NET Framework 支援。</span><span class="sxs-lookup"><span data-stu-id="8925f-121">Describes the .NET Framework support for Store apps, which can be deployed to Windows computers and devices.</span></span>

<span data-ttu-id="8925f-122">[適用於 Windows Phone Silverlight 的 .NET API](https://docs.microsoft.com/previous-versions/windows/apps/jj207211\(v=vs.105\))</span><span class="sxs-lookup"><span data-stu-id="8925f-122">[.NET API for Windows Phone Silverlight](https://docs.microsoft.com/previous-versions/windows/apps/jj207211\(v=vs.105\))</span></span>  
<span data-ttu-id="8925f-123">列出可用於建置 Windows Phone Silverlight 應用程式的 .NET Framework API。</span><span class="sxs-lookup"><span data-stu-id="8925f-123">Lists the .NET Framework APIs you can use for building apps with Windows Phone Silverlight.</span></span>
  
[<span data-ttu-id="8925f-124">進行多平台開發</span><span class="sxs-lookup"><span data-stu-id="8925f-124">Developing for Multiple Platforms</span></span>](../../docs/standard/cross-platform/index.md)  
<span data-ttu-id="8925f-125">描述您可以針對多種用戶端應用程式類型使用 .NET Framework 的不同方法。</span><span class="sxs-lookup"><span data-stu-id="8925f-125">Describes the different methods you can use the .NET Framework to target multiple client app types.</span></span>

[<span data-ttu-id="8925f-126">開始使用 ASP.NET 網站</span><span class="sxs-lookup"><span data-stu-id="8925f-126">Get Started with ASP.NET Web Sites</span></span>](https://www.asp.net/get-started/websites)  
<span data-ttu-id="8925f-127">描述您可以使用 ASP.NET 開發 Web 應用程式的方式。</span><span class="sxs-lookup"><span data-stu-id="8925f-127">Describes the ways you can develop web apps using ASP.NET.</span></span>

## <a name="see-also"></a><span data-ttu-id="8925f-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8925f-128">See also</span></span>

- [<span data-ttu-id="8925f-129">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="8925f-129">.NET Standard</span></span>](../../docs/standard/net-standard.md)
- [<span data-ttu-id="8925f-130">概觀</span><span class="sxs-lookup"><span data-stu-id="8925f-130">Overview</span></span>](../../docs/framework/get-started/overview.md)
- [<span data-ttu-id="8925f-131">開發指南</span><span class="sxs-lookup"><span data-stu-id="8925f-131">Development Guide</span></span>](../../docs/framework/development-guide.md)
- [<span data-ttu-id="8925f-132">Windows 服務應用程式</span><span class="sxs-lookup"><span data-stu-id="8925f-132">Windows Service Applications</span></span>](../../docs/framework/windows-services/index.md)
