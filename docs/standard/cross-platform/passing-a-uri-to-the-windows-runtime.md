---
title: 傳遞 URI 給 Windows 執行階段
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Runtime, .NET Framework support for
- Windows Runtime, passing a URI to
ms.assetid: 3eb5ce6f-f304-4f87-8e81-0f25092f5ad4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0f019c1075c119c3d814b3b7add8fe30f3e4d107
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2018
ms.locfileid: "45649337"
---
# <a name="passing-a-uri-to-the-windows-runtime"></a><span data-ttu-id="99306-102">傳遞 URI 給 Windows 執行階段</span><span class="sxs-lookup"><span data-stu-id="99306-102">Passing a URI to the Windows Runtime</span></span>
<span data-ttu-id="99306-103">Windows Runtime 方法僅接受絕對 URI。</span><span class="sxs-lookup"><span data-stu-id="99306-103">Windows Runtime methods accept only absolute URIs.</span></span> <span data-ttu-id="99306-104">如果您傳遞相關 URI 至 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 方法，則會擲回 <xref:System.ArgumentException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="99306-104">If you pass a relative URI to a [!INCLUDE[wrt](../../../includes/wrt-md.md)] method, an <xref:System.ArgumentException> exception is thrown.</span></span> <span data-ttu-id="99306-105">原因如下： 當您使用[!INCLUDE[wrt](../../../includes/wrt-md.md)].NET Framework 程式碼，在<xref:Windows.Foundation.Uri?displayProperty=nameWithType>類別會顯示為<xref:System.Uri?displayProperty=nameWithType>在 Intellisense 中。</span><span class="sxs-lookup"><span data-stu-id="99306-105">Here's why: When you use the [!INCLUDE[wrt](../../../includes/wrt-md.md)] in .NET Framework code, the <xref:Windows.Foundation.Uri?displayProperty=nameWithType> class appears as <xref:System.Uri?displayProperty=nameWithType> in Intellisense.</span></span> <span data-ttu-id="99306-106"><xref:System.Uri?displayProperty=nameWithType>類別可讓相對 Uri，但<xref:Windows.Foundation.Uri?displayProperty=nameWithType>類別則否。</span><span class="sxs-lookup"><span data-stu-id="99306-106">The <xref:System.Uri?displayProperty=nameWithType> class allows relative URIs, but the <xref:Windows.Foundation.Uri?displayProperty=nameWithType> class does not.</span></span> <span data-ttu-id="99306-107">對於您公開在 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 元件中的方法也是如此。</span><span class="sxs-lookup"><span data-stu-id="99306-107">This is also true for methods you expose in [!INCLUDE[wrt](../../../includes/wrt-md.md)] Components.</span></span> <span data-ttu-id="99306-108">如果您的元件公開採用 URI 的方法，則程式碼中的簽章包含 <xref:System.Uri?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="99306-108">If your component exposes a method that takes a URI, the signature in your code includes <xref:System.Uri?displayProperty=nameWithType>.</span></span> <span data-ttu-id="99306-109">不過，您的元件的使用者，簽章包含<xref:Windows.Foundation.Uri?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="99306-109">However, to users of your component, the signature includes <xref:Windows.Foundation.Uri?displayProperty=nameWithType>.</span></span> <span data-ttu-id="99306-110">傳遞至元件的 URI 必須是絕對 URI。</span><span class="sxs-lookup"><span data-stu-id="99306-110">A URI that is passed to your component must be an absolute URI.</span></span>  
  
 <span data-ttu-id="99306-111">此主題示範如何偵測絕對 URI，以及參考應用程式套件中的資源時，如何建立 URI。</span><span class="sxs-lookup"><span data-stu-id="99306-111">This topic shows how to detect an absolute URI and how to create one when referring to a resource in the app package.</span></span>  
  
## <a name="detecting-and-using-an-absolute-uri"></a><span data-ttu-id="99306-112">偵測及使用絕對 URI</span><span class="sxs-lookup"><span data-stu-id="99306-112">Detecting and using an absolute URI</span></span>  
 <span data-ttu-id="99306-113">使用 <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType> 屬性可在將 URI 傳遞至 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 之前，先確定 URI 是絕對的。</span><span class="sxs-lookup"><span data-stu-id="99306-113">Use the <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType> property to ensure that a URI is absolute before passing it to the [!INCLUDE[wrt](../../../includes/wrt-md.md)].</span></span> <span data-ttu-id="99306-114">使用此屬性比攔截並處理 <xref:System.ArgumentException> 例外狀況更有效率。</span><span class="sxs-lookup"><span data-stu-id="99306-114">Using this property is more efficient than catching and handling the <xref:System.ArgumentException> exception.</span></span>  
  
## <a name="using-an-absolute-uri-for-a-resource-in-the-app-package"></a><span data-ttu-id="99306-115">將絕對 URI 用於應用程式套件中的資源</span><span class="sxs-lookup"><span data-stu-id="99306-115">Using an absolute URI for a resource in the app package</span></span>  
 <span data-ttu-id="99306-116">如果您想要為應用程式套件中包含的資源指定 URI，可以使用 `ms-appx` 或 `ms-appx-web` 結構描述來建立絕對 URI。</span><span class="sxs-lookup"><span data-stu-id="99306-116">If you want to specify a URI for a resource that your app package contains, you can use the `ms-appx` or `ms-appx-web` scheme to create an absolute URI.</span></span>  
  
 <span data-ttu-id="99306-117">下列範例示範如何設定[來源](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.source.aspx)屬性[WebView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.aspx)控制項和[來源](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.image.source.aspx)屬性[映像](https://msdn.microsoft.com/library/windows/apps/br242752.aspx)控制項若要為 Pages 資料夾中包含的資源，使用 XAML 和程式碼。</span><span class="sxs-lookup"><span data-stu-id="99306-117">The following example shows how to set the [Source](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.source.aspx) property for a [WebView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.aspx) control and the [Source](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.image.source.aspx) property for an [Image](https://msdn.microsoft.com/library/windows/apps/br242752.aspx) control to resources that are contained in a folder named Pages, using both XAML and code.</span></span>  
  
 [!code-xaml[System.URIToWindowsURI#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml#1)]  
[!code-csharp[System.URIToWindowsURI#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml.cs#2)]
[!code-vb[System.URIToWindowsURI#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.uritowindowsuri/vb/mainpage.xaml.vb#2)]  
  
 <span data-ttu-id="99306-118">如需這些結構描述的詳細資訊，請參閱[URI 配置](https://msdn.microsoft.com/library/windows/apps/jj655406.aspx)Windows 開發人員中心。</span><span class="sxs-lookup"><span data-stu-id="99306-118">For more information about these schemes, see [URI schemes](https://msdn.microsoft.com/library/windows/apps/jj655406.aspx) in the Windows Dev Center.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99306-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99306-119">See also</span></span>

- [<span data-ttu-id="99306-120">Windows 市集應用程式和 Windows 執行階段的 .NET Framework 支援</span><span class="sxs-lookup"><span data-stu-id="99306-120">.NET Framework Support for Windows Store Apps and Windows Runtime</span></span>](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
