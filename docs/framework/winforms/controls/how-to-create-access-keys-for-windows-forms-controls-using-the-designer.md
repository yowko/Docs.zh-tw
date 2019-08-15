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
ms.openlocfilehash: 01bed04483702ba2e62162b675aa1138bc1b0e01
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039513"
---
# <a name="how-to-create-access-keys-for-windows-forms-controls-using-the-designer"></a>HOW TO：使用設計工具建立 Windows Forms 控制項的便捷鍵
*存取金鑰*是功能表、功能表項目或控制項標籤的文字中加底線的字元, 例如按鈕。 它可讓使用者按下 ALT 鍵並結合預先定義的存取金鑰, 以「按一下」按鈕。 例如, 如果按鈕執行程式來列印表單, 因此其`Text`屬性設定為 "print", 則在字母 "p" 之前加上連字號 (&) 會在執行時間的按鈕文字中加上底線。 使用者可以按 ALT + P, 執行與按鈕相關聯的命令。 您不能擁有無法接收焦點之控制項的存取金鑰。

## <a name="to-create-an-access-key-for-a-control"></a>建立控制項的存取金鑰

1. 在 [**屬性**] 視窗中, `Text`將屬性設定為字串, 在將成為存取金鑰的字母之前包含連字號 (&)。 例如, 若要將字母 "P" 設定為存取金鑰, 請在方格中輸入 **& 列印**。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Button>
- [如何：回應 Windows Forms 按鈕點擊](how-to-respond-to-windows-forms-button-clicks.md)
- [如何：設定 Windows Forms 控制項所顯示的文字](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [標記個別 Windows Forms 控制項並提供其捷徑](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
