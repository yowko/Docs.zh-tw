---
title: "以矩陣來表示轉換"
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
- composite transformations
- transformations [Windows Forms], linear
- matrices
- translations in matrix representation
- transformations [Windows Forms], composite
- vectors
- linear transformations
- transformations [Windows Forms], matrix representation of
- transformations [Windows Forms], translation
- affine transformations
ms.assetid: 0659fe00-9e0c-41c4-9118-016f2404c905
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 10babac22fd94bd00b14b7f861fe99469d3ecbda
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="matrix-representation-of-transformations"></a>以矩陣來表示轉換
M × n 矩陣是一組數字中的資料列 m 和 n 個資料行排列。 下圖將顯示數個矩陣。  
  
 ![轉換](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art04.gif "AboutGdip05_art04")  
  
 您可以將個別項目加入相同大小的兩個矩陣。 下圖顯示兩個矩陣加法的範例。  
  
 ![轉換](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art05.gif "AboutGdip05_art05")  
  
 M × n 矩陣會乘以 n × p 矩陣，且結果為 m × p 矩陣。 第一個矩陣中的資料行數目必須是第二個矩陣中的資料列數目相同。 例如，一個 4 × 2 矩陣可以乘以 2 × 3 矩陣產生 4 × 3 的矩陣。  
  
 平面及資料列和資料行的矩陣中的點可以視為向量。 例如，（2，5） 是具有兩個元件的向量和 （3，7，1） 是具有三個元件的向量。 兩個向量的內積定義如下：  
  
 (a、 b） • (c，d) = ac + bd  
  
 (a、 b、 c） • （d，e，f） = ad + 是 + cf  
  
 例如，積 （2，3） 和 （5，4） 是 (2)(5) + (3)(4) = 22。 （2，5，1） 的內積和 （4，3，1） 是 (2)(4) + (5)(3) + (1)(1) = 24。 請注意，兩個向量的內積的數字，不另一個向量。 也請注意，只有當兩個向量擁有相同數目的元件，您可以計算的內積。  
  
 可讓 A(i, j) 是矩陣的第 i 資料列和第 j 個資料行中的項目。 如需範例 A （3，2） 是矩陣的第 3 個資料列和第 2 個資料行中的項目。 假設有 A、 B 和 C 是矩陣和 AB = c。C 的項目計算方式如下：  
  
 C （i，j） = （資料列 i A） • （資料行 j B）  
  
 下圖顯示矩陣乘法的數個範例。  
  
 ![轉換](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art06.gif "AboutGdip05_art06")  
  
 如果您認為 1 × 2 矩陣形式平面中的點，您可以藉由將它乘以 2 × 2 矩陣轉換該點。 下圖顯示套用至點 （2，1） 的幾個轉換。  
  
 ![轉換](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art07.gif "AboutGdip05_art07")  
  
 上圖所示的轉換均線性轉換。 某些其他轉換，例如轉譯，不會線性的而且不能表示為乘以 2 × 2 矩陣。 假設您想要開始使用點 （2，1） 旋轉 90 度、 轉換 x 方向的 3 個單位，翻譯 y 方向的 4 個單位。 您可以使用後面的矩陣新增矩陣乘法來完成這項作業。  
  
 ![轉換](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art08.gif "AboutGdip05_art08")  
  
 線性轉換 （由 2 × 2 矩陣乘法） 後面接著轉換 （1 × 2 矩陣） 會呼叫仿射轉換。 儲存仿射轉換矩陣 （一個為線性的一部分），做為轉換的一組中的替代方式是將整個轉換 3 × 3 矩陣中。 若要讓這項工作，在平面的點必須儲存在 1 × 3 包含矩陣 dummy 第 3 個座標。 常用的技巧是讓第 3 個座標都等於 1。 例如，點 （2，1） 會以矩陣 [2 1 1]。 下圖顯示仿射轉換 （旋轉 90 度; 轉換 x 方向的 3 個單位，在 y 方向的 4 個單位） 以乘以 3 × 3 矩陣。  
  
 ![轉換](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art09.gif "AboutGdip05_art09")  
  
 在上述範例中，點 （2，1） 被對應到 （2，6） 的點。 請注意 3 × 3 矩陣的第三個資料行包含數字 0，0，1。 這一律會是 3 × 3 矩陣仿射轉換的情況。 重要的數字是六個資料行 1 和 2 中的數字。 矩陣的左上方 2 × 2 部分代表線性轉換的部分和第 3 個資料列中的前兩個項目代表轉譯。  
  
 ![轉換](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art10.gif "AboutGdip05_art10")  
  
 在[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]，您可以儲存在仿射轉換<xref:System.Drawing.Drawing2D.Matrix>物件。 因為代表仿射轉換矩陣的第三個資料行一律是 （0，0，1），在建構時，在前兩個資料行中指定的六個數字<xref:System.Drawing.Drawing2D.Matrix>物件。 陳述式`Matrix myMatrix = new Matrix(0, 1, -1, 0, 3, 4)`建構上圖所示的矩陣。  
  
## <a name="composite-transformations"></a>複合轉換  
 複合轉換是一串轉換，後面接著另一個。 請考慮下列清單中的轉換與矩陣：  
  
|||  
|-|-|  
|矩陣 A|旋轉 90 度|  
|矩陣 B|在 x 方向的 2 倍縮放|  
|矩陣 C|轉換在 y 方向的 3 個單位|  
  
 如果我們開始點 （2，1） — 矩陣 [2 1 1] 表示的 — 乘以 A，然後 B，則 C 中，點 （2，1） 將會進行三種轉換中列出的順序。  
  
 [2 1 1]ABC = [1-2 5]  
  
 而是比儲存在三個個別的矩陣中的複合轉換的三個部分，您可以將 A、 B 和 C 取得儲存整個複合轉換的單一 3 × 3 矩陣。 假設 ABC = d。然後乘以 D 點會給予發生相同的結果為點乘以 A，然後 B，然後 c。  
  
 [2 1 1]D = [1-2 5]  
  
 下圖顯示矩陣 A、 B、 C 和 d。  
  
 ![轉換](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art12.gif "AboutGdip05_art12")  
  
 可以在個別的轉換矩陣乘以格式正確的複合的轉換矩陣的事實表示仿射轉換的任何序列，可以儲存在單一<xref:System.Drawing.Drawing2D.Matrix>物件。  
  
> [!CAUTION]
>  複合轉換順序很重要。 一般情況下，旋轉，再調整，然後轉換並不相同為小數位數，然後旋轉、，然後轉換。 同樣地，矩陣乘法的順序很重要。 一般情況下，ABC 不是不相同。  
  
 <xref:System.Drawing.Drawing2D.Matrix>類別提供數種方法來建立複合的轉換： <xref:System.Drawing.Drawing2D.Matrix.Multiply%2A>， <xref:System.Drawing.Drawing2D.Matrix.Rotate%2A>， <xref:System.Drawing.Drawing2D.Matrix.RotateAt%2A>， <xref:System.Drawing.Drawing2D.Matrix.Scale%2A>， <xref:System.Drawing.Drawing2D.Matrix.Shear%2A>，和<xref:System.Drawing.Drawing2D.Matrix.Translate%2A>。 下列範例會建立先旋轉 30 度，則 y 方向的 2 倍縮放並再將轉譯 x 方向的 5 個單位的複合轉換的矩陣：  
  
 [!code-csharp[System.Drawing.CoordinateSystems#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.CoordinateSystems#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#11)]  
  
 下圖顯示矩陣。  
  
 ![轉換](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art13.gif "AboutGdip05_art13")  
  
## <a name="see-also"></a>另請參閱  
 [座標系統和轉換](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)  
 [使用 Managed GDI+ 中的轉換](../../../../docs/framework/winforms/advanced/using-transformations-in-managed-gdi.md)
