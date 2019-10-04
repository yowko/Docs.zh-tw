---
title: HOW TO：在 [選擇工具箱項目] 對話方塊中顯示控制項
ms.date: 08/23/2019
helpviewer_keywords:
- global assembly cache [Windows Forms], Choose Toolbox Items dialog box
- AssemblyFoldersEx [Windows Forms], Choose Toolbox Items dialog box
- controls [Windows Forms], display in Choose Toolbox Items dialog box
- assembly folder registration [Windows Forms], Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box [Windows Forms], display control
ms.assetid: 01ef6eba-d044-40f0-951d-78eff7ebd9a9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 86ec8f9ae76f010ebbc3be393d8d257ba5cfc6b6
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834618"
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a>HOW TO：在 [選擇工具箱項目] 對話方塊中顯示控制項

當您開發和散發控制項時，您可能會想要讓這些控制項出現在 Visual Studio 的 [**選擇工具箱專案**] 對話方塊中，當您以滑鼠右鍵按一下 [**工具箱**] 並選取 **[選擇專案**] 時，就會顯示此對話方塊。 您可以使用 AssemblyFoldersEx 註冊程式，讓控制項出現在此對話方塊中。

若要在 [選擇工具箱專案] 對話方塊中顯示控制項：

- 將您的控制群組件安裝到全域組件快取。 如需詳細資訊，請參閱[如何：在全域組件快取中安裝單一組件](../../app-domains/install-assembly-into-gac.md)。

  -或-

- 使用 AssemblyFoldersEx 註冊程式，註冊您的控制項及其相關聯的設計階段元件。 AssemblyFoldersEx 是一個登錄位置，其中協力廠商會儲存其所支援的每個架構版本的路徑。 設計階段解決方案可以在此登錄位置尋找參考元件。 登入指令檔可指定您想要在 [工具箱] 中顯示的控制項。

## <a name="see-also"></a>另請參閱

- [在設計階段開發 Windows Forms 控制項](developing-windows-forms-controls-at-design-time.md)
- [如何：在全域組件快取中安裝單一組件](../../app-domains/install-assembly-into-gac.md)
- [逐步解說：使用自訂群組件自動填入工具箱](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
