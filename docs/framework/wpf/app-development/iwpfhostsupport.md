---
title: IWpfHostSupport
ms.date: 03/30/2017
helpviewer_keywords:
- IWpfHostSupport interface [WPF]
ms.assetid: cc5a0281-de81-4cc1-87e4-0e46b1a811e9
ms.openlocfilehash: 4855fae2954e5650d8c9bbb81153ebe64249a867
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740190"
---
# <a name="iwpfhostsupport"></a><span data-ttu-id="07e76-102">IWpfHostSupport</span><span class="sxs-lookup"><span data-stu-id="07e76-102">IWpfHostSupport</span></span>
<span data-ttu-id="07e76-103">透過 Presentationhost.exe 裝載 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 內容的應用程式會執行此介面，以提供主機和 Presentationhost.exe 之間的整合點。</span><span class="sxs-lookup"><span data-stu-id="07e76-103">Applications that host [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] content via PresentationHost.exe implement this interface to provide a point of integration between the host and PresentationHost.exe.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07e76-104">備註</span><span class="sxs-lookup"><span data-stu-id="07e76-104">Remarks</span></span>  
 <span data-ttu-id="07e76-105">Web 瀏覽器之類的 Win32 應用程式可以裝載 WPF 內容，包括 XAML 瀏覽器應用程式（Xbap）和鬆散的 XAML。</span><span class="sxs-lookup"><span data-stu-id="07e76-105">Win32 applications such as Web browsers can host WPF content, including XAML browser applications (XBAPs) and loose XAML.</span></span> <span data-ttu-id="07e76-106">為了裝載 WPF 內容，Win32 應用程式會建立[WebBrowser 控制項](https://go.microsoft.com/fwlink/?LinkId=97911)的實例。</span><span class="sxs-lookup"><span data-stu-id="07e76-106">To host WPF content, Win32 applications create an instance of the [WebBrowser control](https://go.microsoft.com/fwlink/?LinkId=97911).</span></span> <span data-ttu-id="07e76-107">WPF 會建立 Presentationhost.exe 的實例，它會將裝載的 WPF 內容提供給主控制項，以便在[WebBrowser 控制項](https://go.microsoft.com/fwlink/?LinkId=97911)中顯示。</span><span class="sxs-lookup"><span data-stu-id="07e76-107">To be hosted, WPF creates an instance of PresentationHost.exe, which provides the hosted WPF content to the host for display in the [WebBrowser control](https://go.microsoft.com/fwlink/?LinkId=97911).</span></span>  
  
 <span data-ttu-id="07e76-108">`IWpfHostSupport` 啟用的整合允許 Presentationhost.exe：</span><span class="sxs-lookup"><span data-stu-id="07e76-108">The integration enabled by `IWpfHostSupport` allows PresentationHost.exe to:</span></span>  
  
- <span data-ttu-id="07e76-109">探索並向主機應用程式感興趣的原始輸入裝置（人類介面裝置）進行註冊。</span><span class="sxs-lookup"><span data-stu-id="07e76-109">Discover and register with the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>  
  
- <span data-ttu-id="07e76-110">從已註冊的原始輸入裝置接收輸入訊息，並將適當的訊息轉送至主應用程式。</span><span class="sxs-lookup"><span data-stu-id="07e76-110">Receive input messages from the registered raw input devices and forward appropriate messages to the host application.</span></span>  
  
- <span data-ttu-id="07e76-111">查詢主應用程式中的自訂進度和錯誤使用者介面。</span><span class="sxs-lookup"><span data-stu-id="07e76-111">Query the host application for custom progress and error user interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="07e76-112">僅限在本機用戶端電腦上使用及支援此 API</span><span class="sxs-lookup"><span data-stu-id="07e76-112">This API is only intended and supported for use on the local client machine</span></span>  
  
## <a name="members"></a><span data-ttu-id="07e76-113">Members</span><span class="sxs-lookup"><span data-stu-id="07e76-113">Members</span></span>  
  
|<span data-ttu-id="07e76-114">成員</span><span class="sxs-lookup"><span data-stu-id="07e76-114">Member</span></span>|<span data-ttu-id="07e76-115">描述</span><span class="sxs-lookup"><span data-stu-id="07e76-115">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="07e76-116">GetRawInputDevices</span><span class="sxs-lookup"><span data-stu-id="07e76-116">GetRawInputDevices</span></span>](getrawinputdevices.md)|<span data-ttu-id="07e76-117">可讓 PresentationHost.exe 探索主應用程式有興趣的未經處理輸入裝置 (人性化介面裝置)。</span><span class="sxs-lookup"><span data-stu-id="07e76-117">Allows PresentationHost.exe to discover the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>|  
|[<span data-ttu-id="07e76-118">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="07e76-118">FilterInputMessage</span></span>](filterinputmessage.md)|<span data-ttu-id="07e76-119">除非傳回 E_NOTIMPL，否則每當收到訊息時，都會由 PresentationHost.exe 呼叫。</span><span class="sxs-lookup"><span data-stu-id="07e76-119">Called by PresentationHost.exe whenever a message is received unless E_NOTIMPL is returned.</span></span>|  
|[<span data-ttu-id="07e76-120">GetCustomUI</span><span class="sxs-lookup"><span data-stu-id="07e76-120">GetCustomUI</span></span>](getcustomui.md)|<span data-ttu-id="07e76-121">根據預設，Presentationhost.exe 會提供自己的部署進度和部署錯誤使用者介面，在部署 WPF 內容時顯示。</span><span class="sxs-lookup"><span data-stu-id="07e76-121">By default, PresentationHost.exe provides its own deployment progress and deployment error user interfaces that are displayed when WPF content is deployed.</span></span>|
