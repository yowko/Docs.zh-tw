---
title: 手寫辨識
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- handwriting recognition [WPF]
- recognition of handwriting [WPF]
ms.assetid: f4e8576d-e731-4bac-9818-22e2ae636636
ms.openlocfilehash: d6c09f063b6bd0eef2cb9f6bb444eac980ad4832
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956522"
---
# <a name="handwriting-recognition"></a>手寫辨識
本節討論有關 WPF 平台中數位筆跡的辨識基本概念。  
  
## <a name="recognition-solutions"></a>辨識方案  
 下列範例示範如何使用 [Microsoft.Ink.InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90)) 類別來辨識筆跡。  
  
> [!NOTE]
> 此範例需要在系統上安裝手寫辨識器。  
  
 在 Visual Studio 中，建立稱為 **InkRecognition** 的新 WPF 應用程式專案。 將 Window1.xaml 檔案的內容取代為下列 XAML 程式碼。 此程式碼會轉譯應用程式的使用者介面。  
  
 [!code-xaml[InkRecognition#1](~/samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml#1)]  
  
 新增可在 \Program Files\Common Files\Microsoft Shared\Ink 中找到之 Microsoft Ink 組件的參考 (Microsoft.Ink.dll)。 將程式碼後置檔案的內容取代為下列程式碼。  
  
 [!code-csharp[InkRecognition#2](~/samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml.cs#2)]
 [!code-vb[InkRecognition#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InkRecognition/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>另請參閱

- [Microsoft.Ink.InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90))
