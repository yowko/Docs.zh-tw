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
ms.openlocfilehash: b6b5f47980e7c0c87128b9efb782e637ed7144f4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79181637"
---
# <a name="develop-client-applications-with-net-framework"></a><span data-ttu-id="78ad0-102">使用 .NET 框架開發用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="78ad0-102">Develop client applications with .NET Framework</span></span>

<span data-ttu-id="78ad0-103">有幾種方法可以使用 .NET 框架開發基於 Windows 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="78ad0-103">There are several ways to develop Windows-based applications with .NET Framework.</span></span> <span data-ttu-id="78ad0-104">您可以使用下列任一工具及架構：</span><span class="sxs-lookup"><span data-stu-id="78ad0-104">You can use any of these tools and frameworks:</span></span>

- [<span data-ttu-id="78ad0-105">通用 Windows 平台 (UWP)</span><span class="sxs-lookup"><span data-stu-id="78ad0-105">Universal Windows Platform (UWP)</span></span>](/windows/uwp/)
- [<span data-ttu-id="78ad0-106">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="78ad0-106">Windows Presentation Foundation (WPF)</span></span>](./wpf/index.md)
- [<span data-ttu-id="78ad0-107">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="78ad0-107">Windows Forms</span></span>](./winforms/index.md)

<span data-ttu-id="78ad0-108">本節包含描述如何使用 Windows 演示文稿基礎或 Windows 表單創建基於 Windows 的應用程式的文章。</span><span class="sxs-lookup"><span data-stu-id="78ad0-108">This section contains articles that describe how to create Windows-based applications by using Windows Presentation Foundation or Windows Forms.</span></span> <span data-ttu-id="78ad0-109">但是，您也可以使用 .NET 框架和用戶端應用程式為通過 Microsoft 應用商店（UWP 應用程式）提供的電腦或設備創建 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="78ad0-109">However, you can also create web applications using .NET Framework and client applications for computers or devices that you make available through Microsoft Store (UWP apps).</span></span>

## <a name="related-sections"></a><span data-ttu-id="78ad0-110">相關章節</span><span class="sxs-lookup"><span data-stu-id="78ad0-110">Related sections</span></span>

<span data-ttu-id="78ad0-111">[通用 Windows 平臺](/windows/uwp/)</span><span class="sxs-lookup"><span data-stu-id="78ad0-111">[Universal Windows Platform](/windows/uwp/)</span></span>\
<span data-ttu-id="78ad0-112">介紹如何創建 UWP 應用程式，您可以通過 Microsoft 應用商店提供給使用者。</span><span class="sxs-lookup"><span data-stu-id="78ad0-112">Describes how to create UWP applications that you can make available to users through Microsoft Store.</span></span>

<span data-ttu-id="78ad0-113">[UWP 應用的 .NET API](/dotnet/api/index?view=dotnet-uwp-10.0)</span><span class="sxs-lookup"><span data-stu-id="78ad0-113">[.NET API for UWP apps](/dotnet/api/index?view=dotnet-uwp-10.0)</span></span>\
<span data-ttu-id="78ad0-114">支援 UWP 應用的 .NET 類型的參考。</span><span class="sxs-lookup"><span data-stu-id="78ad0-114">Reference for .NET types that support UWP apps.</span></span>
  
<span data-ttu-id="78ad0-115">[為多個平臺開發](../standard/cross-platform/index.md)</span><span class="sxs-lookup"><span data-stu-id="78ad0-115">[Develop for Multiple Platforms](../standard/cross-platform/index.md)</span></span>\
<span data-ttu-id="78ad0-116">描述可以使用 .NET 框架定位多個用戶端應用類型的不同方法。</span><span class="sxs-lookup"><span data-stu-id="78ad0-116">Describes the different methods you can use .NET Framework to target multiple client app types.</span></span>

<span data-ttu-id="78ad0-117">[開始使用ASP.NET網站](https://dotnet.microsoft.com/apps/aspnet/web-apps)</span><span class="sxs-lookup"><span data-stu-id="78ad0-117">[Get Started with ASP.NET Web Sites](https://dotnet.microsoft.com/apps/aspnet/web-apps)</span></span>\
<span data-ttu-id="78ad0-118">描述您可以使用 ASP.NET 開發 Web 應用程式的方式。</span><span class="sxs-lookup"><span data-stu-id="78ad0-118">Describes the ways you can develop web apps using ASP.NET.</span></span>

<span data-ttu-id="78ad0-119">[.NET API 用於 Windows 手機銀光](https://docs.microsoft.com/previous-versions/windows/apps/jj207211\(v=vs.105\))</span><span class="sxs-lookup"><span data-stu-id="78ad0-119">[.NET API for Windows Phone Silverlight](https://docs.microsoft.com/previous-versions/windows/apps/jj207211\(v=vs.105\))</span></span>\
<span data-ttu-id="78ad0-120">清單 .NET 框架 API 可用於使用 Windows Phone 銀光構建應用。</span><span class="sxs-lookup"><span data-stu-id="78ad0-120">Lists .NET Framework APIs you can use for building apps with Windows Phone Silverlight.</span></span>

## <a name="see-also"></a><span data-ttu-id="78ad0-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78ad0-121">See also</span></span>

- [<span data-ttu-id="78ad0-122">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="78ad0-122">.NET Standard</span></span>](../standard/net-standard.md)
- [<span data-ttu-id="78ad0-123">概觀</span><span class="sxs-lookup"><span data-stu-id="78ad0-123">Overview</span></span>](./get-started/overview.md)
- [<span data-ttu-id="78ad0-124">開發指南</span><span class="sxs-lookup"><span data-stu-id="78ad0-124">Development Guide</span></span>](./development-guide.md)
- [<span data-ttu-id="78ad0-125">Windows 服務應用程式</span><span class="sxs-lookup"><span data-stu-id="78ad0-125">Windows Service Applications</span></span>](./windows-services/index.md)
