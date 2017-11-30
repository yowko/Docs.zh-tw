---
title: "手寫辨識"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- handwriting recognition [WPF]
- recognition of handwriting [WPF]
ms.assetid: f4e8576d-e731-4bac-9818-22e2ae636636
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f8a202d4698c968a91a3d930138290cedfe3a83b
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="handwriting-recognition"></a>手寫辨識
本節討論有關 WPF 平台中數位筆跡的辨識基本概念。  
  
## <a name="recognition-solutions"></a>辨識方案  
 下列範例示範如何使用 [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx) 類別來辨識筆跡。  
  
> [!NOTE]
>  此範例需要在系統上安裝手寫辨識器。  
  
 在 Visual Studio 中，建立稱為 **InkRecognition** 的新 WPF 應用程式專案。 將 Window1.xaml 檔案的內容取代為下列 XAML 程式碼。 此程式碼會轉譯應用程式的使用者介面。  
  
 [!code-xaml[InkRecognition#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml#1)]  
  
 新增可在 \Program Files\Common Files\Microsoft Shared\Ink 中找到之 Microsoft Ink 組件的參考 (Microsoft.Ink.dll)。 將程式碼後置檔案的內容取代為下列程式碼。  
  
 [!code-csharp[InkRecognition#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml.cs#2)]
 [!code-vb[InkRecognition#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InkRecognition/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx)
