---
title: 如何：在選擇工具箱項目對話方塊中顯示控制項
ms.date: 08/23/2019
helpviewer_keywords:
- global assembly cache [Windows Forms], Choose Toolbox Items dialog box
- AssemblyFoldersEx [Windows Forms], Choose Toolbox Items dialog box
- controls [Windows Forms], display in Choose Toolbox Items dialog box
- assembly folder registration [Windows Forms], Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box [Windows Forms], display control
ms.assetid: 01ef6eba-d044-40f0-951d-78eff7ebd9a9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: db4b3ac020e967a6a0c291103d825ac71cebda23
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458278"
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a>如何：在選擇工具箱項目對話方塊中顯示控制項

當您開發和散發控制項時，您可能會想要讓這些控制項出現在 Visual Studio 的 [**選擇工具箱專案**] 對話方塊中，當您以滑鼠右鍵按一下 [**工具箱**] 並選取 **[選擇專案**] 時，就會顯示此對話方塊。 您可以使用 AssemblyFoldersEx 註冊程式，讓控制項出現在此對話方塊中。

若要在 [選擇工具箱專案] 對話方塊中顯示控制項：

- 將您的控制群組件安裝到全域組件快取。 如需詳細資訊，請參閱[如何：將組件安裝到全域組件快取](../../app-domains/install-assembly-into-gac.md)。

  -或-

- 使用 AssemblyFoldersEx 註冊程式，註冊您的控制項及其相關聯的設計階段元件。 AssemblyFoldersEx 是一個登錄位置，其中協力廠商會儲存其所支援的每個架構版本的路徑。 設計階段解決方案可以在此登錄位置尋找參考元件。 登入指令檔可指定您想要在 [工具箱] 中顯示的控制項。

## <a name="see-also"></a>請參閱

- [在設計階段開發 Windows Forms 控制項](developing-windows-forms-controls-at-design-time.md)
- [操作說明：將組件安裝到全域組件快取](../../app-domains/install-assembly-into-gac.md)
- [逐步解說：自動將自訂元件填入工具箱](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
