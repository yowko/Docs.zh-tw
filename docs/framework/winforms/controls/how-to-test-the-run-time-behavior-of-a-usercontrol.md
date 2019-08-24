---
title: 作法：測試 UserControl 的執行階段行為
ms.date: 03/30/2017
helpviewer_keywords:
- UserControl class [Windows Forms], testing
- user controls [Windows Forms], testing
- composite controls [Windows Forms], testing
- UserControl Test Container
- UserControl class [Windows Forms], run-time behavior
ms.assetid: 4e4d5c49-1346-40ac-9d96-40211b573583
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1be79d52be3b5b84938d8548a8f101e965fa9dbb
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015770"
---
# <a name="how-to-test-the-run-time-behavior-of-a-usercontrol"></a>HOW TO：測試 UserControl 的執行時間行為

當您開發<xref:System.Windows.Forms.UserControl>時, 您需要測試其執行時間行為。 您可以建立個別的 Windows 應用程式專案, 並將控制項放在測試表單上, 但此程式並不方便。 更快速且更簡單的方式, 就是使用 Visual Studio 所提供的**UserControl 測試容器**。 此測試容器會直接從您的 Windows 控制項程式庫專案開始。

> [!IMPORTANT]
> 若要讓測試容器載入您<xref:System.Windows.Forms.UserControl>的, 控制項必須至少有一個公用的函式。

> [!NOTE]
> 視覺效果C++控制項無法使用**UserControl 測試容器**進行測試。

## <a name="test-the-run-time-behavior-of-a-usercontrol"></a>測試 UserControl 的執行時間行為

1. 在 Visual Studio 中, 建立 Windows 控制項程式庫專案, 並將其命名為**TestContainerExample**。

2. 在  **Windows Form 設計工具**中, 將<xref:System.Windows.Forms.Label>控制項從 **工具箱** 拖曳至控制項的設計介面上。

3. 按**F5**以建立專案, 並執行**UserControl 測試容器**。 在預覽窗格中, 測試<xref:System.Windows.Forms.UserControl>容器會與您一起顯示。

4. 選取 [ <xref:System.Windows.Forms.Control.BackColor%2A> **預覽**] 窗格右邊<xref:System.Windows.Forms.PropertyGrid>控制項中所顯示的屬性。 將其值變更為**ControlDark**。 觀察控制項是否變更為較暗的色彩。 請嘗試變更其他屬性值, 並觀察對控制項的影響。

5. 按一下**預覽**窗格下方的 [停**駐填滿使用者控制項**] 核取方塊。 觀察控制項已調整大小以填滿窗格。 調整測試容器的大小, 並觀察控制項是否隨著窗格調整大小。

6. 關閉測試容器。

7. 將另一個使用者控制項加入至**TestContainerExample**專案。

8. 在  **Windows Form 設計工具**中, 將<xref:System.Windows.Forms.Button>控制項從 **工具箱** 拖曳至控制項的設計介面上。

9. 按**F5**以建立專案並執行測試容器。

10. 按一下 [**選取使用者] 控制項**<xref:System.Windows.Forms.ComboBox> , 即可在兩個使用者控制項之間切換。

## <a name="test-user-controls-from-another-project"></a>從另一個專案測試使用者控制項

您可以在目前專案的測試容器中, 測試其他專案的使用者控制項。

1. 在 Visual Studio 中, 建立 Windows 控制項程式庫專案, 並將其命名為**TestContainerExample2**。

2. 在  **Windows Form 設計工具**中, 將<xref:System.Windows.Forms.RadioButton>控制項從 **工具箱** 拖曳至控制項的設計介面上。

3. 按**F5**以建立專案並執行測試容器。 在預覽窗格中, 測試<xref:System.Windows.Forms.UserControl>容器會與您一起顯示。

4. 按一下 [**載入**] 按鈕。

5. 在 [**開啟**] 對話方塊中, 流覽至您在上一個程式中建立的**TestContainerExample**。 選取 [ **TestContainerExample**], 然後按一下 [**開啟**] 按鈕以載入使用者控制項

6. 使用 [**選取使用者] 控制項**<xref:System.Windows.Forms.ComboBox> , 從**TestContainerExample**專案中的兩個使用者控制項之間切換。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.UserControl>
- [如何：撰寫複合控制項](how-to-author-composite-controls.md)
- [逐步解說：撰寫複合控制項](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
- [使用者控制項設計工具](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/183c3hth(v=vs.100))
