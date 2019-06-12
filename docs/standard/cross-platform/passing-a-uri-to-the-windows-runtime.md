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
ms.openlocfilehash: c489ec893ea335c8fafc904cf2a12162580ec266
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025433"
---
# <a name="passing-a-uri-to-the-windows-runtime"></a>傳遞 URI 給 Windows 執行階段
Windows Runtime 方法僅接受絕對 URI。 如果您將相對 URI 傳遞給 Windows 執行階段方法時，<xref:System.ArgumentException>擲回例外狀況。 原因如下：當您在.NET Framework 程式碼，使用 Windows 執行階段<xref:Windows.Foundation.Uri?displayProperty=nameWithType>類別會顯示為<xref:System.Uri?displayProperty=nameWithType>在 Intellisense 中。 <xref:System.Uri?displayProperty=nameWithType>類別可讓相對 Uri，但<xref:Windows.Foundation.Uri?displayProperty=nameWithType>類別則否。 這也適用於 Windows 執行階段元件中公開 （expose） 的方法。 如果您的元件公開採用 URI 的方法，則程式碼中的簽章包含 <xref:System.Uri?displayProperty=nameWithType>。 不過，您的元件的使用者，簽章包含<xref:Windows.Foundation.Uri?displayProperty=nameWithType>。 傳遞至元件的 URI 必須是絕對 URI。  
  
此主題示範如何偵測絕對 URI，以及參考應用程式套件中的資源時，如何建立 URI。  
  
## <a name="detecting-and-using-an-absolute-uri"></a>偵測及使用絕對 URI  
使用<xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType>屬性，確定傳遞給 Windows 執行階段之前是絕對 URI。 使用此屬性比攔截並處理 <xref:System.ArgumentException> 例外狀況更有效率。  
  
## <a name="using-an-absolute-uri-for-a-resource-in-the-app-package"></a>將絕對 URI 用於應用程式套件中的資源  
如果您想要為應用程式套件中包含的資源指定 URI，可以使用 `ms-appx` 或 `ms-appx-web` 結構描述來建立絕對 URI。  
  
下列範例示範如何設定<xref:Windows.UI.Xaml.Controls.WebView.Source%2A>屬性<xref:Windows.UI.Xaml.Controls.WebView>控制項並<xref:Windows.UI.Xaml.Controls.Image.Source%2A>屬性<xref:Windows.UI.Xaml.Controls.Image>資源包含在名為網頁，可以使用 XAML 和程式碼的資料夾中的控制。  
  
[!code-xaml[System.URIToWindowsURI#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml#1)]  
[!code-csharp[System.URIToWindowsURI#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml.cs#2)]
[!code-vb[System.URIToWindowsURI#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.uritowindowsuri/vb/mainpage.xaml.vb#2)]  
  
如需這些結構描述的詳細資訊，請參閱[URI 配置](/windows/uwp/app-resources/uri-schemes)Windows 開發人員中心。  
  
## <a name="see-also"></a>另請參閱

- [Windows 市集應用程式和 Windows 執行階段的 .NET Framework 支援](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
