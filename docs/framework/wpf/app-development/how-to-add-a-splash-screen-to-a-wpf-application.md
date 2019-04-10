---
title: HOW TO：將啟動顯示畫面新增至 WPF 應用程式
ms.date: 08/18/2018
helpviewer_keywords:
- WPF [WPF], splash screen
- startup window [WPF]
- SplashScreen class [WPF]
- splash screen [WPF]
ms.assetid: d70a25c4-5fb9-4c27-b01d-b1b8ef39b3fd
ms.openlocfilehash: 3120ee64d65822d323800a89466c6b707169aaaa
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59307472"
---
# <a name="how-to-add-a-splash-screen-to-a-wpf-application"></a>HOW TO：將啟動顯示畫面新增至 WPF 應用程式

本主題說明如何新增 [啟動] 視窗中，或是*啟動顯示畫面*，Windows Presentation Foundation (WPF) 應用程式。

## <a name="to-add-an-existing-image-as-a-splash-screen"></a>若要將現有的映像新增為啟動顯示畫面

1. 建立或尋找您想要使用的啟動顯示畫面的映像。 您可以使用任何支援 Windows Imaging Component (WIC) 的映像格式。 例如，您可以使用 BMP、 GIF、 JPEG、 PNG 或 TIFF 格式。

2. 將映像檔新增至 WPF 應用程式專案中。

3. 在 [**方案總管] 中**，選取的映像。

4. 在 [屬性] 視窗中，按一下下拉式箭號**建置動作**屬性。

5. 選取  **SplashScreen**從下拉式清單。

6. 按 **F5** 鍵建置並執行應用程式。

     啟動顯示畫面影像會出現在螢幕的中心，然後再讓 當主應用程式視窗隨即出現。

## <a name="to-exclude-the-splash-screen-from-build"></a>若要從組建排除啟動顯示畫面

1. 在 **方案總管 中**，選取 啟動顯示畫面影像。

2. 在 **屬性**視窗中，將**建置動作**來**None**。

## <a name="to-remove-the-splash-screen-from-an-application"></a>若要移除應用程式的啟動顯示畫面

在 [**方案總管] 中**，刪除啟動顯示畫面影像。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.SplashScreen>
- [HOW TO：將現有的項目加入至專案](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))
