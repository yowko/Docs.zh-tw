---
title: 雙重緩衝的使用
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], double buffering
- double buffering
- flicker [Windows Forms], reducing in Windows Forms
- buffering [Windows Forms], double buffering
ms.assetid: dc484e33-7101-4e4b-ada5-d3c96155fbcd
ms.openlocfilehash: 5b22336221c7bdda3c9dd7adf23308a2b0bad450
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/18/2019
ms.locfileid: "67169913"
---
# <a name="using-double-buffering"></a>雙重緩衝的使用
若要減少重繪閃動包含複雜繪製作業的應用程式中，您可以使用雙重緩衝的圖形。 .NET Framework 包含雙重緩衝的內建支援，或者您可以管理並手動呈現圖形。  
  
## <a name="in-this-section"></a>本節內容  
 [雙重緩衝的圖形](double-buffered-graphics.md)  
 導入雙重緩衝概念並勾畫.NET Framework 支援。  
  
 [如何：減少使用表單和控制項的雙重緩衝的圖形重繪閃動](how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md)  
 示範如何使用雙重緩衝支援.NET Framework 中的預設值。  
  
 [如何：手動管理已緩衝的圖形](how-to-manually-manage-buffered-graphics.md)  
 示範如何管理應用程式中的雙重緩衝。  
  
 [如何：手動轉譯已緩衝的圖形](how-to-manually-render-buffered-graphics.md)  
 示範如何轉譯雙重緩衝的圖形。  
  
## <a name="reference"></a>參考資料  
 <xref:System.Windows.Forms.Control.SetStyle%2A> 啟用雙重緩衝處理的控制方法。  
  
 <xref:System.Drawing.BufferedGraphicsContext> 提供方法來建立圖形緩衝區。  
  
 <xref:System.Drawing.BufferedGraphicsManager>  
 提供應用程式定義域的存取權的已緩衝的圖形內容。
