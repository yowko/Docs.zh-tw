---
title: HOW TO：使用點擊測試的區域
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [Windows Forms], using regions
- regions [Windows Forms], hit testing
ms.assetid: 3a4c07cb-a40a-4d14-ad35-008f531910a8
ms.openlocfilehash: a9435724e7674fd196ad70bdfd0ab43808a53058
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57709740"
---
# <a name="how-to-use-hit-testing-with-a-region"></a>HOW TO：使用點擊測試的區域
點擊測試的目的是要判斷游標是否位在指定的物件，例如圖示或按鈕。  
  
## <a name="example"></a>範例  
 下列範例會形成兩個矩形區域的聯集，以建立加號形狀的區域。 假設變數`point`保留最新的按一下的位置。 程式碼會檢查是否`point`plus 形狀的區域中。 重點是在區域 （點擊） 中，如果不透明的紅色筆刷填滿區域。 否則，區域填滿半透明的紅色筆刷。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.MiscLegacyTopics#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例設計是為搭配 Windows Form 使用所設計，而且需要 <xref:System.Windows.Forms.PaintEventArgs> `e`，這是 <xref:System.Windows.Forms.PaintEventHandler> 的參數。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Drawing.Region>
- [GDI+ 中的區域](regions-in-gdi.md)
- [如何：使用區域的裁剪部分](how-to-use-clipping-with-a-region.md)
