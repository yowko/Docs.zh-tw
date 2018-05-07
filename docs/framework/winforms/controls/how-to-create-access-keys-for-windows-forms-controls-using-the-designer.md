---
title: 如何：使用設計工具建立 Windows Form 控制項的便捷鍵
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
ms.openlocfilehash: 023973e7fa4ab1e8b802d8c7cd8abef8201ed720
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-access-keys-for-windows-forms-controls-using-the-designer"></a>如何：使用設計工具建立 Windows Form 控制項的便捷鍵
*便捷鍵*是功能表或功能表項目，例如按鈕控制項的標籤文字中加底線的字元。 它可讓使用者 「 按一下 」 按鈕，然後按下 ALT 鍵組合中的預先定義的存取金鑰。 例如，按鈕會執行程序來列印表單中，因此其`Text`屬性設定為"Print"，新增以連字號 (&)"P"字母"P"加上底線的按鈕文字會在執行期間造成的字母前面。 使用者可以執行命令與按鈕按下 ALT + P 關聯。 您不能有無法接收焦點的控制項的便捷鍵。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
### <a name="to-create-an-access-key-for-a-control"></a>若要建立控制項的便捷鍵  
  
1.  在**屬性**視窗中，將`Text`屬性為字串，包含連字號 (&) 會成為存取索引鍵的字母前面。 例如，若要將設定字母"P"的存取金鑰，請輸入 **& 列印**到方格內。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.Button>  
 [操作說明：回應 Windows Forms Button 按一下動作](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [操作說明：設定由 Windows Forms 控制項所顯示的文字](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [標記個別 Windows Forms 控制項並提供其捷徑](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
