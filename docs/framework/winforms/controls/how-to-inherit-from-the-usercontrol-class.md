---
title: 作法：繼承 UserControl 類別
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- UserControl class [Windows Forms], inheriting from
- user controls [Windows Forms], creating
- composite controls [Windows Forms], creating
ms.assetid: 67713625-e2e4-4f6a-bce7-0855ee5043d9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7f4055c2374103b7df941d9a9bef24ed5e6cb27c
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015833"
---
# <a name="how-to-inherit-from-the-usercontrol-class"></a>作法：繼承 UserControl 類別

若要結合一或多個 Windows Forms 控制項的功能與自訂程式碼，您可以建立「使用者控制項」。 使用者控制項可結合快速控制項開發、標準 Windows Forms 控制項功能，以及自訂屬性和方法的各種用途。 當您開始建立使用者控制項時，您會看到吸引人的設計工具，您可以在其上放置標準 Windows Forms 控制項。 這些控制項會保留其所有固有功能，以及標準控制項的外觀和行為 (外觀及操作)。 不過，這些控制項一旦內建於使用者控制項，您就無法再透過程式碼使用它們。 使用者控制項會進行自己的繪製，也會處理與控制項相關聯的所有基本功能。

## <a name="to-create-a-user-control"></a>建立使用者控制項

1. 在 Visual Studio 中建立新的**Windows 控制項程式庫**專案。

   使用空白使用者控制項來建立新專案。

2. 將控制項從 [工具箱] 的 [Windows Forms] 索引標籤拖曳到您的設計工具。

3. 這些控制項的放置和設計方式應該依照您希望它們出現於最終使用者控制項的方式。 如果您想要讓開發人員存取組成控制項，您必須將它們宣告為公用，或選擇性地公開組成控制項的屬性。 如需詳細資訊，請參閱[如何：公開組成控制項](how-to-expose-properties-of-constituent-controls.md)的屬性。

4. 實作您的控制項將併入的任何自訂方法或屬性。

5. 按**F5**以建立專案, 並在**UserControl 測試容器**中執行您的控制項。 如需詳細資訊，請參閱[如何：測試 UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)的執行時間行為。

## <a name="see-also"></a>另請參閱

- [各種自訂控制項](varieties-of-custom-controls.md)
- [如何：繼承自控制項類別](how-to-inherit-from-the-control-class.md)
- [如何：繼承自現有的 Windows Forms 控制項](how-to-inherit-from-existing-windows-forms-controls.md)
- [如何：Windows Forms 的作者控制項](how-to-author-controls-for-windows-forms.md)
- [針對 Visual Basic 中的繼承事件處理常式進行疑難排解](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [如何：測試 UserControl 的執行時間行為](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
