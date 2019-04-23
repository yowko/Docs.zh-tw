---
title: HOW TO：使用設計工具建立 Windows Forms 控制項的便捷鍵
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], access keys
- Button control [Windows Forms], access keys
- dialog box controls [Windows Forms], mnemonics
- access keys [Windows Forms], creating for controls
- mnemonics [Windows Forms], adding to dialog box controls
- ampersand character in shortcut key
- Windows Forms controls, access keys
- examples [Windows Forms], controls
- Text property [Windows Forms], specifying access keys for controls
- keyboard shortcuts [Windows Forms], creating for controls
- access keys [Windows Forms], Windows Forms
- ALT key
ms.assetid: 4c374c4c-4ca9-4a68-ac96-9dc3ab0f518a
ms.openlocfilehash: 410fc0134046c5fa7e05bfcd38ce6818244a0a54
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59307869"
---
# <a name="how-to-create-access-keys-for-windows-forms-controls-using-the-designer"></a>HOW TO：使用設計工具建立 Windows Forms 控制項的便捷鍵
*便捷鍵*是功能表、 功能表項目，或按鈕等控制項的標籤文字中加上底線的字元。 它可讓使用者 「 按一下 」 按鈕，然後按下 ALT 鍵組合中的預先定義的存取金鑰。 例如，如果按鈕會執行將表單，列印程序，因此其`Text`屬性設定為"Print"，將連字號 (&)"P"會導致字母"P"會加上底線的按鈕文字在執行階段的字母前面。 使用者可以執行命令與按鈕關聯，藉由按下 ALT + P。 您不能有無法接收焦點的控制項的便捷鍵。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-create-an-access-key-for-a-control"></a>若要建立控制項的便捷鍵  
  
1. 在 **屬性**視窗中，將`Text`屬性設為字串，包含連字號 (&) 要存取的索引鍵的字母前面。 例如，若要設定為便捷鍵的字母"P"，輸入**列印 &** 到方格內。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Button>
- [如何：回應 Windows Form Button 按一下動作](how-to-respond-to-windows-forms-button-clicks.md)
- [如何：設定所顯示之文字的 Windows Form 控制項](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [標記個別 Windows Forms 控制項並提供其捷徑](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
