---
title: 作法：建立繫結控制項並格式化顯示的資料
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], formatting
- bound controls [Windows Forms], creating
- bound controls [Windows Forms], formatting data
ms.assetid: d5a56228-899d-41d9-8af8-87b3f4ec2f94
ms.openlocfilehash: 052e619acb23fb2e25f42daf7b4eaaacb0688f31
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039430"
---
# <a name="how-to-create-a-bound-control-and-format-the-displayed-data"></a>HOW TO：建立繫結控制項並格式化顯示的資料

藉由 Windows Forms 資料系結, 您可以使用 [**格式化] 和 [高級**系結] 對話方塊來格式化資料繫結控制項中顯示的資料。


### <a name="to-bind-a-control-and-format-the-displayed-data"></a>繫結控制項並格式化顯示的資料

1. 連接至資料來源。

     如需詳細資訊, 請參閱[連接到資料來源](../data/adonet/connecting-to-a-data-source.md)。

2. 在表單中選取控制項，然後開啟屬性視窗。

3. 展開 [ **(** 系結)] 屬性, 然後在 [ **(Advanced)** ] 方塊中, 按一下省略號![按鈕 (屬性視窗](./media/how-to-create-a-bound-control-and-format-the-displayed-data/visual-studio-ellipsis-button.png)中 Visual Studio 的省略號按鈕 (...)) 以顯示**格式設定和 [高級]** [系結] 對話方塊, 其中包含該控制項的完整屬性清單。

4. 選取您要系結的屬性, 然後按一下 [系結] 箭號。

     會顯示可用資料來源清單。

5. 展開您想要繫結的資料來源，直到您找到您要的單一資料項目。

     例如，如果您要在資料集資料表中繫結資料行值，展開資料集的名稱，然後展開資料表名稱來顯示資料行名稱。

6. 按一下要繫結項目的名稱。

7. 在 [**格式類型**] 方塊中, 按一下您要套用至控制項中所顯示之資料的格式。

     在所有情況下，如果資料來源包含 <xref:System.DBNull>，則您可以指定顯示在控制項中的值。 否則，選項會稍微不同，視您所選擇的格式類型而定。 下列表格顯示格式類型和選項。

    |格式類型|格式化選項|
    |-----------------|-----------------------|
    |沒有格式化|沒有選項。|
    |數值|使用 [**小**數位數] 上下按鈕控制項來指定小數點位數。|
    |貨幣|使用 [**小**數位數] 上下按鈕控制項來指定小數點位數。|
    |日期時間|選取 [**類型**] 選取方塊中的其中一個專案, 以選取應如何顯示日期和時間。|
    |科學記號|使用 [**小**數位數] 上下按鈕控制項來指定小數點位數。|
    |自訂|指定使用自訂格式字串。<br /><br /> 如需詳細資訊，請參閱[格式類型](../../standard/base-types/formatting-types.md)。 **注意：** 自訂格式字串不保證能成功地在資料來源和繫結的控制項之間反覆存取。 改為處理 <xref:System.Windows.Forms.Binding.Parse> 或 <xref:System.Windows.Forms.Binding.Format> 繫結的事件，以及在事件處理程式碼中套用自訂格式。|

8. 按一下 **[確定]** 關閉 [**格式化和高級**系結] 對話方塊, 並返回屬性視窗。

## <a name="see-also"></a>另請參閱

- [如何：在 Windows Form 上建立簡單繫結控制項](how-to-create-a-simple-bound-control-on-a-windows-form.md)
- [Windows Forms 中的使用者輸入驗證](user-input-validation-in-windows-forms.md)
- [Windows Forms 資料繫結](windows-forms-data-binding.md)
