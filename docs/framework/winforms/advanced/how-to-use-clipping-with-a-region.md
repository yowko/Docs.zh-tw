---
title: HOW TO：使用區域的裁剪部分
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regions [Windows Forms], clipping
- regions [Windows Forms], restricting drawing surface
ms.assetid: 43d121b4-e14c-4901-b25c-2d6c25ba4e29
ms.openlocfilehash: 5482218a8d6310ce49a1f9f5f02b3b8e36c1fd90
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54590652"
---
# <a name="how-to-use-clipping-with-a-region"></a>HOW TO：使用區域的裁剪部分
其中一個屬性的<xref:System.Drawing.Graphics>類別是裁剪區域。 所有的繪圖，即可指定<xref:System.Drawing.Graphics>物件僅限於的裁剪區域<xref:System.Drawing.Graphics>物件。 您可以藉由呼叫設定的裁剪區域<xref:System.Drawing.Graphics.SetClip%2A>方法。  
  
## <a name="example"></a>範例  
 下列範例會建構單一多邊形所組成的路徑。 然後程式碼會建構一個地區，根據該路徑。 區域會傳遞至<xref:System.Drawing.Graphics.SetClip%2A>方法的<xref:System.Drawing.Graphics>繪製物件，並接著兩個字串。  
  
 下圖顯示裁剪的字串。  
  
 ![Clip](../../../../docs/framework/winforms/advanced/media/clip1.png "clip1")  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.MiscLegacyTopics#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例設計是為搭配 Windows Form 使用所設計，而且需要 <xref:System.Windows.Forms.PaintEventArgs> `e`，這是 <xref:System.Windows.Forms.PaintEventHandler> 的參數。  
  
## <a name="see-also"></a>另請參閱
- [GDI+ 中的區域](../../../../docs/framework/winforms/advanced/regions-in-gdi.md)
- [使用區域](../../../../docs/framework/winforms/advanced/using-regions.md)
