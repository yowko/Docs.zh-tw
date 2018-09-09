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
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2018
ms.locfileid: "44252034"
---
# <a name="passing-a-uri-to-the-windows-runtime"></a>傳遞 URI 給 Windows 執行階段
Windows Runtime 方法僅接受絕對 URI。 如果您傳遞相關 URI 至 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 方法，則會擲回 <xref:System.ArgumentException> 例外狀況。 原因如下： 當您使用[!INCLUDE[wrt](../../../includes/wrt-md.md)].NET Framework 程式碼，在<xref:Windows.Foundation.Uri?displayProperty=nameWithType>類別會顯示為<xref:System.Uri?displayProperty=nameWithType>在 Intellisense 中。 <xref:System.Uri?displayProperty=nameWithType>類別可讓相對 Uri，但<xref:Windows.Foundation.Uri?displayProperty=nameWithType>類別則否。 對於您公開在 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 元件中的方法也是如此。 如果您的元件公開採用 URI 的方法，則程式碼中的簽章包含 <xref:System.Uri?displayProperty=nameWithType>。 不過，您的元件的使用者，簽章包含<xref:Windows.Foundation.Uri?displayProperty=nameWithType>。 傳遞至元件的 URI 必須是絕對 URI。  
  
 此主題示範如何偵測絕對 URI，以及參考應用程式套件中的資源時，如何建立 URI。  
  
## <a name="detecting-and-using-an-absolute-uri"></a>偵測及使用絕對 URI  
 使用 <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType> 屬性可在將 URI 傳遞至 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 之前，先確定 URI 是絕對的。 使用此屬性比攔截並處理 <xref:System.ArgumentException> 例外狀況更有效率。  
  
## <a name="using-an-absolute-uri-for-a-resource-in-the-app-package"></a>將絕對 URI 用於應用程式套件中的資源  
 如果您想要為應用程式套件中包含的資源指定 URI，可以使用 `ms-appx` 或 `ms-appx-web` 結構描述來建立絕對 URI。  
  
 下列範例示範如何設定[來源](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.source.aspx)屬性[WebView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.aspx)控制項和[來源](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.image.source.aspx)屬性[映像](https://msdn.microsoft.com/library/windows/apps/br242752.aspx)控制項若要為 Pages 資料夾中包含的資源，使用 XAML 和程式碼。  
  
 [!code-xaml[System.URIToWindowsURI#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml#1)]  
[!code-csharp[System.URIToWindowsURI#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml.cs#2)]
[!code-vb[System.URIToWindowsURI#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.uritowindowsuri/vb/mainpage.xaml.vb#2)]  
  
 如需這些結構描述的詳細資訊，請參閱[URI 配置](https://msdn.microsoft.com/library/windows/apps/jj655406.aspx)Windows 開發人員中心。  
  
## <a name="see-also"></a>另請參閱

- [Windows 市集應用程式和 Windows 執行階段的 .NET Framework 支援](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
