---
title: "逐步解說：在 WPF 中裝載 Direct3D9 內容 | Microsoft Docs"
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
  - "Direct3D9 [WPF 互通性], 裝載 Direct3D9 內容"
  - "WPF, 裝載 Direct3D9 內容"
ms.assetid: 60983736-0ab5-42cc-8b16-e9fbde261a43
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 逐步解說：在 WPF 中裝載 Direct3D9 內容
本逐步解說示範如何在 Windows Presentation Foundation \(WPF\) 應用程式中裝載 Direct3D9 內容。  
  
 在這個逐步解說中，您會執行下列工作：  
  
-   建立 WPF 專案裝載 Direct3D9 內容。  
  
-   匯入 Direct3D9 內容。  
  
-   使用 <xref:System.Windows.Interop.D3DImage> 類別顯示 Direct3D9 內容。  
  
 完成時，您就會了解如何在 WPF 應用程式中裝載 Direct3D9 內容。  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
-   DirectX SDK 9 \(含\) 以後版本。  
  
-   包含具有 WPF 相容格式之 Direct3D9 內容的 DLL。  如需詳細資訊，請參閱[WPF 和 Direct3D9 互通](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md)和[逐步解說：建立裝載於 WPF 中的 Direct3D9 內容](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)。  
  
## 建立 WPF 專案  
 第一個步驟是建立 WPF 應用程式的專案。  
  
#### 若要建立 WPF 專案  
  
-   在 Visual C\# 中建立名為 `D3DHost` 的新 WPF 應用程式專案。  如需詳細資訊，請參閱 [HOW TO：建立新的 WPF 應用程式專案](http://msdn.microsoft.com/zh-tw/1f6aea7a-33e1-4d3f-8555-1daa42e95d82)。  
  
     MainWindow.xaml 隨即在 [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]中開啟。  
  
## 匯入 Direct3D9 內容  
 藉由使用 `DllImport` 屬性，即可以從 Unmanaged DLL 匯入 Direct3D9 內容。  
  
#### 若要匯入 Direct3D9 內容  
  
1.  在 \[程式碼編輯器\] 中開啟 MainWindow.xaml.cs。  
  
2.  以下列程式碼取代自動產生的程式碼。  
  
     [!code-csharp[System.Windows.Interop.D3DImage#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml.cs#1)]  
  
## 裝載 Direct3D9 內容  
 最後，使用 <xref:System.Windows.Interop.D3DImage> 類別裝載 Direct3D9 內容。  
  
#### 若要裝載 Direct3D9 內容  
  
1.  在 MainWindow.xaml 中，以下列 XAML 取代自動產生的 XAML。  
  
     [!code-xml[System.Windows.Interop.D3DImage#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml#10)]  
  
2.  建置專案。  
  
3.  複製包含 Direct3D9 內容的 DLL 到 bin\/Debug 資料夾。  
  
4.  按 F5 執行專案。  
  
     Direct3D9 內容會出現在 WPF 應用程式內。  
  
## 請參閱  
 <xref:System.Windows.Interop.D3DImage>   
 [Direct3D9 和 WPF 互通性的效能考量](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)