---
title: "逐步解說：建立裝載於 WPF 中的 Direct3D9 內容 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Direct3D9 [WPF 互通性], 建立 Direct3D9 內容"
  - "WPF, 建立 Direct3D9 內容"
ms.assetid: 286e98bc-1eaa-4b5e-923d-3490a9cca5fc
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 逐步解說：建立裝載於 WPF 中的 Direct3D9 內容
本逐步解說示範如何建立適合裝載於 Windows Presentation Foundation \(WPF\) 應用程式中的 Direct3D9 內容。  如需在 WPF 應用程式中裝載 Direct3D9 內容的詳細資訊，請參閱[WPF 和 Direct3D9 互通](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md)。  
  
 在這個逐步解說中，您會執行下列工作：  
  
-   建立 Direct3D9 專案。  
  
-   設定要裝載於 WPF 應用程式中的 Direct3D9 專案。  
  
 完成時，您得到的 DLL 就會包含 WPF 應用程式中使用的 Direct3D9 內容。  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
-   DirectX SDK 9 \(含\) 以後版本。  
  
## 建立 Direct3D9 專案  
 第一個步驟是建立並設定 Direct3D9 專案。  
  
#### 若要建立 Direct3D9 專案  
  
1.  在 C\+\+ 中，建立名為 `D3DContent` 的新 Win32 專案。  
  
     \[Win32 應用程式精靈\] 隨即出現，並顯示歡迎畫面。  
  
2.  按一下 \[**下一步**\]。  
  
     \[應用程式設定\] 畫面隨即出現。  
  
3.  在 \[**應用程式類型**\] 中，選取 \[**DLL**\] 選項。  
  
4.  按一下 \[**完成**\]。  
  
     隨即產生 D3DContent 專案。  
  
5.  以滑鼠右鍵按一下 \[方案總管\] 中的 D3DContent 專案，然後選取 \[**屬性**\]。  
  
     \[**D3DContent 屬性頁**\] 對話方塊隨即開啟。  
  
6.  選取 \[**C\/C\+\+**\] 節點。  
  
7.  在 \[**其他 Include 目錄**\] 欄位中，指定 DirectX Include 資料夾的位置。  這個資料夾的預設位置是 %ProgramFiles%\\Microsoft DirectX SDK \(*version*\)\\Include。  
  
8.  按兩下 \[**連結器**\] 節點進行展開。  
  
9. 在 \[**其他程式庫目錄**\] 欄位中，指定 DirectX 程式庫資料夾的位置。  這個資料夾的預設位置是 %ProgramFiles%\\Microsoft DirectX SDK \(*version*\)\\Lib\\x86。  
  
10. 選取 \[**輸入**\] 節點。  
  
11. 在 \[**其他相依性**\] 欄位中，加入 `d3d9.lib` 和 `d3dx9.lib` 檔案。  
  
12. 在 \[方案總管\] 中，將名為 `D3DContent.def` 的新模組定義檔 \(.def\) 加入至專案中。  
  
## 建立 Direct3D9 內容  
 為了獲得最佳效能，Direct3D9 內容必須使用特殊的設定。  下列程式碼示範如何讓建立的 Direct3D9 介面具有最佳的效能特性。  如需詳細資訊，請參閱 [Direct3D9 和 WPF 互通性的效能考量](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)。  
  
#### 若要建立 Direct3D9 內容  
  
1.  使用 \[方案總管\] 將三個 C\+\+ 類別加入到下列名稱的專案中。  
  
     `CRenderer` \(具有虛擬解構函式\)  
  
     `CRendererManager`  
  
     `CTriangleRenderer`  
  
2.  在 \[程式碼編輯器\] 中開啟 Renderer.h，以下列程式碼取代自動產生的程式碼。  
  
     [!code-cpp[System.Windows.Interop.D3DImage#RendererH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.h#rendererh)]  
  
3.  在 \[程式碼編輯器\] 中開啟 Renderer.cpp，以下列程式碼取代自動產生的程式碼。  
  
     [!code-cpp[System.Windows.Interop.D3DImage#RendererCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderercpp)]  
  
4.  在 \[程式碼編輯器\] 中開啟 RendererManager.h，以下列程式碼取代自動產生的程式碼。  
  
     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.h#renderermanagerh)]  
  
5.  在 \[程式碼編輯器\] 中開啟 RendererManager.cpp，以下列程式碼取代自動產生的程式碼。  
  
     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanagercpp)]  
  
6.  在 \[程式碼編輯器\] 中開啟 TriangleRenderer.h，以下列程式碼取代自動產生的程式碼。  
  
     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.h#trianglerendererh)]  
  
7.  在 \[程式碼編輯器\] 中開啟 TriangleRenderer.cpp，以下列程式碼取代自動產生的程式碼。  
  
     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.cpp#trianglerenderercpp)]  
  
8.  在 \[程式碼編輯器\] 中開啟 stdafx.h，以下列程式碼取代自動產生的程式碼。  
  
     [!code-cpp[System.Windows.Interop.D3DImage#StdafxH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/stdafx.h#stdafxh)]  
  
9. 在 \[程式碼編輯器\] 中開啟 dllmain.cpp，以下列程式碼取代自動產生的程式碼。  
  
     [!code-cpp[System.Windows.Interop.D3DImage#DllMain](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/dllmain.cpp#dllmain)]  
  
10. 在 \[程式碼編輯器\] 中開啟 D3DContent.def。  
  
11. 以下列程式碼取代自動產生的程式碼。  
  
    ```  
  
    LIBRARY "D3DContent"  
  
    EXPORTS  
  
    SetSize  
    SetAlpha  
    SetNumDesiredSamples  
    SetAdapter  
  
    GetBackBufferNoRef  
    Render  
    Destroy  
  
    ```  
  
12. 建置專案。  
  
## 後續步驟  
  
-   將 Direct3D9 內容裝載於 WPF 應用程式中。  如需詳細資訊，請參閱 [逐步解說：在 WPF 中裝載 Direct3D9 內容](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md)。  
  
## 請參閱  
 <xref:System.Windows.Interop.D3DImage>   
 [Direct3D9 和 WPF 互通性的效能考量](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)   
 [逐步解說：在 WPF 中裝載 Direct3D9 內容](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md)