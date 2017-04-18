---
title: "如何：在漸層中使用系統色彩 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "漸層, 系統色彩"
  - "漸層的系統色彩"
ms.assetid: 11942e7e-6300-4b50-8ed1-f50e8d20e7d2
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 如何：在漸層中使用系統色彩
若要在漸層中使用系統色彩，請使用 <xref:System.Windows.SystemColors> 類別的 *\<SystemColor\>*Color 和 *\<SystemColor\>*ColorKey 靜態屬性來取得色彩的參考，其中 *\<SystemColor\>* 是所需系統色彩的名稱。  當您要建立隨著系統主題變更自動更新的動態參考時，請使用 *\<SystemColor\>*ColorKey 屬性。  否則，請使用 *\<SystemColor\>*Color 屬性。  
  
## 範例  
 下列範例會使用動態系統色彩資源建立漸層。  
  
 [!code-xml[brushsamples_snip#GraphicsMMDynamicSystemColorGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemColorExample.xaml#graphicsmmdynamicsystemcolorgradientexamplewholepage)]  
  
 下面的範例則使用靜態系統色彩資源建立漸層。  
  
 [!code-xml[brushsamples_snip#GraphicsMMStaticSystemColorGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemColorExample.xaml#graphicsmmstaticsystemcolorgradientexamplewholepage)]  
  
## 請參閱  
 <xref:System.Windows.SystemColors>   
 [使用系統筆刷繪製區域](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)   
 [使用純色和漸層繪製的概觀](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)