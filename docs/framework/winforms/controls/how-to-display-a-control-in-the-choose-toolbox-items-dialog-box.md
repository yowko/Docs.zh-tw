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
ms.openlocfilehash: 56dad16b7a0bd8f0e7423b4a70e7173578150cbe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54520447"
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a>HOW TO：顯示中的控制項選擇工具箱項目對話方塊
當您開發並散發控制項時，您可能需要才會出現在這些控制項**選擇工具箱項目** 對話方塊中，當您以滑鼠右鍵按一下顯示**工具箱**，然後選取**選擇項目**。 您可以讓您的控制項才會出現在這個對話方塊中，使用 AssemblyFoldersEx 登錄程序。  
  
### <a name="to-display-your-control-in-the-choose-toolbox-items-dialog-box"></a>在 [選擇工具箱項目] 對話方塊中顯示您的控制項  
  
-   您的控制項組件安裝至全域組件快取。 如需詳細資訊，請參閱[＜How to：將組件安裝到全域組件快取](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
  
     -或-  
  
-   使用 AssemblyFoldersEx 登錄程序中註冊您的控制項和其相關聯的設計階段組件。 AssemblyFoldersEx 是 framework 的第三方廠商在其中儲存每個支援版本的路徑的登錄位置。 設計階段解析度可以查看此登錄位置中找到參考組件。 登錄指令碼可以指定您想要出現在工具箱中的控制項。 如需詳細資訊，請參閱 <<c0> [ 部署自訂控制項和設計階段組件 (Visual Studio 2013)](https://msdn.microsoft.com/library/96158eb0-b691-4ae1-9e7b-3c65a1b798cb)。  
  
## <a name="see-also"></a>另請參閱
- [選擇工具箱項目對話方塊 (Visual Studio)](https://msdn.microsoft.com/library/bd07835f-18a8-433e-bccc-7141f65263bb)
- [部署自訂控制項和設計階段組件 (Visual Studio 2013)](https://msdn.microsoft.com/library/96158eb0-b691-4ae1-9e7b-3c65a1b798cb)
- [在設計階段開發 Windows Forms 控制項](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)
- [如何：將組件安裝到全域組件快取](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)
- [逐步解說：自動填入 [工具箱] 中的以自訂元件](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
