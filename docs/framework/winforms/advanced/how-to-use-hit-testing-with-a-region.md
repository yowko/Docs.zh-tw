---
title: 如何：使用區域的使用點擊測試
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [Windows Forms], using regions
- regions [Windows Forms], hit testing
ms.assetid: 3a4c07cb-a40a-4d14-ad35-008f531910a8
ms.openlocfilehash: 40297fada3d042aee8c317eb787de03662f86cfc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523078"
---
# <a name="how-to-use-hit-testing-with-a-region"></a>如何：使用區域的使用點擊測試
點擊測試的目的是要判斷游標是否在指定的物件，例如圖示或按鈕。  
  
## <a name="example"></a>範例  
 下列範例會建立所形成聯集兩個矩形區域的加號形狀的區域。 假設變數`point`保存最近點選位置。 程式碼會檢查以查看是否`point`加號形狀的區域中。 如果點位於區域 （點擊） 時，不透明的紅色筆刷填滿區域。 否則，區域填滿半透明的紅色筆刷。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.MiscLegacyTopics#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例設計是為搭配 Windows Form 使用所設計，而且需要 <xref:System.Windows.Forms.PaintEventArgs> `e`，這是 <xref:System.Windows.Forms.PaintEventHandler> 的參數。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Drawing.Region>  
 [GDI+ 中的區域](../../../../docs/framework/winforms/advanced/regions-in-gdi.md)  
 [操作說明：使用區域的裁剪](../../../../docs/framework/winforms/advanced/how-to-use-clipping-with-a-region.md)
