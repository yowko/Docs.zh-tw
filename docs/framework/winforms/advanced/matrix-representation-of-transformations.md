---
title: 以矩陣來表示轉換
ms.date: 03/30/2017
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
ms.openlocfilehash: 24da407de24a924a68466e4301cc3f4a74cb2e94
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044244"
---
# <a name="matrix-representation-of-transformations"></a>以矩陣來表示轉換
M × n 矩陣是以 m 列和 n 個數據行排列的一組數位。 下圖顯示數個矩陣。  
  
 ![Transformations](./media/aboutgdip05-art04.gif "AboutGdip05_art04")  
  
 您可以藉由加入個別元素, 加入相同大小的兩個矩陣。 下圖顯示兩個矩陣加法的範例。  
  
 ![Transformations](./media/aboutgdip05-art05.gif "AboutGdip05_art05")  
  
 M × n 矩陣可以乘以 n × p 矩陣, 而結果則是 m × p 矩陣。 第一個矩陣中的資料行數目必須與第二個矩陣中的資料列數目相同。 例如, 4 ×2矩陣可以乘以2×3矩陣, 以產生4×3矩陣。  
  
 平面中的點和矩陣的資料列和資料行可以視為向量。 例如, (2, 5) 是包含兩個元件的向量, 而 (3, 7, 1) 是包含三個元件的向量。 兩個向量的點乘積定義如下:  
  
 (a, b) • (c, d) = ac + bd  
  
 (a、b、c) • (d, e, f) = ad + 是 + cf  
  
 例如, (2, 3) 和 (5, 4) 的點乘積為 (2) (5) + (3) (4) = 22。 (2, 5, 1) 和 (4, 3, 1) 的點乘積為 (2) (4) + (5) (3) + (1) (1) = 24。 請注意, 兩個向量的點乘積是一個數位, 而不是另一個向量。 另請注意, 只有當兩個向量具有相同數目的元件時, 您才可以計算網點乘積。  
  
 讓 (i, j) 成為第 i 個數據列和第 j 個數據行中 [矩陣 A] 的專案。 例如, (3, 2) 是第3列和第2個數據行之矩陣 A 中的專案。 假設 A、B 和 C 是矩陣, 而 AB = C。C 的專案計算方式如下:  
  
 C (i, j) = (資料列 i) • (B 的資料行 j)  
  
 下圖顯示數個矩陣乘法的範例。  
  
 ![Transformations](./media/aboutgdip05-art06.gif "AboutGdip05_art06")  
  
 如果您想要將平面中的某個點視為1×2矩陣, 可以將該點乘以2×2矩陣來進行轉換。 下圖顯示數個套用至點的轉換 (2, 1)。  
  
 ![Transformations](./media/aboutgdip05-art07.gif "AboutGdip05_art07")  
  
 上圖中顯示的所有轉換都是線性轉換。 某些其他轉換 (例如轉譯) 不是線性的, 而且無法以2×2矩陣的乘法表示。 假設您想要從點 (2, 1) 開始, 旋轉90度, 將 x 方向轉譯為3個單位, 然後在 y 方向轉譯為4個單位。 您可以使用矩陣乘法, 再加上矩陣加法來完成這項操作。  
  
 ![Transformations](./media/aboutgdip05-art08.gif "AboutGdip05_art08")  
  
 線性轉換 (乘以2×2矩陣) 後面接著平移 (加入1×2矩陣) 稱為「仿射」轉換。 另一個方法是在一對矩陣中儲存仿射轉換 (一個用於線性部分, 另一個用於轉譯), 是將整個轉換儲存在3×3矩陣中。 若要進行這項作業, 平面中的點必須儲存在具有虛擬3座標的1×3矩陣中。 一般的技巧是讓所有的第3個座標都等於1。 例如, 點 (2, 1) 是以矩陣 [2 1 1] 表示。 下圖顯示仿射轉換 (旋轉90度; 以 x 方向轉譯3個單位, y 方向為4個單位), 以乘單一3×3矩陣的方式來表示。  
  
 ![Transformations](./media/aboutgdip05-art09.gif "AboutGdip05_art09")  
  
 在上述範例中, 點 (2, 1) 會對應到點 (2, 6)。 請注意, 3 ×3矩陣的第三個數據行包含數位 0, 0, 1。 這一律是仿射轉換的3×3矩陣的情況。 重要數位是資料行1和2中的六個數字。 矩陣的左上2×2部分代表轉換的線性部分, 而第三個數據列中的前兩個專案代表轉譯。  
  
 ![Transformations](./media/aboutgdip05-art10.gif "AboutGdip05_art10")  
  
 在 gdi + 中, 您可以將仿射<xref:System.Drawing.Drawing2D.Matrix>轉換儲存在物件中。 因為代表仿射轉換之矩陣的第三個數據行一律是 (0, 0, 1), 所以您在建立<xref:System.Drawing.Drawing2D.Matrix>物件時, 只會在前兩個數據行中指定六個數字。 語句`Matrix myMatrix = new Matrix(0, 1, -1, 0, 3, 4)`會結構如上圖所示的矩陣。  
  
## <a name="composite-transformations"></a>複合轉換  
 複合轉換是一系列的轉換, 再接著另一個。 請考慮下列清單中的矩陣和轉換:  
  
|||  
|-|-|  
|矩陣 A|旋轉90度|  
|矩陣 B|以 x 方向的2因數來縮放|  
|矩陣 C|以 y 方向轉譯3個單位|  
  
 如果一開始是以矩陣 [2 1 1] 表示的點 (2, 1), 然後乘以 A、B、C, 則點 (2, 1) 會依照列出的順序進行三個轉換。  
  
 [2 1 1]ABC = [-2 5 1]  
  
 與其將複合轉換的三個部分儲存在三個不同的矩陣中, 您可以將 A、B 和 C 相乘, 以取得儲存整個複合轉換的單一3×3矩陣。 假設 ABC = D。然後乘以 D 的點會得到與點相乘的結果, 再乘以 B, 然後 C。  
  
 [2 1 1]D = [-2 5 1]  
  
 下圖顯示矩陣 A、B、C 和 D。  
  
 ![Transformations](./media/aboutgdip05-art12.gif "AboutGdip05_art12")  
  
 複合轉換的矩陣可以藉由乘以個別轉換矩陣來形成, 這表示任何仿射轉換的順序都可以儲存在單一<xref:System.Drawing.Drawing2D.Matrix>物件中。  
  
> [!CAUTION]
> 複合轉換的順序很重要。 在 [一般] 中, [旋轉]、[調整]、[轉譯] 和 [縮放] 不同, 然後旋轉, 然後平移。 同樣地, 矩陣乘法的順序也很重要。 一般來說, ABC 與 k 不同。  
  
 <xref:System.Drawing.Drawing2D.Matrix.RotateAt%2A> <xref:System.Drawing.Drawing2D.Matrix.Translate%2A> <xref:System.Drawing.Drawing2D.Matrix.Scale%2A> <xref:System.Drawing.Drawing2D.Matrix.Multiply%2A> <xref:System.Drawing.Drawing2D.Matrix.Shear%2A> <xref:System.Drawing.Drawing2D.Matrix.Rotate%2A>類別提供數種方法來建立複合轉換:、、、、和。 <xref:System.Drawing.Drawing2D.Matrix> 下列範例會建立複合轉換的矩陣, 其會先旋轉30度, 然後在 y 方向以2的因數來縮放, 然後在 x 方向轉譯5個單位:  
  
 [!code-csharp[System.Drawing.CoordinateSystems#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.CoordinateSystems#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#11)]  
  
 下圖顯示矩陣。  
  
 ![Transformations](./media/aboutgdip05-art13.gif "AboutGdip05_art13")  
  
## <a name="see-also"></a>另請參閱

- [座標系統和轉換](coordinate-systems-and-transformations.md)
- [使用 Managed GDI+ 中的轉換](using-transformations-in-managed-gdi.md)
