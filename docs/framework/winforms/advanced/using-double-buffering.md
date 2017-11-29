---
title: "雙重緩衝的使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [Windows Forms], double buffering
- double buffering
- flicker [Windows Forms], reducing in Windows Forms
- buffering [Windows Forms], double buffering
ms.assetid: dc484e33-7101-4e4b-ada5-d3c96155fbcd
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b5ad51e27c3d31ece1d11831c953023bedba3a97
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="using-double-buffering"></a>雙重緩衝的使用
若要減少重繪閃動在包含複雜繪製作業的應用程式中，您可以使用雙重緩衝的圖形。 .NET Framework 包含雙重緩衝的內建支援，或您可以管理，並手動呈現圖形。  
  
## <a name="in-this-section"></a>本章節內容  
 [雙重緩衝的圖形](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)  
 導入了雙重緩衝概念和大綱.NET Framework 支援。  
  
 [操作說明：使用表單和控制項的雙重緩衝以減少圖形閃爍](../../../../docs/framework/winforms/advanced/how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md)  
 示範如何使用雙重緩衝支援.NET Framework 中的預設值。  
  
 [操作說明：手動管理已緩衝的圖形](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md)  
 示範如何管理應用程式中的雙重緩衝。  
  
 [操作說明：手動轉譯已緩衝的圖形](../../../../docs/framework/winforms/advanced/how-to-manually-render-buffered-graphics.md)  
 示範如何轉譯雙重緩衝的圖形。  
  
## <a name="reference"></a>參考資料  
 <xref:System.Windows.Forms.Control.SetStyle%2A> ,  
 控制項可讓雙重緩衝的方法。  
  
 <xref:System.Drawing.BufferedGraphicsContext> ,  
 提供方法來建立圖形緩衝區。  
  
 <xref:System.Drawing.BufferedGraphicsManager>  
 提供應用程式定義域已緩衝的圖形內容的存取。
