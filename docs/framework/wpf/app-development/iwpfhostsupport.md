---
title: IWpfHostSupport
ms.date: 03/30/2017
helpviewer_keywords:
- IWpfHostSupport interface [WPF]
ms.assetid: cc5a0281-de81-4cc1-87e4-0e46b1a811e9
ms.openlocfilehash: 994e5146e9cf49a9b31396d0b51e7be83bbb3cfb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964788"
---
# <a name="iwpfhostsupport"></a><span data-ttu-id="adde8-102">IWpfHostSupport</span><span class="sxs-lookup"><span data-stu-id="adde8-102">IWpfHostSupport</span></span>
<span data-ttu-id="adde8-103">透過 presentationhost.exe 裝載[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]內容的應用程式會執行此介面, 以提供主機和 presentationhost.exe 之間的整合點。</span><span class="sxs-lookup"><span data-stu-id="adde8-103">Applications that host [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] content via PresentationHost.exe implement this interface to provide a point of integration between the host and PresentationHost.exe.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="adde8-104">備註</span><span class="sxs-lookup"><span data-stu-id="adde8-104">Remarks</span></span>  
 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]<span data-ttu-id="adde8-105">Web 瀏覽器之類的應用程式[!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)]可以裝載內容[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] , 包括和鬆散的 XAML。</span><span class="sxs-lookup"><span data-stu-id="adde8-105">applications such as Web browsers can host [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] content, including [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] and loose XAML.</span></span> <span data-ttu-id="adde8-106">若要[!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)]裝載內容[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] , 應用程式會建立[WebBrowser 控制項](https://go.microsoft.com/fwlink/?LinkId=97911)的實例。</span><span class="sxs-lookup"><span data-stu-id="adde8-106">To host [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] content, [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] applications create an instance of the [WebBrowser control](https://go.microsoft.com/fwlink/?LinkId=97911).</span></span> <span data-ttu-id="adde8-107">若要裝載, [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)]會建立 presentationhost.exe 的實例, 它會將主控[!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)]的內容提供給主控制項, 以便在[WebBrowser 控制項](https://go.microsoft.com/fwlink/?LinkId=97911)中顯示。</span><span class="sxs-lookup"><span data-stu-id="adde8-107">To be hosted, [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] creates an instance of PresentationHost.exe, which provides the hosted [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] content to the host for display in the [WebBrowser control](https://go.microsoft.com/fwlink/?LinkId=97911).</span></span>  
  
 <span data-ttu-id="adde8-108">啟用的整合`IWpfHostSupport`允許 presentationhost.exe:</span><span class="sxs-lookup"><span data-stu-id="adde8-108">The integration enabled by `IWpfHostSupport` allows PresentationHost.exe to:</span></span>  
  
- <span data-ttu-id="adde8-109">探索並向主機應用程式感興趣的原始輸入裝置 (人類介面裝置) 進行註冊。</span><span class="sxs-lookup"><span data-stu-id="adde8-109">Discover and register with the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>  
  
- <span data-ttu-id="adde8-110">從已註冊的原始輸入裝置接收輸入訊息, 並將適當的訊息轉送至主應用程式。</span><span class="sxs-lookup"><span data-stu-id="adde8-110">Receive input messages from the registered raw input devices and forward appropriate messages to the host application.</span></span>  
  
- <span data-ttu-id="adde8-111">查詢主應用程式中的自訂進度和錯誤使用者介面。</span><span class="sxs-lookup"><span data-stu-id="adde8-111">Query the host application for custom progress and error user interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="adde8-112">僅限在本機用戶端電腦上使用及支援此 API</span><span class="sxs-lookup"><span data-stu-id="adde8-112">This API is only intended and supported for use on the local client machine</span></span>  
  
## <a name="members"></a><span data-ttu-id="adde8-113">成員</span><span class="sxs-lookup"><span data-stu-id="adde8-113">Members</span></span>  
  
|<span data-ttu-id="adde8-114">成員</span><span class="sxs-lookup"><span data-stu-id="adde8-114">Member</span></span>|<span data-ttu-id="adde8-115">描述</span><span class="sxs-lookup"><span data-stu-id="adde8-115">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="adde8-116">GetRawInputDevices</span><span class="sxs-lookup"><span data-stu-id="adde8-116">GetRawInputDevices</span></span>](getrawinputdevices.md)|<span data-ttu-id="adde8-117">可讓 PresentationHost.exe 探索主應用程式有興趣的未經處理輸入裝置 (人性化介面裝置)。</span><span class="sxs-lookup"><span data-stu-id="adde8-117">Allows PresentationHost.exe to discover the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>|  
|[<span data-ttu-id="adde8-118">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="adde8-118">FilterInputMessage</span></span>](filterinputmessage.md)|<span data-ttu-id="adde8-119">除非傳回 E_NOTIMPL，否則每當收到訊息時，都會由 PresentationHost.exe 呼叫。</span><span class="sxs-lookup"><span data-stu-id="adde8-119">Called by PresentationHost.exe whenever a message is received unless E_NOTIMPL is returned.</span></span>|  
|[<span data-ttu-id="adde8-120">GetCustomUI</span><span class="sxs-lookup"><span data-stu-id="adde8-120">GetCustomUI</span></span>](getcustomui.md)|<span data-ttu-id="adde8-121">根據預設, Presentationhost.exe 會提供自己的部署進度和部署錯誤使用者介面, 在部署 WPF 內容時顯示。</span><span class="sxs-lookup"><span data-stu-id="adde8-121">By default, PresentationHost.exe provides its own deployment progress and deployment error user interfaces that are displayed when WPF content is deployed.</span></span>|
