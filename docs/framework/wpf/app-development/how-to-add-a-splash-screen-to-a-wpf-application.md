---
title: 如何新增啟動顯示畫面
ms.date: 08/18/2018
helpviewer_keywords:
- WPF [WPF], splash screen
- startup window [WPF]
- SplashScreen class [WPF]
- splash screen [WPF]
ms.assetid: d70a25c4-5fb9-4c27-b01d-b1b8ef39b3fd
ms.openlocfilehash: 39f53e21c40f036c65894b4f275cd5fb414999be
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740444"
---
# <a name="how-to-add-a-splash-screen-to-a-wpf-application"></a>如何：在 WPF 應用程式中加入啟動顯示畫面

本主題說明如何將啟動視窗或啟動顯示*畫面*新增至 WINDOWS PRESENTATION FOUNDATION （WPF）應用程式。

## <a name="to-add-an-existing-image-as-a-splash-screen"></a>新增現有的影像做為啟動顯示畫面

1. 建立或尋找您要用於啟動顯示畫面的影像。 您可以使用 Windows 影像處理元件（WIC）所支援的任何影像格式。 例如，您可以使用 BMP、GIF、JPEG、PNG 或 TIFF 格式。

2. 將影像檔案新增至 WPF 應用程式專案。

3. 在 **方案總管**中，選取映射。

4. 在 屬性視窗中，按一下 **組建動作** 屬性的下拉箭號。

5. 從下拉式清單中選取 [ **SplashScreen** ]。

6. 按 **F5** 鍵以建置並執行應用程式。

     啟動顯示畫面影像會出現在螢幕的中央，然後在主應用程式視窗出現時淡化。

## <a name="to-exclude-the-splash-screen-from-build"></a>若要從組建中排除啟動顯示畫面

1. 在 **方案總管**中，選取啟動顯示畫面影像。

2. 在 [**屬性**] 視窗中，將 [**建立] 動作**設定為 [**無**]。

## <a name="to-remove-the-splash-screen-from-an-application"></a>若要從應用程式移除啟動顯示畫面

在**方案總管**中，刪除啟動顯示畫面影像。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.SplashScreen>
- [如何：將現有的專案加入至專案](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))
