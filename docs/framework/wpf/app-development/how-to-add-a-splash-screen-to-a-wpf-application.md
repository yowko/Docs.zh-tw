---
title: "如何：在 WPF 應用程式中加入啟動顯示畫面 | Microsoft Docs"
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
  - "啟動顯示畫面 [WPF]"
  - "SplashScreen 類別 [WPF]"
  - "啟動視窗 [WPF]"
  - "WPF, 啟動顯示畫面"
ms.assetid: d70a25c4-5fb9-4c27-b01d-b1b8ef39b3fd
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：在 WPF 應用程式中加入啟動顯示畫面
本主題說明如何在 Windows Presentation Foundation \(WPF\) 應用程式中加入啟動視窗，或稱「*啟動顯示畫面*」\(Splash Screen\)。  
  
### 若要加入現有影像做為啟動顯示畫面  
  
1.  建立或找出要用於啟動顯示畫面的影像。  您可以使用 Windows 影像處理元件 \(WIC\) 所支援的任何影像格式。  例如，可以使用 BMP、GIF、JPEG、PNG 或 TIFF 格式。  
  
2.  將影像檔加入至 WPF 應用程式專案。  如需詳細資訊，請參閱 [NIB:How to: Add Existing Items to a Project](http://msdn.microsoft.com/zh-tw/15f4cfb7-78ab-457f-9f14-099a25a6a2d3)。  
  
3.  在 \[方案總管\] 中，選取影像。  
  
4.  按一下 \[屬性\] 視窗中 \[**建置動作**\] 屬性的下拉箭號。  
  
5.  從下拉式清單中選取 \[**SplashScreen**\]。  
  
    > [!NOTE]
    >  如果沒有看到 \[**SplashScreen**\] 選項，請確認您使用的是 [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)] SP1 \(含\) 以後版本。  
  
6.  按 F5 建置並執行應用程式。  
  
     畫面中央會出現啟動顯示畫面影像，然後在主應用程式視窗出現時淡出。  
  
### 若要移除應用程式的啟動顯示畫面  
  
1.  在 \[方案總管\] 中，選取啟動顯示畫面影像。  
  
2.  在 \[屬性\] 視窗中，將 \[**建置動作**\] 設為 \[**無**\]。  
  
### 若要移除應用程式的啟動顯示畫面  
  
-   在 \[方案總管\] 中，刪除啟動顯示畫面影像。  
  
-   從專案中排除啟動顯示畫面影像。  
  
## 請參閱  
 <xref:System.Windows.SplashScreen>   
 [NIB:How to: Add Existing Items to a Project](http://msdn.microsoft.com/zh-tw/15f4cfb7-78ab-457f-9f14-099a25a6a2d3)