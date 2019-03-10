---
title: HOW TO：顯示中的控制項選擇工具箱項目對話方塊
ms.date: 03/30/2017
helpviewer_keywords:
- global assembly cache [Windows Forms], Choose Toolbox Items dialog box
- AssemblyFoldersEx [Windows Forms], Choose Toolbox Items dialog box
- controls [Windows Forms], display in Choose Toolbox Items dialog box
- assembly folder registration [Windows Forms], Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box [Windows Forms], display control
ms.assetid: 01ef6eba-d044-40f0-951d-78eff7ebd9a9
ms.openlocfilehash: 191a0848d01eb043420866052b64e2284eb92b49
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720130"
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a>HOW TO：顯示中的控制項選擇工具箱項目對話方塊
當您開發並散發控制項時，您可能需要才會出現在這些控制項**選擇工具箱項目** 對話方塊中，當您以滑鼠右鍵按一下顯示**工具箱**，然後選取**選擇項目**。 您可以讓您的控制項才會出現在這個對話方塊中，使用 AssemblyFoldersEx 登錄程序。  
  
### <a name="to-display-your-control-in-the-choose-toolbox-items-dialog-box"></a>在 [選擇工具箱項目] 對話方塊中顯示您的控制項  
  
-   您的控制項組件安裝至全域組件快取。 如需詳細資訊，請參閱[如何：在全域組件快取中安裝單一組件](../../app-domains/how-to-install-an-assembly-into-the-gac.md)  
  
     -或-  
  
-   使用 AssemblyFoldersEx 登錄程序中註冊您的控制項和其相關聯的設計階段組件。 AssemblyFoldersEx 是 framework 的第三方廠商在其中儲存每個支援版本的路徑的登錄位置。 設計階段解析度可以查看此登錄位置中找到參考組件。 登錄指令碼可以指定您想要出現在工具箱中的控制項。 如需詳細資訊，請參閱 <<c0> [ 部署自訂控制項和設計階段組件](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee849818(v=vs.100))。  
  
## <a name="see-also"></a>另請參閱
- [選擇工具箱項目對話方塊 (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100))
- [部署自訂控制項和設計階段組件](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee849818(v=vs.100))
- [在設計階段開發 Windows Forms 控制項](developing-windows-forms-controls-at-design-time.md)
- [如何：在全域組件快取中安裝單一組件](../../app-domains/how-to-install-an-assembly-into-the-gac.md)
- [逐步解說：自動填入 [工具箱] 中的以自訂元件](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
