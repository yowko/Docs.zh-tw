---
title: 如何：在 WPF 應用程式中加入啟動顯示畫面
ms.date: 03/30/2017
helpviewer_keywords:
- WPF [WPF], splash screen
- startup window [WPF]
- SplashScreen class [WPF]
- splash screen [WPF]
ms.assetid: d70a25c4-5fb9-4c27-b01d-b1b8ef39b3fd
ms.openlocfilehash: 06d6cb7c5a5081d3b6c4979ab50e1caaa726acbe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546997"
---
# <a name="how-to-add-a-splash-screen-to-a-wpf-application"></a>如何：在 WPF 應用程式中加入啟動顯示畫面
本主題說明如何新增到 [啟動] 視窗或*啟動顯示畫面*，Windows Presentation Foundation (WPF) 應用程式。  
  
### <a name="to-add-an-existing-image-as-a-splash-screen"></a>將現有的映像新增為啟動顯示畫面  
  
1.  建立或尋找您想要使用的啟動顯示畫面影像。 您可以使用任何支援 Windows 影像處理元件 (WIC) 的映像格式。 例如，您可以使用 BMP、 GIF、 JPEG、 PNG 或 TIFF 格式。  
  
2.  將影像檔加入至 WPF 應用程式專案。 如需詳細資訊，請參閱[NIB： 如何： 加入現有項目加入至專案](http://msdn.microsoft.com/library/15f4cfb7-78ab-457f-9f14-099a25a6a2d3)。  
  
3.  在 [方案總管] 中選取的映像。  
  
4.  在 [屬性] 視窗中，按一下下拉式箭號**建置動作**屬性。  
  
5.  選取**啟動顯示畫面**從下拉式清單。  
  
    > [!NOTE]
    >  如果您沒有看到**啟動顯示畫面**選項，請務必檢查您使用[!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)]SP1 或更新版本。  
  
6.  按 F5 鍵建置並執行應用程式。  
  
     啟動顯示畫面影像出現在螢幕的中央，並再讓主應用程式視窗出現時。  
  
### <a name="to-remove-the-splash-screen-from-an-application"></a>若要移除應用程式的啟動顯示畫面  
  
1.  在 方案總管 中，選取 啟動顯示畫面影像。  
  
2.  在 [屬性] 視窗中，設定**建置動作**至**無**。  
  
### <a name="to-remove-the-splash-screen-from-an-application"></a>若要移除應用程式的啟動顯示畫面  
  
-   在 方案總管刪除啟動顯示畫面影像。  
  
-   從專案排除啟動顯示畫面影像。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.SplashScreen>  
 [NIB： 如何： 將現有的項目加入至專案](http://msdn.microsoft.com/library/15f4cfb7-78ab-457f-9f14-099a25a6a2d3)
