---
title: "以矩陣來表示轉換 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "仿射轉換"
  - "複合轉換"
  - "線性轉換"
  - "矩陣"
  - "轉換, 複合"
  - "轉換, 線性"
  - "轉換, 矩陣表示"
  - "轉換, 轉譯"
  - "矩陣表示中的轉譯"
  - "向量"
ms.assetid: 0659fe00-9e0c-41c4-9118-016f2404c905
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 以矩陣來表示轉換
m×n 矩陣是按照 m 資料列和 n 資料行排列的一組數字。  下圖將顯示幾種矩陣。  
  
 ![轉換](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art04.png "AboutGdip05\_art04")  
  
 您可以利用增加個別項目來加入兩個大小相同的矩陣。  下圖將顯示兩個矩陣加法範例。  
  
 ![轉換](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art05.png "AboutGdip05\_art05")  
  
 m×n 矩陣可乘以 n×p 矩陣，其產生的結果便為 m×p 矩陣。  第一個矩陣的資料行數目必須和第二個矩陣的資料列數目相同。  例如，4×2 矩陣可乘以 2×3 矩陣以產生 4×3 矩陣。  
  
 平面上的點和矩陣的資料列和資料行都可視為向量。  例如，\(2, 5\) 是具有兩個元件的向量，而 \(3, 7, 1\) 是具有三個元件的向量。  這兩種向量所產生的點的定義如下：  
  
 \(a, b\)•\(c, d\) \= ac \+ bd  
  
 \(a, b, c\)‧\(d, e, f\) \= ad \+ be \+ cf  
  
 例如，\(2, 3\) 和 \(5, 4\) 產生的點是 \(2\)\(5\) \+ \(3\)\(4\) \= 22。  \(2, 5, 1\) 和 \(4, 3, 1\) 產生的點是 \(2\)\(4\) \+ \(5\)\(3\) \+ \(1\)\(1\) \= 24。  請注意，這兩種向量所產生的點是數字，而非另一個向量。  此外，只有當這兩個向量擁有相同的元件數目時，您才可以計算產生的點數目。  
  
 假設 A\(i, j\) 是矩陣 A 第 i 個資料列和第 j 個資料行中的項目。  例如 A\(3, 2\) 是矩陣 A 第 3 個資料列和第 2 個資料行中的項目。  假設 A、B 和 C 都是矩陣，而 AB \= C。  C 項目的計算結果如下：  
  
 C\(i, j\) \= \(A 的第 i 個資料列\)‧\(B 的第 j 個資料行\)  
  
 下圖將顯示數個矩陣乘法的範例。  
  
 ![轉換](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art06.png "AboutGdip05\_art06")  
  
 如果將平面中的點視為 1×2 矩陣，您可以將該矩陣乘以 2×2 矩陣以進行轉換。  下圖將說明數個套用到點 \(2, 1\) 的轉換。  
  
 ![轉換](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art07.gif "AboutGdip05\_art07")  
  
 上圖所顯示的所有轉換皆為線性轉換。  特定其他轉換是非線性的，例如轉換 \(Translation\)，而且無法乘以 2×2 矩陣來表示。  假設您想要以點 \(2, 1\) 做為開始、將它旋轉 90 度、在 X 方向轉換 3 個單位和在 Y 方向轉換 4 個單位。  您可以使用矩陣加法之後的矩陣乘法來完成這項作業。  
  
 ![轉換](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art08.gif "AboutGdip05\_art08")  
  
 轉換 \(加上 1×2 矩陣\) 之後的線性轉換 \(乘以 2×2 矩陣\) 稱為仿射轉換 \(Affine Transformation\)。  另一種將仿射轉換儲存為矩陣組 \(其中一個做為線性部分，另一個做為轉換部分\) 的方法是將整個轉換儲存在 3×3 矩陣中。  若要執行這項工作，平面的其中一點必須以虛設的第三座標儲存於 1×3 矩陣中。  常用的技巧是讓所有第三座標都為 1。  例如，點 \(2, 1\) 便以矩陣 \[2 1 1\] 表示。  下圖將顯示仿射轉換 \(旋轉 90 度；在 X 方向轉換 3 個單位、在 Y 方向轉換 4 個單位\) 將乘以 3×3 矩陣來表示。  
  
 ![轉換](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art09.png "AboutGdip05\_art09")  
  
 上例中，點 \(2, 1\) 將對應到點 \(2, 6\)。  請注意，3×3 矩陣的第三個資料行包含數字 0, 0, 1。  仿射轉換的 3×3 矩陣一律都是這樣。  資料行 1 和 2 中的六個數字非常重要。  矩陣的左上 2×2 部分代表轉換的線性部分，而第三個資料列的前兩個項目則代表轉換。  
  
 ![轉換](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art10.gif "AboutGdip05\_art10")  
  
 在 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 中，您可以將仿射轉換儲存在 <xref:System.Drawing.Drawing2D.Matrix> 物件中。  由於用來表示仿射轉換的矩陣第三個資料行永遠為 \(0, 0, 1\)，因此在建立 <xref:System.Drawing.Drawing2D.Matrix> 物件時，您只能指定前兩個資料行中的六個數字。  `Matrix myMatrix = new Matrix(0, 1, -1, 0, 3, 4)` 陳述式建構上圖中顯示的矩陣。  
  
## 複合轉換  
 複合轉換是由轉換序列組成，其中序列會緊跟著另一個序列。  舉下表的矩陣和轉換為例：  
  
|||  
|-|-|  
|矩陣 A|旋轉 90 度|  
|矩陣 B|在 X 方向縮放 2 個係數|  
|矩陣 C|在 Y 方向轉換 3 個單位|  
  
 如果我們從點 \(2, 1\) 開始 \(以矩陣 \[2 1 1\] 代表\)，並且乘以 A，然後乘以 B，再乘以 C，則點 \(2, 1\) 將會依照列出的順序經歷三種轉換。  
  
 \[2 1 1\]ABC \= \[\-2 5 1\]  
  
 如果不想將複合轉換的三個部分儲存在三個個別的矩陣中，您可以同時乘以 A、B 和 C 以取得儲存整個複合轉換的單一 3×3 矩陣。  假設 ABC \= D。  任何一個點乘以 D 所得的結果都等於任何一個點乘以 A、然後 B、然後 C。  
  
 \[2 1 1\]D \= \[\-2 5 1\]  
  
 下圖將顯示矩陣 A、B、C 和 D。  
  
 ![轉換](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art12.png "AboutGdip05\_art12")  
  
 藉由乘以個別轉換矩陣可形成複合轉換的矩陣，這表示仿射轉換的任何序列都可以儲存在單一 <xref:System.Drawing.Drawing2D.Matrix> 物件中。  
  
> [!CAUTION]
>  複合轉換的順序非常重要。  通常，旋轉、然後縮放、然後轉換與縮放、然後旋轉、然後在轉換並不相同。  同樣的，矩陣乘法的順序也很重要。  一般而言，ABC 與 BAC 並不相同。  
  
 <xref:System.Drawing.Drawing2D.Matrix> 類別提供幾個方法，用來建置複合轉換：<xref:System.Drawing.Drawing2D.Matrix.Multiply%2A>、<xref:System.Drawing.Drawing2D.Matrix.Rotate%2A>、<xref:System.Drawing.Drawing2D.Matrix.RotateAt%2A>、<xref:System.Drawing.Drawing2D.Matrix.Scale%2A>、<xref:System.Drawing.Drawing2D.Matrix.Shear%2A> 和 <xref:System.Drawing.Drawing2D.Matrix.Translate%2A>。  下列範例建立複合轉換矩陣，它會先旋轉 30 度、然後在 Y 方向縮放 2 個係數，然後在 X 方向轉換 5 個單位：  
  
 [!code-csharp[System.Drawing.CoordinateSystems#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.CoordinateSystems#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#11)]  
  
 下列圖示將顯示該矩陣。  
  
 ![轉換](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art13.png "AboutGdip05\_art13")  
  
## 請參閱  
 [座標系統和轉換](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)   
 [使用 Managed GDI\+ 中的轉換](../../../../docs/framework/winforms/advanced/using-transformations-in-managed-gdi.md)