---
title: IWpfHostSupport
ms.date: 03/30/2017
helpviewer_keywords:
- IWpfHostSupport interface [WPF]
ms.assetid: cc5a0281-de81-4cc1-87e4-0e46b1a811e9
ms.openlocfilehash: 97a120c57624ada32e6661bd8a613c4ea1d01b2f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64591373"
---
# <a name="iwpfhostsupport"></a><span data-ttu-id="06891-102">IWpfHostSupport</span><span class="sxs-lookup"><span data-stu-id="06891-102">IWpfHostSupport</span></span>
<span data-ttu-id="06891-103">裝載的應用程式[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]內容 PresentationHost.exe 透過實作這個介面來提供主機和 PresentationHost.exe 之間的整合點。</span><span class="sxs-lookup"><span data-stu-id="06891-103">Applications that host [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] content via PresentationHost.exe implement this interface to provide a point of integration between the host and PresentationHost.exe.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06891-104">備註</span><span class="sxs-lookup"><span data-stu-id="06891-104">Remarks</span></span>  
 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] <span data-ttu-id="06891-105">應用程式，例如網頁瀏覽器可以裝載[!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)]內容，包括[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]鬆散 XAML。</span><span class="sxs-lookup"><span data-stu-id="06891-105">applications such as Web browsers can host [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] content, including [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] and loose XAML.</span></span> <span data-ttu-id="06891-106">主機[!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)]內容[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]應用程式建立的執行個體[WebBrowser 控制項](https://go.microsoft.com/fwlink/?LinkId=97911)。</span><span class="sxs-lookup"><span data-stu-id="06891-106">To host [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] content, [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] applications create an instance of the [WebBrowser control](https://go.microsoft.com/fwlink/?LinkId=97911).</span></span> <span data-ttu-id="06891-107">要裝載[!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)]建立 PresentationHost.exe，提供所裝載的執行個體[!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)]的主控件中的顯示內容[WebBrowser 控制項](https://go.microsoft.com/fwlink/?LinkId=97911)。</span><span class="sxs-lookup"><span data-stu-id="06891-107">To be hosted, [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] creates an instance of PresentationHost.exe, which provides the hosted [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] content to the host for display in the [WebBrowser control](https://go.microsoft.com/fwlink/?LinkId=97911).</span></span>  
  
 <span data-ttu-id="06891-108">藉由啟用整合`IWpfHostSupport`可讓 PresentationHost.exe:</span><span class="sxs-lookup"><span data-stu-id="06891-108">The integration enabled by `IWpfHostSupport` allows PresentationHost.exe to:</span></span>  
  
- <span data-ttu-id="06891-109">探索並向未經處理輸入裝置 （人性化介面裝置） 的主應用程式有興趣。</span><span class="sxs-lookup"><span data-stu-id="06891-109">Discover and register with the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>  
  
- <span data-ttu-id="06891-110">主應用程式，從已註冊的未經處理輸入的裝置與正向適當的訊息接收輸入的訊息。</span><span class="sxs-lookup"><span data-stu-id="06891-110">Receive input messages from the registered raw input devices and forward appropriate messages to the host application.</span></span>  
  
- <span data-ttu-id="06891-111">查詢主應用程式自訂進度和錯誤的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="06891-111">Query the host application for custom progress and error user interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="06891-112">僅限在本機用戶端電腦上使用及支援此 API</span><span class="sxs-lookup"><span data-stu-id="06891-112">This API is only intended and supported for use on the local client machine</span></span>  
  
## <a name="members"></a><span data-ttu-id="06891-113">成員</span><span class="sxs-lookup"><span data-stu-id="06891-113">Members</span></span>  
  
|<span data-ttu-id="06891-114">成員</span><span class="sxs-lookup"><span data-stu-id="06891-114">Member</span></span>|<span data-ttu-id="06891-115">描述</span><span class="sxs-lookup"><span data-stu-id="06891-115">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="06891-116">GetRawInputDevices</span><span class="sxs-lookup"><span data-stu-id="06891-116">GetRawInputDevices</span></span>](getrawinputdevices.md)|<span data-ttu-id="06891-117">可讓 PresentationHost.exe 探索主應用程式有興趣的未經處理輸入裝置 (人性化介面裝置)。</span><span class="sxs-lookup"><span data-stu-id="06891-117">Allows PresentationHost.exe to discover the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>|  
|[<span data-ttu-id="06891-118">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="06891-118">FilterInputMessage</span></span>](filterinputmessage.md)|<span data-ttu-id="06891-119">除非傳回 E_NOTIMPL，否則每當收到訊息時，都會由 PresentationHost.exe 呼叫。</span><span class="sxs-lookup"><span data-stu-id="06891-119">Called by PresentationHost.exe whenever a message is received unless E_NOTIMPL is returned.</span></span>|  
|[<span data-ttu-id="06891-120">GetCustomUI</span><span class="sxs-lookup"><span data-stu-id="06891-120">GetCustomUI</span></span>](getcustomui.md)|<span data-ttu-id="06891-121">根據預設，PresentationHost.exe 提供它自己的部署進度和部署錯誤會顯示部署的 WPF 內容時的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="06891-121">By default, PresentationHost.exe provides its own deployment progress and deployment error user interfaces that are displayed when WPF content is deployed.</span></span>|
