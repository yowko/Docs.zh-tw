---
title: 使用 .NET Framework 開發以 Windows 為基礎的用戶端應用程式
description: 使用 .NET 開發以 Windows 為基礎的應用程式。 您可以使用通用 Windows 平臺（UWP）、Windows Presentation Foundation （WPF）或 Windows Forms。
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
ms.openlocfilehash: 5920ecfae60274a8a504e4d300e531fd8b512901
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619386"
---
# <a name="develop-client-applications-with-net-framework"></a><span data-ttu-id="2b1c0-104">使用 .NET Framework 開發用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="2b1c0-104">Develop client applications with .NET Framework</span></span>

<span data-ttu-id="2b1c0-105">有數種方式可使用 .NET Framework 開發 Windows 應用程式。</span><span class="sxs-lookup"><span data-stu-id="2b1c0-105">There are several ways to develop Windows-based applications with .NET Framework.</span></span> <span data-ttu-id="2b1c0-106">您可以使用下列任一工具及架構：</span><span class="sxs-lookup"><span data-stu-id="2b1c0-106">You can use any of these tools and frameworks:</span></span>

- [<span data-ttu-id="2b1c0-107">通用 Windows 平台 (UWP)</span><span class="sxs-lookup"><span data-stu-id="2b1c0-107">Universal Windows Platform (UWP)</span></span>](/windows/uwp/)
- [<span data-ttu-id="2b1c0-108">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="2b1c0-108">Windows Presentation Foundation (WPF)</span></span>](./wpf/index.md)
- [<span data-ttu-id="2b1c0-109">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2b1c0-109">Windows Forms</span></span>](./winforms/index.md)

<span data-ttu-id="2b1c0-110">本節包含的文章說明如何使用 Windows Presentation Foundation 或 Windows Forms 來建立以 Windows 為基礎的應用程式。</span><span class="sxs-lookup"><span data-stu-id="2b1c0-110">This section contains articles that describe how to create Windows-based applications by using Windows Presentation Foundation or Windows Forms.</span></span> <span data-ttu-id="2b1c0-111">不過，您也可以針對透過 Microsoft Store （UWP 應用程式）提供的電腦或裝置，使用 .NET Framework 和用戶端應用程式來建立 web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="2b1c0-111">However, you can also create web applications using .NET Framework and client applications for computers or devices that you make available through Microsoft Store (UWP apps).</span></span>

## <a name="related-sections"></a><span data-ttu-id="2b1c0-112">相關章節</span><span class="sxs-lookup"><span data-stu-id="2b1c0-112">Related sections</span></span>

<span data-ttu-id="2b1c0-113">[通用 Windows 平臺](/windows/uwp/)</span><span class="sxs-lookup"><span data-stu-id="2b1c0-113">[Universal Windows Platform](/windows/uwp/)</span></span>\
<span data-ttu-id="2b1c0-114">描述如何建立 UWP 應用程式，讓使用者可以透過 Microsoft Store 來使用。</span><span class="sxs-lookup"><span data-stu-id="2b1c0-114">Describes how to create UWP applications that you can make available to users through Microsoft Store.</span></span>

<span data-ttu-id="2b1c0-115">[適用于 UWP 應用程式的 .NET API](/dotnet/api/index?view=dotnet-uwp-10.0)</span><span class="sxs-lookup"><span data-stu-id="2b1c0-115">[.NET API for UWP apps](/dotnet/api/index?view=dotnet-uwp-10.0)</span></span>\
<span data-ttu-id="2b1c0-116">支援 UWP 應用程式之 .NET 類型的參考。</span><span class="sxs-lookup"><span data-stu-id="2b1c0-116">Reference for .NET types that support UWP apps.</span></span>
  
<span data-ttu-id="2b1c0-117">[針對多個平臺進行開發](../standard/cross-platform/index.md)</span><span class="sxs-lookup"><span data-stu-id="2b1c0-117">[Develop for Multiple Platforms](../standard/cross-platform/index.md)</span></span>\
<span data-ttu-id="2b1c0-118">描述您可以用來 .NET Framework 以多個用戶端應用程式類型為目標的不同方法。</span><span class="sxs-lookup"><span data-stu-id="2b1c0-118">Describes the different methods you can use .NET Framework to target multiple client app types.</span></span>

<span data-ttu-id="2b1c0-119">[開始使用 ASP.NET Web Sites](https://dotnet.microsoft.com/apps/aspnet/web-apps)</span><span class="sxs-lookup"><span data-stu-id="2b1c0-119">[Get Started with ASP.NET Web Sites](https://dotnet.microsoft.com/apps/aspnet/web-apps)</span></span>\
<span data-ttu-id="2b1c0-120">描述您可以使用 ASP.NET 開發 Web 應用程式的方式。</span><span class="sxs-lookup"><span data-stu-id="2b1c0-120">Describes the ways you can develop web apps using ASP.NET.</span></span>

<span data-ttu-id="2b1c0-121">[適用于 Windows Phone Silverlight 的 .NET API](https://docs.microsoft.com/previous-versions/windows/apps/jj207211\(v=vs.105\))</span><span class="sxs-lookup"><span data-stu-id="2b1c0-121">[.NET API for Windows Phone Silverlight](https://docs.microsoft.com/previous-versions/windows/apps/jj207211\(v=vs.105\))</span></span>\
<span data-ttu-id="2b1c0-122">列出 .NET Framework Api，您可以使用 Windows Phone Silverlight 來建立應用程式。</span><span class="sxs-lookup"><span data-stu-id="2b1c0-122">Lists .NET Framework APIs you can use for building apps with Windows Phone Silverlight.</span></span>

## <a name="see-also"></a><span data-ttu-id="2b1c0-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b1c0-123">See also</span></span>

- [<span data-ttu-id="2b1c0-124">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="2b1c0-124">.NET Standard</span></span>](../standard/net-standard.md)
- [<span data-ttu-id="2b1c0-125">概觀</span><span class="sxs-lookup"><span data-stu-id="2b1c0-125">Overview</span></span>](./get-started/overview.md)
- [<span data-ttu-id="2b1c0-126">開發指南</span><span class="sxs-lookup"><span data-stu-id="2b1c0-126">Development Guide</span></span>](./development-guide.md)
- [<span data-ttu-id="2b1c0-127">Windows 服務應用程式</span><span class="sxs-lookup"><span data-stu-id="2b1c0-127">Windows Service Applications</span></span>](./windows-services/index.md)
