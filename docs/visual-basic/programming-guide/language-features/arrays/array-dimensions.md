---
title: Array Dimensions in Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- dimensions, arrays
- arrays [Visual Basic], dimensions
- arrays [Visual Basic], rectangular
- arrays [Visual Basic], rank
- rectangular arrays
- ranking, arrays
ms.assetid: 385e911b-18c1-4e98-9924-c6d279101dd9
ms.openlocfilehash: bbc9e523e9b74cf380c65135e7416f1feba01a2e
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512887"
---
# <a name="array-dimensions-in-visual-basic"></a>Array Dimensions in Visual Basic

*維度*是一種可以改變陣列元素規格的方向。 保存當月每一天之銷售總額的陣列, 有一個維度 (當月的第一天)。 每個月的銷售總額依部門保存的陣列有兩個維度 (部門編號和月份的日期)。 陣列所擁有的維度數目稱為其*次序*。

> [!NOTE]
> 您可以使用<xref:System.Array.Rank%2A>屬性來判斷陣列具有多少維度。

## <a name="working-with-dimensions"></a>使用維度

您可以為每個維度提供*索引*或注*標*, 藉以指定陣列的元素。 元素是從索引0到該維度的最高索引的每個維度的連續。

下圖顯示具有不同排名之陣列的概念結構。 圖例中的每個元素都會顯示存取它的索引值。 例如, 您可以藉由指定索引`(1, 0)`來存取二維陣列中第二個數據列的第一個元素。

![顯示一維陣列的圖表。](./media/array-dimensions/one-dimensional-array.gif)

![顯示二維陣列的圖表。](./media/array-dimensions/two-dimensional-array.gif)

![顯示三維陣列的圖表。](./media/array-dimensions/three-dimensional-array.gif)

### <a name="one-dimension"></a>一個維度

許多陣列只有一個維度, 例如每個年齡的人員人數。 唯一指定專案的需求是該元素持有計數的年齡。 因此, 這類陣列只會使用一個索引。 下列範例會宣告一個變數, 以保留*一維*的年齡計數陣列, 用於年齡0到120。

```vb
Dim ageCounts(120) As UInteger
```

### <a name="two-dimensions"></a>兩個維度

有些陣列有兩個維度, 例如校園上每個建築物的每個樓層的辦公室數目。 元素的規格需要建築物編號和樓層, 而且每個專案都包含該建築物和樓層的計算計數。 因此, 這類陣列會使用兩個索引。 下列範例會宣告一個變數, 以保存一維的 office 計數*陣列*, 適用于建築物0到 40, 而樓層0到5的一個。

```vb
Dim officeCounts(40, 5) As Byte
```

二維陣列也稱為「*矩形陣列*」。

### <a name="three-dimensions"></a>三個維度

幾個陣列有三個維度, 例如3d 空間中的值。 這類陣列使用三個索引, 在此案例中代表實體空間的 x、y 和 z 座標。 下列範例會宣告一個變數, 以在三維磁片區中的不同點上保留一維空氣溫度*陣列*。

```vb
Dim airTemperatures(99, 99, 24) As Single
```

### <a name="more-than-three-dimensions"></a>三個以上的維度

雖然陣列最多可以有32個維度, 但很少會有三個以上的大小。

> [!NOTE]
> 當您將維度新增至陣列時, 陣列所需的總儲存空間會大幅增加, 因此請小心使用多維陣列。

## <a name="using-different-dimensions"></a>使用不同的維度

假設您想要追蹤目前月份每天的銷售金額。 您可以宣告一維陣列, 其中包含31個元素, 每個月一天一個, 如下列範例所示。

```vb
Dim salesAmounts(30) As Double
```

現在假設您想要追蹤相同的資訊, 而不只是每個月的一天, 而且每個月都有。 您可以宣告具有12個數據列 (適用于月份) 和31個數據行 (代表天) 的二維陣列, 如下列範例所示。

```vb
Dim salesAmounts(11, 30) As Double
```

現在假設您決定讓陣列保存超過一年的資訊。 如果您想要追蹤5年的銷售量, 您可以宣告具有5個圖層、12個數據列和31個數據行的三維陣列, 如下列範例所示。

```vb
Dim salesAmounts(4, 11, 30) As Double
```

請注意, 因為每個索引的大小從0到最大值, `salesAmounts`所以的每個維度都會宣告為小於該維度所需的長度。 另請注意, 陣列的大小會隨著每個新的維度而增加。 上述範例中的三個大小分別為31、372和1860個元素。

> [!NOTE]
> 您可以建立陣列, 而不使用`Dim`語句`New`或子句。 例如, 您可以呼叫<xref:System.Array.CreateInstance%2A>方法, 或另一個元件可以將以這種方式建立的陣列傳遞給您的程式碼。 這類陣列可以具有小於0的下限。 您一律可以使用<xref:System.Array.GetLowerBound%2A>方法`LBound`或函數, 測試維度的下限。

## <a name="see-also"></a>另請參閱

- [陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [陣列的疑難排解](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
