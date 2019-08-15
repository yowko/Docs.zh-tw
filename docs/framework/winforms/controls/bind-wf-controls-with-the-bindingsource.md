---
title: 作法：使用設計工具繫結 Windows Forms 控制項和 BindingSource 元件
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], binding
- BindingSource component [Windows Forms], binding controls
- data binding [Windows Forms], BindingSource component
ms.assetid: 391ae170-de5c-40f8-8233-91cb2ee4683a
ms.openlocfilehash: 180fafa9ace5927fd84ec5dc0a1b2a342f771efd
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040023"
---
# <a name="how-to-bind-windows-forms-controls-with-the-bindingsource-component-using-the-designer"></a>作法：使用設計工具繫結 Windows Forms 控制項和 BindingSource 元件
將控制項新增至表單並決定應用程式的使用者介面之後, 您可以將控制項系結至資料來源, 以便在執行時間, 使用者可以改變和儲存與應用程式相關的資料。

 在 Windows Forms 中系結控制項或一系列控制項, 最容易就能<xref:System.Windows.Forms.BindingSource>使用控制項做為表單上的控制項和資料來源之間的橋樑。

 表單上的一或多個控制項可以系結至資料;在下列程式中, <xref:System.Windows.Forms.TextBox>控制項系結至資料來源。

 若要完成此程式, 假設您將系結至衍生自資料庫的資料來源。 如需從其他資料存放區建立資料來源的詳細資訊, 請參閱[加入新的資料來源](/visualstudio/data-tools/add-new-data-sources)。

## <a name="to-bind-a-control-at-design-time"></a>若要在設計階段系結控制項

1. <xref:System.Windows.Forms.TextBox>將控制項拖曳至表單。

2. 在 [**屬性**] 視窗中:

    1. 展開 [ **(** 系結)] 節點。

    2. 按一下<xref:System.Windows.Forms.TextBox.Text%2A>屬性旁的箭號。

         [ **DataSource** UI 類型編輯器] 隨即開啟。

         如果先前已設定專案或表單的資料來源, 就會出現。

3. 按一下 [新增專案資料來源] 以連接至資料，並建立資料來源。

4. 在 [資料來源組態精靈] 歡迎頁面上，按 [下一步]。

5. 在 [**選擇資料來源類型**] 頁面上, 選取 [**資料庫**]。

6. 在 [**選擇您的資料連線**] 頁面上, 從可用的連接清單中選取資料連線。 如果您想要的資料連線無法使用, 請選取 [**新增連接**] 來建立新的資料連線。

7. 選取 [**是, 儲存連接],** 將連接字串儲存在應用程式佈建檔中。

8. 選取要帶入應用程式中的資料庫物件。 在此情況下, 請在資料表中選取您想要顯示的<xref:System.Windows.Forms.TextBox>欄位。

9. 您可以視需要更換預設資料集名稱。

10. 按一下 [ **完成**]。

11. 在 [**屬性**] 視窗中, 再次按一下<xref:System.Windows.Forms.TextBox.Text%2A>屬性旁的箭號。 在 [ **DataSource** UI 類型編輯器] 中, 選取要<xref:System.Windows.Forms.TextBox>系結之欄位的名稱。

     [ **DataSource** UI 類型編輯器] 會關閉, 而且該<xref:System.Windows.Forms.BindingSource>資料連線特定的資料集和資料表介面卡會加入至您的表單。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.BindingNavigator>
- [新增資料來源](/visualstudio/data-tools/add-new-data-sources)
- [[資料來源] 視窗](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120))
