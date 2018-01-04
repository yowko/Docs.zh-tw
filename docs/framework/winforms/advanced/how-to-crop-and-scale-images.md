---
title: "如何：裁剪和縮放影像"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], cropping
- images [Windows Forms], scaling
ms.assetid: 053e3360-bca0-4b25-9afa-0e77a6f17b03
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: de905cf70013098a4282e3f4af092ccbea16ccfd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-crop-and-scale-images"></a>如何：裁剪和縮放影像
<xref:System.Drawing.Graphics>類別提供幾種<xref:System.Drawing.Graphics.DrawImage%2A>方法，其中有些具有來源和目的地矩形參數可用來裁剪和縮放影像。  
  
## <a name="example"></a>範例  
 下列範例會建構<xref:System.Drawing.Image>從磁碟檔案 Apple.gif 物件。 程式碼會在其原始大小繪製整個 apple 映像。 然後程式碼會呼叫<xref:System.Drawing.Graphics.DrawImage%2A>方法<xref:System.Drawing.Graphics>apple 映像的一部分繪製大於原始 apple 映像的目的地矩形的物件。  
  
 <xref:System.Drawing.Graphics.DrawImage%2A>方法會判斷藉由查看來源矩形中，第四個，指定第三個、 第 5 個和第六個引數，讓 apple 的哪一部分。 在此情況下，將 apple 裁剪成 75%的寬度和高度的 75%。  
  
 <xref:System.Drawing.Graphics.DrawImage%2A>方法會判斷繪製裁剪的 apple 位置和大小，以便進行裁剪的 apple 查看目的矩形，也就是第二個引數所指定。 在此情況下，目的地矩形是較寬的 30%，而 30%高於原始映像。  
  
 下圖顯示原始 apple 和縮放裁剪 apple。  
  
 ![裁剪 & 縮放](../../../../docs/framework/winforms/advanced/media/cscropscale1.png "csCropScale1")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.WorkingWithImages#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例是為了搭配 Windows Form 使用而設計，且其需要 <xref:System.Windows.Forms.PaintEventArgs> `e`，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。 請務必取代`Apple.gif`映像檔案名稱與您系統為有效的路徑。  
  
## <a name="see-also"></a>請參閱  
 [影像、點陣圖和中繼檔](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [使用影像、點陣圖、圖示和中繼檔](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
