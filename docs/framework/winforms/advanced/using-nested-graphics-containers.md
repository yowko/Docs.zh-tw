---
title: "使用巢狀圖形容器"
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
- graphics [Windows Forms], nested containers
- graphics [Windows Forms], clipping
- graphics [Windows Forms], transformations in nested objects
ms.assetid: a0d9f178-43a4-4323-bb5a-d3e3f77ae6c1
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 512c8903611f025364a1af2cb6cbaaffc8d759eb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="using-nested-graphics-containers"></a>使用巢狀圖形容器
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]提供可用來暫時取代或擴充部分的狀態中的容器<xref:System.Drawing.Graphics>物件。 您可以建立一個容器呼叫<xref:System.Drawing.Graphics.BeginContainer%2A>方法<xref:System.Drawing.Graphics>物件。 您可以呼叫<xref:System.Drawing.Graphics.BeginContainer%2A>重複，以形成巢狀的容器。 每次呼叫<xref:System.Drawing.Graphics.BeginContainer%2A>必須搭配呼叫<xref:System.Drawing.Graphics.EndContainer%2A>。  
  
## <a name="transformations-in-nested-containers"></a>巢狀容器中的轉換  
 下列範例會建立<xref:System.Drawing.Graphics>物件和容器內的<xref:System.Drawing.Graphics>物件。 自然變換<xref:System.Drawing.Graphics>物件是在 x 方向轉譯 100 單位而 80 y 方向的單位。 容器的自然變換是 30 度旋轉。 程式碼會呼叫`DrawRectangle(pen, -60, -30, 120, 60)`兩次。 第一次呼叫<xref:System.Drawing.Graphics.DrawRectangle%2A>位於容器; 亦即，呼叫是對呼叫之間<xref:System.Drawing.Graphics.BeginContainer%2A>和<xref:System.Drawing.Graphics.EndContainer%2A>。 第二個呼叫<xref:System.Drawing.Graphics.DrawRectangle%2A>之後呼叫<xref:System.Drawing.Graphics.EndContainer%2A>。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.MiscLegacyTopics#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#61)]  
  
 在上述程式碼中，從容器內繪製的矩形會轉換先依容器 （輪替） 的自然變換和的自然變換<xref:System.Drawing.Graphics>物件 （轉譯）。 從容器之外繪製的矩形會轉換只能由的自然變換<xref:System.Drawing.Graphics>物件 （轉譯）。 下圖顯示兩個矩形。  
  
 ![巢狀容器](../../../../docs/framework/winforms/advanced/media/csnestedcontainers1.png "csnestedcontainers1")  
  
## <a name="clipping-in-nested-containers"></a>巢狀容器中的裁剪功能  
 下列範例會示範如何巢狀的容器處理裁剪區域。 程式碼會建立<xref:System.Drawing.Graphics>物件和容器內的<xref:System.Drawing.Graphics>物件。 裁剪區域<xref:System.Drawing.Graphics>物件是一個矩形，而容器的裁剪區域是橢圓形。 程式碼，使兩個呼叫<xref:System.Drawing.Graphics.DrawLine%2A>方法。 第一次呼叫<xref:System.Drawing.Graphics.DrawLine%2A>位於容器中，且第二個呼叫<xref:System.Drawing.Graphics.DrawLine%2A>超出容器 (在呼叫之後<xref:System.Drawing.Graphics.EndContainer%2A>)。 第一行會遭到裁剪，由兩個的裁剪區域的交集。 第二行只會裁剪矩形的裁剪區域<xref:System.Drawing.Graphics>物件。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#62](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#62)]
 [!code-vb[System.Drawing.MiscLegacyTopics#62](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#62)]  
  
 下圖顯示兩個裁剪的線條。  
  
 ![巢狀容器](../../../../docs/framework/winforms/advanced/media/nestedcontainers2.png "nestedcontainers2")  
  
 如上述兩個範例所示，轉換和裁剪區域是累計巢狀容器中。 如果您將容器的全局轉換和<xref:System.Drawing.Graphics>物件，這兩種轉換會套用至繪製從容器內的項目。 容器的轉換會套用第一個，並轉換<xref:System.Drawing.Graphics>物件將會套用第二個。 如果您將容器的裁剪區域和<xref:System.Drawing.Graphics>物件，在兩個裁剪區域的交集會裁剪繪製從容器內的項目。  
  
## <a name="quality-settings-in-nested-containers"></a>巢狀容器中的品質設定  
 品質設定 (<xref:System.Drawing.Graphics.SmoothingMode%2A>， <xref:System.Drawing.Graphics.TextRenderingHint%2A>，等等) 中巢狀的容器並不會累計; 相反地，容器的品質設定暫時取代的品質設定<xref:System.Drawing.Graphics>物件。 當您建立新的容器時，該容器的品質設定會設定為預設值。 例如，假設您有<xref:System.Drawing.Graphics>平滑化模式的物件<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>。 當您建立一個容器時，容器內的平滑化模式是預設的平滑化模式。 您可以自由地設定平滑模式的容器，並繪製從容器內的任何項目會繪製根據您設定的模式。 繪製呼叫之後的項目<xref:System.Drawing.Graphics.EndContainer%2A>會繪製平滑模式根據 (<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>) 的已備妥的呼叫之前<xref:System.Drawing.Graphics.BeginContainer%2A>。  
  
## <a name="several-layers-of-nested-containers"></a>數個層級的巢狀容器  
 您並不限於一個容器中<xref:System.Drawing.Graphics>物件。 您可以建立一連串的容器、 每個巢狀方式置於前面，和您可以指定全局轉換、 裁剪區域和每個巢狀容器的品質設定。 如果您呼叫最內層的容器中的繪圖方法時，會將轉換套用順序，與最內層的容器開始和結束與最外層的容器。 所有的裁剪區域的交集會裁剪取自最內層的容器項目。  
  
 下列範例會建立<xref:System.Drawing.Graphics>物件，並將其文字呈現提示設定為<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>。 程式碼會建立兩個容器，其中巢狀方式置於另一個。 外部容器的文字呈現提示設定為<xref:System.Drawing.Text.TextRenderingHint.SingleBitPerPixel>，而且文字呈現提示的內部的容器設定為<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>。 程式碼繪製三個字串： 從內部的容器，一個是從外部的容器，從<xref:System.Drawing.Graphics>物件本身。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#63](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#63)]
 [!code-vb[System.Drawing.MiscLegacyTopics#63](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#63)]  
  
 下圖顯示三個字串。 繪製從內部的容器以及字串<xref:System.Drawing.Graphics>平滑的反鋸齒功能的物件。 因為取自外部容器的字串不由消除鋸齒平滑<xref:System.Drawing.Graphics.TextRenderingHint%2A>屬性設定為<xref:System.Drawing.Text.TextRenderingHint.SingleBitPerPixel>。  
  
 ![巢狀容器](../../../../docs/framework/winforms/advanced/media/nestedcontainers3.png "nestedcontainers3")  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Drawing.Graphics>  
 [管理圖形物件的狀態](../../../../docs/framework/winforms/advanced/managing-the-state-of-a-graphics-object.md)
