---
title: IWpfHostSupport
ms.date: 03/30/2017
helpviewer_keywords:
- IWpfHostSupport interface [WPF]
ms.assetid: cc5a0281-de81-4cc1-87e4-0e46b1a811e9
ms.openlocfilehash: 91a29233d12a842a64b7d3dd497312f6dc6742ca
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423642"
---
# <a name="iwpfhostsupport"></a><span data-ttu-id="00256-102">IWpfHostSupport</span><span class="sxs-lookup"><span data-stu-id="00256-102">IWpfHostSupport</span></span>
<span data-ttu-id="00256-103">透過 Presentationhost.exe 裝載 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 內容的應用程式會執行此介面，以提供主機和 Presentationhost.exe 之間的整合點。</span><span class="sxs-lookup"><span data-stu-id="00256-103">Applications that host [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] content via PresentationHost.exe implement this interface to provide a point of integration between the host and PresentationHost.exe.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00256-104">備註</span><span class="sxs-lookup"><span data-stu-id="00256-104">Remarks</span></span>  
 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] <span data-ttu-id="00256-105">的應用程式（例如網頁瀏覽器）可以裝載 WPF 內容，包括 XAML 瀏覽器應用程式（Xbap）和鬆散的 XAML。</span><span class="sxs-lookup"><span data-stu-id="00256-105">applications such as Web browsers can host WPF content, including XAML browser applications (XBAPs) and loose XAML.</span></span> <span data-ttu-id="00256-106">若要裝載 WPF 內容，[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] 應用程式會建立[WebBrowser 控制項](https://go.microsoft.com/fwlink/?LinkId=97911)的實例。</span><span class="sxs-lookup"><span data-stu-id="00256-106">To host WPF content, [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] applications create an instance of the [WebBrowser control](https://go.microsoft.com/fwlink/?LinkId=97911).</span></span> <span data-ttu-id="00256-107">WPF 會建立 Presentationhost.exe 的實例，它會將裝載的 WPF 內容提供給主控制項，以便在[WebBrowser 控制項](https://go.microsoft.com/fwlink/?LinkId=97911)中顯示。</span><span class="sxs-lookup"><span data-stu-id="00256-107">To be hosted, WPF creates an instance of PresentationHost.exe, which provides the hosted WPF content to the host for display in the [WebBrowser control](https://go.microsoft.com/fwlink/?LinkId=97911).</span></span>  
  
 <span data-ttu-id="00256-108">`IWpfHostSupport` 啟用的整合允許 Presentationhost.exe：</span><span class="sxs-lookup"><span data-stu-id="00256-108">The integration enabled by `IWpfHostSupport` allows PresentationHost.exe to:</span></span>  
  
- <span data-ttu-id="00256-109">探索並向主機應用程式感興趣的原始輸入裝置（人類介面裝置）進行註冊。</span><span class="sxs-lookup"><span data-stu-id="00256-109">Discover and register with the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>  
  
- <span data-ttu-id="00256-110">從已註冊的原始輸入裝置接收輸入訊息，並將適當的訊息轉送至主應用程式。</span><span class="sxs-lookup"><span data-stu-id="00256-110">Receive input messages from the registered raw input devices and forward appropriate messages to the host application.</span></span>  
  
- <span data-ttu-id="00256-111">查詢主應用程式中的自訂進度和錯誤使用者介面。</span><span class="sxs-lookup"><span data-stu-id="00256-111">Query the host application for custom progress and error user interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="00256-112">僅限在本機用戶端電腦上使用及支援此 API</span><span class="sxs-lookup"><span data-stu-id="00256-112">This API is only intended and supported for use on the local client machine</span></span>  
  
## <a name="members"></a><span data-ttu-id="00256-113">Members</span><span class="sxs-lookup"><span data-stu-id="00256-113">Members</span></span>  
  
|<span data-ttu-id="00256-114">成員</span><span class="sxs-lookup"><span data-stu-id="00256-114">Member</span></span>|<span data-ttu-id="00256-115">描述</span><span class="sxs-lookup"><span data-stu-id="00256-115">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="00256-116">GetRawInputDevices</span><span class="sxs-lookup"><span data-stu-id="00256-116">GetRawInputDevices</span></span>](getrawinputdevices.md)|<span data-ttu-id="00256-117">可讓 PresentationHost.exe 探索主應用程式有興趣的未經處理輸入裝置 (人性化介面裝置)。</span><span class="sxs-lookup"><span data-stu-id="00256-117">Allows PresentationHost.exe to discover the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>|  
|[<span data-ttu-id="00256-118">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="00256-118">FilterInputMessage</span></span>](filterinputmessage.md)|<span data-ttu-id="00256-119">除非傳回 E_NOTIMPL，否則每當收到訊息時，都會由 PresentationHost.exe 呼叫。</span><span class="sxs-lookup"><span data-stu-id="00256-119">Called by PresentationHost.exe whenever a message is received unless E_NOTIMPL is returned.</span></span>|  
|[<span data-ttu-id="00256-120">GetCustomUI</span><span class="sxs-lookup"><span data-stu-id="00256-120">GetCustomUI</span></span>](getcustomui.md)|<span data-ttu-id="00256-121">根據預設，Presentationhost.exe 會提供自己的部署進度和部署錯誤使用者介面，在部署 WPF 內容時顯示。</span><span class="sxs-lookup"><span data-stu-id="00256-121">By default, PresentationHost.exe provides its own deployment progress and deployment error user interfaces that are displayed when WPF content is deployed.</span></span>|
