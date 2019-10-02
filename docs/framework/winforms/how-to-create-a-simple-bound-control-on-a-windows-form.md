---
title: 作法：在 Windows Form 上建立簡單繫結控制項
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [Windows Forms], simple data binding
- Windows Forms controls, data binding
ms.assetid: 3bcaded8-0f1a-4cc0-8830-f59be253bf4e
ms.openlocfilehash: df87f00e6e03de67c3fb1adc28472c96f4a47ef4
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015637"
---
# <a name="how-to-create-a-simple-bound-control-on-a-windows-form"></a>HOW TO：在 Windows Form 上建立簡單繫結控制項

使用*簡單*系結, 您可以在控制項中顯示單一資料元素, 例如資料集資料表中的資料行值。 您可以簡單地將控制項的任何屬性系結至資料值。

## <a name="to-simple-bind-a-control"></a>簡單-系結控制項

1. 連接至資料來源。 如需詳細資訊, 請參閱[連接到資料來源](../data/adonet/connecting-to-a-data-source.md)。

2. 在 Visual Studio 中, 選取表單上的控制項, 並顯示 [**屬性**] 視窗。

3. 展開 [ **(** 系結)] 屬性。

     最常系結的屬性會顯示在 [(系結 **)** ] 屬性底下。 例如, 在大部分的控制項中, **Text**屬性最常系結。

4. 如果您要系結的屬性不是其中一個常用的屬性, 請按一下 [ **(Advanced)** ] 方塊中的](./media/how-to-create-a-simple-bound-control-on-a-windows-form/visual-studio-ellipsis-button.png)**省略號**按鈕 (![屬性視窗中 Visual Studio 的省略號按鈕 (...), 以顯示 **[格式化] 和 [Advanced Binding** ] 對話方塊, 其中包含該控制項的完整屬性清單。

5. 選取您想要系結的屬性, 然後按一下 [系結]底下的下拉箭號。

     會顯示可用資料來源清單。

6. 展開您想要繫結的資料來源，直到您找到您要的單一資料項目。 例如，如果您要在資料集資料表中繫結資料行值，展開資料集的名稱，然後展開資料表名稱來顯示資料行名稱。

7. 按一下要繫結項目的名稱。

8. 如果您是在 [**格式化和 Advanced Binding** ] 對話方塊中工作, 請按一下 **[確定**] 以返回 [**屬性**] 視窗。

9. 如果您想要系結控制項的其他屬性, 請重複步驟3到7。

    > [!NOTE]
    > 由於簡單繫結控制項只會顯示單一資料元素, 因此通常會將導覽邏輯包含在具有簡單繫結控制項的 Windows Form 中。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Binding>
- [Windows Forms 資料繫結](windows-forms-data-binding.md)
- [資料繫結和 Windows Forms](data-binding-and-windows-forms.md)
