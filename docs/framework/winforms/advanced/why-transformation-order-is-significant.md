---
title: 為何轉換順序很重要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- transformations [Windows Forms], order significance
ms.assetid: 37d5f9dc-a5cf-4475-aa5d-34d714e808a9
ms.openlocfilehash: 9fd0764e3e3754fbbaa16441737e0463db3f99a0
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57503173"
---
# <a name="why-transformation-order-is-significant"></a>為何轉換順序很重要

單一<xref:System.Drawing.Drawing2D.Matrix>物件可用來儲存單一轉換的序列。 後者稱為 「 複合 」 轉換。 複合轉換矩陣被取得個別轉換的矩陣相乘。

## <a name="composite-transform-examples"></a>複合轉換範例

在複合的轉換中，個別轉換的順序很重要的。 例如，如果先旋轉，再調整，然後轉譯，得到不同的結果比先轉換再旋轉，然後調整。 在  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]，複合轉換是從左到右。 如果 S、 R 和 T 分別調整、 旋轉和轉譯矩陣，然後產品 SRT （依此順序） 調整規模的第一個是 「 複合 」 轉換的矩陣、 旋轉，然後將轉譯。 該產品所產生的矩陣 SRT 是不同於產品 TRS 所產生的矩陣。

順序很重要的其中一個原因是，例如旋轉和縮放轉換會完成方面座標系統的原點。 縮放中心位於原點的物件產生不同的結果調整已離開來源的物件。 同樣地，旋轉的中心位於原點的物件所產生的旋轉物件已移動離開來源不同的結果。

下列範例會結合以形成複合的轉換縮放、 旋轉和平移 （依此順序）。 引數<xref:System.Drawing.Drawing2D.MatrixOrder.Append>傳遞至<xref:System.Drawing.Graphics.RotateTransform%2A>方法表示旋轉會遵循的縮放比例。 同樣地，引數<xref:System.Drawing.Drawing2D.MatrixOrder.Append>傳遞至<xref:System.Drawing.Graphics.TranslateTransform%2A>方法表示轉譯會遵循旋轉。 <xref:System.Drawing.Drawing2D.MatrixOrder.Append> 並<xref:System.Drawing.Drawing2D.MatrixOrder.Prepend>屬於<xref:System.Drawing.Drawing2D.MatrixOrder>列舉型別。

[!code-csharp[System.Drawing.MiscLegacyTopics#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#21)]
[!code-vb[System.Drawing.MiscLegacyTopics#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#21)]

下列範例會進行相同的方法呼叫，如同上述範例中，但呼叫的順序相反。 產生作業的順序先轉換、 然後旋轉、 縮放比例，會產生第一個標尺非常不同的結果，然後旋轉，然後再轉譯。

[!code-csharp[System.Drawing.MiscLegacyTopics#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#22)]
[!code-vb[System.Drawing.MiscLegacyTopics#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#22)]

複合轉換中的個別轉換的順序相反的方法之一是一系列的方法呼叫的順序相反。 控制作業的順序的第二個方式是變更矩陣的 order 引數。 下列範例等同於上述範例中，不同之處在於<xref:System.Drawing.Drawing2D.MatrixOrder.Append>已變更為<xref:System.Drawing.Drawing2D.MatrixOrder.Prepend>。 SRT，其中 S、 R、 T 縮放、 旋轉的矩陣和是分別轉譯順序是矩陣相乘。 複合轉換的順序是第一個標尺，然後旋轉，然後轉譯。

[!code-csharp[System.Drawing.MiscLegacyTopics#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#23)]
[!code-vb[System.Drawing.MiscLegacyTopics#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#23)]

前一個範例的結果會是相同本主題中的第一個範例的結果。 這是因為我們反轉方法呼叫的順序和矩陣相乘的順序。

## <a name="see-also"></a>另請參閱

- <xref:System.Drawing.Drawing2D.Matrix>
- [座標系統和轉換](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)
- [使用 Managed GDI+ 中的轉換](../../../../docs/framework/winforms/advanced/using-transformations-in-managed-gdi.md)
