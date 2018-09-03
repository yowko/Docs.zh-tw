---
title: 如何：在選擇工具箱項目對話方塊中顯示控制項
ms.date: 03/30/2017
helpviewer_keywords:
- global assembly cache [Windows Forms], Choose Toolbox Items dialog box
- AssemblyFoldersEx [Windows Forms], Choose Toolbox Items dialog box
- controls [Windows Forms], display in Choose Toolbox Items dialog box
- assembly folder registration [Windows Forms], Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box [Windows Forms], display control
ms.assetid: 01ef6eba-d044-40f0-951d-78eff7ebd9a9
ms.openlocfilehash: fdda72d60b0f18e76b03e9b7f05060a09763a3f7
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2018
ms.locfileid: "43488257"
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a>如何：在選擇工具箱項目對話方塊中顯示控制項
當您開發並散發控制項時，您可能需要才會出現在這些控制項**選擇工具箱項目** 對話方塊中，當您以滑鼠右鍵按一下顯示**工具箱**，然後選取**選擇項目**。 您可以讓您的控制項才會出現在這個對話方塊中，使用 AssemblyFoldersEx 登錄程序。  
  
### <a name="to-display-your-control-in-the-choose-toolbox-items-dialog-box"></a>在 [選擇工具箱項目] 對話方塊中顯示您的控制項  
  
-   您的控制項組件安裝至全域組件快取。 如需詳細資訊，請參閱[How to： 將組件安裝到全域組件快取](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
  
     -或-  
  
-   使用 AssemblyFoldersEx 登錄程序中註冊您的控制項和其相關聯的設計階段組件。 AssemblyFoldersEx 是 framework 的第三方廠商在其中儲存每個支援版本的路徑的登錄位置。 設計階段解析度可以查看此登錄位置中找到參考組件。 登錄指令碼可以指定您想要出現在工具箱中的控制項。 如需詳細資訊，請參閱 <<c0> [ 部署自訂控制項和設計階段組件 (Visual Studio 2013)](https://msdn.microsoft.com/library/96158eb0-b691-4ae1-9e7b-3c65a1b798cb)。  
  
## <a name="see-also"></a>另請參閱  
 [選擇工具箱項目對話方塊 (Visual Studio)](https://msdn.microsoft.com/library/bd07835f-18a8-433e-bccc-7141f65263bb)  
 [部署自訂控制項和設計階段組件 (Visual Studio 2013)](https://msdn.microsoft.com/library/96158eb0-b691-4ae1-9e7b-3c65a1b798cb)  
 [在設計階段開發 Windows Forms 控制項](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 [操作說明：將組件安裝到全域組件快取](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
 [逐步解說：自動將自訂元件填入工具箱](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
