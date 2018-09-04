---
title: IWpfHostSupport
ms.date: 03/30/2017
helpviewer_keywords:
- IWpfHostSupport interface [WPF]
ms.assetid: cc5a0281-de81-4cc1-87e4-0e46b1a811e9
ms.openlocfilehash: 57d9ef87a078655a89a5869a48a1bd16f21b000f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43500922"
---
# <a name="iwpfhostsupport"></a><span data-ttu-id="a5511-102">IWpfHostSupport</span><span class="sxs-lookup"><span data-stu-id="a5511-102">IWpfHostSupport</span></span>
<span data-ttu-id="a5511-103">裝載的應用程式[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]內容 PresentationHost.exe 透過實作這個介面來提供主機和 PresentationHost.exe 之間的整合點。</span><span class="sxs-lookup"><span data-stu-id="a5511-103">Applications that host [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] content via PresentationHost.exe implement this interface to provide a point of integration between the host and PresentationHost.exe.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5511-104">備註</span><span class="sxs-lookup"><span data-stu-id="a5511-104">Remarks</span></span>  
 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]<span data-ttu-id="a5511-105"> 應用程式，例如網頁瀏覽器可以裝載[!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)]內容，包括[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]鬆散 XAML。</span><span class="sxs-lookup"><span data-stu-id="a5511-105"> applications such as Web browsers can host [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] content, including [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] and loose XAML.</span></span> <span data-ttu-id="a5511-106">主機[!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)]內容[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]應用程式建立的執行個體[WebBrowser 控制項](https://go.microsoft.com/fwlink/?LinkId=97911)。</span><span class="sxs-lookup"><span data-stu-id="a5511-106">To host [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] content, [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] applications create an instance of the [WebBrowser control](https://go.microsoft.com/fwlink/?LinkId=97911).</span></span> <span data-ttu-id="a5511-107">要裝載[!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)]建立 PresentationHost.exe，提供所裝載的執行個體[!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)]的主控件中的顯示內容[WebBrowser 控制項](https://go.microsoft.com/fwlink/?LinkId=97911)。</span><span class="sxs-lookup"><span data-stu-id="a5511-107">To be hosted, [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] creates an instance of PresentationHost.exe, which provides the hosted [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] content to the host for display in the [WebBrowser control](https://go.microsoft.com/fwlink/?LinkId=97911).</span></span>  
  
 <span data-ttu-id="a5511-108">藉由啟用整合`IWpfHostSupport`可讓 PresentationHost.exe:</span><span class="sxs-lookup"><span data-stu-id="a5511-108">The integration enabled by `IWpfHostSupport` allows PresentationHost.exe to:</span></span>  
  
-   <span data-ttu-id="a5511-109">探索並向未經處理輸入裝置 （人性化介面裝置） 的主應用程式有興趣。</span><span class="sxs-lookup"><span data-stu-id="a5511-109">Discover and register with the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>  
  
-   <span data-ttu-id="a5511-110">主應用程式，從已註冊的未經處理輸入的裝置與正向適當的訊息接收輸入的訊息。</span><span class="sxs-lookup"><span data-stu-id="a5511-110">Receive input messages from the registered raw input devices and forward appropriate messages to the host application.</span></span>  
  
-   <span data-ttu-id="a5511-111">查詢主應用程式自訂進度和錯誤的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="a5511-111">Query the host application for custom progress and error user interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a5511-112">僅限在本機用戶端電腦上使用及支援此 API</span><span class="sxs-lookup"><span data-stu-id="a5511-112">This API is only intended and supported for use on the local client machine</span></span>  
  
## <a name="members"></a><span data-ttu-id="a5511-113">成員</span><span class="sxs-lookup"><span data-stu-id="a5511-113">Members</span></span>  
  
|<span data-ttu-id="a5511-114">成員</span><span class="sxs-lookup"><span data-stu-id="a5511-114">Member</span></span>|<span data-ttu-id="a5511-115">描述</span><span class="sxs-lookup"><span data-stu-id="a5511-115">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a5511-116">GetRawInputDevices</span><span class="sxs-lookup"><span data-stu-id="a5511-116">GetRawInputDevices</span></span>](../../../../docs/framework/wpf/app-development/getrawinputdevices.md)|<span data-ttu-id="a5511-117">可讓 PresentationHost.exe 探索主應用程式有興趣的未經處理輸入裝置 (人性化介面裝置)。</span><span class="sxs-lookup"><span data-stu-id="a5511-117">Allows PresentationHost.exe to discover the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>|  
|[<span data-ttu-id="a5511-118">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="a5511-118">FilterInputMessage</span></span>](../../../../docs/framework/wpf/app-development/filterinputmessage.md)|<span data-ttu-id="a5511-119">除非傳回 E_NOTIMPL，否則每當收到訊息時，都會由 PresentationHost.exe 呼叫。</span><span class="sxs-lookup"><span data-stu-id="a5511-119">Called by PresentationHost.exe whenever a message is received unless E_NOTIMPL is returned.</span></span>|  
|[<span data-ttu-id="a5511-120">GetCustomUI</span><span class="sxs-lookup"><span data-stu-id="a5511-120">GetCustomUI</span></span>](../../../../docs/framework/wpf/app-development/getcustomui.md)|<span data-ttu-id="a5511-121">根據預設，PresentationHost.exe 提供它自己的部署進度和部署錯誤會顯示部署的 WPF 內容時的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="a5511-121">By default, PresentationHost.exe provides its own deployment progress and deployment error user interfaces that are displayed when WPF content is deployed.</span></span>|
